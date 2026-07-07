# Software as Glass 🧠💎

**An institutional-grade multi-tenant architecture for unmediated intent, digital gardens, and aesthetic software engineering.**

> *"Software is glass—transparent, fragile, refracting light into new forms of consciousness. The only remaining alpha is not found in depth, but in width."*

Software as Glass is a Next.js monorepo engineered to collapse the latency between human intent, product design, and algorithmic execution. Rather than maintaining fragmented codebases that generate cognitive entropy, this architecture serves as a single, unified operating system powering a network of distinct, high-fidelity digital properties.

---

## 🌐 The Multi-Tenant Architecture

The system utilizes Host-header interception and edge-level middleware routing to serve completely separate web experiences from a single runtime. This allows for shared utility layers, global design tokens, and synchronized database clients, while preserving total brand isolation at the edge.

```
                  ┌──────────────────────┐
                  │   Edge Middleware    │ (Host-Header Inspection)
                  └──────────┬───────────┘
                             │
         ┌───────────────────┼───────────────────┐
         ▼                   ▼                   ▼
┌────────────────┐  ┌────────────────┐  ┌────────────────┐
│ nicholasmacaskill.com │  │ flocanolabs.com │  │ memoirs...     │
│   (Portfolio & │  │ (Product &     │  │ (Digital Garden│
│   Engineering) │  │  Venture Corp) │  │  & Philosophy) │
└────────┬───────┘  └────────┬───────┘  └────────┬───────┘
         │                   │                   │
         └─────────────┬─────┴───────────────────┘
                       ▼
         ┌───────────────────────────┐
         │ Shared UI & Token Engine  │ (Tailwind v4, Radix, Lucide)
         ├───────────────────────────┤
         │ Prisma ORM & Database L0  │ (Vercel Postgres Core)
         └───────────────────────────┘
```

### Powered Properties:
1. **[nicholasmacaskill.com](https://nicholasmacaskill.com)**: Personal portfolio, canonical identity database, and professional engineering dossier.
2. **[flocanolabs.com](https://flocanolabs.com)**: Flocano Labs | Product Studio. A high-leverage venture hub and software engineering firm.
3. **[memoirsofamultidisciplinary.com](https://memoirsofamultidisciplinary.com)**: A digital sanctuary exploring the biology of software, spiritual protocols, and real-time execution telemetry.
4. **[softwareasglass.com](https://softwareasglass.com)**: The administrative portal, refraction sitemap, and overarching philosophical portal.

---

## 🛡️ The System Layers

The monorepo operates across two primary architectural layers designed to bridge biological capability with programmable scale:

### Level 0 (L0) — The Biological Substrate (The Glass Metric)
Modern technical stacks optimize cloud infrastructure but ignore the state of the human operator. Software as Glass treats human physiology as Level 0:
- **Biometric Gating**: State-aware integration (HRV, BPM, sleep architecture) acts as leading indicators of creative and execution capacity.
- **The Physiology of "Tilt"**: The architecture utilizes physiological metrics to enforce system-level guardrails, dynamically scaling execution risk and throttling complexity when sympathetic-dominant spikes are detected.
- **Statistical Séance**: Hardening the "vibe" (gut feeling) into logic by auditing biometric logs against execution outcomes to map and refine human intuition.

### Level 1 (L1) — The Summoning Layer (Agentic Swarms)
Value is no longer in writing boilerplate code or manual assets; value is in the speed of the orchestration loop:
- **Liquid Context**: Replacing isolated files with persistent context layers, acting as a digital twin of the creator's cognition.
- **Instant Summoning**: Transitioning from passive search queries to active agentic manifestation of code, assets, and layouts at marginal-cost-zero.

---

## 🎨 The Forged-Glass Design System

The visual layout is designed to feel tactile, alive, and premium. Built on Tailwind CSS (v4) and Framer Motion, it features:
- **Opaque Glass Panels**: Dynamic micro-interaction containers that adapt to light and dark modes with high-contrast borders.
- **Observatory Uplink Orb**: An interactive viewport element pinned above the mobile navigation grid, representing real-time system connection.
- **Refraction Prism**: Generative canvas and CSS particle effects (Rain, Snow, Spotlight) that dynamically map ambient conditions.
- **Prop Firm Terminal HUD**: Pinned HUD displaying mock/real execution telemetry, featuring a custom scrollable, scrubbable equity curve and live performance tracking.

---

## ⚡ Technical Optimizations & Performance

### 1. Cumulative Layout Shift (CLS) Stabilization
- **The Challenge**: Multi-domain rendering and dynamic bottom navigation bars caused minor rendering offsets on mobile viewports.
- **The Optimization**: Rebuilt the mobile bottom navigation into a standardized, CSS-grid-locked layout with predefined aspect ratios. Isolated the mobile subscribe bar to prevent vertical container pushing.
- **The Result**: Clean **0.00 CLS** across all viewports, verified via Playwright integration testing.

### 2. Multi-Domain Asset Pipeline
- Unified font architecture mapping global variables (Syne, Rajdhani, Outfit, Inter) directly to CSS roots, avoiding fallback rendering lag.
- Asset loading and routing middleware optimized to serve pages under **120ms Edge Response Time**.

### 3. Polymarket CLOB Gateway
- A built-in transaction gateway monitoring market prediction networks using central limit order book (CLOB) clients.
- Features transaction status caching, error-resilient recovery for incident logs, and event handling for outcome payouts.

---

## ⚙️ Quick Start (Local Development)

### 1. Prerequisites
- Node.js v20+
- PostgreSQL instance (or Vercel Postgres connection string)

### 2. Install Dependencies
```bash
npm install
```

### 3. Database Initialization
```bash
npx prisma generate
npx prisma db push
```

### 4. Run Development Server
```bash
npm run dev
```

To test the host-header routing locally, add the following to your `/etc/hosts` file:
```text
127.0.0.1 nicholasmacaskill.local
127.0.0.1 flocanolabs.local
127.0.0.1 memoirs.local
```
And navigate to `http://nicholasmacaskill.local:3000` to test domain isolation.

---

*Software as Glass: Built for the sovereign architects who out-scale the legacy world through the sheer structural density of their unmediated intent.*
