---
layout: post
title: "Loss.backward #00 — Ultrasound Reports Without the Pager"
categories:
  - loss.backward
tags:
  - medical imaging
  - vision-language
  - report generation
  - clinical ai
excerpt: >-
  How we paired BLIP-style encoders with T5 generators and clinician-in-the-loop evaluation to draft
  trustworthy ultrasound findings at UBC.
---

Generating medical reports is more than captioning—the structure, lexicon, and implied clinical decisions all
carry legal weight. At the University of British Columbia we built a pipeline that couples ViT/BLIP encoders
with a T5 generation head to propose structured ultrasound findings.

* Contrastive pretraining aligned acoustic windows with textual labels before we ever attempted generation.
* Retrieval-augmented prompting grounded the generator in real radiology exemplars.
* Clinician review dashboards surfaced hallucinated anatomy, enabling us to retrain on the exact slices that
  confused the model.

The resulting system beat our baselines across BLEU, ROUGE-L, and clinical efficacy scores while remaining
explainable thanks to the saliency overlays we ship alongside every paragraph. The accompanying
[`ultrasound-report-lab`](https://github.com/AliNikkhah2001/ultrasound-report-lab) repo includes the anonymised
pipelines, evaluation harnesses, and monitoring notebooks.
