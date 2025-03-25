# <img src="assets/am_logo.png" style="vertical-align: middle; width: 35px;"> a-m-models [![Generic badge](https://img.shields.io/badge/🤗-am%20team-green.svg)](https://huggingface.co/a-m-team)

*[中文README](README.md).*

a-m-models is an open-source initiative led by the a-m-team, dedicated to in-depth exploration and practical application of cutting-edge technologies in Large Language Models (LLMs) and Artificial General Intelligence (AGI). Our team, composed of passionate researchers and developers, focuses on theoretical innovation, architectural design, and practical deployment of large models, aiming to gradually approach the realization of AGI. This project aims to openly share our latest research results and practical experiences in the domain of large models, fostering deeper community exchanges and mutual advancement in AGI technology.

## 🔄 Recent Updates

* [2024-03-25] Updated technical report [1.4 Million Open-Source Distilled Reasoning Dataset to Empower Large Language Model Training](https://github.com/a-m-team/a-m-models/blob/main/docs/AM-DeepSeek-R1-Distilled-Dataset.pdf), open-sourced 1.4 million distilled reasoning data entries, reproducing the performance of DeepSeek-R1 distilled models.

* [2024-03-25] Updated the technical report [Think Twice: Enhancing LLM Reasoning by Scaling Multi-round Test-time Thinking](https://github.com/a-m-team/a-m-models/blob/main/docs/Think-Twice.pdf), introducing a simple yet effective test-time scaling approach—Multi-round Thinking—which further advances the state-of-the-art model performance

## 📑 Research Reports

### [Think Twice: Enhancing LLM Reasoning by Scaling Multi-round Test-time Thinking](https://github.com/a-m-team/a-m-models/blob/main/docs/Think-Twice.pdf)

Recent advances in large language models (LLMs), such as OpenAI-o1 and DeepSeek-R1, have demonstrated the effectiveness of test-time scaling, where extended reasoning processes substantially enhance model performance. Despite this, current models are constrained by limitations in handling long texts and reinforcement learning (RL) training efficiency. To address these issues, we propose a simple yet effective test-time scaling approach—\textbf{Multi-round Thinking}. This method iteratively refines model reasoning by leveraging previous answers as prompts for subsequent rounds. Extensive experiments across multiple models, including QwQ-32B and DeepSeek-R1, consistently show performance improvements on various benchmarks such asAIME 2024, MATH-500, GPQA-diamond, and LiveCodeBench. For instance, the accuracy of QwQ-32B improved from 80.3\% (Round 1) to 82.1\% (Round 2) on theAIME 2024 dataset, while DeepSeek-R1 showed a similar increase from 79.7\% to 82.0\%. These results confirm that \textbf{Multi-round Thinking} is a broadly applicable, straightforward approach to achieving stable enhancements in model performance, underscoring its potential for future developments in test-time scaling techniques.

The key prompt:
```
Original question prompt
The assistant’s previous answer is: <answer> last round answer </answer>, and please re-answer.
```

![alt text](assets/Think-Twice-QwQ.png)
![alt text](assets/Think-Twice-DeepSeek-R1.png)


### [1.4 Million Open-Source Distilled Reasoning Dataset to Empower Large Language Model Training](https://github.com/a-m-team/a-m-models/blob/main/docs/AM-DeepSeek-R1-Distilled-Dataset.pdf) [![Generic badge](https://img.shields.io/badge/🤗-1.4M-green.svg)](https://huggingface.co/datasets/a-m-team/AM-DeepSeek-R1-Distilled-1.4M)

The AM-DeepSeek-R1-Distilled is a large-scale dataset with thinking traces for general reasoning tasks, composed of high-quality and challenging reasoning problems. These problems are collected from a multitude of open-source datasets, subjected to semantic deduplication and meticulous cleaning to eliminate test set contamination. All responses within the dataset are distilled from reasoning models (pre-dominantly DeepSeek-R1) and have undergone rigorous verification procedures. Mathematical problems are validated by checking against reference answers, code problems are verified using test cases, and other tasks are evaluated with the aid of a reward model. The AM-Distill-Qwen-32B model, which was trained through only simple Supervised Fine-Tuning (SFT) using this batch of data, outperformed the DeepSeek-R1-Distill-Qwen-32B model on four benchmarks: AIME2024, MATH-500, GPQA-Diamond, and LiveCodeBench. We are releasing these 1.4 million problems and their corresponding responses to the research community with the objective of fostering the development of powerful reasoning-oriented Large Language Models (LLMs). The dataset was published in <https://huggingface.co/datasets/a-m-team/AM-DeepSeek-R1-Distilled-1.4M>. 

![alt text](assets/AM-DeepSeek-R1-Distilled.jpeg)

## Citation

If you find our work helpful to your research, please star our repository :star: and cite our work :pencil:

```BibTeX
@misc{AM-DeepSeek-R1-Distilled-1.4M,
      title={AM DeepSeek R1 Distilled 1.4M}, 
      author={Han Zhao and Haotian Wang and Yiping Peng and Sitong Zhao and Xiaoyu Tian and Shuaiting Chen and Yunjie Ji and Xiangang Li},
      year={2025}
}
```
