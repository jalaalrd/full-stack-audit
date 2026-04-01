---
name: full-stack-audit
description: "Comprehensive website and web app audit covering security, UX, performance, accessibility, SEO, compliance, and revenue protection. Use this skill whenever the user asks to audit, review, check, or score a website or web application. Also use when the user says 'full-stack audit', 'UX audit', 'security audit', 'launch checklist', 'is my site ready to launch', 'check my site', 'review my code for issues', 'what did I miss', or any variation of wanting a comprehensive quality review before or after launch. This skill catches the issues that AI-built and vibe-coded sites consistently get wrong: client-side paywalls, exposed database tables, missing security headers, broken mobile layouts, and trust gaps that kill conversion. Triggers even if the user only asks about one area (e.g., 'check my security') because problems compound across categories."
---

# Full-Stack Website Audit

A 90-checkpoint audit for websites and web apps. Covers security, revenue protection, UX, performance, accessibility, SEO, compliance, and infrastructure. Designed for solo founders, indie hackers, and developers shipping products built with AI assistance.

## Before Starting

1. Read every file in the project. Not just the pages — read API routes, middleware, config files, environment examples, database schemas, and package.json.
2. Check the live site if a URL is provided. Open it in a browser and test the actual user flow.
3. Do NOT ask the user questions. Audit everything, score every checkpoint, then report.

## How Scoring Works

Each checkpoint is PASS, FAIL, or N/A. Every FAIL must include:
- What's wrong (specific, not vague)
- Why it matters (impact on users, security, or revenue)
- How to fix it (concrete steps, not general advice)

Score each category, then total. Categories with N/A items: adjust denominator.

---

## PART 1: FULL-STACK AUDIT (50 checkpoints)

### CATEGORY 1: VISUAL DESIGN & FRONTEND (5 checks)

1.1 **Typography hierarchy**
FAIL if there's no clear distinction between headings, body, and labels. FAIL if more than 2 font families are used without reason. FAIL if font sizes are inconsistent across similar elements.
PASS requires: Clear heading/body/label hierarchy. Maximum 2 font families. Consistent sizing system.

1.2 **Colour system**
FAIL if colours are hardcoded throughout instead of using CSS variables or a theme. FAIL if the palette has more than 5 colours with no system. FAIL if it looks like a default template.
PASS requires: CSS variables or theme tokens for all colours. Intentional palette with primary, secondary, accent, muted, and danger colours.

1.3 **Layout and composition**
FAIL if the layout is a single centred column with no visual interest. FAIL if spacing is inconsistent between sections.
PASS requires: Intentional layout choices (grid, asymmetry, full-bleed elements). Consistent spacing system.

1.4 **Backgrounds and depth**
FAIL if the site is flat with no visual depth (no shadows, borders, or surface variation). FAIL if depth is overdone (excessive shadows, gradients everywhere).
PASS requires: Shadow hierarchy (sm, md, lg). Surface elevation for cards and interactive elements.

1.5 **Motion and interactions**
FAIL if there are no hover states or transitions. FAIL if animations play with no way to disable them. FAIL if CSS animations are used in contexts where they won't render (e.g., programmatic video).
PASS requires: Hover/focus states on interactive elements. prefers-reduced-motion support. Transitions feel intentional.

### CATEGORY 2: USER FLOW & UX (5 checks)

2.1 **Hero and first impression**
FAIL if a new visitor can't understand what the product does within 5 seconds. FAIL if there's no clear call-to-action above the fold. FAIL if there's no "How It Works" or explanation section.
PASS requires: Value proposition visible immediately. CTA above the fold. Explainer section (e.g., 3-step process).

2.2 **Navigation and information architecture**
FAIL if navigation has more than 7 items. FAIL if current page has no active state. FAIL if labels are ambiguous.
PASS requires: 5-7 nav items max. Active state on current page. Clear labels.

2.3 **Conversion flow and CTAs**
FAIL if CTAs use generic text ("Submit", "Click Here"). FAIL if primary and secondary CTAs look identical.
PASS requires: CTAs describe action and outcome ("Analyze My Profile", not "Submit"). Primary CTA visually dominant. Secondary CTA visually subordinate.

2.4 **Journey completeness**
FAIL if any async action (form submit, payment, API call) has no loading state. FAIL if success states are missing. FAIL if errors show raw technical messages.
PASS requires: Loading states with contextual messages. Success confirmations. Plain-language errors with recovery suggestions.

