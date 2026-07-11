# Software as Glass (Private Monorepo)

**The central infrastructure and unmediated viewport powering the Nicholas MacAskill digital ecosystem.**

This repository is a Next.js multi-domain monorepo serving as the foundation for several interconnected properties. It utilizes robust Host-header routing and Vercel edge capabilities to deliver distinct web experiences from a single, unified codebase, while housing proprietary automation, AI orchestration workflows, and sovereign digital engines.

## 🌐 Architecture & Managed Domains

The application dynamically routes traffic based on the incoming `Host` header via `vercel.json` rewrites and Next.js middleware, decoupling domains from explicit project repositories:

1. **nicholasmacaskill.com**: The Terminal / Identity Layer. Centralized orchestration root utilizing multi-agent workflows (Manager-Worker pattern).
2. **flocanolabs.com**: Flocano Labs | Product Studio. A meta-interface for systemic clarity and high-velocity delivery pipelines.
3. **memoirsofamultidisciplinary.com**: A digital garden mapping the intersection of design, code, and first-principles philosophy.
4. **softwareasglass.com**: The protocol and overarching philosophical framework—collapsing the 80-tool tax into a single high-leverage operating model.
5. **Artifact Domains**: Domain-specific routing for deployed protocols and engines (e.g., `glassmetric.com`, `betbodhi.com`, `verithra.com`).

## 🛠️ Comprehensive Tech Stack

- **Core Framework**: Next.js 16 (App Router), React 19, TypeScript
- **Styling & UI**: Tailwind CSS v4, Radix UI Primitives, Framer Motion (for high-fidelity micro-animations), Zustand (state management)
- **Database & Storage**: Vercel Postgres with Prisma ORM, Supabase, SQLite (for local edge data)
- **AI Integration**: Vercel AI SDK (`@ai-sdk/google`, `@ai-sdk/openai`) for on-demand generation and Bayesian belief updating.
- **Authentication**: NextAuth.js
- **Deployment**: Vercel (Edge network, cron jobs, serverless functions)

## 🏆 Case Study Wins & Sovereign Engines

This codebase acts as the delivery pipeline for several autonomous engines and proof-of-alpha protocols. Key deployed artifacts include:

### Bet Bodhi (betbodhi.com)
- **Concept**: Sovereign Web3 arbitrage scanner executing on Polymarket.
- **Architecture**: Serverless compute mesh ingesting high-frequency sports data to generate an 'Alpha Score' against on-chain crowd prices.
- **Tech Stack**: TypeScript, Ethers.js v6, Polymarket CLOB, Node.js, Supabase.
- **Wins**: Operates completely autonomously with high edge velocity, securing true market edge without emotional interference.

### Verithra (verithra.com)
- **Concept**: The Attested Vault. A proof-of-alpha standard and liquidity layer for quant engines.
- **Architecture**: Dual-stack. Fixed-point Noir (Aztec) circuits and zkTLS over trading history. On-chain smart vaults gate deposits on cryptographic proof thresholds. 
- **Tech Stack**: Noir (Aztec), zkTLS, viem/ethers.js, Rust.
- **Wins**: Verifiable edge exposure with zero IP leakage. Proof generation remains local. 

### Glassmetric (glassmetric.com)
- **Concept**: The Momentum Matrix. Unified analytics correlating biometric readiness with financial/creative output.
- **Architecture**: A sovereign performance HUD feeding disparate streams (HRV, sleep, P&L) into a unified PostgreSQL database via Apple HealthKit.
- **Wins**: Successfully active bio-to-finance link, turning siloed metrics into calibrated intuition across 4 performance pillars.

### Bayesian Pivot (bayesianpivot.com)
- **Concept**: Dedicated framework for recursive belief updating and noise-filtration.
- **Tech Stack**: Python, Gemini API, Vertex AI, CCXT, yFinance.
- **Wins**: Sub-5ms pivot latency and a 0.92 confidence score in filtering market signal from noise.

### Flocano Labs Pipeline (flocanolabs.com)
- **Concept**: The forge for the sovereign architect.
- **Wins**: Reduced "tool tax" by 80% while increasing delivery velocity by 115% through unified orchestration.

## 🤖 Proprietary Engines & Automations

The repository also contains internal tactical data pipelines, SEO pulse testing, and social growth automations:
- **`agent:grow`**: Automated social interaction and growth engines.
- **`tiktok:pivot`**: Bayesian content syndication and predictive data pipelines.
- **`agent:boost` / `agent:pulse`**: Automated SEO monitoring and testing.
- **Multi-channel Orchestration**: Scripts for broadcast execution and automated portfolio case-study generation.

*(Note: These scripts run via `npx tsx` and rely on strict environment variable constraints in `.env.local` and `.env.social`.)*

## ⚙️ Development Setup

1. **Install Dependencies**: 
   ```bash
   npm install
   ```
2. **Environment Variables**:
   Copy `.env.example` to `.env.local` and `.env.social.example` to `.env.social`. Configure database URIs, AI provider keys (OpenAI, Google), and Vercel tokens.
3. **Database Setup**:
   ```bash
   npx prisma generate
   npx prisma db push
   ```
4. **Run Local Server**:
   ```bash
   npm run dev
   ```
   *Note: To test specific domains locally, modify your `/etc/hosts` file or use `ngrok`.*

## 🔒 OPSEC & Privacy

This is the **PRIVATE** version of the codebase. 
- Do not publicly expose the internal `social/`, `cron/`, `strategies/`, or `data/` automation scripts.
- Ensure all API tokens and cron secrets remain securely encrypted in Vercel.
- When creating a public fork, strip out proprietary execution logic and only share public API routes and structural UI components.
