# Software as Glass (Private Monorepo)
**The Central Orchestration Root & Master Artifact**

> *"Software as glass—transparent, fragile, refracting light into new forms of consciousness."*

This repository is the central orchestration root for a portfolio of sovereign architectures and deployed protocols. Built on Next.js 16, React 19, and Tailwind v4, it is an advanced, multi-domain monorepo architected not just to serve content, but to operate as a production-grade business engine. 

By collapsing the traditional "80-tool tax" into a unified, high-leverage operating model, this architecture powers multiple distinct venture brands, autonomous Web3 execution engines, and bespoke digital experiences from a single, deeply interconnected execution context.

---

## 🏛️ I. Edge Routing & Multi-Domain Architecture

This codebase acts as a centralized CI/CD and telemetry hub while serving radically different front-ends. Rather than fragmenting projects across isolated repositories with disjointed CI/CD pipelines, traffic is dynamically parsed at the edge.

### Intelligent Host-Header Routing (`src/middleware.ts`)
The custom Next.js middleware intercepts incoming `Host` headers and dynamically rewrites paths to their respective domain directories (`/src/projects/*`), sharing the same global state, Postgres database, and Vercel execution environment:

```typescript
// src/middleware.ts
export function middleware(request: NextRequest) {
  const host = request.headers.get("host") || ""
  const cleanHost = host.replace(/^www\./, "").split(":")[0].toLowerCase()

  const requestHeaders = new Headers(request.headers)
  const pathname = request.nextUrl.pathname

  const spokeSubdomains = [
    "glassmetric.com",
    "betbodhi.com",
    "verithra.com",
    "bayesianpivot.com",
    "engineeringofmomentum.com",
  ]

  // Dynamic route selection
  let activeProject = "default"
  if (pathname.startsWith("/memoirs")) {
    activeProject = "memoirs"
  } else if (pathname.startsWith("/nicholasmacaskill")) {
    activeProject = "nicholasmacaskill"
  } else if (cleanHost.includes("flocanolabs") || pathname.startsWith("/flocanolabs")) {
    activeProject = "flocanolabs"
  } else if (spokeSubdomains.includes(cleanHost)) {
    activeProject = pathname.startsWith("/flocanolabs") ? "flocanolabs" : "default"
  } else if (cleanHost.includes("nicholasmacaskill") || pathname === "/") {
    activeProject = "nicholasmacaskill"
  }

  requestHeaders.set("x-active-project", activeProject)
  requestHeaders.set("x-url-pathname", pathname)

  // Strip legacy prefixes
  if (cleanHost.includes("nicholasmacaskill.com") && pathname.startsWith("/nicholasmacaskill")) {
    const url = request.nextUrl.clone()
    url.pathname = normalizeNicholasPathname(pathname)
    return NextResponse.redirect(url, 301)
  }

  return NextResponse.next({
    request: {
      headers: requestHeaders,
    },
  })
}
```

### Decoupled Routing Layer (`vercel.json`)
The Vercel Edge configuration maps domain rewrites seamlessly to internal projects without exposing the monorepo structure to the public:
- `flocanolabs.com` / `www.flocanolabs.com` ➔ `/flocanolabs`
- `nicholasmacaskill.com` / `www.nicholasmacaskill.com` ➔ `/nicholasmacaskill`
- `glassmetric.com` ➔ `/flocanolabs/artifacts/glassmetric`
- `betbodhi.com` ➔ `/flocanolabs/artifacts/bet-bodhi`
- `verithra.com` ➔ `/flocanolabs/artifacts/verithra`

**Business Advantage**: Consolidated hosting, shared component design systems (Tailwind v4, Radix), and unified PostgreSQL telemetry under one project lifecycle, eliminating multi-repository deployment latency.

---

## 🔍 II. The "Software as Glass" Thesis (Core Philosophy)

The monorepo is engineered to reflect the **Software as Glass** manifesto—the pursuit of unmediated truth in software design. It is built on three core pillars:

