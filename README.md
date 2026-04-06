# Forensic-AC: Quantifying Cognitive Integrity in Autonomous AI Agents

### **Author:** [Shreya Katti] | Master’s in Cyber Forensics
**Project Status:** Research-Grade Framework for Orchestration-Layer Security


## Overview
As autonomous LLM-based agents are integrated into critical financial and corporate infrastructure, they become prime targets for **Adversarial Social Engineering** and **Indirect Prompt Injection**. 

Traditional security focuses on input/output filtering. **Forensic-AC** shifts the focus to the **Orchestration Layer**. By extracting and analyzing **Chain-of-Thought (CoT) Artifacts**, this framework calculates an **Attribution Certainty (AC) Score** to detect when an agent’s internal decision-making has been subverted, even if the final output appears compliant.


## The Mathematical Framework
The core of this research is the **AC Score**, a multi-dimensional metric that anchors an agent's statutory duty to its cognitive stability.

$$AC = T \times (1 - \mathcal{H}_{total})$$

Where:
* **$T$ (Tool Correctness):** The binary anchor ensuring mandatory audit tools (e.g., `verify_gst`, `check_ledger`) are invoked.
* **$\mathcal{H}_{total}$:** The combined stochastic entropy of the agent's actions and reasoning across multiple passes.


### **Combined Entropy Calculation**
$$\mathcal{H}_{total} = \lambda_{tools} \mathcal{H}_{action} + \lambda_{reason} \mathcal{H}_{semantic}$$

* **$\mathcal{H}_{action}$:** Jaccard-based drift in tool invocation.
* **$\mathcal{H}_{semantic}$:** Word-level Jaccard similarity of sanitized reasoning traces.
* **$\lambda$ (Lambda):** Defaulted to $0.8$ for tools and $0.2$ for reasoning to prioritize **Action over Voice**.


## Methodology: 3-Pass Monte Carlo Seeding
To detect "Cognitive Friction," the framework employs a **3-Pass Monte Carlo approach**:
1.  **Stochastic Seeding:** The agent is run 3 times with varying seeds to observe decision drift.
2.  **Artifact Extraction:** Uses a robust Regex parser to identify bracketed forensic signatures (e.g., `[verify_gst]`) within the CoT.
3.  **Semantic Sanitization:** Reasoning traces are stripped of stopwords and punctuation to isolate core logic stability.


## Forensic Proof of Concept
The framework was tested against **25 Adversarial Scenarios** (including CFO pressure and technical bypass vectors) and **25 Clean Baseline Audits**.

* **Sensitivity:** 100% (AUC = 1.00)
* **Statistical Separation:** Achieved total non-overlap between Clean and Injected distributions.

