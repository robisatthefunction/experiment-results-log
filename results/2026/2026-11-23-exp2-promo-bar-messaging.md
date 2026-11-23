---
experiment_name: "EXP2 – Promo Bar Messaging"
experiment_id: "4985313280393216"
project: "eCommerce Optimization Program"
platform: "Web Experimentation"
area: "promo banner"
owner: "Not specified"
start_date: "2026-11-18"
conclusion_date: "2026-11-23"
outcome: "win"
decision: "ship"
primary_metric: "Promo Bar Click"
primary_metric_lift: "+29.4% (V2 – Free Shipping Bundle vs Control)"
statistical_significance: "99.9% (V2 vs Control; 90% confidence threshold)"
tags: ["promo-banner", "global-pages", "copy-change", "free-shipping", "direct-traffic"]
optimizely_results_url: ""
---

# EXP2 – Promo Bar Messaging

## Summary
Three alternative promo-bar messages (V1 – Limited Time Savings, V2 – Free Shipping Bundle, V3 – Treat Yourself) were tested against the original banner on all pages for everyone. V2 beat the control on the primary metric, Promo Bar Click (+29.4%, 99.9% significance), V3 clearly lost (−39.3%, significant) and V1 was flat; the decision is to ship V2 with conditions, roll back V3 and retire V1.

## Hypothesis
Reframing the $50-off offer around value or free shipping will lift promo clicks and purchases (hypothesis as recorded in the Optimizely experiment description).

## Setup
| Item | Detail |
|---|---|
| Pages | Global – All Pages. Each variation changes only the banner text on elements matching `[class*='promo'], [class*='top-banner']` |
| Audience | Everyone |
| Traffic allocation | 25% per variation across 4 arms. Actual shares were 26.0% control, 24.7% V1, 24.5% V2 and 24.8% V3, so there is no sample-ratio concern |
| Variations | Control (Original); V1 – Limited Time Savings: "Spend $500, Save $50 – Limited Time Only" (40 characters); V2 – Free Shipping Bundle: "Free Shipping + $50 Off Orders $500+" (36 characters); V3 – Treat Yourself: "Treat Yourself: Take $50 Off When You Spend $500" (48 characters) |
| Visitors | 5,000 total: Control 1,302, V1 1,233, V2 1,223, V3 1,242 |
| Duration | Started 2026-11-18, concluded 2026-11-23. The recorded results window is only about 96 seconds (2026-11-18 17:22:33 to 17:24:09 UTC); see the data quality notes under Decision and next steps |

Primary metric assumption: Optimizely does not label a primary metric. Promo Bar Click is treated as primary because it is the first metric configured on the experiment. The secondary metrics are Checkout Started and Purchase. The project confidence threshold is 90%.

## Results
| Metric | Variation | Lift | Statistical significance | Confidence interval |
|---|---|---|---|---|
| Promo Bar Click (primary) | V1 – Limited Time Savings | −3.3% (33.5% vs 34.6% control) | Not significant | −18.3% to +11.7% |
| Promo Bar Click (primary) | V2 – Free Shipping Bundle | +29.4% (44.8% vs 34.6% control) | Significant (99.9%) | +11.1% to +47.6% |
| Promo Bar Click (primary) | V3 – Treat Yourself | −39.3% (21.0% vs 34.6% control) | Significant (>99.9%) | −50.2% to −28.5% |
| Checkout Started | V1 – Limited Time Savings | −7.1% (8.3% vs 8.9% control) | Not significant | −58.2% to +43.9% |
| Checkout Started | V2 – Free Shipping Bundle | +63.4% (14.6% vs 8.9% control) | Not significant | −23.6% to +150.4% |
| Checkout Started | V3 – Treat Yourself | −58.4% (3.7% vs 8.9% control) | Significant (99.99%) | −78.1% to −38.7% |
| Purchase | V1 – Limited Time Savings | −5.5% (1.4% vs 1.5% control) | Not significant | Not available |
| Purchase | V2 – Free Shipping Bundle | +180.2% (4.1% vs 1.5% control; 50 vs 19 purchases) | Not significant | Not available |
| Purchase | V3 – Treat Yourself | −39.3% (0.9% vs 1.5% control) | Not significant | Not available |

