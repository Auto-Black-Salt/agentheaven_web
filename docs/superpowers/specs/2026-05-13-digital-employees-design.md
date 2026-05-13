# AgentHeaven — Digital Employees Pivot

**Date:** 2026-05-13
**Status:** Design approved, pending implementation plan
**Scope:** Business plan + landing page rebuild

---

## 1. Positioning

**One-line:**
> AgentHeaven is the flat-fee AI workforce for SMBs. We set up, host, and quietly improve a digital employee that handles the repetitive work you keep meaning to delegate.

**Sub-line (Day 1 → Day 90 arc):**
> Start fast with a capable generalist. We turn it into your specialist.

**Tone:** Outsource-the-boring-work. Lead with the customer's pain. Calm, confident, slightly understated. "We've shipped enterprise systems for 20 years" — not "we're AI-native disruptors."

---

## 2. Ideal Customer Profile

- 5–50 employees
- Owner-operator or small ops/marketing team that is overwhelmed
- Already uses cloud tools (Gmail/Outlook, a CRM, a helpdesk, a shared drive)
- EU first: Hungary, Germany, English-speaking EU (matches existing HU/DE/EN locales)
- Currently considering a part-time hire for a repetitive role but can't justify the salary or recruiting overhead

---

## 3. The Offer

One generic, self-improving AI employee, **configured and continuously tuned by the AgentHeaven team**. Subscription tiers vary by how many hours of human tuning are included per month.

1. **Configured by us** — discovery call → we configure the Hermes Agent harness for the customer's job → connect their tools → write the runbook
2. **Continuously tuned by us** — depth scales with tier; we adjust prompts, memory, routing, and tool access weekly or monthly
3. **Hosted on our infrastructure** — agent runtime on EU VPS; LLM routed to the best-fit model per task (open-source self-hosted or frontier API). **Customer pays nothing for compute or tokens.**
4. **Self-improving** — memory + feedback loop. Thumbs-up/down and corrections feed the agent's memory. No fine-tuning at launch.
5. **Day 1 → Day 90 journey** — launches as a capable generalist; grows into the customer's specialist as feedback accumulates and we tune.
6. **Flat fee, cancel anytime** — no annual lock-in at launch; we earn renewal.

**Explicitly NOT:**
- Not a website chatbot widget (chat may be a feature of some roles, not the product)
- Not a self-serve "agent platform" — the customer never configures anything
- Not unlimited — each agent has one defined job, not "do anything"

---

## 4. Featured Role Examples (Landing Page)

These are illustrative — the actual product is one configurable employee. Six examples shown on the page:

1. **Repetitive task assistant** — data entry, weekly reports, copying info between tools
2. **Research assistant** — market/competitor research, lead enrichment, summarizing briefs
3. **Inbox & triage assistant** — sorts emails, drafts replies, flags what matters
4. **Customer support agent** — handles FAQs and tickets, escalates the rest
5. **Internal knowledge assistant** — answers team questions from internal docs/SOPs
6. **Ops / back-office assistant** — reconciles invoices, vendor follow-ups, order processing

---

## 5. Pricing

Three flat-monthly tiers. No setup fee. Cancel anytime. Onboarding via consultation call.

| Tier | Price | Tuning hours included | Connected tools | Best for |
|---|---|---|---|---|
| **Starter** | **€299/mo** | 1 hr / mo | 1 source | Trying it; light repetitive tasks |
| **Specialist** ★ | **€699/mo** | 3 hr / mo | up to 5 | Most customers — real role replacement |
| **Workforce** | **€1,499/mo** | 8 hr / mo + dedicated specialist | unlimited + custom | Deep specialist, mission-critical |

Specialist is the highlighted "most popular" tier. Each tier's CTA button is *"Book a call to start"* — onboarding goes through a consultation, not direct self-serve checkout at launch.

---

## 6. Unit Economics (Internal)

**Per-customer COGS per month:**

| Cost line | Starter | Specialist | Workforce |
|---|---|---|---|
| LLM (smart-routed mix: open-source for routine, frontier API for complex) | €40 | €70 | €120 |
| Orchestration (Hermes harness, memory store, integration glue) | €15 | €25 | €35 |
| Tuning time (~€60/hr loaded) | €60 (1h) | €180 (3h) | €480 (8h) |
| **Total COGS** | **~€115** | **~€275** | **~€635** |
| **Gross margin** | **~62%** | **~61%** | **~58%** |

**Assumptions:**
- One GPU node serves ~15–25 SMB agents concurrently (workloads are bursty, batching works); first 5–10 customers are less efficient per head
- Routing rules keep LLM costs predictable: cheap models triage, frontier models only on complex tasks
- Per-customer setup ~6 hours of internal time (~€360); payback is ~2 months on Starter, ~1 month on Specialist, under 3 weeks on Workforce
- Annual logo retention target: 70%+ once tuned into a specialist

**Risks to watch:**
1. **Workforce-tier API costs** — heavy users on frontier APIs can shrink margin; needs strict routing rules and monthly review
2. **Routing complexity** — "cheap unless complex, then escalate" requires real engineering, not a free lunch
3. **Hermes harness maturity** — Nous's harness is real but young; be prepared to fork/augment
4. **API price volatility** — providers can raise prices or rate-limit; maintain at least two providers + one self-hosted fallback per task class

---

## 7. Tech Stack (Customer-Facing Narrative)

