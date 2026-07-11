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

## 🌌 II. Flocano Labs: The Glass UI & Engineering Shards

The design language of Flocano Labs abandons static web patterns in favor of **Digital Physics** and a deep "glass" aesthetic. The interface is a responsive, living HUD (Heads-Up Display) that reacts to telemetry.

### The Glass Style Matrix
The UI leverages massive computational aesthetics: `backdrop-blur-xl`, custom SVG grids, Framer Motion-based particle physics, and absolute precision typography (*Syne* + *IBM Plex Mono*). Components like `<SystemStatusCard />` act as live dashboards mapping biological and technical states into a unified view.

### The GitHub Observatory (`ObservatoryClient.tsx`)
A prime example of **Engineering as Marketing**. The Flocano Labs Observatory integrates directly with the GitHub API via Next.js Server Actions, rendering commits as a cyber-styled, pulsing HUD:

```typescript
// src/app/flocanolabs/observatory/observatory-client.tsx
export default function ObservatoryClient() {
    const [entries, setEntries] = useState<LogEntry[]>([]);
    const [pulseIntensity, setPulseIntensity] = useState(1);

    useEffect(() => {
        const load = async () => {
            const data = await fetchRecentCommits(); // Server Action
            const { commits, todayCount } = data;
            
            // Dynamic pulse based on daily commit density
            const intensity = 1 + Math.min(todayCount, 10) * 0.2;
            setPulseIntensity(intensity);
            setEntries(commits);
        };
        load();
    }, []);

    return (
        <motion.div
            animate={{
                opacity: [0.1, 0.2 * pulseIntensity, 0.1],
                scale: [0.8, 1, 0.8]
            }}
            transition={{ duration: 4 / pulseIntensity, repeat: Infinity }}
            className="w-[40vw] h-[40vw] bg-brand-blue/10 blur-[100px] rounded-full"
        />
    );
}
```

### Engineering Shards & The Knowledge Base (`EntityData.ts`)
The architecture treats knowledge as modular "shards" rather than static pages. Data is structurally typed and mapped through recursive routing (`/philosophy/[slug]`), allowing existential principles and engineering concepts to be queried and interconnected dynamically as a living knowledge base.

Key structural shards in Flocano include:
- `orchestration`: Active-state agent swarms that operate with wide-spectrum autonomy.
- `automation`: Invisible cognitions that remove the 80-tool tax, collapsing multi-step processes.
- `verithra`: Proving Sharpe/PnL off-chain via Aztec Noir zk-circuits prior to liquidity release.
- `rapid-refraction`: Our 48-hour sprint framework designed to liquidate legacy business friction.

---

## 🎭 III. Memoirs: The Narrative & Taste Layer

The Memoirs project (`memoirsofamultidisciplinary.com`) serves as the artistic and philosophical mirror to the hard engineering of the repo.

### Music & Code Telemetry (`MusicCodeBanner.tsx`)
Rather than static portfolios, Memoirs integrates live environmental and creative data feeds directly into the UI header:
```typescript
// src/projects/memoirs/components/MusicCodeBanner.tsx
// Integrates live browser and code telemetry (drawdowns, active file paths, Tone.js synthesis)
// to bridge biological and artistic streams in real-time.
```

### Interactive Cognitive Tools
- `<SocialOrbit />`: Visualizes the mathematical geometry of human alignment and social resonance.
- `<PropFirmTerminal />`: A simulated terminal mapping the trader's cognitive edge, psychological "tilt" thresholds, and recovery curves.

---

## 🧠 IV. Advanced SEO & Answer Engine Optimization (AEO)

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

---

## 🏆 V. The Portfolio: Deployed Sovereign Engines

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

## ⚙️ VI. Developer Initialization

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

## 🔒 VII. OPSEC & Compliance Protocol

**Warning: PRIVATE REPOSITORY**
- Internal automations (`social/`, `cron/`, `strategies/`, `data/`) contain proprietary execution logic and alpha. **DO NOT LEAK**.
- All chron jobs and social tokens must remain entirely within encrypted Vercel Edge variables.
- The public clone of this repository (`software-as-glass-public`) must only contain structural UI, layouts, and public API interfaces. Ensure internal logic is fully stripped before upstreaming public changes.
