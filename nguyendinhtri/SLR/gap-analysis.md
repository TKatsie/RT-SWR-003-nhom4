# GAP Analysis – **Non-determinism and Hallucination Mitigation in LLM-based Traceability**

**Member: Nguyễn Đình Trí**  
**GAP type:** GAP-T (Technical)  
**Date:** 2026-07-16  
**Evidence table source:** evidence-table-merged.md (N \= 34 papers)

## 1\. GAP Description

The primary challenge lies in the **unreliability and lack of reproducibility of trace links produced by LLMs due to their non-deterministic nature and propensity for hallucinations.** Current research identifies these as persistent limitations where models generate "Phantom Links" (hallucinated artifacts) or produce inconsistent results across identical queries, yet there is a lack of standardized frameworks to quantify and mitigate this variance in a production environment.  
**Evidence from evidence table:**

* **Metric / Limitation:** The source paper explicitly lists the "non-deterministic nature of LLMs" as a core threat to internal validity.  
* **Observed Patterns:** In the Crawl4AI dataset, **Phantom Link (PAL) errors**—where the LLM traces to code that doesn't actually exist—accounted for up to **30.7% of false positives** for models like Claude 3.5 Sonnet.  
* **Pattern:** Only 1 out of 34 papers (Alor et al., 2025\) systematically quantified these specific error types through multiple experimental runs.

## 2\. Counter-evidence Check

| Paper | Addressed this GAP? | Details |
| :---- | :---- | :---- |
| Alor et al. (2025/2026) | Partially | Conducted five runs with different seeds to measure variance and categorized "Phantom Link" errors, but did not propose a mitigation algorithm." |
| Ahmed et al. (2024) | Partially | "Discussed if LLMs can replace manual annotation and noted hallucinations, but focused on general SE artifacts." |
| Dealing with Data for RE (2024) | Partially | Noted LLM hallucinations as a limitation in NFR classification but lacked a technical solution for traceability. |

**Conclusion:** GAP confirmed ✅ (While recognized as a limitation, there is no established "verification layer" or "consensus mechanism" in the literature to solve the non-determinism and phantom-link issue in software traceability.)

## 3\. Feasibility Check

| Criteria | Level | Note |
| :---- | :---- | :---- |
| Dataset | ✅ | "Use Crawl4AI and Unity Catalog as they already contain ""Phantom Link"" ground truth markers." |
| API/Tool | ✅ | Access to GPT-4o and o3-mini (with reasoning effort settings) is available. |
| Computation | ✅ | "Measuring variance requires repeated API calls, which is feasible with current caching mechanisms." |
| Ground truth | ✅ | High-quality manual verification (κ \= 0.94) is already available in the source paper. |
| Code base | ✅ | Open-source projects post-April 2024 provide a clean testbed. |
| Skills | ✅ | Requires statistical analysis of variance and prompt engineering for verification agents. |

**Result:** 6/6 ✅ → **High Feasibility / Low Risk**

## 4\. Formal GAP Statement

**"There is a lack of robust verification protocols and automated mitigation frameworks designed to handle the non-deterministic output variance and the high frequency of 'phantom-link' hallucinations in LLM-based documentation-to-code traceability."**

## 5\. Preliminary Proposal for the Team

* **Feasible Dataset:** **Crawl4AI** (selected due to its high rate of narrative-induced hallucinations in previous tests).  
* **Proposed Metric:** **Trace Stability Score (TSS)** (measuring link consistency across 10+ runs) and **Phantom Link Rate (PLR)**.  
* **Proposed LLM/Tool:** **o3-mini (High reasoning effort)** as a "Verifier Agent" to cross-reference the primary model's outputs.  
* **Proposed Baseline:** The **One-to-many strategy** from the Alor et al. (2025) paper, which reported a 95.3%–100% precision but noted high non-determinism threats.  
* **Preliminary Solution:** Implement a **"Multi-Agent Consensus" framework** where a primary LLM proposes links and a secondary "Auditor LLM" (using a different architecture) verifies each link against the actual file directory to filter out hallucinations.

