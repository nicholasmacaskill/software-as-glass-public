# Software as Glass (Private Monorepo)

**The Master Artifact & Unmediated Viewport**

> *"Software as glass—transparent, fragile, refracting light into new forms of consciousness."*

This repository is the central orchestration root for a portfolio of sovereign architectures and deployed protocols. Built on Next.js 16, React 19, and Tailwind v4, it is an advanced, multi-domain monorepo architected not just to serve content, but to operate as a production-grade business engine. 

By collapsing the traditional "80-tool tax" into a unified, high-leverage operating model, this architecture powers multiple distinct venture brands, autonomous Web3 execution engines, and bespoke digital experiences from a single, deeply interconnected execution context.

---

## 🏛️ High-Level System Architecture: Multi-Domain Edge Middleware

Rather than fragmenting projects across isolated repositories with disjointed CI/CD pipelines, this architecture relies on a unified backend with dynamic front-end decryption at the Vercel Edge.

### Intelligent Host-Header Routing (`src/middleware.ts`)
The custom Next.js middleware dynamically intercepts incoming `Host` headers and rewrites internal paths to their respective domain directories (`/src/projects/*`), sharing the same global state, Postgres database, and Vercel compute layer:

```typescript
// src/middleware.ts logic for Domain Routing
const host = request.headers.get("host") || "";
const cleanHost = host.replace(/^www\./, "").split(":")[0].toLowerCase();
let activeProject = "default";

if (cleanHost.includes("flocanolabs") || pathname.startsWith("/flocanolabs")) {
    activeProject = "flocanolabs"; // The Forge
} else if (spokeSubdomains.includes(cleanHost)) {
    // Spoke domains (e.g. glassmetric.com, betbodhi.com) serve distinct Flocano UI roots
    activeProject = pathname.startsWith("/flocanolabs") ? "flocanolabs" : "default";
} else if (cleanHost.includes("nicholasmacaskill") || pathname === "/") {
    activeProject = "nicholasmacaskill"; // The L0 Identity Terminal
}
```
**Business Value**: Absolute systemic clarity and massive delivery velocity. A change to foundational UI primitives or database schemas immediately cascades across 5+ distinct web properties.

---

## 🌌 Flocano Labs: The Glass UI & Engineering Shards

The design language Abandons passive web patterns in favor of **Digital Physics**. The interface is a responsive, living HUD (Heads-Up Display) that acts as a viewport into the system's telemetry.

### The Glass Style Matrix
The UI leverages massive computational aesthetics: `backdrop-blur-xl`, multi-layered linear and radial mix-blend gradients, and precision typography (Syne + IBM Plex Mono). Components like `<SystemStatusCard />` act as live dashboards mapping biological and technical states into a unified view.

### The GitHub Observatory (`ObservatoryClient.tsx`)
A prime example of **Engineering as Marketing**. The Flocano Labs Observatory integrates directly with the GitHub API via robust Next.js Server Actions, rendering commits as a cyber-styled, pulsing HUD:

```typescript
// src/app/flocanolabs/observatory/observatory-client.tsx
const data = await fetchRecentCommits();
const { commits, todayCount } = data;
const intensity = 1 + Math.min(todayCount, 10) * 0.2; // Framer Motion Pulse Scaling

<motion.div animate={{ opacity: [0.1, 0.2 * pulseIntensity, 0.1] }}>
   // HUD renders dynamic connection pulse based on daily commit velocity
</motion.div>
```
**The Value**: Visually proves high-velocity development and "Proof of Alpha." It transforms standard git history into an immersive data visualization of real-time momentum.

### Engineering Shards (`EntityData.ts`)
The architecture treats knowledge as modular "shards" rather than static pages. Data is structurally typed and mapped through recursive routing (`/philosophy/[slug]`), allowing existential principles (like the Bayesian Pivot) to be queried and interconnected dynamically as a living knowledge base.

---

## 🎭 Memoirs: The Taste Layer & Data Feeds

The Memoirs project (`memoirsofamultidisciplinary.com`) serves as the artistic and philosophical mirror to the hard engineering of the repo.

- **Music & Code Telemetry (`MusicCodeBanner.tsx`)**: Integrates live environmental and creative data feeds directly into the UI. It bridges biological and artistic data streams, proving that the code is a living extension of the architect.
- **Philosophical Encoding**: Components like `<SocialOrbit />` and `<PropFirmTerminal />` physically encode existential philosophy and the "Bayesian Pivot" framework into interactive digital art, anchoring the "Taste Layer."

---

## 🧠 Advanced SEO & Answer Engine Optimization (AEO)

Discovery is engineered into the L0 root. The repo employs state-of-the-art Search Engine and Answer Engine Optimization (AEO) strategies designed explicitly for LLM ingestion (OpenAI, Perplexity, Gemini).

### Dynamic Schema Injection (`src/lib/nicholas-metadata.ts`)
Generates highly structured `JSON-LD` data injected directly into the DOM to explicitly dictate semantic relationships:
```typescript
export function getNicholasIdentityGraphSchema() {
  return {
    "@context": "https://schema.org",
    "@graph": [
      {
        "@type": "WebSite",
        "@id": NICHOLAS_WEBSITE_ID,
        "name": "Nicholas Alexander MacAskill",
        // Forces disambiguation away from "Nick Alexander" (consultant) or "Farmer Nick"
        "differentFrom": [...NICHOLAS_DIFFERENT_FROM],
        "knowsAbout": [...NICHOLAS_EXPERTISE_STACK] // Injects Sovereign Architecture, Agentic Swarms
      }
    ]
  }
}
```
### Centralized Metadata Router (`buildNicholasMetadata`)
Guarantees high-fidelity Open Graph data, canonical linking (preventing Linktree SEO cannibalization), dynamic routing states, and rich social previews across every active domain.

---

## 🏆 The Portfolio: Deployed Sovereign Engines

This monorepo serves as the backend intelligence and frontend display for several highly successful, autonomous engines:

### 1. Bayesian Pivot (`bayesianpivot.com`)
**High-Resolution Intuition Framework**
- **Architecture**: A bespoke branding layer backed by a recursive belief-updating framework. It leverages Python, Gemini API, and CCXT to filter absolute market signal from noise.
- **Data Matrix**: Utilizes Supabase and SQLite for low-latency telemetry logging.
- **Wins**: Sub-5ms pivot latency and a 0.92 confidence score in adaptation modeling.

### 2. Bet Bodhi (`betbodhi.com`)
**Sovereign Web3 Arbitrage Engine**
- **Architecture**: A serverless compute mesh utilizing TypeScript, Ethers.js v6, and the Polymarket CLOB. It ingests high-frequency sports data (MLB APIs) to compute an internal *Alpha Score* against on-chain crowd prices.
- **Execution**: Routes capital through a Psychological Risk Intelligence & Sentiment Module (PRISM) and automated slump circuit breakers.
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

## ⚙️ Developer Initialization

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

## 🔒 OPSEC & Compliance Protocol

**Warning: PRIVATE REPOSITORY**
- Internal automations (`social/`, `cron/`, `strategies/`, `data/`) contain proprietary execution logic and alpha. **DO NOT LEAK**.
- All chron jobs and social tokens must remain entirely within encrypted Vercel Edge variables.
- The public clone of this repository (`software-as-glass-public`) must only contain structural UI, layouts, and public API interfaces. Ensure internal logic is fully stripped before upstreaming public changes.
