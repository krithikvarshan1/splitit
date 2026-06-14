# Squad Split — Vercel Deployment

A fully static group expense splitter. No build step required.

## Deploy to Vercel

### Option A: Vercel CLI
```bash
npm i -g vercel
vercel --prod
```

### Option B: Vercel Dashboard
1. Push this folder to a GitHub repo
2. Import the repo at vercel.com/new
3. Leave all build settings blank — Vercel auto-detects static from `outputDirectory: "public"`
4. Click Deploy

## Project structure
```
squad-split-vercel/
├── index.html   ← entire app (self-contained, no dependencies)
├── vercel.json      ← static output config
├── package.json
└── README.md
```

## Why this works
The original Lovable project used TanStack Start (SSR) + Cloudflare Workers.
Vercel doesn't support Cloudflare Workers adapter out of the box, and the original
`vercel.json` only had SPA rewrites which can't handle SSR.

This version strips the SSR layer entirely — the app is 100% client-side
(localStorage for persistence, vanilla JS, no server needed) so it works
perfectly as a static site on Vercel's CDN.