1. **The "Width" Moat (Collapsing the 80-Tool Tax)**:
   In the era of zero-marginal-cost execution, depth is a liquid utility (programmable assets accessible via API). The only remaining competitive edge is **width**—integrating design, code, web3 protocols, and biological feedback loops into a single, cohesive geometry. Software as Glass collapses SaaS sprawl into unified, local-first viewports.

2. **The Bayesian Pivot (Recursive Adaptation)**:
   Vision is treated purely as a prior—a high-conviction guess designed to be updated dynamically based on real-world telemetry. If the system is not designed to be wrong initially, it can never be perfect eventually. SFT loops and real-time PnL/biometric updates continuously shape the execution parameters.

3. **Zero-Opacity Systems**:
   Interfaces must stop functioning as opaque black boxes that hide complexity. Instead, they act as transparent lenses (HUDs) reflecting the operator’s exact performance substrate, making the machine a direct extension of human intent.

---

## 🌌 III. Flocano Labs: The Glass UI & Engineering Shards

The design language of Flocano Labs abandons static web patterns in favor of **Digital Physics** and a deep "glass" aesthetic. The interface is a responsive, living HUD (Heads-Up Display) that reacts to telemetry.

### The Glass Style Matrix
The UI leverages massive computational aesthetics: `backdrop-blur-xl`, custom SVG grids, Framer Motion-based particle physics, and absolute precision typography (*Syne* + *IBM Plex Mono*). Components like `<SystemStatusCard />` act as live dashboards mapping biological and technical states into a unified view.

### Real-Time GitHub Telemetry Ecosystem
A cornerstone of the monorepo's positioning is **Engineering as Marketing**—translating live code execution and updates into a raw visual narrative. The codebase runs a three-tiered GitHub integration:

1. **The Full-Screen Observatory (`ObservatoryClient.tsx`)**:
   An immersive, terminal-themed dashboard (`/flocanolabs/observatory`) powered by a Next.js Server Action (`fetchRecentCommits`) that polls the GitHub API for pushes across all portfolio repositories.
   ```typescript
   // src/app/flocanolabs/observatory/observatory-client.tsx
   // Computes background pulse scale in real-time based on today's commit velocity:
   const intensity = 1 + Math.min(todayCount, 10) * 0.2;
   ```
   Renders custom glow filters and modular log layouts representing systemic events, providing users with a secure data uplink showing actual hourly production activity.

2. **Planetary Live Commits Orb (`LiveCommitOrb.tsx`)**:
   A floating planetary UI element positioned across Flocano layout frames. It initiates a background polling loop (every 60 seconds). When a new commit is detected on the repo:
   - Triggers an expanding **frost-white activity flash** using Framer Motion (`scale: 3, opacity: 0`).
   - Animates a glassy, rotating cloud overlay at 360 degrees as a specular-shining silver sphere.
   - Serves as an atmospheric, low-profile click-through gateway routing users directly to the Observatory dashboard.

3. **Context-Filtered Commit Feed (`CommitFeed.tsx`)**:
   Rendered directly on individual Case Study and Artifact detail pages (e.g. the Bet Bodhi or Verithra dashboards). It queries `/api/github-commits` but filters the results to only match the active asset:
   ```typescript
   // Filters commits dynamically by active project identifier while allowing core logs
   filteredCommits = fetchedCommits.filter((commit) => {
       const isSystem = ['core', 'local', 'system'].includes(commit.repo.toLowerCase());
       const matchesRepo = commit.repo.toLowerCase().includes(repoFilter.toLowerCase());
       return isSystem || matchesRepo;
   });
   ```
   Exposes relative times (`10m ago`, `3d ago`), short commit hashes, and direct link-outs to GitHub commits, proving real-time engineering iterations on each specific venture.