- **Reading "significant":** the difference is unlikely to be random noise at Optimizely's 90% confidence threshold. "Not significant" means the data can't yet separate the result from chance. It does not mean "no effect".
- **Verdicts:** Optimizely's conclusion block names only V3 as the loser. V2's primary-metric result is statistically significant, but Optimizely did not attach an explicit "winner" label. V1 is inconclusive.
- **Purchase is underpowered:** only 97 purchases were recorded across all four arms.
- **Source of intervals:** intervals for Checkout Started on V1 and V3 were not in the insights report and were read from the Optimizely results (last calculated 2026-11-23). Optimizely returned no intervals for Purchase.

## Why it happened
Evidence from Optimizely results and Quantum Metric (same pages and date window). Quantum Metric sessions: Control 1,566, V1 1,478, V2 1,471, V3 1,489 (about 1.2 sessions per Optimizely visitor).

- **Insight 1: Free shipping framing earned more banner engagement. (Confirmed)**
  - Optimizely: V2 lifted Promo Bar Click by +29.4% (44.8% vs 34.6%, 99.9% significance).
  - Quantum Metric: 35.1% of V2 sessions clicked the promo bar vs 28.4% for control. The median time to first banner interaction was faster (5.9s vs 6.8s), and 22.9% of V2 sessions reached the cart vs 17.5% for control.
- **Insight 2: V3's longer copy created friction that cost clicks and checkout starts. (Confirmed)**
  - Optimizely: V3 lost on Promo Bar Click (−39.3%) and Checkout Started (−58.4%), both significant. Its copy is 48 characters, 33% longer than V2's.
  - Quantum Metric: V3 banner text was clipped in 22% of sessions, and the "$500" threshold sits at the end of the string, so it is cut off first. V3 had the highest promo-bar rage-click rate (4.6% vs 1.8% control) and dead-click rate (8.8% vs 3.9%). Page speed was equal across arms (75th-percentile load time of 2.4–2.5s), so speed is not the cause.
  - Session replay **QM-SR-482917** (V3, desktop 1,366px, search arrival): the banner reads "Treat Yourself: Take $50 Off When You Spe…", clipped before the threshold. The visitor clicks the text four times in three seconds and nothing happens (rage click and dead click). They scroll to the product grid and leave after 38 seconds without adding to cart.
  - Why the clipping happens (the longer text pushes the "Shop now" link out of view) is an interpretation from the replays, but the clipping itself is measured.
- **Insight 3: V2's extra clicks appear to be turning into checkouts and purchases, but Optimizely hasn't proven it. (Hypothesis)**
  - Optimizely: V2 Checkout Started was +63.4% and Purchase +180.2%, both not significant. Optimizely estimates about 214 more visitors are needed for Checkout Started to reach a conclusion.
  - Quantum Metric: V2 had higher cart-to-checkout progression (51.6% vs 44.2%) and higher checkout completion (32.8% vs 20.7%). The most-abandoned checkout field moved from *Shipping method* (control) to *Promo code* (V2). This suggests free shipping removes the shipping-cost surprise.
  - **Leak to fix:** V2 sessions show twice the promo-code error clicks (2.4% vs 1.1% of checkout sessions) and more discount API errors (1.4% vs 0.6%). This may mean the $50 offer doesn't stack cleanly with other codes.
  - Session replay **QM-SR-483306** (V2, desktop, campaign email arrival): the visitor clicks the banner within 4 seconds and adds three items (cart $547). They enter their email code at checkout and get "code can't be combined with this offer" twice (error clicks). They retry without the code and complete the purchase in 6m12s. This shows V2's pull and its discount-stacking friction.
  - Session replay **QM-SR-481754** (V2, direct, returning customer): the cart is $412, below the $500 threshold. The visitor clicks the banner expecting free shipping, then sees a $14.95 shipping fee at checkout. They click the shipping line three times and abandon at the shipping step after 1m48s. This suggests the V2 copy may read as "free shipping on everything".
- **Insight 4: V1's "limited time" wording made no meaningful difference. (Confirmed)**
  - Optimizely: V1 was −3.3% on Promo Bar Click, not significant. The range runs from −18.3% to +11.7%.
  - Quantum Metric: V1 behaved almost identically to control. Promo-bar interaction was 40.5% vs 41.2%, and every funnel step was within about 0.7 points. Urgency wording alone doesn't change behavior when the offer itself is unchanged.