2.5 **Trust and social proof**
FAIL if there's zero social proof (no testimonials, user counts, or reviews). FAIL if testimonials are generic or clearly fake. FAIL if social proof is positioned far from the decision point (CTA/payment).
PASS requires: Real social proof near the CTA. Testimonials with names and verifiable source. N/A only for pre-launch with zero users.

### CATEGORY 3: RESPONSIVE & MOBILE (5 checks)

3.1 **Responsive breakpoints** — Grids and layouts adapt. No horizontal scroll.
3.2 **Touch targets** — All interactive elements 44px minimum.
3.3 **Mobile typography** — Readable without zooming. 14px minimum body text.
3.4 **Mobile navigation** — Functional on mobile. Hamburger or adapted layout.
3.5 **Mobile performance** — No heavy unoptimised images. Lazy loading where needed.

### CATEGORY 4: PERFORMANCE & WEB VITALS (5 checks)

4.1 **LCP (Largest Contentful Paint)** — Font preloading, critical CSS, no render-blocking resources.
4.2 **INP (Interaction to Next Paint)** — No heavy synchronous computation on user actions.
4.3 **CLS (Cumulative Layout Shift)** — No layout shifts from late-loading content.
4.4 **Asset optimisation** — Images compressed, SVG for icons, no unnecessary large bundles.
4.5 **Caching and CDN** — Static assets cached. CDN for global distribution.

### CATEGORY 5: ACCESSIBILITY (5 checks)

5.1 **Semantic HTML** — Correct use of header, nav, main, footer, section, article. ARIA roles where needed.
5.2 **Keyboard navigation** — All interactive elements reachable via Tab. :focus-visible styles.
5.3 **Screen reader support** — aria-live for dynamic content. aria-label on icon-only buttons. Form labels.
5.4 **Colour accessibility** — Text contrast meets WCAG AA (4.5:1 normal, 3:1 large). Don't rely on colour alone.
5.5 **Motion and cognitive** — prefers-reduced-motion disables animations. No auto-playing media.

### CATEGORY 6: SECURITY (10 checks)

**This is where AI-built sites fail most often. Check every item carefully.**

6.1 **Secret management**
FAIL if API keys, database credentials, or payment secret keys are in client-side code. FAIL if secrets are committed to git history. FAIL if .env files are in the repo.
PASS requires: All secrets in server-side environment variables only. .env in .gitignore. No secrets in NEXT_PUBLIC_ or VITE_ prefixed variables (except public keys designed to be public like Paystack public key).

6.2 **Client-side secrets exposure audit**
FAIL if NEXT_PUBLIC_, VITE_PUBLIC_, or equivalent variables contain anything that should be secret. FAIL if the Supabase anon key is exposed AND Row Level Security is not enabled.
PASS requires: Audit every NEXT_PUBLIC_ variable. Verify each one is genuinely safe to expose. Document why each is public.

6.3 **Input validation and sanitisation**
FAIL if AI/LLM output is rendered with dangerouslySetInnerHTML without sanitising script tags and event handlers. FAIL if user input is inserted into queries without sanitisation.
PASS requires: All dynamic HTML output sanitised. No raw user input in database queries.

6.4 **Server-side paywall (CRITICAL for paid products)**
FAIL if paid content is sent to the browser before payment is verified. FAIL if the paywall is implemented with CSS (blur, overlay, display:none) while the full content exists in the DOM or API response. FAIL if the payment callback sets a client-side flag (like isPaid=true) without server verification. FAIL if the payment error handler unlocks content anyway ("catch: setIsPaid(true)").
PASS requires: Paid content stored server-side (database). API returns only teaser/preview before payment. Full content only returned after server-side payment verification. Payment failure does NOT unlock content.

**This is the #1 revenue-critical issue in AI-built paid products. The natural pattern when building fast is: generate content → send to client → hide behind a paywall UI. This NEVER works. Anyone with browser DevTools can read the full response. The only secure pattern is: generate content → store server-side → return teaser only → verify payment server-side → then return full content.**

6.5 **Payment replay protection**
FAIL if a valid payment reference can be reused to unlock multiple items. FAIL if the verify endpoint doesn't check if a reference was already used.
PASS requires: Each payment reference can only unlock one item. Server checks for duplicate references before unlocking.