### The Taste Layer Page (`/flocanolabs/taste`)
The "Taste Index" (curated via `/flocanolabs/taste` and `/flocanolabs/taste/[venue]`) is an interactive, highly stylistic visual temple designed to represent the studio’s sensory architecture:
- **Atmospheric Visuals**: Built using a dynamic mix of custom grainy film overlays (`noise.svg` at 7% opacity), floating spotlight vectors (`SpotlightEffect`), and drifting digital snow (`SnowEffect`) to provide a moody, tactile texture.
- **Sensory Progression Routing**: Maps structural design and code courses (Courses I - VI, followed by Course VII: Stack Trace and Course VIII: The Cloud) like a fine-dining menu. Users trigger interactive session handshakes ("INITIATE_PROTOCOL") which adjust visual color temperatures, ambient lighting, and backdrop layouts.
- **Audio Synced Physics**: Interlinks with the client-side Tone.js generator to switch audio genres (e.g. Toronto's deep 600Hz underwater filters or London's grime patterns) depending on which venue nodes are active.

### The Bayesian Pivot Branding Page (`/flocanolabs/artifacts/bayesian` or `bayesianpivot.com`)
This dynamic artifact page serves as the public landing and proof-of-concept for the recursive belief-updating framework.
- **Live Decision Mesh**: Showcases how the underlying algorithm filters market noise from signal with a target confidence score of `0.92` and a structural pivot latency floor under `5ms`.
- **Infrastructure Auditing**: Displays live metrics (drawdown gates, ATR-swept fractals) and lists the unified Python/NumPy, Gemini, and Supabase tech stack powering the decision engine.
- **Dynamic Schema Matching**: Generates custom breadcrumb and article metadata schemas dynamically, mapping requests straight to `bayesianpivot.com` when incoming edge traffic originates from the sovereign domain redirect.

### Engineering Shards (`case-studies/page.tsx`)
The architecture maps its core engineering achievements as modular, granular "shards" that act as the structural ledger of our workspace. On the Case Studies page, the **Software as Glass Monorepo** project exposes these distinct technical shards:

- **`sag-monorepo` (Hardened Local-First Dev Workspace)**: Uses Turborepo caching hash checks and lock-free layouts to minimize compile redundancy and workspace start latency under 200ms.
- **`sag-tooling` (Dev Swarm Orchestration Tooling)**: Utilizes multi-agent manager-worker parallel orchestration to automate styling compiles and tests.
- **`sag-spoke-domain-routing` (Spoke Domain & Path Routing)**: A middleware-driven router executing host-header checks at the edge, injecting the `x-active-project` header to dynamically switch layout themes.
- **`sag-cross-project-nav` (Cross-Project Navigation Normalization)**: Normalizes client-side path prefixes and maps unified theme classes (`flocano-theme`, `memoirs-theme`) to force global footer/nav synchronization across hostname transitions.
- **`sag-identity-disambiguation` (Semantic Identity & AEO Control)**: Implements dynamic JSON-LD injection, crawler exclusions (via custom `ai.txt` and `llms.txt`), and `data-nosnippet` boundary gating to protect public search snippet outputs from terminal UI fragments.
- **`memoirs-banner-intent` (Stacked Marquee Observability Layer)**: Drives nine parallel scrolling marquee bands on the Memoirs home page, isolating crypto/sports WebSockets to prevent slow upstream APIs from freezing UI render.
- **`memoirs-polymarket-feed` (Polymarket Gamma & Activity Feed Resolver)**: Isolates moneyline contracts from Polymarket's Gamma sports feeds, implementing authenticated CLOB routing with automated public activity fallbacks.
- **`memoirs-tiered-stats-cache` (Tiered Stats Cache & Fast Route)**: Splits sports stats from live odds payloads using a fast stats route, caching PnL calculations for 300 seconds using in-flight promise deduplication.
- **`memoirs-client-polling` (Client Polling & Stale-State Merge)**: A dual-fetch loop syncing stats at 10-second intervals while merging and preserving last-known bookmaker odds if slower routes time out.

---

## 🎭 IV. Memoirs: The Narrative & Taste Layer

The Memoirs project (`memoirsofamultidisciplinary.com`) serves as the artistic and philosophical mirror to the hard engineering of the repo.

