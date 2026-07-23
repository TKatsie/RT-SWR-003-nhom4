#### **1\. Title & Team Information**

**Research Proposal:** Mitigating Hallucinations and Uncertainty in Documentation-to-Code Traceability Using a Multi-Agent Consensus Framework

**Team:** 4

**Members:** Nguyen Dinh Tri, Nguyen Cao Phuong Binh, Ho Minh Quan

**Topic code:** RBL-SWR

**Submission date:** 2026-07-16

**Version:** 1.0

**Status:** Pending Approval

#### **2\. Research Problem Statement**

##### **2.1 Background & Importance**

In software engineering, maintaining traceability between technical documentation and source code is a key factor in ensuring system consistency. However, applying Large Language Models (LLMs) to this task faces major reliability hurdles due to their non-deterministic nature and tendency to generate hallucinated links.

##### **2.2 State of the Art**

Recent studies, such as *Evaluating the Use of LLMs for Documentation to Code Traceability* (2026, TOSEM), have achieved F1 scores of up to 80.4% on the Unity Catalog dataset. However, the authors themselves admit that LLM non-determinism is a major threat to practical value. Tools like SpecMap or LiSSA have begun using layered tasks or RAG, but they still lack an automated validation mechanism to eliminate "Phantom Links" — links pointing to files or functions that do not actually exist in the source code.

##### **2.3 GAP**

**GAP-T (Technical GAP):** There is currently a lack of robust validation protocols and automated mitigation frameworks to handle the highly volatile, non-deterministic outputs and high frequency of "Phantom Link" hallucinations in LLM-based documentation-to-code traceability. Out of 34 reviewed papers, only one quantified this error, but it did not propose a mitigation algorithm.

##### **2.4 Motivation**

If this GAP is not addressed, AI-driven traceability systems cannot be deployed in real-world production environments because engineers cannot trust results that change with every run or instructions that point to non-existent code. Establishing an "Auditor" mechanism will help increase the reliability and reproducibility of the entire workflow.

#### **3\. Related Work**

##### **3.1 Overview**

| Study | Tool/LLM | Dataset | Outstanding Results | Main Limitations |
| :---- | :---- | :---- | :---- | :---- |
| *Evaluating the Use of LLMs for Documentation to Code Traceability* (2026, TOSEM) | "Claude 3.5, GPT-4o" | Unity Catalog | F1: 80.4% | High non-determinism |
| *SpecMap* (2026) | Gemini 2.5 Flash | Embedded systems | Acc: 73.3% | Confidence calibration issues |
| *GPT-5.1* (2026) | GPT-5.1 | Apache | P@1: 95.3% | Focused only on Issue-to-Commit |
| *CoT-TLR* (2025) | LLM \+ CoT | CoEST | MAP increased by 125% | Not purely zero-shot |
| *LiSSA* (2025) | LLM \+ RAG | Multi-task | Achieved qualitative SOTA | Lacks sequential quantitative analysis |

##### 

##### **3.2 Pattern Analysis**

Studies show that hallucination-driven errors (Phantom Links) can account for up to 30.7% in narrative documentation datasets such as Crawl4AI. Most current tools rely on a single run, which leads them to overlook accuracy variance across different execution cycles.

##### **3.3 GAP Mapping**

| GAP Type | Evidence | Status |
| :---- | :---- | :---- |
| GAP-T (Hallucination Validation) | *Evaluating the Use of LLMs for Documentation to Code Traceability* (2026, TOSEM) confirms PAL errors up to 30.7% | Confirmed |
| GAP-S (Reproducibility) | 33 out of 34 papers do not measure variance between runs | Confirmed |

#### **4\. Research Questions**

**RQ1:** Does the Multi-Agent Consensus framework help achieve a **Trace Stability Score (TSS) \> 90%** across 10 repeated runs?

* **Metric:** Trace Stability Score (TSS) \- measures the consistency of the generated links.  
* **Threshold:** 90%.  
* **Statistical test:** Wilcoxon signed-rank test.

**RQ2:** Does using **o3-mini (High reasoning effort)** as an auditor agent help reduce the **Phantom Link Rate (PLR)** below a **5%** threshold?

