# Hypotheses

**Study:** GPT-4 Zero-Shot Requirement-to-Source-Code Traceability Link Recovery
**Derived from:** `01_rq.md` — Refined RQ (final)

> Each RQ maps to one or more H0/H1 pairs. H0 is the null hypothesis (negation of what we aim to demonstrate). H1 is the research hypothesis (the expected result).

---

## RQ1 — MAP@10 and Recall vs. IR Baselines

**Question:** Do GPT-4 zero-shot generated traceability links achieve MAP@10 ≥ 0.70 and Recall ≥ 0.80 at class-level granularity on CoEST benchmark datasets, compared to the best-performing IR baseline among VSM, LSI, and BM25?

| | Hypothesis |
|---|---|
| **H0₁ₐ** | Mean MAP@10 of GPT-4 zero-shot generated traceability links on CoEST datasets is **≤ 0.70** — i.e., GPT-4 does **not** reach the MAP@10 threshold. |
| **H1₁ₐ** | Mean MAP@10 of GPT-4 zero-shot generated traceability links on CoEST datasets is **> 0.70**. |
| **H0₁ᵦ** | Mean Recall of GPT-4 zero-shot generated traceability links on CoEST datasets is **≤ 0.80** — i.e., GPT-4 does **not** reach the Recall threshold. |
| **H1₁ᵦ** | Mean Recall of GPT-4 zero-shot generated traceability links on CoEST datasets is **> 0.80**. |
| **H0₁꜀** | MAP@10 of GPT-4 zero-shot is **≤** MAP@10 of the best-performing IR baseline (VSM/LSI/BM25) — i.e., GPT-4 does **not** outperform the strongest IR method. |
| **H1₁꜀** | MAP@10 of GPT-4 zero-shot is **>** MAP@10 of the best-performing IR baseline. |

**Statistical test:** Wilcoxon signed-rank test (one-sample, non-parametric; H0₁ₐ/H0₁ᵦ against fixed thresholds), paired Wilcoxon signed-rank test (H0₁꜀, GPT-4 vs. best IR baseline on the same requirement set)
**Significance level:** α = 0.05
**Interpretation example:** If p = 0.02 < 0.05 for H0₁ₐ, reject H0₁ₐ and conclude mean MAP@10 significantly exceeds 0.70.

---

## RQ2 — Cross-Project Generalization

**Question:** Does GPT-4 zero-shot traceability performance generalize consistently across the 3 CoEST projects (iTrust, eTour, EasyClinic) without prompt retuning, and how does its cross-project performance variance compare to IR-based methods?

| | Hypothesis |
|---|---|
| **H0₂** | The variance of GPT-4 zero-shot performance (MAP@10) across the 3 CoEST projects is **≥** the variance of the best-performing IR baseline — i.e., GPT-4 does **not** generalize more consistently than IR methods. |
| **H1₂** | The variance of GPT-4 zero-shot performance (MAP@10) across the 3 CoEST projects is **<** the variance of the best-performing IR baseline — i.e., GPT-4 generalizes **more consistently** (lower cross-project variance) than IR methods. |

**Statistical test:** Levene's test for equality of variances (robust to non-normality), applied to per-project MAP@10 scores of GPT-4 vs. best IR baseline
**Significance level:** α = 0.05
**Interpretation example:** If p = 0.04 < 0.05, reject H0₂ and conclude GPT-4 zero-shot has significantly more consistent (lower-variance) cross-project performance than the IR baseline.

---

## RQ3 — Hallucination Rate (Zero-Shot vs. Few-Shot)

**Question:** What is the hallucination rate of GPT-4-generated traceability links (links to non-existent classes), and does few-shot prompting with example requirement-class pairs significantly reduce hallucination compared to zero-shot?

| | Hypothesis |
|---|---|
| **H0₃** | The hallucination rate (proportion of generated links pointing to non-existent classes) of GPT-4 few-shot prompting is **≥** the hallucination rate of GPT-4 zero-shot prompting — i.e., few-shot examples do **not** reduce hallucination. |
| **H1₃** | The hallucination rate of GPT-4 few-shot prompting is **<** the hallucination rate of GPT-4 zero-shot prompting — i.e., few-shot examples **significantly reduce** hallucination. |

