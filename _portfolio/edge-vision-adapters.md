---
title: "Efficient Mobile Transformer Models for Wildlife Monitoring on the Edge"
excerpt: 'A deployable adapter-mixture for compact vision transformers that keeps static execution graphs for edge accelerators — and asks whether expert-style mixtures actually help.'
collection: portfolio
permalink: /portfolio/edge-vision-adapters/
header:
  teaser: compass_edge_vision_teaser.png
---

<span style="color:#2a7de1;font-weight:600">COMPASS 2026</span> &middot; <span style="color:#888">under review</span>

![Deployable adapter-mixture for compact vision transformers](/images/compass_edge_vision_teaser.png){: .align-center}

**TL;DR** — Vision models deployed *in place* (ecological monitoring, biodiversity sensing)
must run under strict compute, energy, connectivity, and privacy limits. We add
**input-dependent adaptability to compact vision transformers** (MobileViT, EfficientFormer)
using lightweight convolutional **adapter experts combined by continuous sigmoid gating** —
deliberately avoiding the sparse routing and dynamic control flow that break deployment on
edge accelerators. This keeps a **static execution graph** (e.g., Apple Neural Engine,
~1.0 ms). A controlled comparison of four adapter designs shows they **perform similarly**,
with a modest, consistent edge for sequential input-conditioned adapters — i.e., **more
experts is not a reliable path to more accuracy** on edge vision.

## Why this problem

Many edge deployments fail not because of insufficient benchmark accuracy, but because of
**brittleness, unpredictable latency, or hardware incompatibility.** Expert- and
mixture-style adapters promise input-dependent capacity, but the usual machinery — softmax
routing, sparse expert activation, dynamic control flow — introduces non-deterministic
execution and hardware-dependent performance that undermine long-running monitoring systems.

## The approach: HyViT–AdapterMixture

- Wrap the last stages of a **hybrid compact ViT** (MobileViT / EfficientFormer) with
  **lightweight convolutional adapters**.
- Combine them with **continuous sigmoid gating** rather than top-k routing — so the whole
  model stays a **static, deterministic graph** deployable on mobile accelerators.
- Study adapter **multiplicity as a lens** on adaptive capacity under edge constraints,
  not as a guaranteed accuracy lever.

## What we found

A systematic comparison of **four adapter composition strategies** — parallel /
sequential × input-conditioned / fixed — on biodiversity-recognition benchmarks under
mobile-scale conditions, across multiple seeds:

- **All configurations perform similarly**, with a modest but consistent preference for
  **sequential input-conditioned** adapters.
- Much of the benefit does **not** come from increasing the number of experts.
- The result clarifies the **practical limits of expert-style adapter mixtures** for edge
  vision, and offers guidance on adapter design for deployment-oriented ecological
  monitoring.

---

*Paper is under review; the preprint, code, and BibTeX will be linked here once the review
period closes.*
