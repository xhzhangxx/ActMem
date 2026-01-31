# ActMem: Bridging the Gap Between Memory Retrieval and Reasoning in LLM Agents

<div align="center">

[![Paper](https://img.shields.io/badge/Paper-ArXiv-b31b1b.svg)](LINK_TO_YOUR_PAPER_IF_AVAILABLE)
[![License](https://img.shields.io/badge/License-Apache_2.0-green.svg)](LICENSE)
![Status](https://img.shields.io/badge/Status-Code_Coming_Soon-orange)


</div>

---

## 📢 News
* **[2026.01]** We released the paper "ActMem: Bridging the Gap Between Memory Retrieval and Reasoning in LLM Agents".
* **[Coming Soon]** Source code and the **ActMemEval** dataset will be released shortly!

---

## 📖 Overview

Existing memory frameworks for LLM agents typically act as passive **"recorders"**. They are good at retrieving facts but often fail to understand the deeper implications of memories for current decision-making.

**ActMem** is a novel actionable memory framework that transforms the agent from a passive retriever to an **active reasoner**. By integrating memory retrieval with active causal reasoning, ActMem enables agents to deduce implicit constraints and resolve potential conflicts between past states and current intentions.

---

## 🚀 Methodology

ActMem transforms unstructured dialogue history into a structured **Memory Knowledge Graph (KG)** with both semantic and causal edges.

![Framework Overview](figs/framework.png)
*(Figure: The overview of the ActMem framework)*

The framework consists of four key modules:
1.  **Memory Fact Extraction**
    Compresses raw dialogue history into a set of atomic, declarative facts to eliminate noise and redundancy.
2.  **Fact Clustering**
    Groups topic-related facts using incremental clustering to ensure topical coherence and reduce computational overhead for causal mining.
3.  **Memory KG Construction**
    Transforms unstructured facts into a structured graph:
    *   **Semantic Edges:** Established based on vector similarity to preserve contextual connectivity.
    *   **Causal Edges:** Identified by LLMs and filtered through a **PMI-based validation** mechanism to remove spurious correlations and hallucinations.
4.  **Counterfactual-based Retrieval**
    Implements a **retrieval-reasoning-refinement loop**. Instead of simple matching, it generates commonsense consequences (e.g., *"If the user does X, what negative outcomes might occur?"*) and uses this reasoning to retrieve implicitly connected memory constraints.
---

## 📊 ActMemEval Benchmark

To evaluate reasoning capabilities and move beyond simple fact retrieval, we introduce **ActMemEval**, a dataset designed for logic-driven scenarios.

* **Logic-Driven:** Focuses on scenarios requiring causal deduction and conflict resolution.
* **Low Similarity:** Unlike LongMemEval, answers in ActMemEval cannot be directly retrieved via surface-level overlap; they must be inferred.

---

## 📈 Experiments

ActMem significantly outperforms state-of-the-art baselines (including Mem0, LightMem, and NaiveRAG) on complex, memory-dependent tasks.

| Method | Retrieval Acc. | QA Acc. |
| :--- | :---: | :---: |
| NaiveRAG | **84.86** | 61.54 |
| Mem0 | 68.02 | 41.80 |
| A-Mem | 64.31 | - |
| MemoryOS | - | 13.36 |
| LightMem | 56.88 | 63.97 |
| **ActMem (Ours)** | 71.66 | **76.52** |

*(Results based on DeepSeek-V3 backbone. See paper for full details.)*

---

## 🗓️ Roadmap

- [ ] Release the **ActMemEval** benchmark dataset.
- [ ] Release the code for ActMem.

---

##  citation

If you find this work useful, please consider citing our paper:

```bibtex
@article{zhang2026actmem,
  title={ActMem: Bridging the Gap Between Memory Retrieval and Reasoning in LLM Agents},
  author={Zhang, Xiaohui and Sun, Zequn and Yang, Chengyuan and Jin, Yaqin and Zhang, Yazhong and Hu, Wei},
  journal={arXiv preprint},
  year={2026}
}