* **Metric:** Phantom Link Rate (PLR).  
* **Threshold:** 5% (a significant reduction from the current \~30% level).  
* **Statistical test:** Binomial exact test.

#### **5\. Experiment Protocol**

##### **5.1 Pipeline Overview**

1. **Link Proposal:** Use GPT-4o (Primary Agent) to propose traceability links from the documentation.  
2. **Cross-Verification:** Use o3-mini (Auditor Agent) with high reasoning mode to cross-reference these links against the actual repository structure.  
3. **Consensus Filtering:** Keep only the links agreed upon by both agents and confirmed by the Auditor to exist in the source code.  
4. **Stability Testing:** Run the workflow 10 times repeatedly using different seeds to measure the TSS.  
5. **Evaluation:** Compare the outcomes against the ground truth to calculate the PLR.

   ##### **5.2 Dataset**

* **Dataset name:** Crawl4AI.  
* **Selection rationale:** Contains a large amount of narrative documentation prone to LLM hallucinations and already provides ground truth labels for Phantom Links.

  ##### **5.3 LLM/Tool Configuration**

* **Primary Agent:** GPT-4o (Temperature \= 0.7 to evaluate stability).  
* **Auditor Agent:** o3-mini (Temperature \= 0, Reasoning effort \= High).

  ##### **5.4 Measurement**

* **Metric 1:** Trace Stability Score (TSS).  
* **Metric 2:** Phantom Link Rate (PLR).

#### **6\. Evaluation Plan**

| RQ | Metric | Threshold | Test | H0 is rejected when... |
| :---- | :---- | :---- | :---- | :---- |
| **RQ1** | **TSS** | **90%** | **Wilcoxon** | **p-value \< 0.05 & Median \> 0.90** |
| **RQ2** | **PLR** | **5%** | **Binomial** | **p-value \< 0.05 & Rate \< 5%** |

#### **7\. Threats to Validity**

* #### **Internal Validity: API costs associated with multiple repeated runs and the latency introduced by the o3-mini model.**

* #### **External Validity: The effectiveness of the consensus framework may vary depending on the programming language of the source code.**

* #### **Construct Validity: The definition of "hallucination" might shift if the source code contains auto-generated (dynamic) components.**

#### **8\. Timeline & Resources**

#### 

##### **8.0 Role Assignments**

| Role | Member | Responsibilities in the experiment |
| :---- | :---- | :---- |
| PL  | Nguyen Dinh Tri | Manages overall progress and ensures report consistency. |
| DG | Nguyen Cao Phuong Binh | Preprocesses the Crawl4AI dataset and sets up the source code validation environment. |
| LR  | Nguyen Cao Phuong Binh | Configures prompts, manages the o3-mini and GPT-4o APIs, and executes the multi-agent framework. |
| MS | Ho Minh Quan | Develops scripts to calculate TSS and PLR, and performs statistical testing. |
| RW  | Nguyen Dinh Tri | Synthesizes results, plots error distribution charts, and finalizes the paper. |

##### **8.1 Resource Inventory**

* **Software:** Python 3.11, OpenAI SDK, Pandas, and Scipy libraries.  
* **Data:** Crawl4AI dataset (Ground truth available).  
* **Budget:** Estimated at $200 USD for API expenses (prioritizing repeated runs for RQ1).

  ##### **8.3 Detailed Timeline**

* **Weeks 1-2:** Set up the environment and prepare source code directory structure extraction scripts (Static Analysis).  
* **Weeks 3-4:** Build the Multi-Agent framework and run tests on a small sample set.  
* **Weeks 5-6:** Run the formal experiment 10 times to collect data on stability.  
* **Weeks 7-8:** Perform error analysis, calculate metrics, and execute Wilcoxon/Binomial statistical tests.  
* **Weeks 9-10:** Finalize the ultimate report and prepare the presentation.

  ##### **8.4 Contingency Plan**

* **If API costs exceed the budget:** Reduce the number of repeated runs from 10 to 5\.  
* **If o3-mini is too slow:** Substitute GPT-4o-mini as the Auditor but apply enhanced Few-shot prompting techniques to offset reasoning capabilities.

