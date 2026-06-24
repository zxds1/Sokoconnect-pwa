# SConnect PWA

[![Built with TypeScript](https://img.shields.io/badge/built%20with-TypeScript-3178c6?style=flat-square)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/powered%20by-Vite-646cff?style=flat-square)](https://vitejs.dev/)

> A Progressive Web App (PWA) for SConnect — a comprehensive customer-facing platform with integrated admin operations management.

## Overview

**SConnect PWA** is a modern, full-stack Progressive Web Application built with TypeScript and Vite. It provides a seamless customer experience for the SConnect ecosystem while offering a dedicated admin panel for operational workflows. The application is designed for scalability, with independent deployable components and support for multiple deployment targets (Docker, Netlify, Vercel).

### Key Features

- 📱 **Progressive Web App** – Installable, offline-capable, and mobile-optimized
- 👥 **Dual Interface** – Separate customer and admin experiences
- 🔑 **Multi-Tenant Architecture** – Support for multiple tenant configurations
- 🚀 **Modern Stack** – TypeScript, Vite, and containerized deployment
- 🎯 **Production Ready** – Netlify & Vercel deployment support
- 🐳 **Docker Support** – Local development and deployment with Docker Compose

## Repository Structure

### Apps in This Repo

- **Root App** (`/PWA`) – Main SConnect web experience for customers and sellers
- **Admin Panel** (`/PWA/admin-panel/`) – Standalone Vite app for admin and operational workflows

### Directory Layout

```
sconnect-pwa/
├── PWA/
│   ├── src/                    # Main PWA source code
│   ├── admin-panel/
│   │   └── src/                # Admin panel source code
│   ├── .env.example            # Environment template
│   ├── Dockerfile.local        # Local container image
│   └── docker-compose.local.yml # Local development setup
├── netlify.toml                # Production build configuration
└── README.md
```

## Getting Started

### Prerequisites

- Node.js 16+
- npm or yarn
- Docker & Docker Compose (optional, for containerized development)

### Main PWA Setup

From the `PWA/` directory:

```bash
npm install
npm run dev      # Start development server
npm run build    # Build for production
npm run preview  # Preview production build
npm run lint     # Run ESLint
```

### Environment Configuration

Create `PWA/.env.local` from `PWA/.env.example` and configure:

#### Required Variables

- `VITE_API_BASE_URL` – API gateway URL (Kong or custom)
  - Local development: `http://localhost:8000`

#### Optional Variables (Local Development)

- `VITE_GUEST_TENANT_ID` – Guest tenant ID for public flows (e.g., `tenant_001`)
- `VITE_TENANT_ID` – Override tenant ID for session
- `VITE_USER_ID` – Override user ID for session
- `VITE_AUTH_TOKEN` – Override authentication token
- `VITE_ROLE` – Override user role

**Example `.env.local`:**

```env
VITE_API_BASE_URL=http://localhost:8000
VITE_GUEST_TENANT_ID=tenant_001
```

## Development

### Local Docker Setup

Run the PWA container and connect to a backend already running on the host:

```bash
docker compose -f docker-compose.local.yml up -d --build
```

The app will be available at `http://localhost:3000`.

### Admin Panel

The admin panel is a separate Vite application located in `PWA/admin-panel/`.

#### Scripts

From `PWA/admin-panel/`:

```bash
npm install
npm run dev      # Start development server
npm run build    # Build for production
npm run preview  # Preview production build
```

#### Configuration

- The admin panel is intentionally separate from the main PWA for independent deployment and scaling
- Configure its API client to point to your backend gateway

## Deployment

### Netlify

The project includes a pre-configured `netlify.toml` that:
- Builds the root app with `npm run build`
- Publishes the `dist/` directory

Deploy to Netlify by connecting your repository.

### Vercel

The app is optimized for Vercel deployment. Use the homepage URL as a reference:
- **Preview:** https://sconnect-pwa.vercel.app

### Docker

For production containerization, use the provided `Dockerfile.local` as a reference.

## Project Configuration

- **Framework:** Vite (TypeScript)
- **Language:** 99% TypeScript
- **Build Output:** `dist/`
- **Default Branch:** `main`

## Available Scripts

### PWA Root

| Command | Purpose |
|---------|---------|
| `npm run dev` | Start dev server on `http://localhost:5173` |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build locally |
| `npm run lint` | Run ESLint |

### Admin Panel

| Command | Purpose |
|---------|---------|
| `npm run dev` | Start dev server |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build |

## Environment Requirements

- **API Gateway URL:** Required for all environments
- **Tenant Configuration:** Multi-tenant support for different customer organizations
- **Authentication:** Token-based session management with role support

## Contributing

1. Ensure TypeScript compilation passes
2. Run ESLint before committing
3. Test changes in Docker environment before deployment

## License

[Add license information here]

## Support

For issues, feature requests, or questions, please open an issue on this repository.

---

**SConnect PWA** is actively maintained and production-ready. For the latest updates, visit the [GitHub repository](https://github.com/zxds1/sconnect-pwa).