### Music & Code Telemetry (`MusicCodeBanner.tsx`)
Rather than static portfolios, Memoirs integrates live environmental, creative, and financial data feeds directly into the UI header:
- **Real-Time Trading Data Feed**: Initiates a background WebSocket connection directly to Coinbase (`wss://ws-feed.exchange.coinbase.com`), streaming real-time price updates for high-signal assets (BTC-USD, ETH-USD, SOL-USD). This is paired with a 10-second polling sequence querying the internal `/memoirs/api/market` router to fetch macro indicators (NDX, SPX, US10Y) to monitor the global financial state.
- **Sports Arbitrage & Odds Data Feed**: Hydrates baseball performance parameters dynamically. Polls `/memoirs/api/sports/odds` to display upcoming MLB moneyline markets filtered from Polymarket's Gamma endpoint. Simultaneously queries `/memoirs/api/sports/stats` to aggregate on-chain USDC.e volumes, cumulative ROI, and win-rate ratios computed via Gnosis Safe proxy addresses.
- **Generative Audio Synthesis (Tone.js)**: Feeds this live price velocity into a client-side synthesizer using Tone.js, translating market movements and scroll parameters into dynamic ambient audio keynotes (chords/LPF cutoff modifiers).

### Interactive Cognitive Tools & Progress Feeds
- **`<PropFirmTerminal />` (Live Prop Firm Progress Feed)**: A highly sophisticated, floating HUD interface mapping active prop-firm accounts in real-time. It queries `/memoirs/api/btc-pnl` to pull live trade logs, total equity watermarks, and closed-trade performance metrics directly from the **TradeLocker** backend API. Features an interactive, scrubbable SVG equity-curve chart allowing the observer to audit exact historical account growth, drawdown margins, and percentage gains interactively.
- **`<SocialOrbit />`**: Visualizes the mathematical geometry of human alignment and social resonance.

---

## 🧠 V. Advanced SEO & Answer Engine Optimization (AEO)

Discovery is engineered into the L0 root. The repo employs state-of-the-art Search Engine and Answer Engine Optimization (AEO) strategies designed explicitly for LLM ingestion (OpenAI, Perplexity, Gemini).

### Dynamic Schema Injection (`src/lib/nicholas-metadata.ts`)
Generates highly structured `JSON-LD` data injected directly into the DOM to explicitly dictate semantic relationships:
```typescript
export function getNicholasIdentityGraphSchema(overrides?: Record<string, unknown>) {
  return {
    "@context": "https://schema.org",
    "@graph": [
      {
        "@type": "WebSite",
        "@id": NICHOLAS_WEBSITE_ID,
        "name": "Nicholas Alexander MacAskill",
        "alternateName": ["Nicholas MacAskill", "The Sovereign Architect"],
        "url": NICHOLAS_CANONICAL_ORIGIN,
        "publisher": { "@id": NICHOLAS_PERSON_ID },
        "about": { "@id": NICHOLAS_PERSON_ID }
      },
      {
        "@type": "Person",
        "@id": NICHOLAS_PERSON_ID,
        "name": "Nicholas Alexander MacAskill",
        "worksFor": {
          "@type": "Organization",
          "name": "Flocano Labs",
          "url": "https://flocanolabs.com"
        },
        // Force disambiguation away from other "Nick Alexanders" or Michigan biologists
        "differentFrom": [
          {
            "@type": "Person",
            "name": "Nicholas MacAskill (Farmer Nick)",
            "jobTitle": "Conservation biologist",
            "url": "https://www.sweetwater-organic.org/an-interview-with-farmer-nick/"
          }
        ],
        "knowsAbout": [
          "Sovereign Architecture",
          "Agentic Swarms",
          "Web3 Protocols",
          "Bayesian Inference",
          "Biometric Mapping"
        ]
      }
    ]
  }
}
```

### Centralized Metadata Router (`buildNicholasMetadata`)
Guarantees high-fidelity Open Graph data, canonical linking (preventing Linktree SEO cannibalization), and rich social previews across every active domain.

