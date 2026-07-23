# Blueprint2Motion

<p align="center">
  <strong>Two-Stage Human-Object Manipulation Motion Synthesis via Limb-Object Blueprint</strong>
</p>

<p align="center">
  <a href="https://doi.org/10.1002/cav.70160">Paper</a>
  &nbsp;|&nbsp;
  <a href="#overview">Overview</a>
  &nbsp;|&nbsp;
  <a href="#citation">Citation</a>
</p>

> Official source-code repository for **Blueprint2Motion**, a two-stage approach to synthesizing human-object manipulation motions through a limb-object blueprint.

## Overview

Human-object manipulation motion is challenging because realistic motion must preserve both human-body plausibility and meaningful interaction with the object. Blueprint2Motion frames this problem as a two-stage synthesis process, using a limb-object blueprint to guide motion generation.

This repository is being prepared to host the project implementation, training and evaluation code, pretrained checkpoints, and reproducible experiment instructions.

## Project Status

The codebase is under preparation. The repository will include:

- Data preparation and preprocessing scripts
- Model training and inference pipelines
- Evaluation tools for generated human-object motions
- Checkpoints and reproduction instructions

## Paper

**Blueprint2Motion: Two-Stage Human-Object Manipulation Motion Synthesis via Limb-Object Blueprint**  
L. Li, Z. Liu, T. Liu, X. Dai, and Y. Chai.  
*Computer Animation and Virtual Worlds*, 37(4), e70160, 2026.

