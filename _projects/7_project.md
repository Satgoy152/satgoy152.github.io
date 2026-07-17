---
layout: page
title: "what's next: diffusion-native optimizers & long-context MDLMs"
description: Early-stage ideas on training and scaling MDLMs more efficiently
importance: 4
category: academic
related_publications: false
giscus_comments: false
---

## Overview

Two open problems I'm actively thinking through beyond the current experiments in [ECHO](/projects/3_project/), [`mdlm_refine`](/projects/5_project/), and [`dvd`](/projects/6_project/). Both are early-stage — ideas and initial exploration, not yet shipped repos — but they're the direction this research is heading.

## A Diffusion-Native Optimizer

Every widely-used optimizer (Adam, AdamW, Lion, etc.) was tuned against the loss landscape of autoregressive next-token prediction. MDLM training doesn't look like that: the loss is averaged over randomly sampled mask ratios and timesteps, and the difficulty of the denoising objective varies enormously depending on how corrupted the input is — predicting a token from a 5%-masked sequence and a 95%-masked sequence are very different optimization problems, but standard optimizers treat every gradient update the same way.

Continuous diffusion models already address an analogous issue with SNR-weighted losses that account for noise-level-dependent difficulty. The open question here is whether that idea should live in the optimizer itself, not just the loss — e.g., timestep-conditioned learning rates or update scaling that accounts for the very different gradient statistics at different mask ratios, rather than asking a single global learning rate schedule to do that job.

## MLA + Sparse Attention for Long-Context MDLMs

MLA (Multi-Head Latent Attention) and DSA (DeepSeek Sparse Attention) were both built to cut the cost of attention in autoregressive causal models — compressing the KV cache and sparsifying attention patterns, respectively. MDLMs have arguably more to gain from both, for the opposite reason DVD exists: since there's no causal KV cache to reuse across steps, an MDLM pays full quadratic attention cost over the *entire* context at *every single denoising step*, not once per generated token. That cost compounds fast as context length grows, and it's a big part of why MDLMs are hard to scale to long-context use cases today.

Applying MLA and DSA here isn't a direct port, since both were designed around causal, incremental decoding rather than bidirectional, full-context, multi-step denoising. The interesting part is figuring out how latent-compressed and sparse attention patterns should adapt to a setting where the model re-attends to the whole (evolving) sequence dozens of times per generation instead of extending a cache by one token at a time.

**Status**: Exploratory — these are the two problems I'm currently most focused on solving next.