6.6 **Database security (RLS / public access)**
FAIL if database tables are publicly readable or writable. FAIL if Supabase has RLS disabled on tables containing user data. FAIL if Firebase/Firestore rules allow public read/write.
PASS requires: Row Level Security enabled on all tables with user data. No public policies unless intentionally public data. Service role key used only server-side.

**Supabase with RLS disabled means anyone with your project URL can read, edit, and delete all data. This is a critical vulnerability that Supabase will email you about, but many builders ignore the warning.**

6.7 **HTTP security headers**
FAIL if missing: Content-Security-Policy, X-Frame-Options, Strict-Transport-Security, X-Content-Type-Options, Referrer-Policy.
PASS requires: All five headers set via middleware or server config.

6.8 **API route protection**
FAIL if API routes accept requests from any origin with no rate limiting. FAIL if authenticated endpoints don't verify the session/token.
PASS requires: Rate limiting on expensive endpoints (especially AI/LLM calls). CORS restrictions or origin checking where appropriate.

6.9 **Webhook security**
FAIL if payment/service webhooks don't verify signatures. FAIL if webhooks blindly trust the request body.
PASS requires: HMAC signature verification on all webhooks (Paystack, Stripe, etc.). N/A if no webhooks.

6.10 **Production console cleanup**
FAIL if console.log statements expose sensitive data (payment references, user emails, API responses) in the browser console.
PASS requires: No sensitive data in browser console.log statements. Server-side logging is fine.

### CATEGORY 7: BACKEND & API QUALITY (5 checks)

7.1 **API design** — Consistent naming, proper HTTP methods, appropriate status codes.
7.2 **Rate limiting** — Expensive operations (AI calls, payments) rate-limited per IP.
7.3 **Error handling** — Errors caught, logged server-side, sanitised messages to client.
7.4 **Data handling** — Unicode sanitised for database storage. Large inputs truncated. File uploads size-limited.
7.5 **Timeout configuration** — Serverless function timeouts set appropriately for long operations (AI calls need 30-60s, not the 10s default).

### CATEGORY 8: SEO & DISCOVERABILITY (5 checks)

8.1 **Meta and Open Graph** — Title, description, og:image, Twitter cards.
8.2 **Structured data** — JSON-LD schema appropriate for the content type.
8.3 **Technical SEO** — Canonical URL, robots.txt, sitemap.xml, lang attribute.
8.4 **Heading structure** — Single H1, logical hierarchy.
8.5 **Social presence** — Social media links accessible from the site.

### CATEGORY 9: PRIVACY, LEGAL & COMPLIANCE (5 checks)

**Regulators now fine for cookie consent violations specifically. SHEIN paid €150M in September 2025 for a "Reject All" button that didn't actually stop tracking. Three new US state privacy laws took effect January 2026. This category is not optional.**

9.1 **Cookie consent**
FAIL if analytics, advertising, or third-party scripts fire before the user has given consent. FAIL if there's no cookie banner and the site uses tracking cookies. FAIL if the "Reject" button is visually smaller, lighter, or harder to find than "Accept" (this is a dark pattern — regulators fine for it). FAIL if consent choices aren't logged with timestamps.
PASS requires: No non-essential scripts fire before consent. Accept and Reject buttons have equal visual weight. Consent logged. Banner respects choice on return visits. N/A only for sites with zero cookies and zero third-party scripts.

9.2 **Legal pages**
FAIL if there's no privacy policy. FAIL if the privacy policy doesn't match what the site actually collects (says "we don't track" but loads Google Analytics). FAIL if there's no Terms of Service. FAIL if legal pages are unreachable from the footer.
PASS requires: Privacy policy accessible from every page (footer link). Policy accurately describes all data collection, storage, and third-party sharing. Terms of Service present. Both contain real content, not placeholder text.

9.3 **Data minimisation**
FAIL if forms collect more data than needed (asking for phone number on a newsletter signup). FAIL if there's no way for users to request deletion of their data.
PASS requires: Forms collect only necessary fields. Data deletion mechanism exists (email, form, or automated). For GDPR: data processing purpose stated at point of collection.

9.4 **Third-party script audit**
FAIL if third-party scripts are loaded without being disclosed in the privacy policy. FAIL if third-party scripts load additional nested trackers not documented anywhere. FAIL if external scripts from CDNs lack Subresource Integrity (SRI) hashes.
PASS requires: All third-party scripts inventoried. Privacy policy discloses all third-party data processors. External scripts use SRI where possible.

