# AirInk.ai
AirInk Platform
# AIRINK CLAUDE CODE EXECUTION PLAN — MASTER ORCHESTRATION

**Version:** 1.0  
**Date:** April 25, 2026  
**Status:** Complete execution plan for AirInk platform build  
**Target Launch:** Mid-May 2026 (4-6 weeks from start)

-----

## OVERVIEW

This document is your master plan for building the AirInk platform using Claude Code. It outlines 18 sequential prompts that build the complete platform from scratch — including PWA installation, haptic feedback, world-class animations, and all the features specified in the AirInk PRD.

### Critical Principles (Apply to Every Prompt)

1. **PWA-first** — Every screen works as an installed app, with offline support where relevant
1. **Mobile-first** — Design for thumbs, then scale up to desktop
1. **Haptic feedback** — Used judiciously to confirm important actions
1. **Animations** — Smooth, organic, never frantic — using Framer Motion + custom SVG
1. **Accessibility** — WCAG 2.1 AA compliance baseline, AAA where reasonable
1. **Performance** — Lighthouse score >90 across all categories
1. **Type safety** — TypeScript strict mode, Zod runtime validation
1. **Error handling** — Every async operation has explicit error states with recovery paths

-----

## EXECUTION SEQUENCE

### Phase 1: Foundation (Days 1-3)

- **PROMPT_00:** Project Foundation + PWA + Haptic Infrastructure
- **PROMPT_01:** Design System & Component Library

### Phase 2: Database & Auth (Days 3-5)

- **PROMPT_02:** Supabase Setup + Database Schema (65 tables)
- **PROMPT_03:** Authentication Flows (4 personas)

### Phase 3: Public Pages (Days 5-7)

- **PROMPT_04:** Landing Page (with AirInk visual identity)
- **PROMPT_05:** Marketing Pages (pricing, about, for vendors/clients/planners)

### Phase 4: Vendor Experience (Days 7-12)

- **PROMPT_06:** Vendor Onboarding (7-layer verification)
- **PROMPT_07:** Vendor Dashboard & Profile Management

### Phase 5: Payment Infrastructure (Days 12-19)

- **PROMPT_08:** Stripe Connect Integration + Fee Engine
- **PROMPT_09:** Contract System (creation, signing, amendments)

### Phase 6: Transaction Flows (Days 19-24)

- **PROMPT_10:** Milestone Payments & Escrow
- **PROMPT_11:** Disputes & Compassionate Coverage

### Phase 7: Client & Planner Experiences (Days 24-28)

- **PROMPT_12:** Client Experience (contract review, payments, wallet)
- **PROMPT_13:** Planner Experience (projects, multi-vendor coordination)

### Phase 8: AI & Intelligence (Days 28-33)

- **PROMPT_14:** AI Agent Infrastructure (all 17 agents)
- **PROMPT_15:** Smart Search, Recommendations, & Help System

### Phase 9: Operations (Days 33-37)

- **PROMPT_16:** Admin Dashboard & Operations Tools
- **PROMPT_17:** Notifications, Support, & Walkthroughs

### Phase 10: Launch (Days 37-42)

- **PROMPT_18:** Performance Optimization, Analytics, & Launch Prep

-----

## VALIDATION CHECKPOINTS

After each prompt, verify these criteria before proceeding:

### After PROMPT_00 (Foundation)

