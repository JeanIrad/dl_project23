# 🌍 Dynamic Perceptual Steering

**Orchestrating Shape and Texture Biases in Vision Language Models for African Cultural Competency**

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/PyTorch-Ready-red.svg)](https://pytorch.org/)
[![Models](https://img.shields.io/badge/VLMs-LLaVA--NeXT--7B%20%7C%20InternVL--Chat-green.svg)]()

> This repository contains the code, data curation scripts, and evaluation framework for the project: **Dynamic Perceptual Steering**. We investigate how to use language prompts to dynamically steer Vision-Language Models (VLMs) to recognize African cultural cues, overcoming inherent Western-centric geographical biases.

## 📑 Table of Contents

- [Abstract](#-abstract)
- [Motivation & Objectives](#-motivation--objectives)
- [Background & Related Work](#-background--related-work)
- [Methodology](#-methodology)
- [Datasets & Evaluation](#-datasets--evaluation)
- [Baselines & Experiments](#-baselines--experiments)
- [Expected Results & Analysis](#-expected-results--analysis)
- [Project Roadmap](#-project-roadmap)
- [Team Contributions](#-team-contributions)
- [References](#-references)

---

## 📖 Abstract

Vision-Language Models (VLMs) are increasingly used to describe and categorize the visual world, yet they suffer from a significant geographical bias. Primarily trained on Western data, these models often "perceive" African objects through a Western lens—either misidentifying them or ignoring their unique cultural details.

This project investigates whether we can "talk" these models into seeing differently by using specific language prompts to steer their focus. We propose a **"Dynamic Steering"** framework that allows a model to first use its "shape bias" to identify what an object is (e.g., a bowl) and then switch to its "texture bias" to recognize its cultural origin (e.g., a specific African artisan style).

---

## 🎯 Motivation & Objectives

### The Problem: Perceptual Erasure

As AI tools are deployed globally, they risk **"perceptual erasure"**—the failure to recognize the cultural and material diversity of the Global South. Current models are often "stubborn," favoring universal shapes over local textures, leading to a loss of important cultural context in applications like digital heritage, education, and e-commerce.

### Broad Objectives:

1. **Measure Stubbornness:** Quantify how resistant current VLMs are when faced with African-specific textures and materials compared to Western ones.
2. **Develop Dynamic Steering:** Create a method that uses language to unlock a model's hidden ability to recognize African cultural cues _without_ needing to retrain the model.
3. **Demonstrate Runtime Alignment:** Show that multi-modal fusion allows us to align a model's visual perception to different cultures at runtime solely by changing the prompt.

---

## 📚 Background & Related Work

- **Active Steering via LLMs:** Building on the foundation of _"Can We Talk Models Into Seeing the World Differently?"_ (Gavrikov et al., 2025), we utilize the LLM component of VLMs to actively steer visual perception, applying this steerability specifically to African-centric visual data.
- **Shape vs. Texture Bias:** We utilize the Shape Bias metric (Geirhos et al., 2019) to quantify the ratio of shape-based vs. texture-based decisions using "cue-conflict" images (e.g., an object with a recognizable shape but an out-of-distribution African texture).

---

## ⚙️ Methodology

### Model Description: Sequential Dual-Lens

We employ a **"Sequential Dual-Lens"** approach using state-of-the-art open-source VLMs (`LLaVA-NeXT-7B` and `InternVL-Chat 1.1`).

1. **Structural Lens:** Steers the model toward its inherent shape bias to establish functional identity.
2. **Cultural Lens:** Steers the model toward learned texture representations to extract regional and material context.

### Automated Prompt Optimization (APO)

Beyond manual steering, we implement an APO loop. Using an LLM (e.g., GPT-4) as an optimizer, we automatically discover "non-intuitive" prompts (e.g., _"Analyze the repetitive geometric motifs and weave patterns"_) that maximize the VLM's sensitivity to suppressed African textures.

---

## 📊 Datasets & Evaluation

### Datasets

- **Primary Source:** **SURA Benchmark** & **Africa-500**.
- **Curation Strategy:** We construct a **"Cultural Cue-Conflict" test set** featuring high-resolution imagery of African architecture, textiles, and everyday objects exhibiting "out-of-distribution" textures compared to standard Western datasets.

### Evaluation Metrics

- **Cue Accuracy:** `(Shape Accuracy + Texture Accuracy)` – measures the overall ability to assign a correct label.
- **Shape Bias:** `(Shape Accuracy / Cue Accuracy)` – quantifies how often the model prioritizes structural form over cultural texture.
- **Steerability Range:** The ability to significantly shift these percentages using language alone without dropping overall accuracy.

---

## 🧪 Baselines & Experiments

### Baselines

1. **Neutral VLM Baseline:** Evaluating models with a "Neutral" prompt (_"What is in this image?"_) to observe default shape bias and perceptual erasure.
2. **Vision-Only Baseline:** Using the **CLIP ViT-L/14 encoder** to determine how much erasure is caused by the vision encoder's data deficiency vs. the LLM's selection process.

### Implemented Extensions

- **Mechanistic Confidence Probing:** Analyzing Token Logit Confidence scores for "Shape" vs. "Texture" tokens to verify if the model "sees" the African texture but lacks confidence to output it.
- **Adversarial Texture Steering:** Testing "Cultural Stubbornness" by applying African textures to highly iconic Western shapes (e.g., a British-style phone booth with Zulu beadwork) to test the limits of runtime alignment.

---

## 📈 Expected Results & Analysis

- **Performance Gains:** We anticipate the Dynamic Steering framework will improve cultural recognition (texture-bias scores) by **15–25%** over the neutral baseline.
- **Failure Case Analysis:** \* _Stereotypical Collapses:_ When steering causes the model to hallucinate broad stereotypes (e.g., classifying modern architecture as a "hut").
  - _Linguistic Stubbornness:_ When the vision encoder provides a zero-signal for an unfamiliar material, rendering prompts ineffective.
- **Ablation Studies:** Testing _Prompt Granularity_ (Generic vs. Localized prompts) and scaling effects (7B vs. 13B+ parameters).

---

## 🚀 Project Roadmap

- [ ] **Phase 1 (Pre-Midterm):** Curate a subset of 200 "African Cue-Conflict" images using SURA and Africa-500.
- [ ] **Phase 2 (Pre-Midterm):** Conduct baseline "Neutral" and "Manual Steering" evaluations on LLaVA-NeXT-7B and InternVL.
- [ ] **Phase 3 (Post-Midterm):** Implement the Automated Prompt Optimization (APO) loop and analyze token-level confidence (Mechanistic Probing).
- [ ] **Phase 4 (Final):** Result synthesis, failure case analysis, and final reporting.

---

## 👥 Team Contributions

- **Member A:** Dataset curation, African cue-conflict image synthesis, and SURA API integration.
- **Member B:** VLM inference pipeline setup, prompt engineering, and logit confidence analysis.
- **Member C:** Automated Prompt Optimization (APO) implementation and statistical evaluation.
- **Member D:** Baseline evaluation metrics (Cue Accuracy & Shape Bias), Vision-Only (CLIP) pipeline implementation, adversarial texture testing, and final result synthesis.

---

## 🔗 References

1. Gavrikov, P., et al. (2025). _"Can We Talk Models Into Seeing the World Differently?"_ Proceedings of the International Conference on Learning Representations (ICLR).
2. Geirhos, R., et al. (2019). _"ImageNet-trained CNNs are biased towards texture; increasing shape bias improves accuracy and robustness."_ ICLR.

---

_Developed at Carnegie Mellon University Africa_