9.5 **Data protection registration**
FAIL if serving UK users and not registered with ICO when thresholds are met. FAIL if processing 200+ Nigerian data subjects and not registered with NDPC. FAIL if serving EU users with no GDPR-compliant data processing documentation.
PASS requires: Registered with relevant authority if thresholds met. Data processing purposes documented. N/A for pre-launch or personal projects with no real user data.

### CATEGORY 10: INFRASTRUCTURE & POLISH (5 checks)

**These are the "last 5%" items that separate a prototype from a product. Vibe coders skip all of them.**

10.1 **Error pages**
FAIL if navigating to a non-existent URL shows the default framework error (Next.js 404, Vite white screen, browser default). FAIL if server errors show raw stack traces or framework defaults to users. FAIL if empty states (zero-data dashboards, empty search results, empty lists) show a blank screen.
PASS requires: Custom 404 page with navigation back to the site. Custom 500/error page with a user-friendly message. Empty states with helpful messaging and a CTA.

10.2 **Favicon and manifest**
FAIL if there's no favicon (blank browser tab). FAIL if using the default framework favicon (Next.js black triangle, Vite lightning bolt). FAIL if there's no apple-touch-icon for iOS bookmarks. FAIL if there's no web manifest for PWA readiness.
PASS requires: Custom favicon.ico (32x32). Apple-touch-icon (180x180). Web manifest (manifest.json or manifest.webmanifest) with 192x192 and 512x512 icons. Theme colour set.

10.3 **Dark mode**
FAIL if the site is dark by default but flashes white on load before CSS applies. FAIL if dark mode exists but has contrast issues (dark text on dark backgrounds, invisible borders). FAIL if a dark mode toggle exists but doesn't persist across sessions.
PASS requires: No white flash on load for dark-themed sites (handle at CSS level or with a blocking script). If supporting both modes, persist user choice. All colour pairings tested in both modes. N/A if single-theme with no flash issues.

10.4 **Analytics and monitoring**
FAIL if there's no analytics installed (no way to measure traffic or conversions). FAIL if analytics is installed but not tracking key conversion events (signups, payments, wallet connections). FAIL if there's no error monitoring (Sentry, LogRocket, or equivalent). FAIL if analytics fires before cookie consent.
PASS requires: Analytics tracking pageviews and key conversions. Error monitoring configured for production. Analytics respects consent settings.

10.5 **Content quality**
FAIL if any page contains placeholder text ("Lorem ipsum", "Coming soon", "TBD", "[Insert text here]"). FAIL if there are spelling or grammar errors on key pages (homepage, pricing, about). FAIL if body content contains broken or outdated links. FAIL if the site has broken images or unstyled fallback states visible to users.
PASS requires: No placeholder text on the live site. Clean copy on all key pages. All links working. All images loading. No visible broken states.

---

## PART 2: UX AUDIT (40 checkpoints)

### CATEGORY 1: SYSTEM STATUS & FEEDBACK (5 checks)

1.1 **Loading states** — Every async action shows contextual loading (not just "Loading..."). Buttons disable during processing. No double-submit possible.
1.2 **Success confirmations** — Every completed action (payment, form submit) shows visible inline confirmation. Persists 3-6 seconds or is dismissible.
1.3 **Error communication** — Plain language. Recovery suggestion included. Positioned near the source. No silent failures.
1.4 **Progress indicators** — Multi-step flows show step count. Long operations show progress or status messages.
1.5 **Real-time feedback** — Required fields validated on submit with specific field names. File uploads show filename confirmation.

### CATEGORY 2: NAVIGATION & IA (5 checks)

2.1 **Primary navigation** — Active state, clear labels, consistent across pages.
2.2 **Mobile navigation** — Functional hamburger or adapted layout. Auto-close on selection.
2.3 **Search** — Available if 10+ content items. "No results" message if empty. N/A for simple sites.
2.4 **Breadcrumbs** — Back navigation on pages 2+ levels deep. N/A for single-page apps.
2.5 **Footer** — Legal links, contact info, social links. Cohesive design.

### CATEGORY 3: USER CONTROL & FREEDOM (5 checks)

