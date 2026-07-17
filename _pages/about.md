---
layout: about
title: about
permalink: /
subtitle: AI Researcher — Diffusion Language Models & ML Systems

profile:
  align: right
  image: prof_pic.jpg
  image_circular: true # crops the image to make it circular
  more_info: >
    <p>Ann Arbor, MI / Bay Area, CA</p>

news: true # includes a list of news items
selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page
---
Hi, I'm Satyam Goyal. I work on diffusion language models — trying to make masked diffusion a real alternative to autoregressive generation, and building the systems that let those ideas run at scale. I'm a Masters student in Computer Science at the University of Michigan, and currently an AI Research Intern at Snowflake.

**Diffusion language models.** At the University of Michigan AI Lab, advised by Prof. JJ Park, I'm building **ECHO**, a sampling-aware training algorithm for Masked Diffusion Language Models (MDLMs) grounded in constrained Gibbs sampling (MCMC) — it outperforms comparable SOTA methods by 15% on reasoning benchmarks, and I've used it to pretrain and finetune models from 100M to 8B parameters on up to 50B tokens across 8xA100 clusters. Alongside that, I'm building [`mdlm_refine`](https://github.com/Satgoy152/mdlm_refine), which bakes self-correction directly into training instead of leaving it to inference-time decoding tricks — a training-time counterpart to work like Kuleshov et al.'s recent *Learn from Your Mistakes: Self-Correcting Masked Diffusion Models* (Cornell / Inception Labs). Early results (`refine_3`) hit perfect accuracy on Sudoku and beat inference-time-correction baselines on Boolean SAT and Countdown at matched compute.

I'm also chasing the systems bottlenecks that keep MDLMs from scaling: `dvd`, a speculative decoding scheme pairing a lightweight KV-cached MDLM drafter with a bidirectional verifier; a training optimizer designed around diffusion's noise-level-dependent loss landscape instead of one borrowed from autoregressive pretraining; and adapting Multi-Head Latent Attention and DeepSeek Sparse Attention to MDLMs, since bidirectional diffusion pays full quadratic attention cost at *every* denoising step rather than once per token — the thing that currently caps how far these models can push context length.

**Systems.** I like sitting on both sides of the stack — designing the algorithm and making sure it survives a real cluster. At Snowflake, I work on the GLM 5.2 serving team: KV transfer, routing layers in llm-d, and vLLM kernel optimizations that helped bring Snowflake among the top-3 DeepSeek V4 Pro inference providers. Before that, at IBM Research, I built a KV-cache-aware router for IBM/Google/Red Hat's distributed inference platform and an open-source vLLM simulator (Go/Python) predicting TTFT and ITL with 95% accuracy at 500x real-time speed.

**Other research.** A transformer for NP-hard fair division problems with Dr. Mithun Chakraborty, retrofitting Qwen-2.5 with sparse memory layers for continual learning (90% less catastrophic forgetting) with Prof. Samet Oymak, and [IOLBench](https://arxiv.org/abs/2501.04249), a 1,000+ task benchmark exposing a 40% reasoning degradation across SOTA LLMs, with Dr. Soham Dan (Microsoft Research).

Outside of all this, I play the Hindustani flute and I'm always up for a game of table tennis.
