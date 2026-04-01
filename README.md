# Full-Stack Website Audit

A 90-checkpoint audit skill for websites and web apps. Covers security, revenue protection, UX, performance, accessibility, SEO, privacy compliance, and infrastructure polish.

Built for solo founders, indie hackers, and developers shipping products with AI assistance. Catches the issues that vibe-coded sites consistently get wrong.

## What It Catches

**90 checkpoints across a combined full-stack + UX audit:**

### Full-Stack Audit (50 checkpoints)

| Category | What it checks |
|----------|---------------|
| Visual Design & Frontend | Typography hierarchy, colour system, layout, depth, motion |
| User Flow & UX | Hero clarity, navigation, CTAs, journey completeness, social proof |
| Responsive & Mobile | Breakpoints, touch targets, mobile typography/nav/performance |
| Performance & Web Vitals | LCP, INP, CLS, asset optimisation, caching |
| Accessibility | Semantic HTML, keyboard nav, screen reader, colour contrast, motion |
| Security (10 checks) | Secrets, client-side exposure, input validation, paywall bypass, payment replay, database access, HTTP headers, API protection, webhooks, console cleanup |
| Backend & API | API design, rate limiting, error handling, data handling, timeouts |
| SEO & Discoverability | Meta/OG tags, structured data, technical SEO, headings, social presence |
| Privacy, Legal & Compliance | Cookie consent, legal pages, data minimisation, third-party scripts, data protection registration |
| Infrastructure & Polish | Error pages, favicon/manifest, dark mode, analytics, content quality |

### UX Audit (40 checkpoints)

| Category | What it checks |
|----------|---------------|
| System Status & Feedback | Loading states, success confirmations, error communication, progress indicators, real-time validation |
| Navigation & IA | Primary nav, mobile nav, search, breadcrumbs, footer |
| User Control & Freedom | Undo/reversibility, form preservation, escape hatches, settings persistence, logout/sessions |
| Consistency & Standards | Visual consistency, language consistency, platform conventions, icon usage, responsive parity |
| Error Prevention & Forms | Input constraints, validation timing, error recovery, destructive action prevention, smart defaults |
| Empty States & Onboarding | First-time experience, empty data states, zero-data dashboards, onboarding flow, help access |
| Microcopy & Content UX | CTA clarity, labels vs placeholders, error message quality, consequence copy, microcopy consistency |
| Trust & Credibility | Social proof, transparency, security signals, professional polish, brand consistency |

## Why Security Gets 10 Checks

AI-generated code fails security more than anything else. 196 out of 198 vibe-coded apps scanned in one study had vulnerabilities. This skill specifically catches:

- **Client-side paywalls** — paid content visible in the DOM or API response before payment
- **Exposed databases** — Supabase with RLS disabled, Firebase with public read/write rules
- **Leaked secrets** — API keys in NEXT_PUBLIC_ variables, .env files committed to git
- **Payment replay** — reusing a valid payment reference to unlock multiple items
- **Webhook forgery** — payment webhooks that don't verify HMAC signatures

## Installation

### Claude Code

```bash
# Copy SKILL.md to your skills directory
cp SKILL.md ~/.claude/skills/full-stack-audit/SKILL.md
```

### Other AI Tools (Cursor, Codex, Gemini CLI)

Copy the SKILL.md file to your tool's skills directory. The SKILL.md format is cross-compatible.

### Any AI Chat (ChatGPT, Claude.ai, Gemini)

Copy the contents of SKILL.md and paste it at the start of a conversation with your codebase.

## Usage

The skill activates automatically when you ask to audit, review, or check a website. You can also invoke it directly:

```
/full-stack-audit
```

Or just say: "Audit this site", "Is this ready to launch?", "What did I miss?", "Check my security."

## How It Works

1. Reads every file in the project (not just pages — API routes, configs, env files, schemas)
2. Scores each checkpoint PASS / FAIL / N/A
3. Every FAIL includes: what's wrong, why it matters, how to fix it
4. Outputs a scorecard with priority classification (CRITICAL → HIGH → MEDIUM → LOW)
5. Fixes every failure with tagged comments (`// AUDIT FIX [X.X]`)
6. Outputs complete corrected files and a grouped changelog

## Part of the Founder Toolkit

This skill is part of a collection of open-source AI skills for founders:

- [anti-ai-slop-writing](https://github.com/jalaalrd/anti-ai-slop-writing) — Forces AI to produce human-sounding text by eliminating detectable AI writing patterns

More skills coming soon: `ux-audit`, `security-audit`, `web3-security-audit`.

## Author

Created by [Jalaaldeen](https://x.com/jalaal_tweets) — builder of Wardex, ZakatChain, and open-source AI tooling for founders.

## License

MIT
