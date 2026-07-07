# Software as Glass

**A multi-domain Next.js architecture exploring digital identity, product design, and the aesthetics of software.**

This repository serves as the unified foundation for a portfolio of interconnected web properties. Built around the concept that "Software is glass—transparent, fragile, refracting light into new forms of consciousness," it uses Next.js Host-header routing to deliver distinctly styled, high-performance web experiences from a single, maintainable codebase.

## 🌐 Properties Powered by this Architecture

- **NicholasMacAskill.com**: Personal portfolio and engineering dossier.
- **Flocano Labs**: A specialized product and venture studio.
- **Memoirs of a Multi-Disciplinary**: A digital garden and long-form content exploration.
- **Software as Glass**: The central portal and design system origin.

## 🛠️ Technology Stack

- **Framework**: Next.js (App Router), React 19, TypeScript
- **Styling**: Tailwind CSS (v4), Radix UI Primitives, Framer Motion for fluid micro-animations
- **Database**: PostgreSQL with Prisma ORM
- **AI Integration**: AI SDK for on-demand content processing and dynamic generation.
- **UI Architecture**: A custom, glassmorphism-inspired design system focusing on rich aesthetics, typography, and responsive micro-interactions.

## 🏗️ Core Concepts

### Multi-Domain Routing
Instead of maintaining separate repositories for each project, this architecture intercepts incoming requests and routes them to dedicated component trees based on the `Host` header. This allows for shared utilities, UI components, and design tokens, while maintaining completely separate public-facing brands.

### Aesthetic Focus
The UI emphasizes premium, modern web design:
- Tailored color palettes and sophisticated dark modes.
- Fluid typography utilizing Syne, Rajdhani, and Inter.
- Smooth transitions and interactive, tactile components.

## ⚙️ Running Locally

1. **Install Dependencies**: 
   ```bash
   npm install
   ```
2. **Environment Configuration**:
   Copy `.env.example` to `.env.local` and configure your database and necessary provider keys.
3. **Database Initialization**:
   ```bash
   npx prisma generate
   npx prisma db push
   ```
4. **Start Development Server**:
   ```bash
   npm run dev
   ```

*To test the multi-domain routing locally, you can map the domains to `127.0.0.1` in your local `hosts` file, allowing you to view each property exactly as it appears in production.*
