## Overview

This dataset is a hybrid collection of **6,660 samples** (human-generated + synthetic data) specifically curated to train **CLAIRE** (Conversational Language AI for Resolution & Engagement).

CLAIRE is an intelligent banking assistant designed for secure, inclusive, and real-time customer support in the Philippine financial sector. This dataset and the development of CLAIRE are part of the **BPI Datawave 2025**.

> 🔗 **Project Repository:** [PROJECT-CLAIRE](https://github.com/BPI-MangTomas/PROJECT-CLAIRE)

The core knowledge base is sourced from: [BPI Help Center - General Questions](https://help.bpi.com.ph/s/article/General-Questions)

---
## Methodology: RAFT Inspiration

The dataset structure is inspired by the **RAFT (Retrieval-Augmented Fine-Tuning)** methodology ([arXiv:2403.10131](https://arxiv.org/abs/2403.10131)). RAFT trains models to discern relevant information from "noise" and reduces the likelihood of hallucinations in specialized domains.

### Key Components: Q, D, A

1. **Question (Q):** The user's query or the question CLAIRE is being trained to resolve.
2. **Documents (D):** A set of 4 documents retrieved from the knowledge base:
   * **Golden Documents (D\*):** Factual information required to correctly answer the question.
   * **Distractor Documents (Dk):** Irrelevant documents used to teach the model to ignore non-pertinent information.
   * *Note: The position of the Golden Document is randomized within each set of four to prevent positional bias.*
3. **Answer (A):** A factual response grounded in the Golden Documents, reflecting both the correct information and the appropriate empathetic tone.

### The 1-P Ratio (P = 0.8)

Following RAFT guidelines, we utilize a strategic split to balance "open-book" and "closed-book" learning:

* **P = 0.8 (The Open-Book Scenario):** 80% of the data includes a golden document. CLAIRE learns to search through the context, identify the relevant fact, and formulate a well-grounded answer.
* **1-P = 0.2 (The Closed-Book Challenge):** 20% of the data contains **only distractors**. This forces CLAIRE to recognize when the answer is not present. Instead of hallucinating, CLAIRE learns to identify that the context is insufficient and responds with a fallback or escalation message.

---
## Dataset Analytics

### 1. General Statistics

| Metric                        | Value               |
| :---------------------------- | :------------------ |
| **Total Samples**             | 6,660               |
| **Category**                  | `general_questions` |
| **Avg. Documents per Sample** | 4.00                |

### 2. Linguistic Distribution

To ensure inclusivity in the Philippine market, the dataset is perfectly balanced across three linguistic styles:

* **English:** 2,220 (33.3%)
* **Tagalog:** 2,220 (33.3%)
* **Taglish:** 2,220 (33.3%)

### 3. Emotional Intelligence (EQ) Distribution

CLAIRE is trained to adapt its tone based on the user's emotional state. Each language contains exactly 370 samples per emotion:

* **Neutral:** 1,110 (16.7%)
* **Urgent:** 1,110 (16.7%)
* **Grateful:** 1,110 (16.7%)
* **Frustrated:** 1,110 (16.7%)
* **Confused:** 1,110 (16.7%)
* **Worried:** 1,110 (16.7%)

### 4. Document Relevance (RAFT Split)

* **Samples with 1 'Golden' Document:** 5,328 (80.0%)
* **Samples with 'Distractor' Documents Only:** 1,332 (20.0%)

---
## Technical Use Case

This dataset is designed for fine-tuning CLAIRE to achieve:

1. **Contextual Precision:** High accuracy in filtering out irrelevant noise.
2. **Linguistic Inclusivity:** Seamless transitions between English, Tagalog, and Taglish.
3. **Emotional Resonance:** Tailored responses that de-escalate frustration and provide comfort to worried users.
4. **Operational Trust:** Significant reduction in hallucinations through the 20% "Closed-Book" training.

**Developed by Team MangTomas under Track 3 of BPI Datawave 2025.**