### Host-Aware Dynamic Sitemaps (`src/app/sitemap.ts`)
To prevent cross-domain index pollution, duplicate content penalties, and search console fragmentation, the monorepo runs an edge-aware dynamic sitemap generator. When a search crawler hits `sitemap.xml` on any domain:
- On `nicholasmacaskill.com`: Renders only identity and portfolio pages (priority 1.0 down to 0.6).
- On `flocanolabs.com`: Renders only product studio, case studies, and artifact routes.
- On `memoirsofamultidisciplinary.com`: Dynamically fetches and maps individual blog entries (`BLOG_POSTS`) as indexable nodes.
- On sovereign spoke domains (`glassmetric.com`, `betbodhi.com` etc.): Resolves only the root domain canonical location.
This forces search engines to crawl and index content exactly under its native domain context, bypassing Next.js monorepo path leaking.

### AEO (Answer Engine Optimization) Graph Schema (`src/lib/seo-config.ts`)
Specifically engineered to feed LLM scrapers (OpenAI, Gemini, Perplexity) with structured definitions of all sovereign assets:
- Custom semantic definitions mapped inside `SEO_CONFIG.aeo` clarify definitions for softwareasglass.com, Verithra, Bet Bodhi, BayesianPivot, GlassMetric, and Nicholas Alexander MacAskill.
- Excludes crawlers from terminal HUD elements using custom boundary exclusions and selective indexing gates.
- Explicitly registers a **Verified Social Media Graph** mapping 11 distinct networks (X/Twitter, GitHub, LinkedIn, Medium, Bluesky, Instagram, Threads, Telegram, TikTok, Substack, Upwork) to establish a hardened EOA cryptographic signature matrix for Nicholas MacAskill across the web.

---

## 🎨 VI. Decoupled Brand Layouts & Design Strategy

The monorepo operates as a single codebase that maps multiple, distinct visual identities depending on the incoming edge routing header:

### The Decoupled "About" Pages Architecture
Rather than maintaining separate pages or duplicate files, the codebase utilizes a unified component schema (`<AboutProfile />`) that is dynamically hydrated with theme parameters at runtime:
- **Identity Portal (`/nicholasmacaskill/about-nicholas-macaskill`)**: Renders a high-fidelity personal portal focused on experience, code archives, and chronological venture telemetry.
- **Product Studio (`/flocanolabs/about-nicholas-macaskill`)**: Re-themes the layout into a cyber-brutalist tech studio interface, highlighting structural "Sovereign Architecture," the 80-tool tax, and agentic swarms.
- **Narrative Mirror (`/memoirs/about-nicholas-macaskill`)**: Hydrates a grainy, minimal, serif-focused layout highlighting artistic "Refractive UI," geometric resonance, and temporal sovereignty.

### Tailwind v4 Variable-Based Design Strategy (`src/app/shared-theme.css`)
Visual consistency is enforced through a centralized Tailwind CSS v4 design token ledger. The codebase maps specific typography styles directly to brand contexts using variable overrides:
- **`--font-orbitron`**: Used in Flocano's agentic swarm dashboards.
- **`--font-rajdhani`**: Used in Verithra's ZK cryptographic stats tables.
- **`--font-sovereign`**: Enforces a high-contrast serif typeface for the Memoirs narrative.
- **`--font-sans` & `--font-mono`**: Custom font pairings (*Syne* + *IBM Plex Mono*) dynamically matched to HUD layouts to represent zero-opacity telemetry.

---

## ⚙️ VII. Sovereign Business & Telemetry Engines (Backend Services)

The monorepo contains complex, background-running business services that automate media footprint management and productivity telemetry:

### 1. Cross-Platform Social Publishing & Analytics Engine (`src/lib/social/`)
A fully modular, automated engine that scales marketing footprint and collects distribution metrics:
- **API Clients Integration**: Built-in clients for Meta (Instagram, Facebook, Threads), Bluesky, Medium, and Twitter/X APIs.
- **Media Pre-Processing (`content-formatter.ts`)**: Automatic image scaling, dynamic watermarking, and aspect-ratio padding to accommodate native requirements across platforms.
- **Scheduler & Queue**: Implements an edge-scheduled queue that fetches assets from a Vercel Postgres DB, executes container uploads, and records platform response endpoints.
- **Analytics Accumulator**: Automatically polls likes, engagement rates, impressions, and saves on active posts, storing them into Postgres via Prisma schema indexes to map causal marketing links.

