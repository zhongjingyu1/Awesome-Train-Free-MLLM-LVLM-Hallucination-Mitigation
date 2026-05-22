# Awesome Train-Free MLLM / LVLM Hallucination Mitigation

> A curated GitHub-style list of **training-free** papers for hallucination mitigation in **Multimodal Large Language Models (MLLMs)** and **Large Vision-Language Models (LVLMs)**.  
> Last updated: **2026-05-22**.  
> Scope: methods that mainly work at **inference / decoding / prompting / post-hoc verification** and do **not require re-training or fine-tuning the target LVLM**. Some methods use auxiliary vision models, retrieval, feedback, or optional learnable variants; these are explicitly marked in the table.

## Contents

- [Scope and Inclusion Criteria](#scope-and-inclusion-criteria)
- [Common Benchmarks and Datasets](#common-benchmarks-and-datasets)
- [Common Base Models](#common-base-models)
- [Papers by Year](#papers-by-year)
  - [2026](#2026)
  - [2025](#2025)
  - [2024](#2024)
  - [2023](#2023)
- [Suggested Repository Structure](#suggested-repository-structure)
- [Contribution Template](#contribution-template)

---

## Scope and Inclusion Criteria

This list focuses on **train-free hallucination mitigation** in MLLMs/LVLMs, including:

- **Contrastive decoding / decoding intervention** methods.
- **Attention / logit / hidden-state intervention** methods applied at inference time.
- **Prompting, self-checking, or post-hoc correction** methods that do not tune the target model.
- **Retrieval / feedback / auxiliary-tool methods** when the target LVLM itself is not fine-tuned.

Not included by default:

- Methods that require instruction tuning, DPO/RLHF, supervised fine-tuning, or re-training the LVLM.
- General hallucination benchmarks or surveys unless they are directly useful for this repository.

Legend used below:

- **CD**: Contrastive Decoding.
- **IT**: Inference-Time intervention.
- **Post-hoc**: generates first, then verifies/corrects.
- **Aux**: uses auxiliary models/tools/retrieval but does not train the target LVLM.
- **Code TBA / —**: official code was not found or not verified when this README was drafted.

---

## Common Benchmarks and Datasets

| Benchmark / Dataset | Main Usage | Notes | Link |
|---|---|---|---|
| **POPE** | Object hallucination evaluation | Polling-based object probing; widely used with LLaVA, InstructBLIP, MiniGPT-4, Shikra, Qwen-VL, etc. | [Paper](https://arxiv.org/abs/2305.10355) / [Code](https://github.com/RUCAIBox/POPE) |
| **CHAIR / MSCOCO** | Caption hallucination evaluation | CHAIR measures object hallucination using MSCOCO object annotations and captions. | [Paper](https://aclanthology.org/D18-1437/) / [COCO](https://cocodataset.org/) |
| **MME** | Comprehensive MLLM evaluation | Measures both perception and cognition abilities across multiple subtasks. | [Paper](https://arxiv.org/abs/2306.13394) |
| **LLaVA-Bench in-the-Wild** | Open-ended instruction-following and hallucination-related evaluation | Frequently used with GPT-4/GPT-4V/LLM-assisted judging. | [Dataset](https://huggingface.co/datasets/liuhaotian/LLaVA-Bench-in-the-Wild) |
| **MMHal-Bench** | Hallucination benchmark | Used for answer-level hallucination evaluation and GPT-assisted scoring. | [Paper](https://arxiv.org/abs/2309.14525) |
| **AMBER** | Hallucination and object-level evaluation | Covers discriminative and generative hallucination evaluation. | [Paper](https://arxiv.org/abs/2311.07397) |
| **HallusionBench** | Visual illusion / reasoning hallucination | Tests language hallucination and visual illusion in multimodal reasoning. | [Paper](https://arxiv.org/abs/2310.14566) |

---

## Common Base Models

| Model Family | Typical Use in Train-Free Hallucination Papers | Link |
|---|---|---|
| **LLaVA / LLaVA-1.5 / LLaVA-NeXT** | Most common open-source LVLM backbone for POPE, MME, CHAIR, LLaVA-Bench. | [LLaVA](https://github.com/haotian-liu/LLaVA) |
| **MiniGPT-4** | Early LVLM backbone, often used in POPE and CHAIR comparisons. | [MiniGPT-4](https://github.com/Vision-CAIR/MiniGPT-4) |
| **InstructBLIP** | Frequently used as a strong BLIP-2-based instruction model. | [InstructBLIP](https://github.com/salesforce/LAVIS/tree/main/projects/instructblip) |
| **Shikra** | Often used in POPE/CHAIR hallucination comparisons. | [Shikra](https://github.com/shikras/shikra) |
| **Qwen-VL / Qwen2-VL / Qwen2.5-VL** | Strong open-source LVLM family; used increasingly in recent train-free decoding work. | [Qwen-VL](https://github.com/QwenLM/Qwen-VL) |
| **mPLUG-Owl / mPLUG-Owl2** | Common in hallucination and instruction-following evaluation. | [mPLUG-Owl](https://github.com/X-PLUG/mPLUG-Owl) |
| **InternVL / InternVL2** | Strong recent LVLM family; useful for modern benchmark extensions. | [InternVL](https://github.com/OpenGVLab/InternVL) |
| **BLIP-2** | Backbone or auxiliary model in several early LVLM settings. | [BLIP-2](https://github.com/salesforce/LAVIS) |
| **GPT-4V / GPT-4o / GPT-4.1 style judges** | Used as evaluator or reference model in open-ended answer scoring. | [OpenAI](https://openai.com/) |
| **CLIP / SAM / GroundingDINO / Detectors** | Auxiliary visual grounding, filtering, segmentation, or feedback modules in some train-free or post-hoc methods. | [CLIP](https://github.com/openai/CLIP) / [SAM](https://github.com/facebookresearch/segment-anything) / [GroundingDINO](https://github.com/IDEA-Research/GroundingDINO) |

---

## Papers by Year

> The year below mainly follows the **first public release year**. The **Venue** column records the published venue when available.

---

## 2026

| Paper | Venue | Type | Paper / Homepage | Code | Common Datasets | Common Models |
|---|---|---|---|---|---|---|
| **GEASS: Training-Free Caption Steering with Gradient-guided Extrapolation and Adaptive Semantic Suppression** | arXiv 2026 | IT / caption steering | [Paper](https://arxiv.org/abs/2605.01733) | — | COCO / CHAIR-style caption hallucination | LVLM captioning models |
| **CRoPS: Correct and Robust Prompt Steering for Mitigating Hallucinations in MLLMs** | TMLR 2026 / to verify | IT / prompt steering | [Code/Homepage](https://github.com/ubamba98/CRoPS-Correct-and-Robust-Prompt-Steering-for-Mitigating-Hallucinations-in-MLLMs) | [Code](https://github.com/ubamba98/CRoPS-Correct-and-Robust-Prompt-Steering-for-Mitigating-Hallucinations-in-MLLMs) | POPE / MME / hallucination benchmarks | LLaVA-style MLLMs |
| **ASCD: Attention-Steerable Contrastive Decoding for Reducing Hallucination in MLLMs** | AAAI 2026 / to verify | CD / attention steering | [Paper](https://arxiv.org/abs/2506.14766) | — | POPE / MME / CHAIR-style benchmarks | LLaVA-style MLLMs |

---

## 2025

| Paper | Venue | Type | Paper / Homepage | Code | Common Datasets | Common Models |
|---|---|---|---|---|---|---|
| **Nullu: Mitigating Object Hallucinations in LVLMs via HalluSpace Projection** | CVPR 2025 | IT / hidden-space projection | [Paper](https://arxiv.org/abs/2412.13817) | [Code](https://github.com/Ziwei-Zheng/Nullu) | POPE / MME / CHAIR-style benchmarks | LLaVA / Qwen-VL / other LVLMs |
| **VASparse: Towards Efficient Visual Hallucination Mitigation for LVLMs via Visual-Aware Sparsification** | CVPR 2025 | IT / token sparsification | [Paper](https://arxiv.org/abs/2501.06553) | [Code](https://github.com/mengchuang123/VASparse-github) | Multiple hallucination benchmarks | LLaVA / MiniGPT-4 / InstructBLIP-style LVLMs |
| **IMCCD: Boosting Multimodal LLMs with Inter-Modality Correlation Calibration Decoding** | arXiv 2025 | CD / modality calibration | [Paper](https://arxiv.org/abs/2501.01926) | — | POPE / MME / CHAIR-style benchmarks | LLaVA-style LVLMs |
| **MINT: Mitigating Hallucinations in LVLMs via Token Reduction** | arXiv 2025 | IT / token reduction | [Paper](https://arxiv.org/abs/2502.00717) | — | POPE / MME / CHAIR-style benchmarks | LLaVA-style LVLMs |
| **IFCD: Internal Fact-based Contrastive Decoding for LVLMs** | arXiv 2025 | CD / internal facts | [Paper](https://arxiv.org/abs/2502.01056) | — | POPE / hallucination benchmarks | LLaVA-style LVLMs |
| **UAC / DAC: Universal and Differential Attention Calibration for LVLMs** | arXiv 2025 | IT / attention calibration | [Paper](https://arxiv.org/abs/2502.01969) | — | POPE / MME / CHAIR-style benchmarks | LLaVA-style LVLMs |
| **VISTA: Visual Information Steering with Token-logit Augmentation** | ICML 2025 | IT / logit steering | [Paper](https://openreview.net/forum?id=7BKcLeHQsm) | [Code](https://github.com/LzVv123456/VISTA) | POPE / MME / CHAIR-style benchmarks | LLaVA / InstructBLIP / Qwen-VL-style LVLMs |
| **DeGF: Debiasing Multimodal Large Language Models via Generative Feedback** | ICLR 2025 | IT / generative feedback | [Homepage](https://zhangce01.github.io/DeGF/) | [Code](https://github.com/zhangce01/DeGF) | Six hallucination benchmarks | LLaVA / Qwen-VL / MiniGPT-4-style LVLMs |
| **MARINE: Mitigating Object Hallucination in LVLMs via Image-grounded Guidance** | ICML 2025 | Aux / image-grounded guidance | [Paper](https://openreview.net/forum?id=w0xYx9CJhY) | [Code](https://github.com/Linxi-ZHAO/MARINE) | Object hallucination benchmarks | LLaVA / MiniGPT-4 / InstructBLIP-style LVLMs |
| **ICT: Image-Object Cross-Level Trusted Intervention for Mitigating Object Hallucination in LVLMs** | CVPR 2025 | IT / image-object intervention | [Homepage](https://chenjz24.github.io/ICT/) | [Code](https://github.com/THU-BPM/ICT) | POPE / CHAIR / MME-style benchmarks | LLaVA / Qwen-VL / LVLM families |
| **AGLA: Assembly of Global and Local Attention for LVLMs** | CVPR 2025 | IT / global-local attention | [Paper](https://arxiv.org/abs/2406.12718) | [Code](https://github.com/Lackel/AGLA) | POPE / CHAIR / MME-style benchmarks | LLaVA / MiniGPT-4 / InstructBLIP-style LVLMs |
| **RVCD: Alleviating Hallucinations in MLLMs via Robust Visual Contrastive Decoding** | Findings of ACL 2025 | CD | [Paper](https://aclanthology.org/2025.findings-acl.430/) | [Code](https://github.com/JiHoonLee9898/RVCD) | Object hallucination benchmarks | LLaVA-style MLLMs |
| **INTER: Mitigating Hallucination in LVLMs by Interaction Guidance** | ICCV 2025 | IT / interaction guidance | [Paper](https://openaccess.thecvf.com/content/ICCV2025/html/Dong_INTER_Mitigating_Hallucination_in_Large_Vision-Language_Models_by_Interaction_Guidance_ICCV_2025_paper.html) | Code TBA | POPE / CHAIR / MME-style benchmarks | LLaVA-style LVLMs |
| **MemVR: Look Twice Before You Answer: Memory-Space Visual Retracing** | ICML 2025 | IT / memory-space retracing | [Paper](https://proceedings.mlr.press/v267/zou25e.html) | [Code](https://github.com/1zhou-Wang/MemVR) | POPE / MME / CHAIR-style benchmarks | LLaVA / Qwen-VL / MiniGPT-4-style LVLMs |
| **FarSight: Mitigating Hallucination in LVLMs via Attention Causal Mask** | CVPR 2025 | IT / attention causal mask | [Homepage](https://mllms-farsight.github.io/) | — | POPE / CHAIR / MME-style benchmarks | LLaVA-style LVLMs |
| **MFCD: Alleviating Hallucinations for LVLMs through Model-Free Confidence Decoding** | EMNLP 2025 | CD / confidence decoding | [Paper](https://aclanthology.org/2025.emnlp-main.1452.pdf) | [Code](https://github.com/liubq-dev/mfcd) | POPE / MME / hallucination benchmarks | LLaVA-style LVLMs |
| **MCA-LLaVA: Multi-Level Cross-Modal Alignment for LVLMs** | arXiv 2025 / to verify | IT / cross-modal alignment | [Paper](https://arxiv.org/abs/2507.20829) | [Code](https://github.com/ErikZ719/MCA-LLaVA) | POPE / MME / CHAIR-style benchmarks | LLaVA-style LVLMs |

---

## 2024

| Paper | Venue | Type | Paper / Homepage | Code | Common Datasets | Common Models |
|---|---|---|---|---|---|---|
| **LogicCheckGPT: Mitigating Multimodal Hallucination via Logical Closed Loop** | Findings of ACL 2024 | Post-hoc / self-checking | [Paper](https://aclanthology.org/2024.findings-acl.414/) | [Code](https://github.com/CRIPAC-DIG/LogicCheckGPT) | Object hallucination benchmarks | Multiple LVLMs |
| **Less is More: Mitigating Multimodal Hallucination from an EOS Decision Perspective** | ACL 2024 | Decoding / EOS decision | [Paper](https://aclanthology.org/2024.acl-long.633/) | [Code](https://github.com/yuezih/less-is-more) | POPE / MME-style benchmarks | LLaVA / MiniGPT-4-style LVLMs |
| **CGD: Seeing is Believing: Mitigating Hallucination in LVLMs via CLIP-Guided Decoding** | ICLR 2024 Workshop / arXiv | CD / CLIP-guided | [Paper](https://arxiv.org/abs/2402.15300) | [Code](https://github.com/d-ailin/CLIP-Guided-Decoding) | POPE / CHAIR / MME-style benchmarks | LLaVA / InstructBLIP / MiniGPT-4-style LVLMs |
| **IBD: Alleviating Hallucinations in LVLMs via Image-Biased Decoding** | CVPRW 2025 / arXiv 2024 | CD / image-biased decoding | [Paper](https://arxiv.org/abs/2402.18476) | — | CHAIR / GPT-4-assisted eval / MME | InstructBLIP / MiniGPT-4 / LLaVA-1.5 / Shikra |
| **HALC: Object Hallucination Reduction via Adaptive Focal-Contrast Decoding** | ICML 2024 | CD / adaptive focal contrast | [Homepage](https://billchan226.github.io/HALC.html) | [Code](https://github.com/BillChan226/HALC) | POPE / CHAIR / MSCOCO / MME-style benchmarks | LLaVA / MiniGPT-4 / InstructBLIP-style LVLMs |
| **M3ID: Mitigating LVLM Hallucination with Mitigated Mutual-Information Decoding** | CVPR 2024 | CD / mutual information | [Paper](https://arxiv.org/abs/2403.14003) | — | POPE / captioning hallucination benchmarks | LLaVA-13B / LVLMs |
| **Pensieve: Retrospect-then-Compare Mitigating Visual Hallucination** | arXiv 2024 | IT / retrieval-compare | [Paper](https://arxiv.org/abs/2403.14401) | [Code](https://github.com/DingchenYang99/Pensieve) | Caption hallucination benchmarks | InstructBLIP-style LVLMs |
| **ESREAL: Mitigating Hallucinations in LVLMs through Enhanced Semantic Reliability** | ECCV 2024 | IT / semantic reliability | [Paper](https://arxiv.org/abs/2403.16167) | [Code](https://github.com/kmy17518/ESREAL) | Caption hallucination benchmarks | LLaVA / InstructBLIP / mPLUG-Owl2 |
| **ICD: Mitigating Object Hallucinations via Image-aware Contrastive Decoding** | Findings of ACL 2024 | CD / image-aware instruction contrast | [Paper](https://aclanthology.org/2024.findings-acl.937/) | [Code](https://github.com/p1k0pan/ICD) | POPE / MME / LLaVA-Bench | LLaVA / MiniGPT-4 / InstructBLIP |
| **CODE: Contrasting Self-generated Description to Combat Hallucination** | NeurIPS 2024 | CD / self-generated description | [Homepage](https://ivy-lvlm.github.io/CODE/) | [Code](https://github.com/IVY-LVLM/CODE) | POPE / CHAIR / MME-style benchmarks | LLaVA / MiniGPT-4 / InstructBLIP-style LVLMs |
| **PAI: Mitigating Hallucination in LVLMs via Attention Intervention** | ECCV 2024 | IT / attention intervention | [Homepage](https://lalbj.github.io/projects/PAI/) | [Code](https://github.com/LALBJ/PAI) | POPE / CHAIR / MME-style benchmarks | LLaVA / MiniGPT-4 / InstructBLIP / Qwen-VL-style LVLMs |
| **LCD: Mitigating Object Hallucinations in LVLMs through Language Contrastive Decoding** | Findings of ACL 2024 | CD / language contrast | [Paper](https://aclanthology.org/2024.findings-acl.359/) | [Code](https://github.com/avshalomman/lcd) | POPE / hallucination benchmarks | LLaVA-style LVLMs |
| **SID: Self-Introspective Decoding for Hallucination Mitigation** | OpenReview / to verify | CD / self-introspective decoding | [Paper](https://openreview.net/forum?id=rsZwwjYHuD) | [Code](https://github.com/huofushuo/SID) | POPE / MME-style benchmarks | LLaVA-1.5 / LVLMs |
| **ConVis: Contrastive Decoding with Hallucination Visualization** | AAAI 2025 / arXiv 2024 | CD / visualization-guided | [Paper](https://arxiv.org/abs/2408.13906) | [Code](https://github.com/yejipark-m/ConVis) | Five hallucination benchmarks | LLaVA-style MLLMs |
| **GTHM: Game-theoretic Hallucination Mitigation** | EMNLP 2024 | Train-free decoding | [Paper](https://aclanthology.org/2024.emnlp-main.998/) | [Code](https://github.com/mengchuang123/GTHM) | Hallucination benchmarks | LVLMs |
| **DeCo: Decoding by Contrasting Layers Improves Factuality in LVLMs** | ICLR 2025 / arXiv 2024 | CD / layer contrast | [Paper](https://openreview.net/forum?id=4z3IguA4Zg) | [Code](https://github.com/zjunlp/Deco) | POPE / CHAIR / MME-style benchmarks | LLaVA / InstructBLIP-style LVLMs |
| **VaLiD: Mitigating Hallucinations in LVLMs through Visual Layer Fusion Contrastive Decoding** | arXiv 2024 | CD / visual-layer fusion | [Paper](https://arxiv.org/abs/2411.15839) | — | POPE / MME / CHAIR-style benchmarks | LVLMs |

---

## 2023

| Paper | Venue | Type | Paper / Homepage | Code | Common Datasets | Common Models |
|---|---|---|---|---|---|---|
| **Woodpecker: Hallucination Correction for Multimodal Large Language Models** | arXiv 2023 / published version to verify | Post-hoc / visual expert correction | [Paper](https://arxiv.org/abs/2310.16045) | [Code](https://github.com/BradyFU/Woodpecker) | POPE / open-ended correction cases | MiniGPT-4 / mPLUG-Owl-style MLLMs |
| **VCD: Mitigating Object Hallucinations in LVLMs through Visual Contrastive Decoding** | CVPR 2024 | CD / distorted visual input | [Paper](https://arxiv.org/abs/2311.16922) | [Code](https://github.com/DAMO-NLP-SG/VCD) | POPE / MME / LLaVA-Bench / GPT-4V eval | LLaVA-1.5 / InstructBLIP / Qwen-VL |
| **OPERA: Alleviating Hallucination in MLLMs via Over-Trust Penalty and Retrospection-Allocation** | CVPR 2024 | Decoding / attention penalty / rollback | [Paper](https://arxiv.org/abs/2311.17911) | [Code](https://github.com/shikiw/OPERA) | MSCOCO / POPE / CHAIR / GPT-4V eval | InstructBLIP / MiniGPT-4 / LLaVA-1.5 / Shikra |

---



---

## Notes

- Some entries are **arXiv-first** papers later published at conferences. The table keeps the first public year while recording the later venue if available.
- For entries marked **to verify**, please check the official project page or authors' repository before using the venue/code link in a public leaderboard.
- This list is intended for GitHub curation rather than formal bibliographic completeness. Pull requests should include official paper links, official code links, and evaluation settings.
