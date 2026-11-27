# EngNepTam-TMT-50K

Official repository for **"Trilingual Machine Translation for English, Nepali, and Tamang: Corpus Development and Evaluation"** *(Accepted at ICON 2026)*.

## Overview
This repository accompanies our work on trilingual machine translation across **English (`en`)**, **Nepali (`ne`)**, and **Tamang (`tmg`)**. It covers:
- A **50,000-sentence trilingual parallel corpus** spanning five domains, with both Nepali and Tamang represented in the Devanagari script.
- Benchmarks of three fine-tuned multilingual NMT models (**NLLB-200**, **M2M-100**, **mBART-50**) and two LoRA-tuned LLMs (**Gemma-4-E4B-it**, **Gemma-4-E2B-it**) across all six translation directions.
- Cross-corpus generalization evaluation on **FLORES-200** (`ne↔en`) and real-world user feedback from our deployed web application.

## Dataset & Models (Hugging Face)
- Links will be made publicly available upon publication of the proceedings.
- **Collection:** [Hugging Face Collection](https://huggingface.co/collections/ilprl-docse/neptamen-tmt-50k)
### Dataset
- **EngNepTam-TMT-50K Parallel Corpus:** [Hugging Face Dataset](https://huggingface.co/datasets/ilprl-docse/NepTamEn-50k) *(Gated — Research & Educational Use Only)*

### Fine-Tuned Models
| Model | Type | Hugging Face Link |
| :--- | :--- | :--- |
| **NLLB-200 (600M)** | Multilingual NMT (Full Fine-Tuning) | [Model Link](https://huggingface.co/ilprl-docse/TMT-en-ne-tam-eq-50k-NLLB-200) |
| **M2M-100 (418M)** | Multilingual NMT (Full Fine-Tuning) | [Model Link](https://huggingface.co/ilprl-docse/TMT-en-ne-tam-eq-50k-M2M-100) |
| **mBART-50 (611M)** | Multilingual NMT (Full Fine-Tuning) | [Model Link](https://huggingface.co/ilprl-docse/TMT-en-ne-tam-eq-50k-mBART-50) |
| **Gemma-4-E4B-it** | LLM (LoRA Adapter) | [Model Link](https://huggingface.co/ilprl-docse/TMT-en-ne-tam-eq-50k-gemma-4-E4B-it) |
| **Gemma-4-E2B-it** | LLM (LoRA Adapter) | [Model Link](https://huggingface.co/ilprl-docse/TMT-en-ne-tam-eq-50k-gemma-4-E2B-it) |

## Corpus Summary
- **Size:** 50,000 parallel sentences (`40,000` train / `5,000` validation / `5,000` test)
- **Domains (10,000 sentences each):** Agriculture, Health, Education, Culture/Society/Tourism, and General Communication
- **Construction:** Nepali–Tamang pairs were professionally translated and verified by a senior Tamang linguist; English translations were generated from Nepali and manually verified/corrected by linguists from the Central Department of Linguistics, Tribhuvan University.

## Key Results

### In-Domain Test Split (5,000 sentences — sacreBLEU / chrF)

| Direction | NLLB-200 | M2M-100 | mBART-50 | Gemma-4-E4B-it | Gemma-4-E2B-it |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **en → ne** | **24.05** / **60.79** | 18.79 / 55.66 | 19.51 / 56.30 | 22.00 / 59.14 | 19.61 / 56.87 |
| **en → tmg** | **20.58** / **60.26** | 17.06 / 56.71 | 16.31 / 55.93 | 14.69 / 54.96 | 12.10 / 51.58 |
| **ne → en** | 49.35 / 70.95 | 38.44 / 63.65 | 40.60 / 64.34 | **52.58** / **73.19** | 46.94 / 68.53 |
| **ne → tmg** | **55.84** / **82.81** | 53.76 / 81.40 | 54.36 / 81.67 | 50.93 / 79.96 | 47.36 / 77.56 |
| **tmg → en** | **42.16** / **65.84** | 33.74 / 59.76 | 34.21 / 59.28 | 39.25 / 63.36 | 30.06 / 54.70 |
| **tmg → ne** | **55.49** / **81.29** | 51.24 / 78.71 | 54.67 / 80.23 | 51.39 / 78.03 | 42.60 / 72.16 |

### Cross-Corpus Generalization (FLORES-200 devtest — sacreBLEU / chrF)

| Direction | NLLB-200 | M2M-100 | mBART-50 | Gemma-4-E4B-it | Gemma-4-E2B-it |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **ne → en** | 32.28 / 60.44 | 22.68 / 53.41 | 21.07 / 48.66 | **37.29** / **63.81** | 33.26 / 60.46 |
| **en → ne** | 10.62 / 47.25 | 6.93 / 41.55 | 5.87 / 37.87 | **12.48** / **49.46** | 11.40 / 47.64 |

### Real-World User Feedback
Across 273 publicly rated translation instances (5-star scale) on the deployed web application, **NLLB-200** achieved the highest mean rating (**3.60**), followed by **mBART-50** (**3.38**) and **M2M-100** (**3.33**), alongside 207 optional user correction submissions.

## Citation
This paper has been **accepted at ICON 2026**; the official proceedings and final bibliographic details are forthcoming after the conference. In the meantime, please cite this work as:

```bibtex
@inproceedings{subedi2026trilingual,
  title     = {Trilingual Machine Translation for English, Nepali, and Tamang: Corpus Development and Evaluation},
  author    = {Subedi, Bipesh and Karki, Nischal and Ghimire, Rupak Raj and Acharya, Praveen and Poudyal, Prakash and Prasain, Balaram and Bal, Bal Krishna},
  booktitle = {Proceedings of the International Conference on Natural Language Processing (ICON 2026)},
  year      = {2026},
  note      = {Accepted; proceedings forthcoming}
}
