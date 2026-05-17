# AI Cost Calculator

**Status:** v0.1 shipped 2026-05-16 (workshop block). Companion to AI Readiness Test. Single-file static HTML/JS.

## What it does

Interactive calculator. User inputs team size, hourly cost, current weekly manual work hours, expected automation %, and consulting session cost. Live-updates hours saved monthly, $ saved monthly + annually, and a payback timeline with calibrated framing (under 1 month = "compounds immediately"; over 24 months = "too slow, do smaller scope").

CTA to purcellventures.co/consulting.

## Why it pairs with the Readiness Test

The two tools form a 2-step funnel:

```
AI Readiness Test → score 8/30 (AT RISK) → "you're behind"
  → AI Cost Calculator → enter numbers → "$2,800/mo saved, payback in 16 days"
  → consulting CTA → high-intent lead
```

The Readiness Test creates the emotional moment ("I'm behind"). The Calculator quantifies the cost-of-inaction in dollars. Together they convert better than either alone.

## How to use

Open `index.html` in a browser. All math runs in-browser. No tracking, no email capture, no backend.

## How to ship to production

Same two paths as AI Readiness Test:

1. **Drop into purcell-ventures-site** as `app/ai-cost-calculator/page.tsx`. Live at purcellventures.co/ai-cost-calculator. Cross-link from /ai-readiness page and from the consulting page hero.

2. **Standalone GitHub Pages** for a sister-subdomain (cost.purcellventures.co).

Either way, link from BOTH tools to each other.

## Conservative assumptions baked in

- 4.33 weeks/month (avg)
- Automation % defaults to 60%, range 20-80%
- Does NOT count quality improvements, error reduction, retention impact, or compounding gains
- Payback math is straight-line, no NPV

These are honest, defensible numbers. Salespeople would inflate them. We don't.

## Tier-based payback messaging

| Payback | Message |
|---|---|
| <1 month | "Pays back in ~X days. Savings compound monthly." |
| 1-6 months | "Pays back in ~X.X months. Savings compound monthly." |
| 6-24 months | "Slower than typical — worth doing if the work drains morale." |
| 24+ months | "Too slow to justify on time-savings alone. Try $175/hr 1-on-1 instead." |

The last tier is the brand differentiator — most calculators on the internet would push the user toward booking anyway. Ours tells them not to.

## v0.2 status

- [x] **Industry presets** — 6 one-tap loads (Real Estate, Dental, Law, Marketing Agency, Ecommerce, Solo Founder). Each loads team/rate/manual/auto/cost defaults plus a contextual description that explains the preset's reasoning. Shipped 2026-05-16.
- [ ] ROI compounding model (year 1, year 2, year 3)
- [ ] Export to PDF
- [ ] Share-able URL with inputs encoded
- [ ] "Compare 1-on-1 vs Small Group vs Half-Day" side-by-side

## Preset rationale

| Preset | Team | Rate | Manual hrs/wk | Auto % | Session $ |
|---|---|---|---|---|---|
| Real Estate Office | 6 | $55 | 12 | 65 | $1500 |
| Dental Practice | 8 | $45 | 10 | 55 | $1500 |
| Law Firm | 5 | $95 | 14 | 60 | $2500 |
| Marketing Agency | 4 | $75 | 18 | 70 | $1500 |
| Ecommerce Brand | 3 | $60 | 15 | 70 | $1500 |
| Solo Founder | 1 | $100 | 20 | 65 | $500 |

Defensible numbers:
- **Rates** = fully-loaded labor (salary + benefits + overhead), median for sub-30-person US small businesses
- **Manual hours/week** = repeatable-non-judgment work — email, content, admin, scheduling, basic research
- **Auto %** = realistic post-session reduction (marketing agencies highest because content workflows automate aggressively; dental practices lower because clinical work has compliance friction)
- **Session cost** = matches PV consulting price points (1-on-1 hourly × estimated session length for solo; flat half-day for teams)

## Test plan

Open `index.html` and verify:
- All 5 inputs update results live
- Slider updates the percent label
- Payback line changes message at the 4 thresholds (try cost=$200 vs $50000)
- Cross-link to AI Readiness Test in footer works (relative path assumes sibling dir)
- Mobile layout is clean