3.1 **Undo and reversibility** — Destructive actions require confirmation with clear language. "Delete" and "Keep", not "OK" and "Cancel".
3.2 **Form preservation** — Warning before navigating away from unsaved form data. Validation errors preserve correct fields.
3.3 **Escape hatches** — Modals closeable via Escape, X button, and backdrop click. Multi-step flows have back/cancel options.
3.4 **Settings persistence** — User preferences persist across sessions. N/A if no settings.
3.5 **Logout and sessions** — Visible logout option. Session expiry shows clear message. N/A if no auth.

### CATEGORY 4: CONSISTENCY & STANDARDS (5 checks)

4.1 **Visual consistency** — Same element types look the same across pages. One primary button style.
4.2 **Language consistency** — Same concept uses same term everywhere. Consistent CTA labels.
4.3 **Platform conventions** — Links visually distinct. External links indicate they leave the site. Form inputs have visible borders and focus states.
4.4 **Icon usage** — Non-universal icons have text labels. Same icon means same thing everywhere.
4.5 **Responsive consistency** — Features available on desktop are available on mobile. Content priority maintained.

### CATEGORY 5: ERROR PREVENTION & FORMS (5 checks)

5.1 **Input constraints** — type="email" for email, type="number" for numbers. Dropdowns for constrained choices. Max length on limited fields.
5.2 **Validation timing** — Required fields validated on blur or submit with specific messages. Email format validated on blur, not every keystroke.
5.3 **Error recovery** — Page scrolls to first error. All errors shown simultaneously. Errors persist until corrected.
5.4 **Destructive action prevention** — Confirmation dialogs on destructive actions. Destructive button visually distinct (red/warning colour).
5.5 **Smart defaults and autofill** — autocomplete attributes on standard fields (name, email, phone). Smart defaults where obvious.

### CATEGORY 6: EMPTY STATES & ONBOARDING (5 checks)

6.1 **First-time experience** — New user sees guidance, not a blank screen. Key features discoverable without docs.
6.2 **Empty data states** — Lists and tables have designed empty states with helpful CTA.
6.3 **Zero-data dashboard** — Charts show placeholder state, not broken visuals. N/A if no dashboard.
6.4 **Onboarding** — Skippable. Progress indicator if multi-step. Only essential info collected. N/A if no onboarding.
6.5 **Help access** — At least one help access point visible (email, FAQ, docs link, chat).

### CATEGORY 7: MICROCOPY & CONTENT UX (5 checks)

7.1 **CTA clarity** — CTAs describe action and outcome. User knows what happens before clicking.
7.2 **Labels vs placeholders** — Every field has a persistent visible label. Placeholders are supplementary.
7.3 **Error message quality** — Specific and instructive ("Password must be at least 8 characters", not "Invalid password"). Different errors get different messages.
7.4 **Consequence copy** — Destructive dialogs state the consequence. Irreversible actions flagged before clicking.
7.5 **Microcopy consistency** — One term per concept. Consistent tone. No AI-generated filler.

### CATEGORY 8: TRUST & CREDIBILITY (5 checks)

8.1 **Social proof** — Real testimonials near the CTA (not buried in the footer). Verifiable source. Specific, not generic.
8.2 **Transparency** — Team/founder info accessible. Pricing transparent. Legal pages findable.
8.3 **Security signals** — Trust badges near sensitive actions (payments, data collection). "Secured by [provider]" or "Your data is encrypted" near forms.
8.4 **Professional polish** — No spelling errors on key pages. No placeholder content. No broken images.
8.5 **Brand consistency** — Logo consistent across pages. Colour palette consistent. Site feels like one cohesive product.

---

## STEP 2: REPORT

Output the scorecard in this exact format:

```
═══════════════════════════════════════════════════════════════════
FULL-STACK AUDIT RESULTS
═══════════════════════════════════════════════════════════════════

CATEGORY 1: VISUAL DESIGN & FRONTEND          SCORE: X/5
  1.1  Typography:             [PASS/FAIL] — reason
  ...

[All 10 categories with all 50 checkpoints]

FULL-STACK TOTAL: XX/50

═══════════════════════════════════════════════════════════════════
UX AUDIT RESULTS
═══════════════════════════════════════════════════════════════════

CATEGORY 1: SYSTEM STATUS & FEEDBACK           SCORE: X/5
  1.1  Loading States:          [PASS/FAIL] — reason
  ...

[All 8 categories with all 40 checkpoints]

UX TOTAL: XX/40

═══════════════════════════════════════════════════════════════════
COMBINED SCORE: XX/90

CRITICAL (blocks launch / loses money):  [count] — [checkpoint numbers]
HIGH (users will struggle):              [count] — [checkpoint numbers]
MEDIUM (users will notice):              [count] — [checkpoint numbers]
LOW (nice to have):                      [count] — [checkpoint numbers]

TOP 5 PRIORITIES:
  1. ...
  2. ...
  3. ...
  4. ...
  5. ...
═══════════════════════════════════════════════════════════════════
```

