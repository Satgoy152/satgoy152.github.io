---
layout: page
title: diffusion language models (ECHO)
description: Sampling-aware MDLM training that outperforms SOTA by 15% on reasoning benchmarks
importance: 1
category: academic
related_publications: false
giscus_comments: false
---

## Overview

Masked Diffusion Language Models (MDLMs) are one of the few credible alternatives to autoregressive generation: bidirectional attention, parallel token generation, and native support for infilling and controllable generation from arbitrary positions. The catch is that they still lag autoregressive models on quality and are expensive to train well. This project, advised by Prof. JJ (Jeong Joon) Park at the University of Michigan, is about closing that gap.

**Timeline**: August 2024 – Present

## ECHO: Sampling-Aware Training

The core of this work is **ECHO**, a training algorithm grounded in constrained Gibbs sampling (MCMC) rather than the standard independent-masking objective most MDLMs use. Instead of training the model to denoise positions independently, ECHO trains against a sampling procedure that better matches how the model will actually be used to generate text at inference time — and it outperforms comparable SOTA MDLM training methods by **15%** on reasoning benchmarks.

- Designed and implemented a sampling-aware training objective built on constrained Gibbs sampling
- Engineered a distributed training pipeline across 8xA100 clusters
- Scaled training to **50B tokens** while cutting memory overhead by **30%**
- Pretrained and finetuned models ranging from **100M to 8B parameters**

## Self-Correction: `mdlm_refine`

A parallel thread of this work asks a more specific question: can an MDLM learn to catch and fix its own generation errors *during training*, instead of relying on inference-time correction procedures bolted on after the fact? That's the idea behind [`mdlm_refine`](https://github.com/Satgoy152/mdlm_refine) — see the [dedicated project page](/projects/5_project/) for details, including how it stacks up against Kuleshov et al.'s recent self-correcting diffusion work out of Cornell / Inception Labs.

## Where This Is Headed

Two problems keep MDLMs from being competitive with autoregressive models at scale, and I'm actively working on both:

- **Inference speed** — see [speculative decoding for diffusion LMs](/projects/6_project/)
- **Training and long-context efficiency** — see [what's next](/projects/7_project/) for early work on a diffusion-native optimizer and long-context attention

## Collaboration

**Prof. JJ (Jeong Joon) Park**
University of Michigan, Ann Arbor