- **Insight 5: Direct visitors respond differently, probably because many are returning customers. (Hypothesis)**
  - Optimizely: in direct traffic V3's loss is not significant (−25.2%) and V1 is directionally positive (+14.5%). V2 shows the biggest lift of any segment (+40.0%) and 15 vs 3 purchases against control. None of these is significant.
  - Quantum Metric: 52% of direct sessions are returning customers, vs about 23% in search and campaign. V3 rage clicks are lower in direct (2.9% vs 4.6% overall).
  - Returning customers likely already know the "$500 / $50" offer, so wording and truncation hurt them less. This needs validating.

**Quantum Metric funnel: % of exposed sessions reaching each step**

| Step | Control | V1 | V2 | V3 |
|---|---|---|---|---|
| Promo bar click | 28.4% | 27.6% | 35.1% | 17.9% |
| Cart view | 17.5% | 17.1% | 22.9% | 12.0% |
| Checkout start | 7.7% | 7.2% | 11.8% | 3.3% |
| Order confirmation | 1.6% | 1.5% | 3.9% | 0.8% |
| Cart to checkout | 44.2% | 41.9% | 51.6% | 27.4% (biggest drop-off) |
| Checkout to purchase | 20.7% | 20.8% | 32.8% | 24.5% (only 49 sessions) |

**Quantum Metric frustration signals**

| Signal | Control | V1 | V2 | V3 |
|---|---|---|---|---|
| Rage clicks, promo bar (% of sessions) | 1.8% | 2.1% | 1.6% | 4.6% |
| Dead clicks, promo bar | 3.9% | 4.7% | 3.4% | 8.8% |
| Banner text clipped | 2% | 4% | 3% | 22% |
| Error clicks, checkout promo-code field (% of checkout sessions) | 1.1% | 1.2% | 2.4% | 1.0% |
| Checkout form abandonment (% of checkout sessions) | 62% | 63% | 51% | 58% |
| Top abandoned field | Shipping method | Shipping method | Promo code | Shipping method |
| Slow page (load over 4s) | 3.1% | 3.2% | 3.3% | 3.2% |
| Cart/discount API errors | 0.6% | 0.7% | 1.4% | 0.7% |

## Segments that moved
Lifts are for **Promo Bar Click** vs control. "Sig." means significant at 90% confidence, and "n.s." means not significant.

| Segment (visitors) | Lift | Statistical significance | Notes |
|---|---|---|---|
| Overall (5,000) | V1 −3.3%; V2 +29.4%; V3 −39.3% | V1 n.s.; V2 sig.; V3 sig. | See Why it happened. |
| Desktop (1,653) | V1 −3.9%; V2 +25.9%; V3 −35.2% | V1 n.s.; V2 n.s.; V3 sig. | V3 text was clipped in 31% of desktop sessions (windows under 1,440px). V3 rage clicks were 5.4% vs 1.9% for control. |
| Search (1,260) | V1 −16.3%; V2 +12.0%; V3 −48.4% | V1 n.s.; V2 n.s.; V3 sig. | Worst segment for V3. V3 banner interaction was 24% vs 40% for control, and median banner dwell was 0.9s vs 1.7s. Product-hunting visitors skipped the indulgent "Treat Yourself" message. |
| Direct (1,213) | V1 +14.5%; V2 +40.0%; V3 −25.2% | V1 n.s.; V2 n.s.; V3 n.s. | Best segment for V2. Returning customers (52% of sessions). V2 interaction was 55% vs 43% for control, and V2 checkout completion was higher (about 36% vs 19%, small sample). |
| Campaign (1,316) | V1 −10.3%; V2 +32.5%; V3 −41.0% | V1 n.s.; V2 n.s.; V3 sig. | V2's offer matches the ad or email promise: 25.8% of V2 sessions reached the cart vs 17.9% for control. V2 promo-code error clicks were highest here (3.1% of checkout sessions), likely from ad or email codes clashing with the banner offer. |
| Mobile, Tablet, Referral | Not available | Not available | Optimizely returned no data for these segments, so no conclusion is possible. |

**Segments that hide a different story:**
- **Direct** is the only segment where V3's loss is not significant and V1 points the other way. V2's strongest purchase signal also sits here. Don't treat the overall result as uniform.
- **V2 is not significant in any single segment**, because each has about a third of the sample. It is positive in all four, which supports the overall result.
- **Segments overlap.** Device and source are separate cuts, so the visitor counts shouldn't be added together.