**Statistical test:** McNemar's test (paired binary outcomes — same requirement set evaluated under both zero-shot and few-shot conditions)
**Significance level:** α = 0.05
**Interpretation example:** If p = 0.01 < 0.05, reject H0₃ and conclude few-shot prompting significantly reduces the hallucination rate compared to zero-shot.

---

## Summary Table

| RQ | Metric | H0 | H1 | Test | α |
|----|--------|----|----|------|---|
| RQ1a | MAP@10 (class-level, CoEST) | MAP@10 ≤ 0.70 | MAP@10 > 0.70 | Wilcoxon signed-rank (one-sample) | 0.05 |
| RQ1b | Recall (class-level, CoEST) | Recall ≤ 0.80 | Recall > 0.80 | Wilcoxon signed-rank (one-sample) | 0.05 |
| RQ1c | MAP@10 vs. best IR baseline | MAP@10_GPT4 ≤ MAP@10_IR | MAP@10_GPT4 > MAP@10_IR | Wilcoxon signed-rank (paired) | 0.05 |
| RQ2 | Cross-project variance (MAP@10) | Var_GPT4 ≥ Var_IR | Var_GPT4 < Var_IR | Levene's test | 0.05 |
| RQ3 | Hallucination rate (zero-shot vs. few-shot) | Rate_fewshot ≥ Rate_zeroshot | Rate_fewshot < Rate_zeroshot | McNemar's test | 0.05 |

---

## Grounding in SLR Evidence

| Hypothesis | Evidence basis |
|------------|---------------|
| H0₁ₐ/H1₁ₐ threshold = 0.70, H0₁ᵦ/H1₁ᵦ threshold = 0.80 | ⚠️ **Không được anchor trực tiếp** bởi số liệu tuyệt đối trong 8 paper — không paper nào báo cáo MAP@10/Recall tuyệt đối. #3 (Wang et al. 2025) chỉ báo cáo % cải thiện tương đối (125.47% so với LSI). Ngưỡng 0.70/0.80 là **giả định nghiên cứu dựa trên thông lệ chung của literature TLR**, cần nhóm xác nhận lại — khác với ví dụ BDD/Gherkin nơi ngưỡng có anchor số liệu trực tiếp. |
| H0₁꜀/H1₁꜀ so với best IR baseline | #1 (Fuchß et al. 2025) cho thấy IR baseline nhạy cảm với hyperparameter, hiệu năng dao động — củng cố lý do cần so sánh GPT-4 với **best-performing** IR baseline (không phải baseline cố định) |
| H0₂/H1₂ cross-project variance | Không paper nào trong 8 paper đo variance cross-project như một chỉ số riêng; #3 dùng 4 dự án khác chuẩn CoEST (thiếu EasyClinic) nên không có số liệu variance trực tiếp để anchor — đây là khoảng trống được xác nhận qua **việc không có evidence**, không phải qua số liệu phủ định |
| H0₃/H1₃ hallucination zero-shot vs. few-shot | #5 (Rodriguez et al. 2023) là paper duy nhất bàn về giảm lỗi link qua prompt engineering nhưng **chỉ định tính**, không có con số hallucination rate cụ thể để anchor ngưỡng hay hiệu ứng kỳ vọng |
| Wilcoxon (không dùng t-test) cho RQ1 | MAP@10/Recall bị chặn trong [0,1] và thường lệch phân phối (skewed) — không thể giả định phân phối chuẩn tiên nghiệm, giống lý do dùng Wilcoxon trong nghiên cứu tương tự (BDD/Gherkin similarity scores) |
| Levene's test cho RQ2 | Levene's test bền vững hơn F-test truyền thống khi dữ liệu không thoả giả định phân phối chuẩn — phù hợp với cỡ mẫu nhỏ (chỉ 3 dự án CoEST) |
| McNemar's test cho RQ3 | Hallucination là outcome nhị phân (có/không) đo trên **cùng một tập requirement** dưới 2 điều kiện (zero-shot, few-shot) — McNemar's test là phương pháp chính xác cho dữ liệu nhị phân bắt cặp (paired binary data), tương tự cách Binomial test được chọn cho outcome nhị phân đơn trong ví dụ BDD/Gherkin |

---

*Save to: `experiment/hypotheses.md`*
