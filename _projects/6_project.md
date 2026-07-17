---
layout: page
title: speculative decoding for diffusion LMs (dvd)
description: A lightweight KV-cached MDLM drafter paired with a bidirectional verifier
importance: 3
category: academic
related_publications: false
giscus_comments: false
---

## Overview

Speculative decoding made autoregressive inference dramatically faster by letting a cheap draft model propose tokens that a larger verifier model checks in parallel. MDLMs can't reuse that trick directly: they're bidirectional, so there's no causal KV cache to carry across denoising steps, and each step re-attends over the full context from scratch. `dvd` (DrafterVerifierDiffusion) is an attempt to bring the speculative decoding idea to diffusion generation anyway.

**Repo**: [github.com/Satgoy152/dvd](https://github.com/Satgoy152/dvd) (earlier iteration: [DualDiffusion](https://github.com/Satgoy152/DualDiffusion))

## Method

`dvd` splits the drafting and verification roles across two MDLMs with different jobs:

- **Drafter**: a lightweight MDLM that keeps a KV cache and rapidly proposes multiple denoising steps ahead, trading some accuracy for speed
- **Verifier**: a full bidirectional MDLM that checks the drafted tokens against the full context in parallel, accepting correct spans and rejecting the rest — the same accept/reject structure that makes autoregressive speculative decoding fast, adapted to a setting where "next token" doesn't exist

## Why This Is Hard (and Worth Doing)

The reason MDLMs are slow isn't just step count — it's that every denoising step pays full, non-causal attention over the entire sequence, since there's no incremental cache to lean on the way autoregressive decoding does. A drafter that can propose several denoising steps cheaply, verified in a single parallel pass by the full model, is one of the more direct ways to cut that cost without changing the underlying MDLM architecture.

**Status**: Active — this work sits alongside the [training-time self-correction](/projects/5_project/) and [ECHO training](/projects/3_project/) work as part of a broader push to make MDLMs practical at scale, both to train and to serve.
