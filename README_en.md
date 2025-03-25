# <img src="assets/am_logo.png" style="vertical-align: middle; width: 35px;"> a-m-models [![Generic badge](https://img.shields.io/badge/🤗-am%20team-green.svg)](https://huggingface.co/a-m-team)

*[中文README](README.md).*

a-m-models is an open-source initiative led by the a-m-team, dedicated to in-depth exploration and practical application of cutting-edge technologies in Large Language Models (LLMs) and Artificial General Intelligence (AGI). Our team, composed of passionate researchers and developers, focuses on theoretical innovation, architectural design, and practical deployment of large models, aiming to gradually approach the realization of AGI. This project aims to openly share our latest research results and practical experiences in the domain of large models, fostering deeper community exchanges and mutual advancement in AGI technology.

## 🔄 Recent Updates

* [2024-03-25] Updated technical report [1.4 Million Open-Source Distilled Reasoning Dataset to Empower Large Language Model Training](https://github.com/a-m-team/a-m-models/blob/main/docs/AM-DeepSeek-R1-Distilled-Dataset.pdf), open-sourced 1.4 million distilled reasoning data entries, reproducing the performance of DeepSeek-R1 distilled models.


## 📑 Research Reports

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
