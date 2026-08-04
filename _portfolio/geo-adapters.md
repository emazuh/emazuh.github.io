---
title: "Towards Geo-Aware Edge Models for Species Recognition"
excerpt: 'When does geography actually improve species recognition — and when does it just re-express what the image already shows?'
collection: portfolio
permalink: /portfolio/geo-adapters/
header:
  teaser: geo_adapters_teaser.png
---

<span style="color:#2a7de1;font-weight:600">WACV 2027</span> &middot; <span style="color:#888">under review</span>

![Geography as a headroom-dependent corrective signal](/images/geo_adapters_teaser.png){: .align-center}

**TL;DR** — Geographic location is widely used as a prior for species recognition, but
its value is governed by a single quantity: the fraction of errors that are
*geographically separable*. That fraction is near-zero for a strong visual backbone
(which already resolves most confusions from imagery) and large for a weak edge model —
so the **same per-region prior that hurts a near-ceiling classifier (−5.4 top-1) helps a
weak on-device model by up to +8.1 top-1.** Geography is a *headroom-dependent corrective
signal*, not a universal accuracy booster.

## The question

Automated species recognition increasingly runs on edge hardware — camera traps, field
sensors, microcontrollers — where the image model must be small, quantized, and cheap. A
natural way to help a weak on-device classifier is to add geographic context: species
occupy restricted ranges, so knowing *where* a photo was taken should narrow *what* it
might contain. Deployed systems like SpeciesNet already filter predictions to a supplied
region as a practical heuristic. But this leaves a question open: **when does geography
improve accuracy, and when does it merely re-express what the image already determines?**

## What we found

**Geography is a region-level signal, not a fine-grained cue.** A location-only probe is
strongly predictive of *region* but collapses at fine resolution (cell purity 0.37 coarse
vs. 0.045 fine). It tells the model *where it is*, not *what species is present*.

**Because it's region-level, a strong backbone has already absorbed it.** Multiplying a
per-region prior into a near-ceiling classifier is non-additive and *reduces* accuracy
(−5.4 top-1). The identical prior applied to a weak edge model recovers many
region-separable errors (+8.1 top-1) — a **headroom-governed sign flip** we make
measurable with an error-geography analysis, whose geo-recoverable ceiling rises ~10× as
the backbone weakens.

**The gains come from a discrete per-region table, not learned feature fusion** — which
matters for deployment.

## Why it matters for on-device deployment

The same region structure a strong model has outgrown remains a *deployment lever*:

- **Classifier-head pruning** — the microcontroller-flash bottleneck — by **1.6–300×**
  depending on region resolution.
- **A lightweight location encoder** distilled from the GeoTessera geographic foundation
  model, providing a known-location tie-breaker on-device at negligible cost (**0.020 ms**).

Both mechanisms rely on known location and do not generalize to unseen regions, unifying
them as *deployment* uses of a shared geographic structure.

## Takeaway

Our results reconcile the classical gains from geographic priors with their failure on
modern backbones, and reframe location in species recognition as a **headroom-dependent
corrective signal** rather than a universal accuracy boost — validated across three
datasets spanning citizen-science and camera-trap settings, with on-device measurements.

---

*Paper is under double-blind review — the manuscript is available on request. The preprint,
code, and BibTeX will be linked here once the review period closes.*
