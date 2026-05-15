# AGENTS.md

Guidance for any AI coding agent (Claude Code, Codex, Cursor, Windsurf, Aider, etc.) working in this repository.

## Project

Personal portfolio site for **Renz Ivan Enguio** — fullstack engineer, Philippines.

- Live: GitHub Pages (`renzivan.github.io`)
- Stack: Single-page static HTML + Tailwind CDN + vanilla JS. No build step.
- Theme: Cosmic (dark default + light mode toggle, localStorage-persisted)
- Typography: Space Grotesk (display) + Inter (body) via Google Fonts

## Files

| File | Purpose |
|------|---------|
| `index.html` | Main portfolio page (cosmic theme). Single-file build — Tailwind CDN, inline CSS, inline JS. |
| `index-legacy.html` | Previous "Hyperspace by HTML5 UP" version. Kept as archive — do not edit. |
| `elements.html`, `generic.html` | Legacy HTML5 UP demo pages. Ignore. |
| `cv.pdf` | Current CV download. |
| `images/` | Project screenshots, OG images. |
| `assets/` | Legacy theme CSS/JS — only used by `index-legacy.html`. |
| `AGENTS.md` | This file. |
| `README.md` | GitHub repo readme. |

## Key conventions

- **Single-file**: keep new design contained inside `index.html`. Do not split into separate CSS/JS files unless explicitly requested.
- **No build tooling**: no npm, no bundler, no PostCSS. Tailwind via Play CDN (`https://cdn.tailwindcss.com`).
- **Theme toggling**: light/dark via `dark` class on `<html>`. CSS variables (`--bg`, `--text`, `--accent`, etc.) drive both modes. Default to dark.
- **Cosmic visual language**: starfield, drifting nebula blobs, gradient text, glassmorphic cards (`.glass`, `.glass-strong`), glow on hover (`.glow-hover`).
- **Accessibility**: all clickable elements need `cursor-pointer`; SVG icons only (no emoji); `prefers-reduced-motion` respected.
- **Project cards** live in `<section id="work">`. Two layouts: single-col (`grid` cell), or `md:col-span-2` for featured/wide.

## Dynamic Years of Experience

**Career start date: April 2018.**

Years of experience is computed live in JS at the bottom of `index.html`:

```js
const start = new Date(2018, 3, 1); // April = month index 3
```

DOM targets:
- `.yoe` — replaced with whole-number years (e.g. `8`)
- `.yoe-plus` — replaced with `N+` (e.g. `8+`)

If editing text that mentions years of experience, wrap the number in `<span class="yoe">` or `<span class="yoe-plus">` rather than hardcoding it. Do NOT remove the IIFE that computes this.

## Content sources of truth

| Field | Source |
|-------|--------|
| Career start | April 2018 |
| Role | Fullstack engineer |
| Location | Philippines |
| Email | renzivanyapenguio@gmail.com |
| GitHub | https://github.com/renzivan |
| Discord | renzy (https://discordapp.com/users/460646553946816554) |
| CV | `cv.pdf` |

## Project list (work section)

Current order (top → bottom):

1. **E.Tel Mobile** — flagship, AU telco. Apply forms (Travel eSIM, Mobile Plans, Activate SIM) + My Account app (web, Android, iOS).
2. **Coffee Mobile** — AU mobile plan + partner-cafe rewards.
3. **Proxima** — PH services marketplace + finance tracker. Built with AI.
4. **Spondise** — Influencer marketplace. Lead frontend Jan–Sep 2023, Nuxt 3.
5. **Dotactics** — React Dota 2 tracker.
5. **Dotanerf** — Vue Dota 2 tracker.
6. **Portfolio Web Design** — Adobe XD.
7. **Flickbox App Design** — Adobe XD.

## Skill domains

| Domain | Stack |
|--------|-------|
| Frontend | HTML, CSS, JS, Vue, React, TypeScript, Tailwind, Bootstrap, shadcn/ui, Material-UI, Quasar |
| Cross-platform | Capacitor (iOS, Android) |
| Backend | Google Cloud Platform (Cloud Functions, Firebase, Storage, Scheduler, APIs), Python |
| Integrations | Google Maps, Payment Gateways (eWAY, Stripe, Square) |
| AI / Automation | Claude Code, Codex, Cursor, custom skills/agents/rules, n8n RAG (Gemini embeddings + OpenAI replies), MCP (Stripe, ClickUp), PaperclipAI orchestration |
| Tools | Git, DevOps, CI/CD (GitHub Actions), API integration, Jira, Confluence, Trello, Monday |
| Design | Adobe Photoshop, Adobe XD, Figma |

## Editing rules

1. **Preserve theme**: do not break light/dark CSS variables. Test both modes if touching color tokens.
2. **Preserve animations**: nebula, starfield, scroll-reveal, shooting stars. Don't remove unless asked.
3. **Don't introduce npm/build tools** unless explicitly requested.
4. **Don't edit `index-legacy.html`** — archive only.
5. **Don't add emojis as icons** — use inline SVG.
6. **Don't hardcode years of experience** — use `.yoe` / `.yoe-plus` spans.
7. **Keep `<head>` lean**: external dependencies allowed are Google Fonts + Tailwind CDN. No more.
8. **Project chips (`.chip`)**: short tech labels only. Avoid full sentences. Use gradient background for highlight chips (Built with AI, Flagship, Latest, etc.).

## When the user asks for a new project card

Pattern (single-col):

```html
<article class="proj-card glass rounded-3xl overflow-hidden glow-hover reveal">
  <div class="overflow-hidden">
    <img src="images/<file>" alt="<alt>" class="proj-img" loading="lazy" />
  </div>
  <div class="p-6">
    <h3 class="font-display text-2xl font-bold mb-2"><title></h3>
    <p class="text-sm text-[var(--text-mute)] mb-4"><desc></p>
    <div class="mb-4"><span class="chip">...</span></div>
    <div class="flex gap-3">
      <a href="<url>" target="_blank" rel="noopener" class="btn-cosmic btn-primary text-sm py-2 px-4">Visit Site</a>
    </div>
  </div>
</article>
```

Featured wide card uses `md:col-span-2` and a `grid md:grid-cols-2` inside.

## Deployment

Pushing to `master` deploys via GitHub Pages. No CI workflow currently. Confirm with user before commit/push.

## Commit rules

- **Never add a `Co-Authored-By` trailer for Claude, Codex, or any AI agent.** Commits must appear authored solely by the user. No `Co-Authored-By: Claude ...`, no `Co-Authored-By: noreply@anthropic.com`, no equivalent for other agents.
- No "Generated with Claude Code" footers or similar attribution lines in commit messages or PR bodies.
