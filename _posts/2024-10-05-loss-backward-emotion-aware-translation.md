---
layout: post
title: "Loss.backward #−1 — Translating Feelings, Not Just Words"
categories:
  - loss.backward
tags:
  - emotion-aware translation
  - speech
  - multimodal
  - research
excerpt: >-
  Notes from the EmoDub project at Trinity College Dublin where we fused SER models, wav2vec 2.0 features,
  and multimodal fusion to keep affect intact during translation.
---

Emotion-aware speech translation sounds romantic until you try to encode tone, intent, and context in a single
model. Our approach at Trinity College Dublin decomposed the problem into three collaborating systems:

1. **SER front-end.** Transformer encoders paired with wav2vec 2.0 embeddings deliver affect logits that we
   treat as controllable metadata.
2. **Text + acoustic fusion.** A cross-modal transformer braids together token embeddings, pitch contours, and
   SER summaries before handing everything to the translation decoder.
3. **Evaluation triad.** BLEU covers adequacy, but we add Emotion F1 and MOS scoring via native speakers to
   quantify expressive faithfulness.

A distilled walkthrough plus dataset recipes live inside the
[`emodub-emotion-translation`](https://github.com/AliNikkhah2001/emodub-emotion-translation) repository for
anyone exploring affective computing.
