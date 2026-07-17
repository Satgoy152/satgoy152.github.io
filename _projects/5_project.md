---
layout: page
title: self-correcting MDLMs (mdlm_refine)
description: Training-time self-correction for masked diffusion, vs. inference-time correction methods
importance: 2
category: academic
related_publications: false
giscus_comments: false
---

## Overview

Masked diffusion language models generate text by iteratively unmasking tokens, but once a token is committed, standard MDLM training gives the model no mechanism to notice or fix a mistake it made a few steps earlier. Most existing fixes for this address it at **inference time** — running extra correction passes after generation. [`mdlm_refine`](https://github.com/Satgoy152/mdlm_refine) takes the opposite approach: teach the model to self-correct **during training**, so correction is part of what the model learns to do rather than a bolted-on decoding trick.

**Repo**: [github.com/Satgoy152/mdlm_refine](https://github.com/Satgoy152/mdlm_refine)
**Status**: Preliminary — LLaDA-scale and molecule-generation experiments in progress

## Related Work

This is a direct response to a growing line of inference-time self-correction work for diffusion LMs, most notably Kuleshov et al.'s recent *Learn from Your Mistakes: Self-Correcting Masked Diffusion Models* (Cornell — Kuleshov is also a co-founder of Inception Labs) and similar approaches like **ProSeCo**. Those methods are effective, but they treat correction as something you graft onto a frozen model after the fact. `refine` asks whether you get better results, and simpler inference, by training the correction behavior in from the start.

## Method

`refine` is a two-pass training procedure:

- **Pass 1**: The model predicts masked tokens in a partially masked sequence, as in standard MDLM training.
- **Pass 2**: The predicted tokens are inserted back into the sequence, and the model is trained to re-examine that sequence and correct pass-1's errors.

Three variants, in increasing order of sophistication:

- **`refine`** — loss computed only on the originally masked positions
- **`refine_2`** — loss spans the full target context, not just the originally masked spots
- **`refine_3`** — unmasked positions are filled with *sampled* (not ground-truth) tokens during pass 2, so the model can't shortcut correction by peeking at the answer

## Results (Preliminary)

On symbolic reasoning tasks, `refine_3` reaches **perfect accuracy on Sudoku (1.000)** and outperforms baselines on **Boolean SAT (0.841)** and **Countdown (0.407)**. On NLP tasks, `refine` achieves better perplexity than the ProSeCo inference-time-correction baseline at lower compute budgets — i.e., cheaper generation for comparable or better quality.

## Why This Matters

If self-correction can be learned during training rather than patched in at inference, it changes the cost model for high-quality diffusion generation: no extra correction passes at decode time, and a model that's internally consistent about fixing its own mistakes rather than relying on external heuristics to catch them.
