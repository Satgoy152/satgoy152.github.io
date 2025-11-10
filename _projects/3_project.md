---
layout: page
title: Improving Masked Diffusion Models
description: Alternative GenAI architectures using RL and confidence-based masking
importance: 3
category: research
related_publications: false
giscus_comments: false
---

## Overview

This research project explores improvements to Masked Diffusion Language Models (MDLMs), an alternative generative AI architecture to traditional autoregressive models. Working with Prof. JJ (Jeong Joon) Park, we're developing novel training techniques and algorithms to enhance the performance and efficiency of MDLMs.

**Timeline**: August 2025 – Present

## Research Goals

Masked Diffusion Language Models represent a promising alternative to standard transformer architectures, offering different trade-offs in generation quality, speed, and training efficiency. Our work focuses on pushing the boundaries of what's possible with MDLMs through innovative training approaches.

## Key Contributions

### Reinforcement Learning Integration
Using Reinforcement Learning techniques combined with confidence-based masking algorithms to improve MDLM performance. This approach allows the model to learn more effective masking strategies during training.

### Large-Scale Training
- Training an **11 billion parameter MDLM** on **100 billion tokens**
- Leveraging Unsloth for efficient training at scale
- Pushing the boundaries of MDLM size and training data

### Novel Algorithmic Approaches
Designing and implementing novel time-based unmasking and masking algorithms that improve upon existing MDLM training procedures. These algorithms optimize:
- Token masking strategies during training
- Unmasking schedules for generation
- Confidence-based decision making

## Technical Approach

- **Model Size**: 11B parameters
- **Training Data**: 100B tokens
- **Training Framework**: Unsloth (optimized training)
- **Key Techniques**:
  - Reinforcement Learning for masking optimization
  - Confidence-based masking algorithms
  - Time-based unmasking strategies
  - Novel masking schedules

## Why MDLMs Matter

Unlike autoregressive models that generate text left-to-right one token at a time, Masked Diffusion Models can:
- Generate multiple tokens in parallel
- Iteratively refine generated text
- Offer different inference speed/quality trade-offs
- Potentially enable new applications

## Research Impact

This work contributes to the growing exploration of alternative architectures for large language models, potentially offering more efficient or capable alternatives to standard transformer-based approaches.

## Collaboration

**Prof. JJ (Jeong Joon) Park**
University of Michigan, Ann Arbor
