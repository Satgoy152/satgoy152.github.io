---
layout: page
title: fairness transformer
description: Transformer architecture for discrete fair division problems
importance: 1
category: academic
related_publications: false
giscus_comments: false
---
## Overview

This research project focuses on designing and training a transformer architecture to solve discrete fair division problems in game theory. Working under the supervision of Dr. Mithun Chakraborty at the University of Michigan, we're developing machine learning approaches to tackle NP-hard allocation problems that are computationally challenging for traditional algorithms.

**Timeline**: June 2025 – October 2025
**Status**: AAMAS Pending

## Research Contributions

### Architecture Design

Designed and trained a novel transformer architecture specifically tailored for discrete fair division problems. The model learns to generate fair allocations by understanding complex fairness constraints and agent preferences.

### Comprehensive Evaluation

- Evaluated 4 baseline approaches on 1 million fairness allocation problems
- Built optimized Python pipelines for large-scale experimentation
- Created robust evaluation framework using NumPy and PyTorch

### Performance Optimization

Achieved dramatic improvements in evaluation efficiency:

- **Original evaluation time**: 4 hours
- **Optimized evaluation time**: 10 minutes
- **Speedup**: 24x improvement through pipeline optimization

### Approximation Accuracy

Approximated NP-hard allocation computations using Linear Programming with **99.1% accuracy**, demonstrating that ML-based approaches can effectively handle computationally intractable problems.

## Technical Approach

- **Model Architecture**: Transformer-based neural network
- **Problem Domain**: Discrete fair division and resource allocation
- **Optimization Technique**: Linear Programming approximations
- **Evaluation Framework**: Custom NumPy/PyTorch pipeline
- **Scale**: Tested on 1 million problem instances

## Key Challenges Addressed

1. **Computational Complexity**: Fair division problems are NP-hard, making exact solutions impractical for large instances
2. **Fairness Guarantees**: Balancing multiple fairness criteria while maintaining computational efficiency
3. **Scalability**: Handling large-scale evaluation across diverse problem instances
4. **Approximation Quality**: Achieving high accuracy when approximating optimal solutions

## Collaboration

**Dr. Mithun Chakraborty**
University of Michigan, Ann Arbor

## Publication Status

Paper submitted to AAMAS (International Conference on Autonomous Agents and Multiagent Systems)
