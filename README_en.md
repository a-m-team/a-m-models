# <img src="assets/am_logo.png" style="vertical-align: middle; width: 35px;"> a-m-models [![Generic badge](https://img.shields.io/badge/🤗-am%20team-green.svg)](https://huggingface.co/a-m-team)

*[中文README](README.md).*

a-m-models is an open-source initiative led by the a-m-team, dedicated to in-depth exploration and practical application of cutting-edge technologies in Large Language Models (LLMs) and Artificial General Intelligence (AGI). Our team, composed of passionate researchers and developers, focuses on theoretical innovation, architectural design, and practical deployment of large models, aiming to gradually approach the realization of AGI. This project aims to openly share our latest research results and practical experiences in the domain of large models, fostering deeper community exchanges and mutual advancement in AGI technology.

## 🔄 Recent Updates

* [2025-04-01] Updated technical report [How Difficulty-Aware Staged Reinforcement Learning Enhances LLMs' Reasoning Capabilities: A Preliminary Experimental Study](https://github.com/a-m-team/a-m-models/blob/main/docs/How-Difficulty-Aware-Staged-Reinforcement-Learning-Enhances-LLMs-Reasoning-Capabilities-A-Preliminary-Experimental-Study.pdf), introduce a staged training approach that gradually exposes models to more challenging tasks, improving their reasoning capabilities.

* [2025-03-25] Updated technical report [1.4 Million Open-Source Distilled Reasoning Dataset to Empower Large Language Model Training](https://github.com/a-m-team/a-m-models/blob/main/docs/AM-DeepSeek-R1-Distilled-Dataset.pdf), open-sourced 1.4 million distilled reasoning data entries, reproducing the performance of DeepSeek-R1 distilled models.

* [2025-03-25] Updated the technical report [Think Twice: Enhancing LLM Reasoning by Scaling Multi-round Test-time Thinking](https://github.com/a-m-team/a-m-models/blob/main/docs/Think-Twice.pdf), introducing a simple yet effective test-time scaling approach—Multi-round Thinking—which further advances the state-of-the-art model performance

## 📑 Research Reports

### [How Difficulty-Aware Staged Reinforcement Learning Enhances LLMs' Reasoning Capabilities: A Preliminary Experimental Study](https://github.com/a-m-team/a-m-models/blob/main/docs/How-Difficulty-Aware-Staged-Reinforcement-Learning-Enhances-LLMs-Reasoning-Capabilities-A-Preliminary-Experimental-Study.pdf)

Improving the reasoning abilities of Large Language Models (LLMs) efficiently and at scale is a key challenge in AI research. This paper investigates how difficulty-aware staged reinforcement learning (RL) strategies can boost LLM performance. We show that selecting training data based on difficulty levels enhances RL optimization. Additionally, we propose a staged training approach that gradually exposes models to more challenging tasks, improving their reasoning capabilities. Besides, our results highlight significant benefits when training models on both mathematical reasoning and code generation tasks.

#### 1. Data Difficulty Selection

Carefully selecting RL training data based on appropriate difficulty metrics is critical. A moderate difficulty level enhances learning efficiency, balancing the need for adequate challenge against the risk of overwhelming the learning process with overly difficult scenarios.

<img src="assets/staged-RL-data-difficulty.png" alt="alt text" width="600px">

#### 2. Staged Training

By selecting appropriately challenging data and incorporating staged training, we can significantly improve the performance of LLMs on reasoning tasks. (Due to the absence of code-related training data, its performance on LiveCodeBench is essentially the same as that of the base model.)

<img src="assets/staged-RL-2stage.png" alt="alt text" width="600px">

#### 3. Simultaneous Training on Mathematics and Code

Mixing mathematical reasoning and code generation tasks during training results in cross-domain improvements, providing strong evidence for the benefits of multi-domain training.

<img src="assets/staged-RL-math-code.png" alt="alt text" width="600px">

### [Think Twice: Enhancing LLM Reasoning by Scaling Multi-round Test-time Thinking](https://github.com/a-m-team/a-m-models/blob/main/docs/Think-Twice.pdf)

Recent advances in large language models (LLMs), such as OpenAI-o1 and DeepSeek-R1, have demonstrated the effectiveness of test-time scaling, where extended reasoning processes substantially enhance model performance. Despite this, current models are constrained by limitations in handling long texts and reinforcement learning (RL) training efficiency. To address these issues, we propose a simple yet effective test-time scaling approach—\textbf{Multi-round Thinking}. This method iteratively refines model reasoning by leveraging previous answers as prompts for subsequent rounds. Extensive experiments across multiple models, including QwQ-32B and DeepSeek-R1, consistently show performance improvements on various benchmarks such as AIME 2024, MATH-500, GPQA-diamond, and LiveCodeBench. For instance, the accuracy of QwQ-32B improved from 80.3\% (Round 1) to 82.1\% (Round 2) on the AIME 2024 dataset, while DeepSeek-R1 showed a similar increase from 79.7\% to 82.0\%. These results confirm that \textbf{Multi-round Thinking} is a broadly applicable, straightforward approach to achieving stable enhancements in model performance, underscoring its potential for future developments in test-time scaling techniques.

The key prompt:
```
Original question prompt
The assistant’s previous answer is: <answer> last round answer </answer>, and please re-answer.
```

<img src="assets/Think-Twice-QwQ.png" alt="alt text" width="600px">
<img src="assets/Think-Twice-DeepSeek-R1.png" alt="alt text" width="600px">

### Model Performance Comparison (pass@1 accuracy) Between Single-round (Round 1) and Multi-round Thinking (Round 2-4) Across Different Benchmarks

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


### [1.4 Million Open-Source Distilled Reasoning Dataset to Empower Large Language Model Training](https://github.com/a-m-team/a-m-models/blob/main/docs/AM-DeepSeek-R1-Distilled-Dataset.pdf) [![Generic badge](https://img.shields.io/badge/🤗-1.4M-green.svg)](https://huggingface.co/datasets/a-m-team/AM-DeepSeek-R1-Distilled-1.4M)

The AM-DeepSeek-R1-Distilled is a large-scale dataset with thinking traces for general reasoning tasks, composed of high-quality and challenging reasoning problems. These problems are collected from a multitude of open-source datasets, subjected to semantic deduplication and meticulous cleaning to eliminate test set contamination. All responses within the dataset are distilled from reasoning models (pre-dominantly DeepSeek-R1) and have undergone rigorous verification procedures. Mathematical problems are validated by checking against reference answers, code problems are verified using test cases, and other tasks are evaluated with the aid of a reward model. The AM-Distill-Qwen-32B model, which was trained through only simple Supervised Fine-Tuning (SFT) using this batch of data, outperformed the DeepSeek-R1-Distill-Qwen-32B model on four benchmarks: AIME2024, MATH-500, GPQA-Diamond, and LiveCodeBench. We are releasing these 1.4 million problems and their corresponding responses to the research community with the objective of fostering the development of powerful reasoning-oriented Large Language Models (LLMs). The dataset was published in <https://huggingface.co/datasets/a-m-team/AM-DeepSeek-R1-Distilled-1.4M>.

<img src="assets/AM-DeepSeek-R1-Distilled.jpeg" alt="alt text" width="600px">


## Citation

If you find our work helpful to your research, please star our repository :star: and cite our work :pencil:

```BibTeX
@misc{ji2025difficultyawarestagedreinforcementlearning,
      title={How Difficulty-Aware Staged Reinforcement Learning Enhances LLMs' Reasoning Capabilities: A Preliminary Experimental Study}, 
      author={Yunjie Ji and Sitong Zhao and Xiaoyu Tian and Haotian Wang and Shuaiting Chen and Yiping Peng and Han Zhao and Xiangang Li},
      year={2025},
      eprint={2504.00829},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2504.00829}, 
}

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
