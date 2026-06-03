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

---

## Common Benchmarks and Datasets

| Benchmark | Main Usage | Notes | Link |
|---|---|---|---|
| **POPE** | Object hallucination evaluation | Polling-based object probing; widely used with LLaVA, InstructBLIP, MiniGPT-4, Shikra, Qwen-VL, etc. | [Paper](https://arxiv.org/abs/2305.10355) / [Code](https://github.com/RUCAIBox/POPE) |
| **CHAIR** | Caption hallucination evaluation | CHAIR measures object hallucination using MSCOCO object annotations and captions. | [Paper](https://aclanthology.org/D18-1437/) 
| **LLaVA-Bench** | Open-ended instruction-following and hallucination-related evaluation | Frequently used with GPT-4/GPT-4V/LLM-assisted judging. | [Dataset](https://huggingface.co/datasets/liuhaotian/LLaVA-Bench-in-the-Wild) |
| **MMBench** | Comprehensive VLM / MLLM evaluation benchmark | Bilingual multiple-choice benchmark for robust and holistic evaluation of vision-language models; uses CircularEval and LLM-assisted answer matching. | [Paper](https://arxiv.org/abs/2307.06281) / [Benchmark](https://github.com/open-compass/MMBench) |
| **MMHal-Bench** | Hallucination benchmark | Used for answer-level hallucination evaluation and GPT-assisted scoring. | [Paper](https://arxiv.org/abs/2309.14525) |
| **MME** | Multimodal evaluation benchmark | A comprehensive benchmark for evaluating MLLMs on perception and cognition tasks, commonly used in hallucination mitigation papers. | [Paper](https://arxiv.org/abs/2306.13394) / [Benchmark](https://github.com/BradyFU/Awesome-Multimodal-Large-Language-Models/tree/Evaluation) |
| **MMVP** | Basic visual perception and visual-grounding evaluation | Multimodal Visual Patterns benchmark constructed from CLIP-blind image pairs; contains 300 test images and evaluates MLLMs through VQA across nine basic visual patterns. | [Paper](https://arxiv.org/abs/2401.06209) / [Benchmark](https://github.com/tsb0601/MMVP) |
| **AMBER** | Hallucination and object-level evaluation | Covers discriminative and generative hallucination evaluation. | [Paper](https://arxiv.org/abs/2311.07397) |
| **GPT-4V Assisted Evaluation** | Open-ended multimodal answer evaluation | Uses GPT-4V or GPT-4V-style multimodal judging for open-ended generation, image-grounded answers, and hallucination-related scoring. | [OpenAI](https://openai.com/) |
| **GPT-4 Assisted Evaluation** | LLM-assisted text evaluation | Uses GPT-4 as a text-based evaluator, often with questions, references, object lists, captions, or model responses as input for hallucination scoring. | [OpenAI](https://openai.com/) |
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
---

## Papers by Year

> The year below mainly follows the **first public release year**. The **Venue** column records the published venue when available.

---

## 2026

| Paper | Venue | Type | Paper | Code |
| --- | --- | --- | --- | --- |
| **[GEASS] GEASS: Training-Free Caption Steering with Gradient-guided Extrapolation and Adaptive Semantic Suppression** | arXiv 2026 | IT / caption steering | [Paper](https://arxiv.org/abs/2605.01733) | — |
| **[CRoPS] CRoPS: CRoPS: A Training-Free Hallucination Mitigation Frame work for Vision-Language Models** | TMLR 2026 | IT / prompt steering | [Paper](https://arxiv.org/pdf/2601.00659) | [Code](https://github.com/ubamba98/CRoPS-A-Training-Free-Hallucination-Mitigation-Framework-for-Vision-Language-Models) |
| **[ASCD] ASCD: Attention-Steerable Contrastive Decoding for Reducing Hallucination in MLLMs** | AAAI 2026 | CD / attention steering | [Paper](https://arxiv.org/abs/2506.14766) | [Code](https://github.com/BroJunn/ASCD) |
| **[IRI] Causal Tracing of Object Representations in Large Vision Language Models: Mechanistic Interpretability and Hallucination Mitigation** | AAAI 2026 | IT / intermediate representation injection | [Paper](https://arxiv.org/abs/2511.05923) | — |
| **[SAVER] SAVER: Mitigating Hallucinations in Large Vision-Language Models via Style-Aware Visual Early Revision** | AAAI 2026 | IT / style-aware visual early revision | [Paper](https://arxiv.org/abs/2508.03177) | — |
| **[TAF] Taming the Phantom: Token-Asymmetric Filtering for Hallucination Mitigation in Large Vision-Language Models** | AAAI 2026 | IT / token-asymmetric filtering | [Paper](https://ojs.aaai.org/index.php/AAAI/article/view/37768) | — |
| **[CAST] CAST: Mitigating Object Hallucination in Large Vision-Language Models via Caption-Guided Visual Attention Steering** | arXiv 2026 | IT / visual attention steering | [Paper](https://arxiv.org/abs/2605.04641) | — |
| **[SelfVal] Countering the Over-Reliance Trap: Mitigating Object Hallucination for LVLMs via a Self-Validation Framework** | arXiv 2026 | Post-hoc / self-validation framework | [Paper](https://arxiv.org/abs/2601.22451) | [Code](https://github.com/Liushiyu-0709/SelfVal) |
| **[AttnReal] Attention Reallocation: Towards Zero-cost and Controllable Hallucination Mitigation of MLLMs** | IJCV 2026 | IT / attention reallocation | [Paper](https://arxiv.org/abs/2503.08342) | — |
| **[AQAH] Asking Questions to Alleviate Object Hallucination in Large Vision-Language Models** | IEEE TCSVT 2026 | Aux / active questioning and answer verification | [Paper](https://doi.org/10.1109/TCSVT.2025.3618949) | [Code](https://github.com/bcxbg/AQAH) |
| **[FLB] First Logit Boosting: Visual Grounding Method to Mitigate Object Hallucination in Large Vision-Language Models** | CVPR 2026 | Decoding / logit boosting | [Paper](https://arxiv.org/abs/2604.00455) | [Code](https://github.com/jiwooha20/FLB) |
| **[MAD] MAD: Modality-Adaptive Decoding for Mitigating Cross-Modal Hallucinations in Multimodal Large Language Models** | CVPR 2026 | CD / modality-adaptive decoding | [Paper](https://arxiv.org/abs/2601.21181) | [Code](https://github.com/top-yun/MAD) |
| **[VECD] Mitigating Hallucinations in Large Vision-Language Models via Visual-Enhanced Contrastive Decoding** | IEEE TMM 2026 | CD / visual-enhanced contrastive decoding | [Paper](https://doi.org/10.1109/TMM.2026.3651099) | — |
---

## 2025

| Paper | Venue | Type | Paper | Code |
| --- | --- | --- | --- | --- |
| **[RUR] Mitigating Hallucinations in Large Vision-Language Models via Reasoning Uncertainty-Guided Refinement** | IEEE TMM 2025 | Post-hoc / reasoning uncertainty-guided refinement | [Paper](https://doi.org/10.1109/TMM.2025.3599076) | [Code](https://github.com/Mrshenshen/RUR) |
| **[IMCCD] Mitigating Hallucination for Large Vision Language Model by Inter-Modality Correlation Calibration Decoding** | arXiv 2025 | CD / modality calibration | [Paper](https://arxiv.org/abs/2501.01926) | [Code](https://github.com/lijm48/IMCCD) |
| **[MINT] MINT: Mitigating Hallucinations in Large Vision-Language Models via Token Reduction** | arXiv 2025 | IT / token reduction | [Paper](https://arxiv.org/abs/2502.00717) | — |
| **[IFCD] Mitigating Hallucinations in Large Vision-Language Models with Internal Fact-based Contrastive Decoding** | arXiv 2025 | CD / internal facts | [Paper](https://arxiv.org/abs/2502.01056) | — |
| **[DAC] Mitigating Object Hallucinations in Large Vision-Language Models via Attention Calibration** | arXiv 2025 | IT / attention calibration | [Paper](https://arxiv.org/abs/2502.01969) | [Code](https://github.com/johnnyzyn/attention-calibration) |
| **[DeGF] Self-Correcting Decoding with Generative Feedback for Mitigating Hallucinations in Large Vision-Language Models** | ICLR 2025 | IT / generative feedback | [Homepage](https://zhangce01.github.io/DeGF/) | [Code](https://github.com/zhangce01/DeGF) |
| **[MAI] Understanding and Mitigating Hallucination in Large Vision-Language Models via Modular Attribution and Intervention** | ICLR 2025 | IT / modular attribution and hallucination-head intervention | [Paper](https://openreview.net/forum?id=Bjq4W7P2Us) | [Code](https://github.com/TianyunYoung/Hallucination-Attribution) |
| **[VISTA] The Hidden Life of Tokens: Reducing Hallucination of Large Vision-Language Models via Visual Information Steering** | ICML 2025 | IT / logit steering | [Paper](https://openreview.net/forum?id=7BKcLeHQsm) | [Code](https://github.com/LzVv123456/VISTA) |
| **[MARINE] Mitigating Object Hallucination in Large Vision-Language Models via Image-Grounded Guidance** | ICML 2025 | Aux / image-grounded guidance | [Paper](https://openreview.net/forum?id=w0xYx9CJhY) | [Code](https://github.com/Linxi-ZHAO/MARINE) |
| **[MemVR] Look Twice Before You Answer: Memory-Space Visual Retracing for Hallucination Mitigation in Multimodal Large Language Models** | ICML 2025 | IT / memory-space retracing | [Paper](https://proceedings.mlr.press/v267/zou25e.html) | [Code](https://github.com/1zhou-Wang/MemVR) |
| **[ICT] ICT: Image-Object Cross-Level Trusted Intervention for Mitigating Object Hallucination in Large Vision-Language Models** | CVPR 2025 | IT / image-object intervention | [Homepage](https://chenjz24.github.io/ICT/) | [Code](https://github.com/THU-BPM/ICT) |
| **[Nullu] Nullu: Mitigating Object Hallucinations in LVLMs via HalluSpace Projection** | CVPR 2025 | IT / hidden-space projection | [Paper](https://arxiv.org/abs/2412.13817) | [Code](https://github.com/Ziwei-Zheng/Nullu) |
| **[VASparse] VASparse: Towards Efficient Visual Hallucination Mitigation via Visual-Aware Token Sparsification** | CVPR 2025 | IT / token sparsification | [Paper](https://arxiv.org/abs/2501.06553) | [Code](https://github.com/mengchuang123/VASparse-github) |
| **[AGLA] Mitigating Object Hallucinations in Large Vision-Language Models with Assembly of Global and Local Attention** | CVPR 2025 | IT / global-local attention | [Paper](https://arxiv.org/abs/2406.12718) | [Code](https://github.com/Lackel/AGLA) |
| **[FarSight] Seeing Far and Clearly: Mitigating Hallucinations in MLLMs with Attention Causal Decoding** | CVPR 2025 | IT / attention causal mask | [Homepage](https://mllms-farsight.github.io/) | [Code](https://github.com/FeilongTangmonash/FarSight) |
| **[INTER] INTER: Mitigating Hallucination in Large Vision-Language Models by Interaction Guidance Sampling** | ICCV 2025 | IT / interaction guidance | [Paper](https://openaccess.thecvf.com/content/ICCV2025/html/Dong_INTER_Mitigating_Hallucination_in_Large_Vision-Language_Models_by_Interaction_Guidance_ICCV_2025_paper.html) | [Code](https://github.com/xxxxx313/INTER) |
| **[MFCD] Alleviating Hallucinations for LVLMs through Model-Free Confidence Decoding** | EMNLP 2025 | CD / confidence decoding | [Paper](https://aclanthology.org/2025.emnlp-main.1452.pdf) | [Code](https://github.com/liubq-dev/mfcd) |
| **[SPIN] Mitigating Hallucinations in Vision-Language Models through Image-Guided Head Suppression** | EMNLP 2025 | IT / image-guided head suppression | [Paper](https://aclanthology.org/2025.emnlp-main.631/) | [Code](https://github.com/yueche77/spin) |
| **[ASD] Activation Steering Decoding: Mitigating Hallucination in Large Vision-Language Models through Bidirectional Hidden State Intervention** | ACL 2025 | IT / activation steering decoding | [Paper](https://aclanthology.org/2025.acl-long.634/) | — |
| **[CLAIM] CLAIM: Mitigating Multilingual Object Hallucination in Large Vision-Language Models with Cross-Lingual Attention Intervention** | ACL 2025 | IT / cross-lingual attention intervention | [Paper](https://aclanthology.org/2025.acl-long.640/) | — |
| **[RVCD] Retrieval Visual Contrastive Decoding to Mitigate Object Hallucinations in Large Vision-Language Models** | Findings of ACL 2025 | CD | [Paper](https://aclanthology.org/2025.findings-acl.430/) | [Code](https://github.com/JiHoonLee9898/RVCD) |
---

## 2024

| Paper | Venue | Type | Paper | Code |
| --- | --- | --- | --- | --- |
| **[CGD] Seeing is Believing: Mitigating Hallucination in LVLMs via CLIP-Guided Decoding** | ICLR 2024 Workshop | CD / CLIP-guided | [Paper](https://arxiv.org/abs/2402.15300) | [Code](https://github.com/d-ailin/CLIP-Guided-Decoding) |
| **[SID] Self-Introspective Decoding: Alleviating Hallucinations for Large Vision-Language Models** | ICLR 2025 / arXiv 2024 | CD / self-introspective decoding | [Paper](https://arxiv.org/abs/2408.02032) | [Code](https://github.com/huofushuo/SID) |
| **[VTI] Reducing Hallucinations in Large Vision-Language Models via Latent Space Steering** | ICLR 2025 / arXiv 2024 | IT / latent-space steering | [Paper](https://openreview.net/forum?id=LBl7Hez0fF) | [Code](https://github.com/shengliu66/vti) |
| **[CausalMM] Mitigating Modality Prior-Induced Hallucinations in Multimodal Large Language Models via Deciphering Attention Causality** | ICLR 2025 / arXiv 2024 | IT / causal attention intervention | [Paper](https://arxiv.org/abs/2410.04780) | [Code](https://github.com/The-Martyr/CausalMM) |
| **[DeCo] MLLM Can See? Dynamic Correction Decoding For Hallucination Mitigation** | ICLR 2025 / arXiv 2024 | CD / layer contrast | [Paper](https://proceedings.iclr.cc/paper_files/paper/2025/hash/24079b91da7257cb78805262996152b8-Abstract-Conference.html) | [Code](https://github.com/zjunlp/DeCo) |
| **[SumGD] Mitigating Hallucinations in Large Vision-Language Models via Summary-Guided Decoding** | Findings of NAACL 2025 / arXiv 2024 | CD / summary-guided decoding | [Paper](https://aclanthology.org/2025.findings-naacl.235/) | [Code](https://github.com/andy9705/SumGD) |
| **[IBD] IBD: Alleviating Hallucinations in Large Vision-Language Models via Image-Biased Decoding** | CVPR 2025 / arXiv 2024 | CD / image-biased decoding | [Paper](https://arxiv.org/abs/2402.18476) | — |
| **[HALC] HALC: Object Hallucination Reduction via Adaptive Focal-Contrast Decoding** | ICML 2024 | CD / adaptive focal contrast | [Homepage](https://billchan226.github.io/HALC.html) | [Code](https://github.com/BillChan226/HALC) |
| **[Pensieve] Pensieve: Retrospect-then-Compare Mitigating Visual Hallucination** | arXiv 2024 | IT / retrieval-compare | [Paper](https://arxiv.org/abs/2403.14401) | [Code](https://github.com/DingchenYang99/Pensieve) |
| **[VaLiD] VaLiD: Mitigating Hallucinations in LVLMs through Visual Layer Fusion Contrastive Decoding** | arXiv 2024 | CD / visual-layer fusion | [Paper](https://arxiv.org/abs/2411.15839) | [Code](https://github.com/RicardoLuL/VaLiD_LVLMs_hallucinations) |
| **[CODE] CODE: Contrasting Self-generated Description to Combat Hallucination in Large Multi-modal Models** | NeurIPS 2024 | CD / self-generated description | [Homepage](https://ivy-lvlm.github.io/CODE/) | [Code](https://github.com/IVY-LVLM/CODE) |
| **[PAI] Paying More Attention to Image: A Training-Free Method for Alleviating Hallucination in LVLMs** | ECCV 2024 | IT / attention intervention | [Homepage](https://lalbj.github.io/projects/PAI/) | [Code](https://github.com/LALBJ/PAI) |
| **[ESREAL] ESREAL: Exploiting Semantic Reconstruction to Mitigate Hallucinations in Vision-Language Models** | ECCV 2024 | IT / semantic reliability | [Paper](https://arxiv.org/abs/2403.16167) | [Code](https://github.com/kmy17518/ESREAL) |
| **[ConVis] ConVis: Contrastive Decoding with Hallucination Visualization for Mitigating Hallucinations in Multimodal Large Language Models** | AAAI 2025 / arXiv 2024 | CD / visualization-guided | [Paper](https://arxiv.org/abs/2408.13906) | [Code](https://github.com/yejipark-m/ConVis) |
| **[ICD] Mitigating Hallucinations in Large Vision-Language Models with Instruction Contrastive Decoding** | Findings of ACL 2024 | CD / instruction contrast | [Paper](https://aclanthology.org/2024.findings-acl.937/) | [Code](https://github.com/p1k0pan/ICD) |
| **[LCD] Mitigating Hallucinations in Large Vision-Language Models (LVLMs) via Language-Contrastive Decoding (LCD)** | Findings of ACL 2024 | CD / language contrast | [Paper](https://aclanthology.org/2024.findings-acl.359/) | [Code](https://github.com/avshalomman/lcd) |
| **[LogicCheckGPT] Logical Closed Loop: Uncovering Object Hallucinations in Large Vision-Language Models** | Findings of ACL 2024 | Post-hoc / self-checking | [Paper](https://aclanthology.org/2024.findings-acl.414/) | [Code](https://github.com/CRIPAC-DIG/LogicCheckGPT) |
| **[Less is More] Less is More: Mitigating Multimodal Hallucination from an EOS Decision Perspective** | ACL 2024 | Decoding / EOS decision | [Paper](https://aclanthology.org/2024.acl-long.633/) | [Code](https://github.com/yuezih/less-is-more) |
| **[GTHM]Game on Tree: Visual Hallucination Mitigation via Coarse-to-Fine View Tree and Game Theory** | EMNLP 2024 | Train-free decoding | [Paper](https://aclanthology.org/2024.emnlp-main.998/) | [Code](https://github.com/mengchuang123/GTHM) |
| **[DAMRO] DAMRO: Dive into the Attention Mechanism of LVLM to Reduce Object Hallucination** | EMNLP 2024 | IT / attention outlier-token filtering | [Paper](https://aclanthology.org/2024.emnlp-main.439/) | [Code](https://github.com/coder-gx/DAMRO) |
| **[Woodpecker] Woodpecker: Hallucination Correction for Multimodal Large Language Models** | SCIS 2024 | Post-hoc / visual expert correction | [Paper](https://arxiv.org/abs/2310.16045) | [Code](https://github.com/BradyFU/Woodpecker) |
| **[M3ID] Multi-Modal Hallucination Control by Visual Information Grounding** | CVPR 2024 | CD / mutual information | [Paper](https://arxiv.org/abs/2403.14003) | — |
| **[VCD] Mitigating Object Hallucinations in LVLMs through Visual Contrastive Decoding** | CVPR 2024 | CD / distorted visual input | [Paper](https://arxiv.org/abs/2311.16922) | [Code](https://github.com/DAMO-NLP-SG/VCD) |
| **[OPERA] OPERA: Alleviating Hallucination in MLLMs via Over-Trust Penalty and Retrospection-Allocation** | CVPR 2024 | Decoding / attention penalty / rollback | [Paper](https://arxiv.org/abs/2311.17911) | [Code](https://github.com/shikiw/OPERA) |

---



---

## Notes

- Some entries are **arXiv-first** papers later published at conferences. The table keeps the first public year while recording the later venue if available.
- This list is intended for GitHub curation rather than formal bibliographic completeness. Pull requests should include official paper links, official code links, and evaluation settings.
