---
title: "Residual Adapters or Backbone Adaptation? Understanding Their Interaction in Edge Wildlife Vision Classifiers"
excerpt: 'Residual adapters and knowledge distillation are usually combined — but they capture the same improvement. A framework for choosing between them when compressing biological foundation models to the edge.'
collection: portfolio
permalink: /portfolio/edge-kd-adapters/
header:
  teaser: kd_adapters_teaser.png
---

<span style="color:#2a7de1;font-weight:600">AAAI 2027</span> &middot; <span style="color:#888">under review</span>

![Residual adapters vs. backbone adaptation on edge wildlife classifiers](/images/kd_adapters_teaser.png){: .align-center}

**TL;DR** — Deploying biological foundation models (e.g., BioCLIP2) on edge devices needs
compact students that stay accurate. Two adaptation strategies — **residual adapters** (add
lightweight trainable modules to a frozen backbone) and **backbone adaptation via knowledge
distillation** — are usually *combined*. We show they capture **largely overlapping**
improvements: on a frozen backbone, adapters add **+13.7 pts** (50.1% → 63.8%); *after*
backbone distillation they add **nothing** (72.3% → 71.5%). The two approaches **substitute,
they don't complement** — and we give a practical framework for choosing between them.

## The problem

Edge-based ecological monitoring runs species classification on camera traps, acoustic
sensors, and microcontrollers — with no cloud, and strict memory, latency, and energy
budgets (Coral Edge TPU, Cortex-M). Biological foundation models like BioCLIP2 are
state-of-the-art but far too large; compact models are deployable but much less accurate.
Practitioners reach for adapters *and* distillation together, assuming the gains stack.

## What we found

- **A continuous substitution relationship.** Across progressive distillation checkpoints,
  adapter gains **decrease monotonically** as the backbone's features become more
  discriminative — the two techniques address the *same* limitation, not independent ones.
- **Two operating regimes.** With a **frozen backbone**, adapter utility is
  *optimization-limited* and tracks adapter–head gradient coupling (adj-R² = 0.97). After
  **backbone adaptation**, performance is *representation-limited*: as within-class scatter
  falls and the Fisher ratio rises, adapter gains vanish — across architectures, objectives,
  and datasets. A plain cross-entropy backbone shows the same trend, so the effect isn't
  specific to distillation.
- **A mechanistic reading.** A simple **Scale-and-Shift Fine-Tuning (SSF)** baseline recovers
  ~**70%** of the frozen-backbone gain with only **48 trainable parameters** — evidence that
  adapters mostly *recalibrate existing feature channels* rather than learn new ones.
- **Distillation choice depends on data structure.** Hierarchical taxonomic datasets benefit
  from intermediate **feature** alignment; scene-dependent camera-trap datasets favor
  **logit** distillation, because teacher features encode environmental context that's lost
  once detections are cropped.
- **Generalizes** across MobileViTv2, MobileNetV2, and ultra-small microcontroller-scale
  networks.

## Why it matters

Together these results give a **practical framework** for when to spend parameters on
adapters versus improving the backbone itself — guidance for anyone compressing biological
foundation models onto resource-constrained edge hardware.

---

*Paper is under review — the manuscript is available on request. The preprint, code, and
BibTeX will be linked here once the review period closes.*