- [ ] `npm run dev` starts without errors
- [ ] `npm run build` completes successfully
- [ ] PWA manifest valid (test at chrome://flags/#enable-desktop-pwas)
- [ ] Service worker registered (visible in DevTools > Application > Service Workers)
- [ ] Haptic feedback fires on Android device test
- [ ] TypeScript strict mode passes with zero errors

### After PROMPT_01 (Design System)

- [ ] All brand colors render correctly (Cloud Blue, Ink Teal, Ink Navy, etc.)
- [ ] Inter font loads from local files (not Google Fonts CDN)
- [ ] Button component supports all variants (primary, secondary, ghost, destructive)
- [ ] Animations respect `prefers-reduced-motion`
- [ ] Components render correctly on mobile (375px) and desktop (1280px)
- [ ] Storybook or component playground accessible at `/_components`

### After PROMPT_02 (Database)

- [ ] All 65 tables created in Supabase
- [ ] RLS policies tested with multiple user contexts
- [ ] Database types generated and imported (`src/types/database.ts`)
- [ ] Migration files saved in `supabase/migrations/`
- [ ] Can connect to Supabase from local development

### After PROMPT_03 (Auth)

- [ ] Sign up works for all 4 personas (vendor, client, planner, admin)
- [ ] Sign in flow handles errors correctly
- [ ] Password reset works end-to-end
- [ ] Email verification flow tested
- [ ] Session persistence across page refreshes

### After PROMPT_04 (Landing Page)

- [ ] Hero section displays AirInk visual effect (air + ink dispersion)
- [ ] Animations smooth at 60fps on mobile
- [ ] All CTAs navigate correctly
- [ ] Mobile responsive at 375px, 768px, 1280px
- [ ] Lighthouse score >90 across all categories
- [ ] Page loads in <1.5s on 4G

### After PROMPT_06 (Vendor Onboarding)

- [ ] All 7 verification layers have UI flows
- [ ] Progress saved between sessions
- [ ] File uploads work (insurance COI, business license)
- [ ] Walkthrough animations engaging
- [ ] Error states helpful and recoverable

### After PROMPT_08 (Stripe Integration)

- [ ] Stripe Connect onboarding completes
- [ ] Test transaction flows work end-to-end
- [ ] Fee calculation correct across all tier/mode combinations
- [ ] Webhook handlers fire correctly
- [ ] Card-on-file authorization works

### After PROMPT_09 (Contracts)

- [ ] Contract creation from template
- [ ] AI-drafted contract generation works
- [ ] E-signature integration with RabbitSign
- [ ] Amendment flow works for all 8 types
- [ ] Multi-payor support tested

### After PROMPT_10 (Milestones)

- [ ] Milestone creation, evidence upload, approval flow
- [ ] 72-hour auto-approval works
- [ ] Escrow release logic correct
- [ ] Notifications fire at right moments

### After PROMPT_14 (AI Agents)

- [ ] All 17 agents have scope enforcement
- [ ] Haiku classifier routes correctly
- [ ] Token budgets enforce per vendor tier
- [ ] Agent responses logged for audit

### After PROMPT_18 (Launch Prep)

- [ ] Load testing at 10x expected Day 1 volume
- [ ] Error tracking via Sentry confirmed
- [ ] Analytics events firing correctly
- [ ] All env vars marked sensitive in Vercel
- [ ] 2FA enforced on infrastructure
- [ ] Production deploy successful

-----

## DEPENDENCIES BETWEEN PROMPTS

```
PROMPT_00 (Foundation)
    ↓
PROMPT_01 (Design System)
    ↓
PROMPT_02 (Database) ←──┐
    ↓                   │
PROMPT_03 (Auth)        │
    ↓                   │
PROMPT_04 (Landing) ────┘
    ↓
PROMPT_05 (Marketing Pages)
    ↓
PROMPT_06 (Vendor Onboarding) ←─ depends on Auth + Database
    ↓
PROMPT_07 (Vendor Dashboard)
    ↓
PROMPT_08 (Stripe Connect) ←─ critical path
    ↓
PROMPT_09 (Contracts) ←─ depends on Stripe + Database
    ↓
PROMPT_10 (Milestones) ←─ depends on Contracts + Stripe
    ↓
PROMPT_11 (Disputes) ←─ depends on Milestones
    ↓
PROMPT_12 (Client Experience) ←─ depends on Contracts + Milestones
    ↓
PROMPT_13 (Planner Experience)
    ↓
PROMPT_14 (AI Agents)
    ↓
PROMPT_15 (Search & Help)
    ↓
PROMPT_16 (Admin) ←─ depends on all transactional flows
    ↓
PROMPT_17 (Support & Notifications)
    ↓
PROMPT_18 (Launch Prep)
```

-----

## TECH STACK (LOCKED — DO NOT CHANGE)

### Frontend

- **Framework:** Next.js 14 (App Router, Server Components)
- **Language:** TypeScript 5+ (strict mode)
- **Styling:** Tailwind CSS 3.4+
- **Components:** shadcn/ui (Radix UI primitives) + custom AirInk components
- **Animation:** Framer Motion 11+
- **Icons:** Lucide React (strokeWidth: 1.8)
- **Forms:** React Hook Form + Zod validation
- **State:** Zustand (lightweight, no Redux)
- **Data Fetching:** TanStack Query (React Query)
- **Charts:** Recharts (for dashboards)
- **Date/Time:** date-fns
- **Notifications:** Sonner (toast library)
- **Bottom Sheets:** Vaul (mobile-native feeling)

### Backend

- **Database:** Supabase (PostgreSQL with RLS)
- **Auth:** Supabase Auth
- **Storage:** Supabase Storage (with policies)
- **Edge Functions:** Supabase Edge Functions (Deno)
- **Realtime:** Supabase Realtime (for live updates)

### Integrations

- **Payments:** Stripe Connect (Express accounts)
- **E-signature:** RabbitSign
- **AI:** Anthropic Claude API (claude-opus-4-7, claude-sonnet-4-6, claude-haiku-4-5)
- **Email:** Resend
- **SMS:** Twilio
- **Identity:** Stripe Identity
- **Fraud:** Stripe Radar + FingerprintJS Pro
- **Maps:** Google Places API (GBP verification)
- **Error Tracking:** Sentry

### PWA Stack

- **Manifest:** Custom manifest.json
- **Service Worker:** next-pwa or custom Workbox setup
- **Push:** Web Push API + service worker
- **Offline:** Background Sync API for queued actions
- **Install:** Custom install prompt UI (not browser default)

### Development Tools

- **Package Manager:** pnpm (faster, disk-efficient)
- **Linter:** ESLint with Next.js + TypeScript configs
- **Formatter:** Prettier
- **Testing:** Vitest + React Testing Library
- **E2E Testing:** Playwright
- **Git Hooks:** Husky + lint-staged

-----

## ANIMATION PRINCIPLES

These principles apply to EVERY animation in the platform:

### When to Animate

- **Always:** Page transitions, modal/sheet entries/exits, success/error confirmations
- **Often:** Hover states on interactive elements, focus transitions
- **Sometimes:** Empty states, loading states, data visualizations entering view
- **Never:** Pure decoration without value, animations that delay critical actions

### Timing Curves (Use These — Don’t Default to Linear)

```typescript
// Custom Tailwind timing functions
const timings = {
  organic: 'cubic-bezier(0.34, 1.56, 0.64, 1)',  // slight overshoot, feels alive
  flow: 'cubic-bezier(0.65, 0, 0.35, 1)',         // smooth, atmospheric
  fast: 'cubic-bezier(0.4, 0, 0.2, 1)',           // quick, professional
  enter: 'cubic-bezier(0, 0, 0.2, 1)',            // ease-out, for entrances
  exit: 'cubic-bezier(0.4, 0, 1, 1)',             // ease-in, for exits
};
```

### Duration Standards

- **Micro-interactions:** 150-250ms (hover, focus, button press)
- **State changes:** 300-400ms (toggle, form transition)
- **Page transitions:** 400-600ms (route change, modal entry)
- **Decorative:** 5-15 seconds (background ink dispersion, slow drifts)

### Reduced Motion

Every animation MUST respect `prefers-reduced-motion`:

```typescript
const prefersReducedMotion = useReducedMotion(); // Framer Motion hook
// Or via CSS:
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

-----

## HAPTIC FEEDBACK STRATEGY

### When to Use Haptics

- **Success confirmation:** Form submitted, payment completed, action confirmed
- **Important toggles:** Tier achievement, milestone approved
- **Errors:** Form validation failed, transaction declined
- **Selections:** Picker selections, swipe completions
- **NOT for:** Every button tap (gets annoying), passive notifications

### Patterns

```typescript
// src/lib/haptics.ts
export const hapticPatterns = {
  light: [10],                    // Light tap (selection)
  medium: [20],                   // Standard tap (button press)
  heavy: [40],                    // Important confirmation
  success: [20, 50, 20],          // Three-pulse celebration
  warning: [10, 30, 10, 30, 10],  // Five-pulse alert
  error: [50, 100, 50],           // Strong alert
};
```

### Platform Support

- **Android Chrome:** Full support via `navigator.vibrate()`
- **iOS Safari:** No support for Vibration API
- **iOS PWA installed:** Limited support
- **Desktop browsers:** No support (graceful degradation)

### Fallback Strategy

On unsupported platforms, replace haptic with:

- Visual pulse animation (scale 1.0 → 1.02 → 1.0 over 200ms)
- Subtle color shift on the element
- Sound (very sparingly, opt-in only)

-----

## PWA INSTALLATION STRATEGY

### Why PWA-First

- 60% lower install friction than native app stores
- Works on all devices (iOS, Android, desktop)
- Push notifications without app store approval
- Faster updates (no store review)
- Cheaper to develop and maintain
- Native apps come later (Phase 2+)

### Install Prompt Behavior

1. **First visit:** No prompt. Let user explore.
1. **Second visit:** Show subtle “Install AirInk” hint in nav.
1. **After signup:** Custom install modal (not browser default) with value props.
1. **After first contract/transaction:** Strong prompt — “Install AirInk for full experience.”
1. **Settings:** Always available in user settings.

### Install Modal Content

```
[AirInk Logo with animation]

Install AirInk on your [device]

✓ Get notifications when clients sign contracts
✓ Faster access than visiting in browser
✓ Works offline — view contracts and history anywhere
✓ Native-app feel with quick actions from home screen

[Install Now] [Maybe Later]
```

### Manifest Configuration

```json
{
  "name": "AirInk",
  "short_name": "AirInk",
  "description": "Payment platform for service businesses",
  "start_url": "/?source=pwa",
  "display": "standalone",
  "orientation": "portrait",
  "background_color": "#FAFBFD",
  "theme_color": "#3874FF",
  "icons": [/* multiple sizes */],
  "shortcuts": [
    { "name": "Create Contract", "url": "/contracts/new" },
    { "name": "Dashboard", "url": "/dashboard" },
    { "name": "Recent Payments", "url": "/payments" }
  ],
  "screenshots": [/* for install prompts */]
}
```

-----

## FILE STRUCTURE (TARGET STATE)

```
airink-platform/
├── public/
│   ├── manifest.json
│   ├── service-worker.js
│   ├── icons/                      # PWA icons (multiple sizes)
│   ├── screenshots/                # Install prompt assets
│   └── fonts/                      # Inter, JetBrains Mono (self-hosted)
│
├── src/
│   ├── app/                        # Next.js App Router
│   │   ├── (public)/               # Public routes
│   │   │   ├── page.tsx            # Landing
│   │   │   ├── pricing/
│   │   │   ├── for-vendors/
│   │   │   ├── for-clients/
│   │   │   └── for-planners/
│   │   │
│   │   ├── (auth)/                 # Auth flows
│   │   │   ├── signin/
│   │   │   ├── signup/
│   │   │   └── reset-password/
│   │   │
│   │   ├── (vendor)/               # Vendor app
│   │   │   ├── onboarding/
│   │   │   ├── dashboard/
│   │   │   ├── contracts/
│   │   │   ├── clients/
│   │   │   ├── payments/
│   │   │   └── settings/
│   │   │
│   │   ├── (client)/               # Client app
│   │   │   ├── dashboard/
│   │   │   ├── contracts/
│   │   │   ├── wallet/
│   │   │   └── vault/
│   │   │
│   │   ├── (planner)/              # Planner app
│   │   │   ├── projects/
│   │   │   ├── vendors/
│   │   │   └── templates/
│   │   │
│   │   ├── (admin)/                # Admin tools
│   │   │   ├── disputes/
│   │   │   ├── verifications/
│   │   │   ├── support/
│   │   │   └── analytics/
│   │   │
│   │   ├── api/                    # API routes
│   │   │   ├── webhooks/
│   │   │   │   ├── stripe/
│   │   │   │   └── rabbitsign/
│   │   │   ├── ai/
│   │   │   └── ...
│   │   │
│   │   ├── layout.tsx              # Root layout
│   │   └── globals.css             # Global styles
│   │
│   ├── components/
│   │   ├── ui/                     # shadcn/ui components
│   │   ├── animations/             # Animation components
│   │   │   ├── InkBloom.tsx
│   │   │   ├── AirParticles.tsx
│   │   │   └── PageTransition.tsx
│   │   ├── forms/                  # Form components
│   │   ├── dashboard/              # Dashboard-specific
│   │   ├── pwa/
│   │   │   ├── InstallPrompt.tsx
│   │   │   └── OfflineIndicator.tsx
│   │   └── ...
│   │
│   ├── lib/
│   │   ├── supabase/
│   │   │   ├── client.ts
│   │   │   ├── server.ts
│   │   │   └── admin.ts
│   │   ├── stripe/
│   │   ├── anthropic/
│   │   │   ├── classifier.ts
│   │   │   └── agents/
│   │   ├── haptics.ts              # Haptic feedback utility
│   │   ├── animations.ts           # Animation primitives
│   │   ├── pwa.ts                  # PWA helpers
│   │   ├── analytics.ts
│   │   └── utils.ts
│   │
│   ├── hooks/
│   │   ├── useHaptic.ts
│   │   ├── useInstallPrompt.ts
│   │   ├── useOnlineStatus.ts
│   │   ├── useReducedMotion.ts
│   │   ├── useVendor.ts
│   │   ├── useClient.ts
│   │   └── ...
│   │
│   ├── types/
│   │   ├── database.ts             # Generated from Supabase
│   │   ├── api.ts
│   │   └── ...
│   │
│   └── styles/
│       ├── tokens.css              # Design tokens
│       └── animations.css          # Custom keyframes
│
├── supabase/
│   ├── migrations/                 # SQL migrations
│   ├── functions/                  # Edge functions
│   └── seed.sql
│
├── tests/
│   ├── e2e/                        # Playwright
│   └── unit/                       # Vitest
│
├── .env.local
├── package.json
├── tailwind.config.ts
├── tsconfig.json
├── next.config.js
└── README.md
```

-----

## ENVIRONMENT VARIABLES (Complete List)

```env
# Supabase
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=

# Stripe
STRIPE_SECRET_KEY=
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=
STRIPE_WEBHOOK_SECRET=
STRIPE_CONNECT_CLIENT_ID=

# Anthropic
ANTHROPIC_API_KEY=

# RabbitSign
RABBITSIGN_API_KEY=
RABBITSIGN_WEBHOOK_SECRET=

# Email (Resend)
RESEND_API_KEY=
RESEND_FROM_EMAIL=noreply@airink.ai

# SMS (Twilio)
TWILIO_ACCOUNT_SID=
TWILIO_AUTH_TOKEN=
TWILIO_PHONE_NUMBER=

# Google Cloud (Places API)
GOOGLE_CLOUD_API_KEY=
GOOGLE_CLOUD_PROJECT_ID=

# FingerprintJS Pro
NEXT_PUBLIC_FINGERPRINTJS_KEY=
FINGERPRINTJS_SECRET_KEY=

# Tyler's Notifications
TYLER_PHONE=
TYLER_EMAIL=

# Sentry
SENTRY_DSN=
NEXT_PUBLIC_SENTRY_DSN=

# Analytics
NEXT_PUBLIC_POSTHOG_KEY=
NEXT_PUBLIC_POSTHOG_HOST=

# App
NEXT_PUBLIC_APP_URL=https://airink.ai
NEXT_PUBLIC_VAPID_PUBLIC_KEY=     # For web push
VAPID_PRIVATE_KEY=                 # For web push
```

**Critical:** Mark ALL of these as “Sensitive” in Vercel. Per the Vercel breach lesson, anything not marked sensitive could be exposed.

-----

## EXECUTION INSTRUCTIONS

### Before Starting Claude Code

1. Open Terminal
1. Create project directory: `mkdir airink-platform && cd airink-platform`
1. Initialize git: `git init`
1. Ensure Node.js 20+ installed: `node --version`
1. Install pnpm: `npm install -g pnpm`
1. Have your AirInk logo files ready in `assets/` directory
1. Have all environment variable values in your password manager

### Starting Each Prompt

For each prompt:

1. **Read the prompt fully** before pasting to Claude Code
1. **Copy the entire prompt content** (don’t truncate)
1. **Paste into Claude Code** as a new task
1. **Monitor execution** — answer clarifying questions promptly
1. **Verify against validation checklist** before proceeding to next prompt
1. **Commit to git** after each successful prompt: `git add . && git commit -m "feat: complete PROMPT_XX"`
1. **Push to GitHub** at least daily

### When Prompts Encounter Errors

Claude Code may hit errors. Standard recovery:

1. **Read the error message carefully** — most are descriptive
1. **Let Claude Code attempt fixes** — usually it can self-correct
1. **If stuck after 3 attempts:** Provide the error context to a new Claude Code session
1. **For database errors:** Check Supabase logs, RLS policies, type generation
1. **For Stripe errors:** Use Stripe test mode, check webhook logs in dashboard
1. **For build errors:** Run `pnpm install` to ensure dependencies fresh

### Rollback Strategy

After each successful prompt, you have a clean git commit. If a subsequent prompt corrupts things:

```bash
# Check status
git status

# Discard uncommitted changes
git checkout .

# Or revert to specific commit
git revert <commit-hash>

# Or hard reset (destructive — only if certain)
git reset --hard <commit-hash>
```

Always commit before starting a new prompt. Always.

-----

## SUCCESS METRICS

You’ll know the build is on track when:

### Week 1

- [ ] PROMPT_00, 01, 02, 03 complete
- [ ] Auth working end-to-end for all 4 personas
- [ ] Landing page deployed at airink.ai
- [ ] PWA installable on iOS and Android
- [ ] Haptic feedback firing on supported devices

### Week 2

- [ ] PROMPT_04, 05, 06, 07 complete
- [ ] Vendor onboarding flow functional (all 7 layers)
- [ ] Vendor dashboard live
- [ ] Visual identity locked across all pages

### Week 3

- [ ] PROMPT_08, 09 complete
- [ ] Stripe Connect onboarding works
- [ ] Test transactions process successfully
- [ ] Contract creation and signing functional

### Week 4

- [ ] PROMPT_10, 11, 12, 13 complete
- [ ] Milestone payments work end-to-end
- [ ] Disputes flow tested
- [ ] Client and planner experiences live

### Week 5

- [ ] PROMPT_14, 15, 16 complete
- [ ] All 17 AI agents deployed
- [ ] Admin dashboard operational
- [ ] First 10 pilot vendors onboarded in staging

### Week 6

- [ ] PROMPT_17, 18 complete
- [ ] Production deploy
- [ ] First real transaction processed
- [ ] **LAUNCH**

-----

## WHAT COMES NEXT

The next 18 documents in this folder are the actual prompts. Execute them in order:

- PROMPT_00_FOUNDATION.md
- PROMPT_01_DESIGN_SYSTEM.md
- PROMPT_02_DATABASE.md
- PROMPT_03_AUTH.md
- PROMPT_04_LANDING.md
- PROMPT_05_MARKETING.md
- PROMPT_06_VENDOR_ONBOARDING.md
- PROMPT_07_VENDOR_DASHBOARD.md
- PROMPT_08_STRIPE.md
- PROMPT_09_CONTRACTS.md
- PROMPT_10_MILESTONES.md
- PROMPT_11_DISPUTES.md
- PROMPT_12_CLIENT.md
- PROMPT_13_PLANNER.md
- PROMPT_14_AI_AGENTS.md
- PROMPT_15_SEARCH_HELP.md
- PROMPT_16_ADMIN.md
- PROMPT_17_NOTIFICATIONS.md
- PROMPT_18_LAUNCH.md

Each prompt is self-contained. Execute in order. Commit after each. Don’t skip ahead.

**Build something exceptional.**
