# <img src="assets/am_logo.png" style="vertical-align: middle; width: 35px;"> a-m-models [![Generic badge](https://img.shields.io/badge/🤗-am%20team-green.svg)](https://huggingface.co/a-m-team)

*Read this in [English](README_en.md).*

a-m-models 是由 a-m-teams 发起的一个开源项目，致力于对大语言模型（LLMs）以及通用人工智能（AGI）的前沿技术进行深入探索与实践。我们的团队由一群充满热情的研究人员和开发者组成，聚焦于大模型的理论创新、架构设计以及实战应用，旨在逐步逼近通用人工智能（AGI）的实现。本项目旨在开源分享我们在大模型领域的最新研究成果与实践经验，希望能够推动社区对AGI技术的深度交流与共同进步。

## 🔄 最近更新

* [2025-03-25] 更新技术报告[1.4 Million Open-Source Distilled Reasoning Dataset to Empower Large Language Model Traning](https://github.com/a-m-team/a-m-models/blob/main/docs/AM-DeepSeek-R1-Distilled-Dataset.pdf)，开源140万条蒸馏推理数据，复现DeepSeek-R1蒸馏模型效果

* [2025-03-25] 更新技术报告[Think Twice: Enhancing LLM Reasoning by Scaling Multi-round Test-time Thinking](https://github.com/a-m-team/a-m-models/blob/main/docs/Think-Twice.pdf)，介绍了一种简单且有效的测试阶段扩展方法——多轮思考，其推动了SOTA模型效果的进一步提升

## 📑 研究报告

### [Think Twice: Enhancing LLM Reasoning by Scaling Multi-round Test-time Thinking](https://github.com/a-m-team/a-m-models/blob/main/docs/Think-Twice.pdf)

近年来，以OpenAI-o1和DeepSeek-R1为代表的大语言模型（LLMs）取得了显著进展，这些进展表明，通过测试阶段扩展推理流程（test-time scaling），可显著提升模型表现。然而，目前的模型仍受到处理长文本能力和强化学习（RL）训练效率的限制。为解决这些问题，我们提出了一种简单且有效的测试阶段扩展方法——多轮思考（Multi-round Thinking）。该方法通过将模型先前的回答作为下一轮推理的提示（prompts），迭代地精进模型的推理过程。在包括QwQ-32B和DeepSeek-R1在内的多个模型上的大量实验表明，多轮思考能够在AIME 2024、MATH-500、GPQA-diamond和LiveCodeBench等多个基准测试中稳定提升模型表现。例如，在AIME 2024数据集中，QwQ-32B的准确率从第一轮的80.3%提高到第二轮的82.1%，DeepSeek-R1也表现出了类似的提升，从79.7%提高到82.0%。这些结果证明，多轮思考是一种适用广泛、实施简单且有效提升模型表现的方法，彰显出该方法在未来测试阶段扩展技术发展中的巨大潜力。

The key prompt:
```
Original question prompt
The assistant’s previous answer is: <answer> last round answer </answer>, and please re-answer.
```

<img src="assets/Think-Twice-QwQ.png" alt="alt text" width="600px">
<img src="assets/Think-Twice-DeepSeek-R1.png" alt="alt text" width="600px">


### 不同基准测试中单轮思考（第1轮）与多轮思考（第2-4轮）的模型表现对比（pass@1）

| **Model**                              | **Round** | **AIME 2024 pass@1** | **MATH500 pass@1** | **GPQA-Diamond pass@1** | **LiveCodeBench pass@1** | **Average** |
|----------------------------------------|-----------|----------------------|--------------------|-------------------------|--------------------------|-------------|
| **Deepseek-R1**                        | 1         | 79.7                 | 97.6               | 74.0                    | 65.3                     | 79.2        |
|                                        | **2**     | **82.0**             | **97.6**           | **74.8**                | **67.1**                 | **80.4**    |
| **QwQ-32B**                            | 1         | 80.3                 | 97.2               | 65.9                    | 63.0                     | 76.6        |
|                                        | 2         | 82.1                 | 97.8               | 67.2                    | 64.7                     | 78.0        |
|                                        | 3         | 82.8                 | 97.8               | 67.5                    | 65.2                     | 78.3        |
|                                        | **4**     | **83.1**             | **97.7**           | **68.1**                | **66.0**                 | **78.7**    |
| **DeepSeek-R1-Distill-Qwen-32B**       | 1         | 72.0                 | 96.0               | 60.1                    | 57.0                     | 71.3        |
|                                        | **2**     | **75.1**             | **96.3**           | **61.3**                | **57.6**                 | **72.6**    |
| **DeepSeek-R1-Distill-Qwen-7B**        | 1         | 56.9                 | 93.4               | 49.2                    | 35.0                     | 58.6        |
|                                        | **2**     | **58.4**             | **93.9**           | **49.4**                | **36.7**                 | **59.6**    |
| **AM-Distill-Qwen-32B**                | 1         | 72.8                 | 96.2               | 62.3                    | 58.3                     | 72.4        |
|                                        | **2**     | **76.7**             | **97.2**           | **62.8**                | **60.2**                 | **74.2**    |

---
---

### [1.4 Million Open-Source Distilled Reasoning Dataset to Empower Large Language Model Traning](https://github.com/a-m-team/a-m-models/blob/main/docs/AM-DeepSeek-R1-Distilled-Dataset.pdf) [![Generic badge](https://img.shields.io/badge/🤗-1.4M-green.svg)](https://huggingface.co/datasets/a-m-team/AM-DeepSeek-R1-Distilled-1.4M)

AM-DeepSeek-R1-Distilled 是一个大规模、带有推理过程的通用推理任务数据集，包含大量高质量且具备挑战性的推理问题。这些问题收集自多个开源数据集，经过语义去重和精细清理，以消除可能的测试集污染风险。数据集中所有的答案均由推理模型（主要为 DeepSeek-R1）蒸馏而成，并经过严格的验证流程：数学问题通过与标准答案对比进行验证，代码问题通过测试用例进行核验，而其他类型任务则通过奖励模型进行评估。基于该数据集仅使用简单监督微调（SFT）训练的 AM-Distill-Qwen-32B 模型，在 AIME2024、MATH-500、GPQA-Diamond 以及 LiveCodeBench 四项基准测试上，均超越了DeepSeek-R1-Distill-Qwen-32B 模型。为了推动更强大的推理导向大语言模型（LLMs）发展，我们开源了这140万条问题及其对应的答案。该数据集已公开在 <https://huggingface.co/datasets/a-m-team/AM-DeepSeek-R1-Distilled-1.4M。>

<img src="assets/AM-DeepSeek-R1-Distilled.jpeg" alt="alt text" width="600px">

## Citation

如果您觉得我们的工作对您的研究有所帮助，欢迎给我们点个星 :star:, 并引用我们的工作:pencil:

```BibTeX
@misc{tian2025thinktwiceenhancingllm,
      title={Think Twice: Enhancing LLM Reasoning by Scaling Multi-round Test-time Thinking}, 
      author={Xiaoyu Tian and Sitong Zhao and Haotian Wang and Shuaiting Chen and Yunjie Ji and Yiping Peng and Han Zhao and Xiangang Li},
      year={2025},
      eprint={2503.19855},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2503.19855}, 
}

@misc{zhao202514millionopensourcedistilled,
      title={1.4 Million Open-Source Distilled Reasoning Dataset to Empower Large Language Model Training}, 
      author={Han Zhao and Haotian Wang and Yiping Peng and Sitong Zhao and Xiaoyu Tian and Shuaiting Chen and Yunjie Ji and Xiangang Li},
      year={2025},
      eprint={2503.19633},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2503.19633}, 
}


```
