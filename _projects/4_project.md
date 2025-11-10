---
layout: page
title: memory layers for continual learning in LLMs
description: efficient continual learning through optimized memory layers
importance: 4
category: research
related_publications: false
giscus_comments: false
---
## Overview

This research project investigates whether large language models can effectively use memory layers through fine-tuning rather than training from scratch. Working under the supervision of Prof. Samet Oymak at the University of Michigan, we're exploring efficient approaches to continual learning that could enable existing models to adapt and learn continuously without catastrophic forgetting.

**Timeline**: Ongoing

## Research Motivation

Traditional approaches to adding memory capabilities to language models require expensive ground-up pretraining. Our research asks a crucial question: **Can we retrofit existing LLMs with memory layers through fine-tuning alone?**

If successful, this approach would:

- Enable many current models to use memory layers efficiently
- Provide an efficient source of continual learning
- Reduce computational costs compared to full retraining

## Catastrophic Forgetting Problem

A fundamental challenge in continual learning is **catastrophic forgetting**, where models lose previously learned knowledge when learning new information. Recent work by Lin et al. (2025) demonstrates that memory layers are resistant to catastrophic forgetting, making them a promising approach for continual learning in LLMs.

## Research Questions

1. **Fine-tuning Feasibility**: Can memory layers be effectively integrated into pre-trained LLMs through fine-tuning?
2. **Performance**: How do fine-tuned memory layers compare to models trained with memory from scratch?
3. **Efficiency**: What are the computational trade-offs between retrofitting vs. full retraining?
4. **Continual Learning**: How well do fine-tuned memory layers support ongoing learning without forgetting?

## Technical Approach

- **Base Models**: Working with existing pre-trained LLMs
- **Memory Layer Integration**: Designing efficient fine-tuning procedures for memory layer insertion
- **Optimization**: Developing optimized training strategies for memory layer adaptation
- **Evaluation**: Measuring continual learning performance and forgetting metrics

## Potential Impact

If successful, this research could:

- **Democratize advanced capabilities**: Enable existing models to gain memory and continual learning abilities
- **Reduce costs**: Avoid expensive retraining from scratch
- **Enable adaptation**: Allow models to continuously learn and adapt in deployment
- **Improve robustness**: Reduce catastrophic forgetting in real-world applications

## Related Work

Building on recent findings (Lin et al. 2025) showing that memory layers provide resistance to catastrophic forgetting, we're exploring practical implementation strategies that make these benefits accessible to existing models.

## Collaboration

**Prof. Samet Oymak**
University of Michigan, Ann Arbor
