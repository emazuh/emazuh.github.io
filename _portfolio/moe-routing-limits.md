---
title: "Understanding the Limits of Mixture-of-Experts Routing in Compact Wildlife Vision Distillation"
excerpt: 'Mixture-of-experts routing has large conditional value with a teacher-informed oracle — but a compact student cannot exploit it once the teacher is gone.'
collection: portfolio
permalink: /portfolio/moe-routing-limits/
header:
  teaser: moe_routing_teaser.png
---

<span style="color:#2a7de1;font-weight:600">WACV 2027</span> &middot; <span style="color:#888">under review</span>

![The limits of mixture-of-experts routing in compact vision distillation](/images/moe_routing_teaser.png){: .align-center}

**TL;DR** — Mixture-of-experts (MoE) architectures promise higher effective capacity through
input-dependent specialization. Does that advantage survive in a **compact vision student**
under limited data and compute, *after* standard distillation has converged? Using a
**BioCLIP2 teacher-informed oracle**, we show the conditional value is large and real —
**+16.3 points at K=4** over uniform routing, with oracle accuracy climbing **0.734 → 0.918**
as experts grow from K=1 to K=32. But **without the teacher, a compact student cannot exploit
it**: deployable routing stays essentially at the uniform baseline. We identify a **scoped
empirical limit on fine-grained routing exploitability**, not evidence that conditional
computation is intrinsically ineffective.

## The question

Biodiversity monitoring increasingly runs species recognition on camera traps and edge
sensors under tight memory, latency, and energy budgets. Large biological vision models
(e.g., BioCLIP2) give strong fine-grained recognition but are too costly to deploy; compact
students are deployable but lower-capacity. MoE is a natural way to recover accuracy by
letting different inputs use different experts — so: **can conditional computation recover
excess accuracy after standard feature distillation, without sacrificing deployability?**

## What we found

- **The ceiling is high.** An oracle that routes with teacher information delivers large gains
  (+16.3 pts at K=4), and oracle accuracy rises steadily with more experts (0.734 → 0.918).
  Parameter-matched *uniform* banks stay nearly flat — the value is genuinely conditional, and
  the effect reproduces across compact backbones and datasets.
- **Students can't reach it.** Student representations retain routing-relevant structure, but
  most recoverable expert identity is **class-mediated**, while deployable routing sits near
  the uniform baseline. The gap is concentrated in **fine-grained, within-class** routing.
- **The gap is stubborn.** Nonlinear probes, boundary-focused training, added student capacity,
  true-class conditioning, and teacher-representation reconstruction all **fail** to recover
  useful additional routing.
- **It's the soft weights, not just the choice.** Interpolation and choice–concentration
  analyses show the conditional value depends strongly on the **soft mixture weights**, not
  simply on which expert is selected.

## Why it matters

Compact students can preserve *coarse* conditional structure while failing to exploit the
*finer* distinctions that make teacher-shaped expert banks valuable. That's a concrete, scoped
limit for anyone hoping MoE routing will cheaply recover accuracy in compact, low-data edge
distillation — and a map of which recovery strategies don't work.

---

*Paper is under review — the manuscript is available on request. The preprint, code, and
BibTeX will be linked here once the review period closes.*