### Priority Classification Rules

CRITICAL = any of these:
- Paid content accessible without payment (6.4)
- Database publicly readable/writable (6.6)
- Secrets exposed client-side (6.1, 6.2)
- No HTTPS or broken payment flow
- Third-party scripts firing before cookie consent in EU/UK-serving sites (9.1)

HIGH = any of these:
- No rate limiting on AI/LLM endpoints (6.8)
- No loading states on async actions (1.1 in UX)
- Serverless timeout too short for AI calls (7.5)
- No error handling on payment verification

MEDIUM = everything else that's FAIL
LOW = items that are N/A-adjacent or cosmetic

---

## STEP 3: FIX

Fix every FAIL in priority order: CRITICAL → HIGH → MEDIUM → LOW.

Tag every fix with a comment: `// AUDIT FIX [X.X]: brief description`

### Fix Rules

- Output complete corrected files, NOT diffs or snippets.
- Preserve ALL existing functionality.
- Follow the project's existing framework conventions.
- For microcopy fixes, match the site's existing tone.
- When adding loading/success/error states, implement the full UI component.
- For security fixes, implement the server-side solution, not a client-side workaround.

### Fix Guidance by Category

**SECURITY (fix these first, they lose money or expose data):**
- Paywall bypass: Move paid content to database storage. API returns teaser only. Full content returned only after server-side payment verification.
- Database exposure: Enable RLS. Create zero public policies. Use service role key server-side only.
- Secret exposure: Move to server-side env vars. Audit every NEXT_PUBLIC_ variable.
- Payment replay: Check if reference was already used before unlocking.

**UX:**
- Loading states: Add contextual messages, disable buttons, prevent double-submit.
- Success states: Inline confirmation that persists 3-6 seconds.
- Error states: Plain language, recovery suggestion, positioned near source.
- Social proof: Position near CTA, not in footer or header. Link to verifiable source.

**PERFORMANCE:**
- Timeout: Set maxDuration on serverless routes that call AI APIs.
- Fonts: Preconnect, font-display:swap.
- Images: Compress, lazy load, use SVG for icons.

**SEO:**
- Add meta tags, OG image, JSON-LD schema.
- Create robots.txt and sitemap.xml.
- Submit to Google Search Console.

**PRIVACY & LEGAL:**
- Cookie consent: Add a banner with equal-weight Accept/Reject buttons. Block non-essential scripts until consent. Log consent with timestamps.
- Legal pages: Scaffold privacy policy and terms of service with [FILL IN] markers for content requiring human/legal review. Never fabricate legal text. Link from footer.
- Third-party scripts: Inventory all scripts, add SRI hashes, disclose in privacy policy.

**INFRASTRUCTURE & POLISH:**
- Error pages: Create custom 404 with nav links and search/home button. Create custom 500 with friendly message.
- Favicon: Generate favicon set (favicon.ico, apple-touch-icon, manifest icons) or flag as TODO with exact specs.
- Dark mode: Add prefers-color-scheme media query or blocking script to prevent white flash.
- Analytics: Flag missing analytics with setup instructions. Do not install tracking without consent mechanism.
- Content: Flag placeholder text and broken links for human review.

---

## STEP 4: OUTPUT

For each corrected file, output:
1. File path
2. Comment block listing addressed checkpoints
3. Complete corrected code

Output a CHANGELOG at the end grouped by priority (CRITICAL → HIGH → MEDIUM → LOW).

### Constraints

- Do NOT change business logic, core features, or branding.
- Do NOT remove features or sections.
- DO keep everything within the existing tech stack.
- DO prioritise fixes that address multiple checkpoints at once.
- When writing microcopy, match the existing site tone.
- When in doubt, add a comment flagging the issue for human review.
- NEVER implement a client-side-only paywall. If the product charges money, the paid content MUST be gated server-side.
- NEVER leave database tables without access controls, even during development.
- ALWAYS ask for URLs, tweet links, or external references rather than guessing them.