### 2. Bayesian Protocol Workspace & Vector Ledger (`src/projects/nicholasmacaskill/app/actions/protocol.ts`)
The private planner where daily checklist states and logs are captured:
- **Vector Embeddings**: Computes local embeddings (`embedding Float[]`) on notes to enable semantic lookup and associative search.
- **Selective Syncing Gates**: Interactive checklist status cards (`protocol-checklist.tsx`) feature explicit visibility switches (`toggleProtocolNotePublic`), letting the operator choose which workspace logs push dynamically to the public viewport.
- **Dynamic Optimization Scoring**: Measures day-over-day task clearance, momentum indexes, and biophysical drawing scores.

---

## 🏆 VIII. The Portfolio: Deployed Sovereign Engines

This monorepo serves as the backend intelligence and frontend display for several highly successful, autonomous engines:

### 1. Bayesian Pivot (`bayesianpivot.com`)
**High-Resolution Intuition Framework**
- **Architecture**: A bespoke branding layer backed by a recursive belief-updating framework. It leverages Python, Gemini API, and CCXT to filter absolute market signal from noise.
- **Wins**: Sub-5ms pivot latency and a 0.92 confidence score in adaptation modeling.

### 2. Bet Bodhi (`betbodhi.com`)
**Sovereign Web3 Arbitrage Engine**
- **Architecture**: A serverless compute mesh utilizing TypeScript, Ethers.js v6, and the Polymarket CLOB. It ingests high-frequency sports data (MLB APIs) to compute an internal *Alpha Score* against on-chain crowd prices.
- **Risk Layer (PRISM)**: Routes capital through a Psychological Risk Intelligence & Sentiment Module and automated slump circuit breakers.
- **Wins**: Completely autonomous trading logic executing with zero emotional interference. 58.2% High-Alpha Win Rate.

### 3. Verithra (`verithra.com`)
**The Attested Vault (Proof-of-Alpha)**
- **Architecture**: Dual-stack cryptography protocol. Client-side Noir (Aztec) circuits and zkTLS attest trading history (Sharpe, PnL) off-exchange. On-chain smart vaults accept pooled USDC only against the verified cryptographic scorecard.
- **Wins**: Absolute zero IP-leakage for quant developers paired with verified liquidity access.

### 4. Glassmetric (`glassmetric.com`)
**The Momentum Matrix**
- **Architecture**: Unified telemetry HUD that correlates biometric data (Apple HealthKit) with financial P&L via a Next.js and Supabase PostgreSQL matrix.
- **Wins**: Successfully mapped the causal bio-finance link, proving that a 5% shift in biological state cascades directly into decision quality.

---

## ⚙️ IX. Developer Initialization

1. **Install Dependencies**: 
   ```bash
   npm install
   ```
2. **Environment Configuration**:
   - Duplicate `.env.example` to `.env.local`.
   - Configure Vercel Postgres endpoints, AI keys (Google/OpenAI), and NextAuth secrets.
3. **Database Hydration**:
   ```bash
   npx prisma generate
   npx prisma db push
   ```
4. **Boot Sequence**:
   ```bash
   npm run dev
   ```
   *(To test distinct domains locally, modify `/etc/hosts` to point `flocanolabs.com` or `glassmetric.com` to `127.0.0.1`)*

---

## 🔒 X. OPSEC & Compliance Protocol

**Warning: PRIVATE REPOSITORY**
- Internal automations (`social/`, `cron/`, `strategies/`, `data/`) contain proprietary execution logic and alpha. **DO NOT LEAK**.
- All chron jobs and social tokens must remain entirely within encrypted Vercel Edge variables.
- The public clone of this repository (`software-as-glass-public`) must only contain structural UI, layouts, and public API interfaces. Ensure internal logic is fully stripped before upstreaming public changes.