- **Agent runtime:** Nous Research Hermes Agent harness (orchestration, tool calling, planning, memory)
- **LLM:** model-agnostic — open-source self-hosted (Llama 3.x, Qwen, Hermes models) + frontier APIs (Claude, GPT) routed per task
- **Hosting:** EU VPS infrastructure; data residency option for sensitive customers
- **Memory:** vector store with per-customer isolation

**Marketing line:** *"Your agent always uses the best model for the job — and we negotiate the bill, not you."*

---

## 8. Go-to-Market

The product capability exists today. The landing page exists to convert paid traffic, not to gather emails.

- **Channel:** Facebook ads targeting SMB owners in EU (HU/DE/EN markets)
- **Funnel:** ad → landing page → consultation booking (Calendly) → 30-min discovery call → onboarding
- **Tracking:** Meta Pixel + conversion API event on the booking action; UTM-tagged links where supported
- **Compliance:** Meta rejects "AI will replace your employees" framing — copy leans toward augmentation, time-saving, relief

---

## 9. Landing Page Design

### 9.1 Visual Identity

**Direction:** "Quietly serious."

- Warm off-white background (not pure white; not gold-tinted like the previous AgentHeaven)
- Deep ink / graphite primary text
- One restrained accent color (proposed: sage green or ochre — final pick during implementation)
- Sans-serif throughout (e.g., Inter or Söhne family — final pick during implementation)
- Optional: one display serif for emphasis in section headings
- Generous white space; subtle motion only; no rocket-ship AI aesthetics

**Reference vibe:** Mercury Bank, Stripe — trustworthy, well-built, no theatrics.

Full visual reset from the previous gold/cream Fraunces+Plus-Jakarta-Sans direction. Logo: open question — likely retains the AgentHeaven wordmark but the existing SVG mark is tied to the social-media-agent product context; may want to evolve it (decided during implementation, not in this design).

### 9.2 Page Structure (Top → Bottom)

1. **Nav** — logo · How it works · Roles · Pricing · CTA: *Book a call*
2. **Hero** — Headline: pain framed as relief. Sub: the mechanism in one sentence. Primary CTA: *Book a free 30-min consultation*. Reassurance microcopy: *"30 min, no slides, no commitment."*
3. **Role examples strip** — 6 cards (the roles in §4), each with a concrete example or "before/after" snippet
4. **How it works** — 4 steps: *Discovery call → We configure → Day 1 generalist → Day 90 specialist*
5. **Day 1 → Day 90 journey** — visual timeline showing the agent's evolution (text + simple progression graphic, not animated video)
6. **What's included / what we handle** — flat fee, absorbed LLM + VPS costs, model-agnostic routing, EU hosting option, monitoring, tuning hours. Designed to counter "but what about hidden costs?"
7. **Pricing** — three tiers (Starter / Specialist★ / Workforce). Each tier CTA: *"Book a call to start"*
8. **Why us** — founder credibility note: *"Built by operators who've shipped enterprise data integration and high-availability systems since 2006."* EU-hosted, model-agnostic, no-lock-in. (No customer logos / testimonials yet — add once available.)
9. **FAQ** — 6–8 objections:
   - What if it makes mistakes?
   - Which LLM does it use?
   - What about my data and privacy?
   - What if I want to cancel?
   - Can it do *[my specific task]*?
   - How is this different from ChatGPT Teams?
   - Can I bring my own model?
   - How long does setup take?
10. **Final CTA** — *Book your consultation* with prominent button to Calendly (or equivalent)
11. **Footer** — Privacy, Terms, contact email, language switcher (EN · HU · DE)

### 9.3 Localization

Maintain the existing three-locale model (EN, HU, DE) using the same `data-i18n` attribute pattern from the current `index.html`. All new copy must ship in all three languages.

### 9.4 Technical Constraints

- **Single static HTML** (no build step) — match the current project's deployment model
- **Self-hosted fonts** — no third-party CDN, no render-blocking external assets (continue the existing approach)
- **Performance:** maintain or exceed current Lighthouse scores; the page is ad-traffic destination so LCP matters
- **Meta Pixel + conversion event** wired to the consultation booking action
- **OG image:** new `og-image.html` + `og-image.png` matching the new visual identity
- **Refresh:** `privacy.html` and `terms.html` to reflect the new offer (digital employees, not social-media agent)

### 9.5 What Goes Away

- The €69/month social-media-agent product copy and pricing
- The live-feed "agent panel" hero illustration (it's specific to the social-media product)
- The local-business audience cards (gyms / salons / restaurants / sports clubs)
- The waitlist email-capture pattern — replaced with a Calendly booking CTA

---

## 10. Out of Scope (For This Spec)

- Per-role detail pages (Roles · Repetitive tasks, Roles · Research, …) — possible future SEO play
- A customer dashboard or self-serve sign-up flow — onboarding is via consultation
- Multi-product navigation — there is one product
- Detailed brand/logo redesign — minor evolution acceptable, full rebrand is a separate workstream
- The actual Calendly setup, Meta Pixel ID provisioning, ad creative — these are operational tasks, not part of the landing-page rebuild

---

## 11. Success Criteria

- Landing page ready to receive Facebook ad traffic in three languages
- Consultation booking rate: target 1–3% of unique visitors at launch (realistic range for B2B service landing pages with cold paid traffic; 3%+ is aspirational)
- Page load: LCP < 2.0s on mid-tier mobile over 4G
- Founders can explain the offer in 30 seconds using only the hero copy