DOI: [10.1002/cav.70160](https://doi.org/10.1002/cav.70160)

## Citation

```bibtex
@article{li2026blueprint2motion,
  title   = {Blueprint2Motion: Two-Stage Human-Object Manipulation Motion Synthesis via Limb-Object Blueprint},
  author  = {Li, L. and Liu, Z. and Liu, T. and Dai, X. and Chai, Y.},
  journal = {Computer Animation and Virtual Worlds},
  volume  = {37},
  number  = {4},
  pages   = {e70160},
  year    = {2026},
  doi     = {10.1002/cav.70160}
}
```

## License

The license for the source code and released assets will be added with the public implementation.

---

## Archived Notes

The previous LLM fine-tuning paper collection is retained below for reference.

# 大模型微调论文整理

整理日期：2026-07-21

这个资料夹按当前大模型微调/后训练技术路线整理。PDF 文件按论文名称命名，分在对应技术方向目录中。

## 建议阅读路线

1. **PEFT 基础**：LoRA -> QLoRA
2. **PEFT 前沿变体**：DoRA -> PiSSA -> MoRA -> GaLore -> Spectrum
3. **偏好对齐**：DPO -> KTO -> ORPO -> SimPO
4. **推理强化学习**：DeepSeekMath/GRPO -> DeepSeek-R1 -> DAPO
5. **长上下文与部署组合**：LongLoRA -> TIES-Merging -> Mixture of LoRA Experts -> DynMoLE
6. **综述补全**：Fine-tuning Large Language Models with Limited Data - A Survey

## 01-PEFT 参数高效微调

| 年份 | 论文 | 本地文件 | 链接 | 关注点 |
|---|---|---|---|---|
| 2021 | LoRA: Low-Rank Adaptation of Large Language Models | `01-PEFT参数高效微调/LoRA - Low-Rank Adaptation of Large Language Models.pdf` | https://arxiv.org/abs/2106.09685 | LoRA 基础方法，低秩增量微调 |
| 2023 | QLoRA: Efficient Finetuning of Quantized LLMs | `01-PEFT参数高效微调/QLoRA - Efficient Finetuning of Quantized LLMs.pdf` | https://arxiv.org/abs/2305.14314 | 4-bit 量化基座 + LoRA |
| 2024 | DoRA: Weight-Decomposed Low-Rank Adaptation | `01-PEFT参数高效微调/DoRA - Weight-Decomposed Low-Rank Adaptation.pdf` | https://arxiv.org/abs/2402.09353 | 把权重更新分成 magnitude 和 direction |
| 2024 | PiSSA: Principal Singular values and Singular vectors Adaptation | `01-PEFT参数高效微调/PiSSA - Principal Singular values and Singular vectors Adaptation.pdf` | https://arxiv.org/abs/2404.02948 | SVD 初始化 adapter，加速收敛 |
| 2024 | MoRA: High-Rank Updating for Parameter-Efficient Fine-Tuning | `01-PEFT参数高效微调/MoRA - High-Rank Updating for Parameter-Efficient Fine-Tuning.pdf` | https://arxiv.org/abs/2405.12130 | 高秩更新，增强学习新知识能力 |
| 2024 | GaLore: Memory-Efficient LLM Training by Gradient Low-Rank Projection | `01-PEFT参数高效微调/GaLore - Memory-Efficient LLM Training by Gradient Low-Rank Projection.pdf` | https://arxiv.org/abs/2403.03507 | 低秩梯度投影，节省优化器显存 |
| 2024 | Spectrum: Targeted Training on Signal to Noise Ratio | `01-PEFT参数高效微调/Spectrum - Targeted Training on Signal to Noise Ratio.pdf` | https://arxiv.org/abs/2406.06623 | 按模块信噪比选择性训练 |

## 02-Preference 偏好对齐

| 年份 | 论文 | 本地文件 | 链接 | 关注点 |
|---|---|---|---|---|
| 2023 | Direct Preference Optimization | `02-Preference偏好对齐/DPO - Direct Preference Optimization.pdf` | https://arxiv.org/abs/2305.18290 | 不显式训练 reward model 的偏好优化 |
| 2024 | KTO: Model Alignment as Prospect Theoretic Optimization | `02-Preference偏好对齐/KTO - Model Alignment as Prospect Theoretic Optimization.pdf` | https://arxiv.org/abs/2402.01306 | 只需要 desirable/undesirable 标签 |
| 2024 | ORPO: Monolithic Preference Optimization without Reference Model | `02-Preference偏好对齐/ORPO - Monolithic Preference Optimization without Reference Model.pdf` | https://arxiv.org/abs/2403.07691 | SFT 和偏好优化合一，无 reference model |
| 2024 | SimPO: Simple Preference Optimization | `02-Preference偏好对齐/SimPO - Simple Preference Optimization.pdf` | https://arxiv.org/abs/2405.14734 | 简化 preference optimization，无 reference model |

## 03-RLVR 强化学习与推理

| 年份 | 论文 | 本地文件 | 链接 | 关注点 |
|---|---|---|---|---|
| 2024 | DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models | `03-RLVR强化学习与推理/DeepSeekMath - Pushing the Limits of Mathematical Reasoning in Open Language Models.pdf` | https://arxiv.org/abs/2402.03300 | GRPO 来源，数学推理 RL |
| 2025 | DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning | `03-RLVR强化学习与推理/DeepSeek-R1 - Incentivizing Reasoning Capability in LLMs via Reinforcement Learning.pdf` | https://arxiv.org/abs/2501.12948 | RL 激发推理能力，多阶段后训练 |
| 2025 | DAPO: An Open-Source LLM Reinforcement Learning System at Scale | `03-RLVR强化学习与推理/DAPO - An Open-Source LLM Reinforcement Learning System at Scale.pdf` | https://arxiv.org/abs/2503.14476 | 大规模开源 RL 系统与训练技巧 |

## 04-LongContext 与领域适配

| 年份 | 论文 | 本地文件 | 链接 | 关注点 |
|---|---|---|---|---|
| 2023 | LongLoRA: Efficient Fine-tuning of Long-Context Large Language Models | `04-LongContext与领域适配/LongLoRA - Efficient Fine-tuning of Long-Context Large Language Models.pdf` | https://arxiv.org/abs/2309.12307 | 长上下文高效微调 |

## 05-Merging 与多专家 LoRA

| 年份 | 论文 | 本地文件 | 链接 | 关注点 |
|---|---|---|---|---|
| 2023 | TIES-Merging: Resolving Interference When Merging Models | `05-Merging与多专家LoRA/TIES-Merging - Resolving Interference When Merging Models.pdf` | https://arxiv.org/abs/2306.01708 | 多模型/adapter 合并中的冲突处理 |
| 2024 | Mixture of LoRA Experts | `05-Merging与多专家LoRA/Mixture of LoRA Experts.pdf` | https://arxiv.org/abs/2404.13628 | 多 LoRA 专家组合 |
| 2025 | DynMoLE: Dynamic Mixture of LoRA Experts | `05-Merging与多专家LoRA/DynMoLE - Dynamic Mixture of LoRA Experts.pdf` | https://arxiv.org/abs/2504.00661 | 动态路由 LoRA experts |

## 06-Surveys 综述

| 年份 | 论文 | 本地文件 | 链接 | 关注点 |
|---|---|---|---|---|
| 2026 | Fine-tuning Large Language Models with Limited Data: A Survey | `06-Surveys综述/Fine-tuning Large Language Models with Limited Data - A Survey.pdf` | https://aclanthology.org/2026.tacl-1.17/ | 少数据微调综述 |

## 只保留链接的补充资料

| 资料 | 链接 | 说明 |
|---|---|---|
| OpenAI Reinforcement Fine-Tuning Guide | https://developers.openai.com/api/docs/guides/reinforcement-fine-tuning | RFT 工程文档，不是论文 PDF |


# 学习笔记

## LoRA ： Low-Rank Adaptation
LoRA : 通过影响原始权重的更新方向，优化垂直任务。

Adapter:
在 Transformer 层中插入小型 bottleneck 模块，只训练 adapter。

Prefix tuning:
第1层 attention: [prefix K/V] + 原始 K/V
第2层 attention: [prefix K/V] + 原始 K/V

Word embeddings in lieu of fine-tuning:
[soft token embeddings] + 用户输入 -> Transformer,
不是 fine-tune 模型，而是 fine-tune 一小段输入 embedding，让冻结模型“以为”自己收到了一个最适合任务的提示。

## DLoRA
LoRA减少了可训练参数的数量，DLoRA则通过减少（冻结模型的参数存储）来提高训练效率，减少显存的占用。具体变化有以下三点体现：
4-bit NormalFloat better than 4-bit int and 4-bit floats in normally distributed data
Double Quantization : a method that quantizes the quantization constants
Paged Optimizers: using NVIDIA unified memory to avoid the gradient checkpointing memory spikes that occur when
processing a mini-batch with a long sequence length. 
