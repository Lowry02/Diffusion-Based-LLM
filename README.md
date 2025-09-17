# From Autoregressive LLM to Diffusion-based LLM

A research project exploring the conversion of pretrained autoregressive Large Language Models into diffusion-based models for text generation.

## Overview

This project investigates whether we can start from a pretrained autoregressive LLM and convert it into a diffusion-based one, potentially gaining efficiency improvements and better global coherence while maintaining text generation quality.

### Key Research Question
*Can we start from a pretrained Autoregressive LLM and convert it into a Diffusion based one?*

## Methodology

### Base Model
- **LLaMA 3.2 - 1B** as the foundation model
- Modified from causal attention to bidirectional attention
- Efficient training using LoRA (Low-Rank Adaptation) adapters

### Training Framework
- **Dataset**: Alpaca instruction dataset (52k examples)
- **Approach**: Question-answer format with diverse instruction types
- **Efficiency**: Only 0.1377% of parameters are trainable (1,703,936 out of 1,237,520,384)

### Key Components

#### Diffusion Process
The diffusion approach gradually transforms data into noise and then reconstructs it step by step:
- **Forward Process**: Progressive masking/noising of tokens
- **Backward Process**: Learning to reverse the noise and reconstruct original text
- **Training**: Sample timestep t, apply forward process, make predictions, evaluate loss

#### Architecture Changes
- **Attention Mechanism**: Converted from causal (autoregressive) to bidirectional attention
- **LoRA Adapters**: Efficient fine-tuning with configurable r, alpha, and dropout parameters
- **Target Modules**: Only Attention layers are optimized

## Advantages of Diffusion-based LLMs

1. **Potential Efficiency Gains**: Especially beneficial for long sequences
2. **Better Use of Context & Global Coherence**: Bidirectional attention allows better understanding
3. **Robustness & Diversity**: More varied and stable text generation

## Results

The converted diffusion-based model shows:
- Acceptable text generation quality
- Some degradation compared to the original autoregressive model
- Promising potential for scaling with more parameters

## Conclusions

1. **Feasibility**: Results demonstrate it's possible to convert autoregressive LLMs to diffusion-based ones
2. **Quality Trade-offs**: While not perfect, the results are acceptable for many use cases
3. **Scalability**: Training only a small portion of parameters suggests promising potential for larger models

## Authors

- Matteo Caiola
- Lorenzo Cusin
