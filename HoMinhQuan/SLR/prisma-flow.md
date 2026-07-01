# PRISMA Flow Diagram

**Topic:** GPT-4 Zero-Shot for Requirement-to-Source-Code Traceability Link Recovery (vs. IR-based methods)
**Search date:** June–July 2026 (pilot run)

---

```
┌─────────────────────────────────────────────────────────┐
│            Records identified from database searching    │
│   String A (IEEE Xplore):            7 records          │
│   String B (IEEE Xplore):            1 records          │
│   String C (IEEE Xplore):            6 records          │
│   String D (IEEE Xplore):            2 records          │
│   Tổng cộng:                        16 records          │
└──────────────────────────┬──────────────────────────────┘
                           │
                           ▼  Xóa duplicate (N = 2)
┌─────────────────────────────────────────────────────────┐
│               Sau khi xóa duplicate                      │
│                      N = 14                              │
└──────────────────────────┬──────────────────────────────┘
                           │
                           ▼  Vòng 1: Title + Abstract Screening
              ┌────────────┴────────────┐
              ▼                         ▼
┌─────────────────────┐    ┌───────────────────────────────┐
│  Records screened   │    │  Excluded (N = 7)              │
│     (N = 14)        │    │  EC4 – Không liên quan TLR      │
│                     │    │        (N = 7)                 │
│  INCLUDE: N = 7     │    │                                │
└──────────┬──────────┘    └───────────────────────────────┘
           │
           ▼  Vòng 2: Full-text Screening
┌─────────────────────────────────────────────────────────┐
│                Full-text assessed (N = 7)                │
└──────────────────────────┬──────────────────────────────┘
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
┌─────────────────────┐    ┌───────────────────────────────┐
│  Included in        │    │  Excluded (N = 0)              │
│  Evidence Table     │    │                                │
│     (N = 7)         │    │                                │
└─────────────────────┘    └───────────────────────────────┘
```

---

## Ghi chú

- **String A:** `("GPT-4" OR "GPT4" OR "large language model" OR "LLM" OR "prompting") AND ("traceability link" OR "software traceability" OR "traceability recovery" OR "requirement-to-source-code") AND ("information retrieval" OR "VSM" OR "LSI" OR "BM25" OR "vector space model")` — 7 records
- **String B:** `("GPT-4" OR "zero-shot") AND ("traceability" OR "traceability link") AND ("CoEST" OR "benchmark") AND ("MAP" OR "MAP@10" OR "Recall" OR "VSM" OR "LSI" OR "BM25")` — 1 record
- **String C:** `("GPT-4" OR "large language model" OR "zero-shot") AND ("traceability" OR "traceability link") AND ("generalize" OR "generalizability" OR "cross-project" OR "variance" OR "retuning" OR "prompt engineering")` — 6 records
- **String D:** `("GPT-4" OR "large language model" OR "LLM") AND ("traceability" OR "traceability link") AND ("hallucination" OR "false positive" OR "non-existent") AND ("few-shot" OR "zero-shot")` — 2 records
- **2 records** trùng lặp (bài "Prompts Matter: Insights and Strategies for Prompt Engineering in Automated Software Traceability" xuất hiện ở cả String A, String C, String D) → gộp thành 1 record duy nhất, xóa 2 duplicate
- **7 records** pass Vòng 1 (INCLUDE) → tiến hành full-text review
- **7 papers** được đưa vào Evidence Table sau full-text screening (không loại thêm ở Vòng 2 do cỡ mẫu pilot nhỏ)

- **String E:** `("LLM" OR "ChatGPT" OR "GPT" OR "large language model") AND ("traceability link" OR "trace link recovery" OR "traceability recovery") AND ("source code" OR "requirement*")` — chạy trực tiếp trên Advanced Search của IEEE Xplore (không qua công cụ search gián tiếp) — **7 records** (export ngày 01/07/2026, file `export2026_07_01-06_53_57.csv`)
  - Đối chiếu DOI: 6/7 records trùng với String A/C/D đã có (Requirements Classification..., Beyond Retrieval..., LiSSA..., Enhancing Requirement-to-Code via CoT..., Enabling Architecture Traceability..., Establishing Traceability Between Release Notes...)
  - **1 record hoàn toàn mới:** *HGTRTracer: Advancing Requirements-Code Traceability with LLM-Augmented Attribution Reasoning and Heterogeneous Graph Transformer* (Jin et al., APSEC 2025) → `id=15` trong `01_all_records.csv`, đã INCLUDE ở cả 2 vòng screening (thoả IC1-IC5 trực tiếp, không cần diễn giải mở rộng)

| Bước | N |
|------|---|
| Records identified (4 chuỗi String A-D) | 16 |
| After duplicate removal | 14 |
| Passed Vòng 1 (INCLUDE) | 7 |
| Excluded Vòng 1 | 7 |
| — EC4: Không liên quan traceability link recovery | 7 |
| Passed Vòng 2 (INCLUDE) | 7 |
| Excluded Vòng 2 | 0 |
| **Final included từ pilot 4-string search** | **7** |
| **+ String E (chạy trực tiếp trên IEEE Xplore, reproducible) — record mới sau khi loại 6 trùng lặp** | **+1** |
| **Tổng Final included in Evidence Table** | **8** |
