---
permalink: /
title: ""
excerpt: "On-device machine learning for the field"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% include base_path %}

![Intelligence that runs where the network doesn't](/images/hero_composite.jpg){: .align-center}

PhD candidate, Paul G. Allen School of Computer Science, University of Washington.
I build efficient, **on-device machine learning** for places with no power budget,
no network, and little context — wildlife camera traps in remote landscapes.
BS/MEng, MIT.

*Open to industry ML / research roles.*

---

## The problem I work on

My dissertation tackles a single question: how do you run capable machine learning
in places with no power to spare, no network to reach, and no context but a GPS
coordinate? Unattended camera traps in the field face exactly this — and each
constraint shapes one thread of the work.

![Dissertation overview: one deployment setting, three bottlenecks](/images/thesis_frame.svg){: .align-center}

---

## Selected projects

<div style="display:flex;gap:1.25em;align-items:flex-start;flex-wrap:wrap;margin:0.5em 0 1.75em">
  <a href="/portfolio/geo-adapters/" style="flex:0 0 300px;max-width:300px;display:block">
    <img src="/images/geo_adapters_teaser.png" alt="Geo-aware edge models for species recognition" style="width:100%;border:1px solid #e2e5ea;border-radius:8px" />
  </a>
  <div style="flex:1 1 320px">
    <a href="/portfolio/geo-adapters/"><strong>Towards Geo-Aware Edge Models for Species Recognition</strong></a><br/>
    <span style="color:#2a7de1;font-weight:600">WACV 2027</span> &middot; <span style="color:#888">under review</span><br/>
    <span style="color:#555"><strong>TL;DR</strong> &mdash; Geographic priors help a weak on-device classifier (<strong>+8.1</strong> top-1) but <em>hurt</em> a strong backbone (<strong>&minus;5.4</strong>): a headroom-dependent sign flip. The same region structure prunes the classifier head 1.6&ndash;300&times; for microcontroller deployment.</span><br/>
    <a class="btn btn--info" href="/portfolio/geo-adapters/" style="margin-top:.6em">Project page</a>
  </div>
</div>

<div style="display:flex;gap:1.25em;align-items:flex-start;flex-wrap:wrap;margin:0.5em 0 1.75em">
  <a href="/portfolio/on-device-ai-conservation/" style="flex:0 0 300px;max-width:300px;display:block">
    <img src="/images/chi_ondevice_ai_teaser.png" alt="On-device AI for conservation work" style="width:100%;border:1px solid #e2e5ea;border-radius:8px" />
  </a>
  <div style="flex:1 1 320px">
    <a href="/portfolio/on-device-ai-conservation/"><strong>The Promise and Peril of On-Device AI for Conservation Work</strong></a><br/>
    <span style="color:#2a7de1;font-weight:600">CHI 2026</span><br/>
    <span style="color:#555"><strong>TL;DR</strong> &mdash; A field study across Pacific Northwest &amp; Namibia conservancies, paired with a working on-device transcription&rarr;LLM prototype on EarthRanger. On-device LLMs show promise for field data collection, but current models' infrastructure clashes with resource-limited conservation settings.</span><br/>
    <a class="btn btn--info" href="/portfolio/on-device-ai-conservation/" style="margin-top:.6em">Project page</a>
    <a class="btn" href="https://dl.acm.org/doi/10.1145/3772318.3791359" style="margin-top:.6em">Paper</a>
  </div>
</div>

<div style="display:flex;gap:1.25em;align-items:flex-start;flex-wrap:wrap;margin:0.5em 0 1.75em">
  <a href="/portfolio/edge-vision-adapters/" style="flex:0 0 300px;max-width:300px;display:block">
    <img src="/images/compass_edge_vision_teaser.png" alt="Efficient mobile transformer models for the edge" style="width:100%;border:1px solid #e2e5ea;border-radius:8px" />
  </a>
  <div style="flex:1 1 320px">
    <a href="/portfolio/edge-vision-adapters/"><strong>Efficient Mobile Transformer Models for Wildlife Monitoring on the Edge</strong></a><br/>
    <span style="color:#2a7de1;font-weight:600">COMPASS 2026</span> &middot; <span style="color:#888">under review</span><br/>
    <span style="color:#555"><strong>TL;DR</strong> &mdash; Convolutional adapter experts on compact vision transformers (MobileViT), combined by continuous gating to keep a <em>static</em> execution graph for edge accelerators (Apple Neural Engine, ~1.0&nbsp;ms). A controlled comparison of four adapter designs shows more experts is not a reliable path to more accuracy.</span><br/>
    <a class="btn btn--info" href="/portfolio/edge-vision-adapters/" style="margin-top:.6em">Project page</a>
  </div>
</div>

<div style="display:flex;gap:1.25em;align-items:flex-start;flex-wrap:wrap;margin:0.5em 0 1.75em">
  <a href="/portfolio/edge-kd-adapters/" style="flex:0 0 300px;max-width:300px;display:block">
    <img src="/images/kd_adapters_teaser.png" alt="Residual adapters vs backbone distillation on edge classifiers" style="width:100%;border:1px solid #e2e5ea;border-radius:8px" />
  </a>
  <div style="flex:1 1 320px">
    <a href="/portfolio/edge-kd-adapters/"><strong>Residual Adapters or Backbone Adaptation?</strong></a><br/>
    <span style="color:#2a7de1;font-weight:600">AAAI 2027</span> &middot; <span style="color:#888">under review</span><br/>
    <span style="color:#555"><strong>TL;DR</strong> &mdash; When compressing biological foundation models to the edge, residual adapters and knowledge distillation are usually combined &mdash; but they capture the <em>same</em> gain. Adapters add <strong>+13.7</strong> pts on a frozen backbone yet <strong>nothing</strong> after distillation: the two substitute rather than complement.</span><br/>
    <a class="btn btn--info" href="/portfolio/edge-kd-adapters/" style="margin-top:.6em">Project page</a>
  </div>
</div>

*Dissertation code is being open-sourced as each paper is released. Manuscripts for papers under review are available on request.*

## Active collaborations

<div style="display:flex;gap:1.25em;align-items:flex-start;flex-wrap:wrap;margin:0.5em 0 1.75em">
  <a href="/portfolio/microrobots-vision/" style="flex:0 0 300px;max-width:300px;display:block">
    <img src="/images/microrobots_vision.png" alt="Battery-free on-board computer vision for insect-scale microrobots" style="width:100%;border:1px solid #e2e5ea;border-radius:8px" />
  </a>
  <div style="flex:1 1 320px">
    <a href="/portfolio/microrobots-vision/"><strong>Battery-free On-Board Computer Vision for Insect-scale Microrobots</strong></a><br/>
    <span style="color:#2a7de1;font-weight:600">In progress</span> &middot; <span style="color:#888">2025</span><br/>
    <span style="color:#555">Battery-free insect detection &amp; classification on solar-powered milli-robots with tiny ML for microcontrollers &mdash; with Kyle Johnson and Vicente Arroyos; late-breaking poster at IEEE ICRA.</span><br/>
    <a class="btn btn--info" href="/portfolio/microrobots-vision/" style="margin-top:.6em">Project page</a>
  </div>
</div>

<div style="display:flex;gap:1.25em;align-items:flex-start;flex-wrap:wrap;margin:0.5em 0 1.75em">
  <a href="/portfolio/metaheuristics-moe/" style="flex:0 0 300px;max-width:300px;display:block">
    <img src="/images/metaheuristics_moe.png" alt="Metaheuristics for mixture-of-expert architecture search" style="width:100%;border:1px solid #e2e5ea;border-radius:8px" />
  </a>
  <div style="flex:1 1 320px">
    <a href="/portfolio/metaheuristics-moe/"><strong>Metaheuristics for Mixture-of-Expert Architecture Search</strong></a><br/>
    <span style="color:#2a7de1;font-weight:600">In progress</span> &middot; <span style="color:#888">2025</span><br/>
    <span style="color:#555">Neuroscience-informed heuristics (with UW neuroscientist Ian Quah) for searching ultra energy-efficient edge vision transformers via data-dependent subnetwork computation.</span><br/>
    <a class="btn btn--info" href="/portfolio/metaheuristics-moe/" style="margin-top:.6em">Project page</a>
  </div>
</div>

---

## Highlights

CHI 2026 · TOCHI 2026 · Interspeech 2019 · IEEE Sensors 2018 · NAIRR Pilot · Azure AI for Earth grant · UW CS for the Environment Fellowship · Qualcomm Innovation Fellowship (selected abstract) · Created the vision unit of MIT's Deep Learning Practicum (6.S198) · BS/MEng, MIT
