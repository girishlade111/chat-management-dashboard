# Chat Management Dashboard

A unified, multi-platform chat management dashboard — manage customer conversations across Facebook, Instagram, and other messaging platforms from a single inbox-style interface. Built with Next.js, React, and shadcn/ui.

![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js)
![React](https://img.shields.io/badge/React-18-61DAFB?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-38B2AC?logo=tailwindcss)

## What it does

This project is a front-end dashboard for handling customer chats from multiple social platforms in one place. It includes a platform switcher, per-account inboxes, a chat thread view with message history, and a customer profile panel — a great starting point or UI reference for building a real multi-channel support/inbox product. It ships with realistic mock data so you can explore it immediately, no backend required.

## Features

- 🌐 **Multi-platform inbox** — switch between platforms (e.g. Facebook, Instagram) from a platform selector
- 👤 **Account management** — manage multiple accounts per platform, each with its own chats
- 💬 **Chat interface** — message threads with send/receive, timestamps, and scrollable history
- 📇 **Customer info panel** — view and edit customer details (name, email, phone, address, notes, online status)
- 🔍 **Search & filters** — find chats and customers quickly
- 🌓 **Dark / light mode** — theme toggle via `next-themes`
- 📱 **Responsive layout** — dashboard layout that adapts to desktop and mobile
- ⚡ **Static site** — exports to fully static HTML, deployable anywhere

## Tech stack

| Layer       | Tech                                      |
|-------------|-------------------------------------------|
| Framework   | Next.js 14 (App Router, static export)    |
| UI library  | React 18                                  |
| Language    | TypeScript 5                              |
| Styling     | Tailwind CSS 3 + `tailwindcss-animate`    |
| Components  | shadcn/ui (Radix UI primitives)           |
| Icons       | Lucide React                              |
| Data        | Local mock data (`lib/data.ts`) — no backend |

## Quick start

**Prerequisites:** Node.js 18+ and npm.

```bash
# Install dependencies
npm install

# Run the dev server
npm run dev
# Open http://localhost:3000 (main dashboard at /dashboard)
```

**Build a static site:**

```bash
npm run build
# Static output is generated in ./out — serve it with any static host
npx serve out
```

## Project structure

```
.
├── app/
│   ├── layout.tsx            # Root layout, theme provider
│   ├── page.tsx              # Landing page
│   ├── loading.tsx
│   ├── globals.css
│   └── dashboard/
│       └── page.tsx          # Main dashboard (inbox UI)
├── components/
│   ├── platform-selector.tsx # Platform switcher (Facebook, Instagram, ...)
│   ├── account-selector.tsx  # Account switcher within a platform
│   ├── chat-dashboard.tsx    # Dashboard shell/layout
│   ├── chat-interface.tsx    # Message thread + composer
│   ├── customer-info.tsx     # Customer profile panel
│   ├── theme-provider.tsx
│   └── ui/                   # shadcn/ui primitives
├── lib/
│   ├── data.ts               # Mock platforms/accounts/chats/messages
│   ├── types.ts              # Platform, Account, Chat, Customer, Message types
│   └── utils.ts
├── src/                      # Legacy standalone React (CRA-style) copy of the dashboard
├── public/                   # Static assets
├── next.config.mjs           # Static export config (output: 'export')
└── tailwind.config.js
```

> The `src/` directory holds an older standalone React (non-Next.js) version of the same dashboard — the `app/` directory is the active Next.js implementation.

## Environment variables

None required — the dashboard runs entirely client-side on mock data.

## Deployment

The app is configured with `output: 'export'`, so `npm run build` produces a static site in `out/` that can be deployed to any static host:

- **Cloudflare Pages:** `cloudflare pages_deploy chat-management-dashboard out/`
- **Vercel / Netlify / GitHub Pages:** point at the `out/` directory after `npm run build`

## Connecting a real backend (roadmap)

To turn this into a production inbox, replace `lib/data.ts` with API calls: add Next.js route handlers (or your own backend) for platforms/accounts/chats, swap the mock hooks in `components/` for `fetch`/`SWR`/`React Query`, and add auth. The component structure already mirrors a typical inbox data model.

## License

MIT — free to use and modify.

---

Built by Girish Lade · [ladestack.in](https://ladestack.in)
