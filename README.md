# Software as Glass (Private Monorepo)
**The Master Artifact & Unmediated Viewport**

> *"Software as glass—transparent, fragile, refracting light into new forms of consciousness."*

This repository is the central orchestration root for the Nicholas MacAskill digital ecosystem. Built on Next.js 16, React 19, and Tailwind v4, it is an advanced, multi-domain monorepo architected not just to serve content, but to operate as a **living, sovereign business engine**. 

By collapsing the traditional "80-tool tax" into a unified, high-leverage operating model, this architecture powers multiple distinct brands, autonomous Web3 execution engines, and bespoke digital experiences from a single, deeply interconnected execution context.

---

## 🏛️ I. Edge Routing & Multi-Domain Architecture

This codebase acts as a centralized CI/CD and telemetry hub while serving radically different front-ends. Rather than fragmenting projects across isolated repositories, traffic is dynamically parsed at the edge.

### Intelligent Host-Header Routing (`src/middleware.ts`)
The custom Next.js middleware intercepts incoming `Host` headers and dynamically rewrites paths to their respective domain directories (`/src/projects/*`), all while sharing the same global state, Postgres database, and Vercel execution environment:

- **Identity Layer (`nicholasmacaskill.com`)**: The L0 terminal and multi-agent monitoring hub.
- **The Forge (`flocanolabs.com`)**: The meta-interface and high-velocity delivery pipeline for venture architecture.
- **The Digital Garden (`memoirsofamultidisciplinary.com`)**: A sovereign narrative and philosophical taste layer.
- **Artifact Spoke Domains (e.g., `glassmetric.com`, `bayesianpivot.com`)**: Specialized artifact domains routed directly to their interactive components via `vercel.json` rewrites.

**Business Value**: Zero redundant deployment overhead. A change to foundational UI primitives or global SEO metadata immediately cascades across 5+ distinct web properties, ensuring perfect brand consistency and massive delivery velocity.

---

## 🌌 II. Flocano Labs: The Glass UI & Live Telemetry

The design language Abandons static web patterns in favor of **Digital Physics** and a deep "glass" aesthetic. The interface is a responsive, living HUD (Heads-Up Display) that reacts to telemetry.

### The Glass Style & System Status
The UI leverages heavy use of `backdrop-blur`, complex multi-layered linear and radial gradients, and absolute precision typography (Syne + IBM Plex Mono). Components like `<SystemStatusCard />` act as live dashboards mapping biological and technical states into a unified view.

### The GitHub Observatory (`ObservatoryClient.tsx`)
A prime example of engineering as marketing. The Flocano Labs Observatory page integrates directly with the GitHub API via robust Next.js Server Actions (`fetchRecentCommits`). 
- **The UI**: Renders commits as a cyber-styled, pulsing HUD with live data uplinks.
- **The Value**: Visually proves high-velocity development and "Proof of Alpha" in real-time. It transforms a standard git history into a compelling, immersive data visualization.

### Engineering Shards (`EntityData.ts`)
The architecture treats knowledge as modular "shards." Instead of static pages, data is structurally typed and mapped through recursive routing (`philosophy/[slug]`), allowing existential principles and engineering concepts to be interconnected and queried dynamically.

---

## 🎭 III. Memoirs: The Taste Layer & Data Feeds

The Memoirs project serves as the artistic and philosophical mirror to the hard engineering of the repo.

- **Music & Code Telemetry (`MusicCodeBanner.tsx`)**: Integrates live environmental and creative data feeds directly into the UI. It bridges biological and artistic data streams, proving that the code is a living extension of the architect.
- **Philosophical Encoding**: Components like `<SocialOrbit />` and `<PropFirmTerminal />` physically encode existential philosophy and the "Bayesian Pivot" framework into interactive digital art.

---

## 🧠 IV. SEO, AEO & Answer Engine Optimization

Discovery is engineered directly into the root level. The repo employs state-of-the-art Search Engine and Answer Engine Optimization (AEO) strategies designed for LLM ingestion:

- **Dynamic Schema Injection**: Utilities like `getNicholasPersonSchema()` inject highly structured JSON-LD data directly into the DOM, ensuring LLMs (OpenAI, Google) perfectly map the semantic relationship between the architect, Flocano Labs, and the deployed artifacts.
- **Centralized Metadata (`buildNicholasMetadata`)**: Guarantees high-fidelity Open Graph data, canonical linking, dynamic routing states, and rich social previews across every single active domain.

---

## 🏆 V. The Portfolio: Deployed Sovereign Engines

This monorepo serves as the backend intelligence and frontend display for several highly successful, autonomous engines:

### 1. Bayesian Pivot (`bayesianpivot.com`)
**High-Resolution Intuition Framework**
- **Architecture**: A bespoke branding layer backed by a recursive belief-updating framework. It leverages Python, Gemini API, and CCXT to filter absolute market signal from noise.
- **Wins**: Sub-5ms pivot latency and a 0.92 confidence score in adaptation modeling.

### 2. Bet Bodhi (`betbodhi.com`)
**Sovereign Web3 Arbitrage Engine**
- **Architecture**: A serverless compute mesh utilizing TypeScript, Ethers.js v6, and the Polymarket CLOB. It ingests high-frequency sports data to compute an internal *Alpha Score* against on-chain crowd prices.
- **Wins**: Completely autonomous trading logic executing with zero emotional interference.

### 3. Verithra (`verithra.com`)
**The Attested Vault (Proof-of-Alpha)**
- **Architecture**: Dual-stack cryptography protocol. Client-side Noir (Aztec) circuits and zkTLS attest trading history off-exchange. On-chain smart vaults accept pooled USDC only against the verified cryptographic scorecard.
- **Wins**: Absolute zero IP-leakage for quant developers paired with verified liquidity access.

### 4. Glassmetric (`glassmetric.com`)
**The Momentum Matrix**
- **Architecture**: Unified telemetry HUD that correlates biometric data (Apple HealthKit) with financial P&L via a Next.js and Supabase PostgreSQL matrix.
- **Wins**: Successfully maps the causal bio-finance link, proving that a 5% shift in biological state cascades directly into decision quality.

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
