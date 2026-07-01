# GAP Statement

**Topic:** GPT-4 Zero-Shot for Requirement-to-Source-Code Traceability Link Recovery (vs. IR-based methods)
**Systematic Literature Review · 2026 (pilot run)**
23 records retrieved (String A–E) → 15 sau dedup → 8 included

---

## Research Question (refined)

> "How effectively does GPT-4 zero-shot prompting generate class-level requirement-to-source-code traceability links in software projects, compared to IR-based automated methods (VSM, LSI, BM25) on CoEST public benchmark datasets?"

**Sub-RQs:**

- **RQ1:** Do GPT-4 zero-shot generated traceability links achieve **MAP@10 ≥ 0.70** and **Recall ≥ 0.80** at class-level granularity on CoEST benchmark datasets, compared to the best-performing IR baseline among VSM, LSI, and BM25?
- **RQ2:** Does GPT-4 zero-shot traceability performance generalize consistently across the **3 CoEST projects** (iTrust, eTour, EasyClinic) without prompt retuning, and how does its cross-project performance variance compare to IR-based methods?
- **RQ3:** What is the **hallucination rate** of GPT-4-generated traceability links (links to non-existent classes), and does few-shot prompting with example requirement-class pairs significantly reduce hallucination compared to zero-shot?

---

## GAP Statement

**Cả 8 papers** được reviewed đều tập trung vào việc dùng LLM (bao gồm GPT-4/GPT-4o, các LLM khác, hoặc LLM kết hợp RAG/GNN) để hỗ trợ hoặc cải thiện traceability link recovery (TLR) giữa requirement và code/artifact khác, có so sánh (trực tiếp hoặc gián tiếp) với các phương pháp IR truyền thống.

Tuy nhiên, **KHÔNG CÓ paper nào**:

1. Dùng **GPT-4 (hoặc GPT-4o)** với **zero-shot prompting thuần** (không CoT, không RAG, không fine-tune, không ví dụ few-shot) để sinh trace link ở **granularity class-level** giữa requirement và source code;
2. So sánh đồng thời với **cả 3 baseline IR truyền thống** (VSM, LSI, BM25) trong cùng một thí nghiệm có kiểm soát — paper gần nhất (#3, Wang et al. 2025) chỉ so với LSI, thiếu VSM và BM25;
3. Đánh giá **cross-project variance** trên đúng **3 dự án CoEST chuẩn** (iTrust, eTour, EasyClinic) — paper gần nhất (#3) dùng iTrust, eTour, eANCI, SMOS (không có EasyClinic); không paper nào báo cáo độ lệch hiệu năng giữa các dự án như một chỉ số riêng;
4. Đo lường **hallucination rate** (tỉ lệ trace link trỏ đến class không tồn tại) một cách **định lượng** — paper gần nhất (#5, Rodriguez et al. 2023) chỉ bàn định tính về prompt engineering để giảm lỗi, không có con số cụ thể; cũng không paper nào so sánh hallucination rate giữa zero-shot và few-shot.

**Hai paper gần RQ nhất nhưng đều không khớp đầy đủ thiết kế nghiên cứu:**
- **#3 (Wang et al., 2025, IEEE APSEC):** đúng dataset CoEST (iTrust, eTour) và có số liệu MAP định lượng, nhưng dùng **Chain-of-Thought prompting** (không phải zero-shot thuần) và chỉ so với **LSI** (thiếu VSM, BM25).
- **#6 (Fuchß et al., 2025, IEEE ICSA):** dùng đúng **GPT-4o** và có F1 định lượng, nhưng ở **granularity kiến trúc** (SAD↔code), không phải **class-level requirement-to-code**; cũng không so với VSM/LSI/BM25.
- **#8 (HGTRTracer, Jin et al., 2025, IEEE APSEC):** là phương pháp LLM-based TLR requirement-to-code khá gần, nhưng dùng **LLM + Graph Neural Network** (không phải zero-shot prompting thuần), đánh giá trên **10 dự án open-source riêng** (không dùng CoEST), nên không đóng góp trực tiếp cho RQ2.

**→ GAP:** Hiện tại chưa có nghiên cứu nào đánh giá toàn diện khả năng của **GPT-4 zero-shot thuần** trong việc sinh trace link ở **class-level** giữa requirement và source code, đồng thời so sánh với **đầy đủ 3 baseline IR (VSM, LSI, BM25)**, đo **cross-project variance** trên đúng **3 dự án CoEST chuẩn**, và định lượng **hallucination rate** — trong cùng một thiết kế thực nghiệm nhất quán.

**→ Contribution của nghiên cứu này:**
Nghiên cứu sẽ thực hiện đánh giá thực nghiệm GPT-4 zero-shot (không CoT, không few-shot) trên **3 dự án CoEST chuẩn (iTrust, eTour, EasyClinic)**, đo **MAP@10 và Recall** ở granularity class-level, so sánh trực tiếp với cả **VSM, LSI, BM25**, phân tích **cross-project performance variance**, và định lượng **hallucination rate** (link đến class không tồn tại) — kèm so sánh với biến thể few-shot để kiểm tra khả năng giảm hallucination — nhằm lấp khoảng trống trên.

---