## Key learnings
- **Lead promo copy with a concrete benefit, not urgency or indulgence.** Free-shipping framing lifted Promo Bar Click by +29.4% (99.9% significance), while "Limited Time Only" urgency wording was flat (−3.3%, not significant) and "Treat Yourself" lost (−39.3%). Urgency alone doesn't change behavior when the offer itself is unchanged.
- **Check that banner copy fits before launch, and put the threshold first.** V3's 48-character copy was clipped in 22% of sessions (31% of desktop sessions under 1,440px) and cut off the "$500" threshold, driving the highest rage-click (4.6%) and dead-click (8.8%) rates. Preview copy at common desktop widths and keep the key condition at the start of the string.
- **Test the offer mechanics before amplifying an offer.** V2 doubled promo-code error clicks (2.4% vs 1.1% of checkout sessions) and discount API errors (1.4% vs 0.6%), and "free shipping" wording may be read as applying to every order. Confirm discount stacking and that the copy matches cart behavior first.
- **Don't call a banner test on clicks alone.** Promo Bar Click is a proximate metric, and only 97 purchases were recorded across all four arms, so Purchase is underpowered. Size the next test with Purchase as primary (a 50% relative lift from a 1.5% baseline needs roughly 4,000 visitors per arm, a rough fixed-sample estimate).

## Decision and next steps
**Decision:** Ship V2 – Free Shipping Bundle with conditions, roll back V3 – Treat Yourself, and retire V1 – Limited Time Savings.

- **V2:** Roll out in stages, with a 10% holdback on the original banner to keep measuring Purchase. The click lift is significant and the direction is positive across all four segments and all three metrics.
- **Before the rollout:** confirm the $50 offer stacks properly with other codes, and that the free-shipping terms in the copy match what the cart does.
- **V3:** Do not ship. It is the only variation with significant downstream harm (Checkout Started −58.4%).
- **V1:** Drop it. It adds no value over control.
- **Caveat:** Promo Bar Click is a proximate metric. The business outcome, Purchase, isn't yet proven.

**Follow-up test ideas:**
1. **Clarify the V2 offer.**
   - *Hypothesis:* "Free Shipping on All Orders + $50 Off $500+" (or the accurate equivalent) will cut shipping surprise and raise checkout completion.
   - *Target:* direct and campaign visitors, especially carts under $500.
   - *Metric:* Purchase as primary, with Checkout Started and promo-code error clicks as secondary.
   - *Sample:* detecting a 50% relative purchase lift from a 1.5% baseline needs roughly 4,000 visitors per arm (a rough fixed-sample estimate).
2. **Retest V3's emotional framing in a shorter form.**
   - *Hypothesis:* "Treat Yourself – $50 Off $500" (36 characters or fewer, threshold first) recovers V3's losses, which came from clipping rather than the message.
   - *Target:* desktop windows under 1,440px and search traffic.
3. **Urgency plus a concrete benefit for returning customers.**
   - *Hypothesis:* "Free Shipping + $50 Off $500+ – Ends Sunday" will outperform V2 for returning visitors, since V1 leaned positive in direct.
   - *Target:* the direct-traffic audience.

**Implementation and data quality issues:**
- **Results window is only about 96 seconds.** The recorded window is 2026-11-18 17:22:33 to 17:24:09 UTC, yet it holds 5,000 visitors. That is too short to cover weekday or weekend cycles. Check whether the traffic was backfilled or test traffic, or whether the timestamps are an artefact.
- **Segment coverage gaps.** Mobile, tablet and referral returned no data. Desktop covers only 33% of visitors, and the three source segments cover 76%. Mobile effects can't be assessed, and 24% of visitors have no traffic-source label.
- **Broad selector on a global page.** `[class*='promo'], [class*='top-banner']` runs on "Global – All Pages". It could rewrite promo badges, cart banners or checkout promo boxes, not only the top bar. Use a narrower selector and scope it to specific pages.
- **No explicit winner flag.** V2 is significant on the primary metric but only V3 carries a conclusion label. Confirm the intended primary metric and the decision rule in the experiment setup.
- **V2 discount stacking.** Fix or clarify before full rollout (see Insight 3).

## Related
- Related experiments: Not specified
- Supporting docs: Optimizely Web Experimentation results for experiment ID 4985313280393216 (eCommerce Optimization Program, results last calculated 2026-11-23); Quantum Metric session replays QM-SR-482917, QM-SR-483306 and QM-SR-481754
