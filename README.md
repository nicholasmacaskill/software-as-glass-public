# Software as Glass (Private Monorepo)
**The Master Artifact & Unmediated Viewport**

> *"Software as glass—transparent, fragile, refracting light into new forms of consciousness."*

This repository is the central orchestration root for the Nicholas MacAskill digital ecosystem. It is architected as a Next.js multi-domain monorepo that collapses the traditional "80-tool tax" into a singular, high-leverage operating model. 

More than a codebase, this is a **living protocol**. It acts as an unmediated viewport, turning passive interfaces into sovereign, physics-based environments powered by continuous Bayesian updates and multi-agent AI orchestration.

---

## 🏛️ I. Architecture: Multi-Domain Edge Middleware

Rather than fragmenting projects across repositories, this architecture relies on a unified backend with decoupled, dynamic frontends. The core routing mechanism is handled at the edge.

### Host-Header Routing (`src/middleware.ts`)
The custom Next.js middleware dynamically intercepts incoming `Host` headers to route traffic into distinct sub-projects, all sharing the same state and database execution context:

- **Identity & Orchestration (`nicholasmacaskill.com`)**: Maps to `/src/projects/nicholasmacaskill`. Serves as the L0 terminal and multi-agent monitoring hub.
- **The Forge (`flocanolabs.com`)**: Maps to `/src/projects/flocanolabs`. The meta-interface and high-velocity delivery pipeline for venture architecture.
- **The Digital Garden (`memoirsofamultidisciplinary.com`)**: Maps to `/src/projects/memoirs`. A sovereign narrative layer rendering Markdown/MDX through custom physics components.
- **Spoke Domains (e.g., `glassmetric.com`, `betbodhi.com`)**: Specialized artifact domains routed directly to their respective interactive components via Vercel Rewrites, while inheriting the core Flocano design system.

This design enables **absolute systemic clarity**. A change to the foundational UI primitives immediately cascades across 5+ distinct web properties with zero redundant deployment overhead.

---

## 🌌 II. "Living" UI & Digital Physics

The interface abandons traditional, static web design in favor of **Digital Physics**. It is a responsive, living environment that reacts to user intent, utilizing advanced mathematics for micro-animations.

- **Physics-Based Rendering**: Components such as `<AgenticSwarm />`, `<FlyingBirds />`, and `<SymbioticWhirlpools />` utilize Framer Motion to create localized physics engines, ensuring elements feel tactile and alive.
- **Intent-Driven UX**: Traditional passive navigation is replaced by components like `<IntentPortal />` and `<ProtocolScheduler />`. The system assumes the user is taking action (a "Protocol") rather than just browsing.
- **Design System Matrix**: 
  - **Frameworks**: React 19, Next.js 16 (App Router)
  - **Styling**: Tailwind CSS v4, Radix UI Primitives
  - **State**: Zustand for global, low-latency UI telemetry
  - **Typography**: Bespoke integration of *Syne* and *IBM Plex Mono* to contrast structural logic with artistic fluidity.

---

## 🧠 III. Sovereign Data & The Agentic Swarm

Beneath the UI glass lies a deeply integrated, autonomous intelligence layer designed to execute logic in the background without human intervention.

- **Vercel AI SDK Integration**: Directly utilizes `@ai-sdk/google` and `@ai-sdk/openai` to power "Agentic Swarm" processing. Background workers process data, classify intent, and execute code generation workflows.
- **Edge Data Fabric**: Vercel Postgres alongside Prisma ORM provide type-safe, global data synchronization. Supabase and SQLite are leveraged for edge-local fast telemetry.
- **Proprietary Automation Pipelines**:
  - `agent:grow`: Automated social orchestration and interaction mapping.
  - `tiktok:pivot`: Bayesian content syndication predicting optimal engagement states.
  - `agent:pulse`: Autonomous SEO generation and pulse testing.

*(Note: These execution scripts remain strictly within `scripts/social` and `cron/`, bound by strict `.env.local` constraints, ensuring complete OPSEC).*

---

## 🏆 IV. Deployed Artifacts & Case Studies

This monorepo serves as the execution layer for several highly successful, sovereign digital engines:

### 1. Bet Bodhi (`betbodhi.com`)
**Sovereign Web3 Arbitrage Engine**
- **Architecture**: A serverless compute mesh that ingests high-frequency sports data (MLB APIs) to calculate true baseline probabilities. 
- **Execution**: Computes an internal *Alpha Score* against the on-chain crowd prices of Polymarket (via CLOB API).
- **Result**: High-velocity edge execution without human emotional interference. Completely autonomous trading logic.

### 2. Verithra (`verithra.com`)
**The Attested Vault (Proof-of-Alpha)**
- **Architecture**: Dual-stack cryptography protocol. Client-side Noir (Aztec) circuits and zkTLS attest trading history (Sharpe, PnL) off-exchange.
- **Execution**: On-chain smart vaults accept pooled USDC only against the verified cryptographic scorecard, never exposing the underlying quant blueprint.
- **Result**: Absolute zero IP-leakage for quant developers, paired with verified liquidity access.

### 3. Glassmetric (`glassmetric.com`)
**The Momentum Matrix**
- **Architecture**: Unified telemetry HUD that correlates biometric data (via Apple HealthKit) with financial and creative P&L. 
- **Execution**: A Next.js/Supabase architecture feeding into a unified PostgreSQL matrix.
- **Result**: successfully mapped a bio-finance link demonstrating that a 5% shift in biological state cascades directly into decision quality across four pillars.

### 4. Bayesian Pivot (`bayesianpivot.com`)
**High-Resolution Intuition Framework**
- **Architecture**: Dedicated pipeline for recursive belief updating. 
- **Execution**: Leverages Python, Gemini API, and CCXT to filter absolute market signal from noise.
- **Result**: Reached a sub-5ms pivot latency with a 0.92 confidence score in adaptation modeling.

### 5. Flocano Labs (`flocanolabs.com`)
**The Sovereign Forge**
- **Architecture**: The meta-interface orchestrating the entire stack.
- **Result**: Reduced external tool dependency (the 80-tool tax) by 80% while simultaneously increasing delivery velocity by 115%.

---

## ⚙️ V. Developer Initialization

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

## 🔒 VI. OPSEC & Compliance Protocol

**Warning: PRIVATE REPOSITORY**
- Internal automations (`social/`, `cron/`, `strategies/`, `data/`) contain proprietary execution logic and alpha. **DO NOT LEAK**.
- All chron jobs and social tokens must remain entirely within encrypted Vercel Edge variables.
- The public clone of this repository (`software-as-glass-public`) must only contain structural UI, layouts, and public API interfaces. Ensure internal logic is fully stripped before upstreaming public changes.
