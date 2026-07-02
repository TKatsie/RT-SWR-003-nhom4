# Search Log - Software Traceability Link Recovery: GPT-4 vs. IR Method
**Thành viên:** Nguyễn Cao Phương Bình
**Ngày thực hiện:** 2026-06-28

---

## Chuỗi tìm kiếm (Query Strings)

### String A
**Query nguyên văn:**
("GPT-4" OR "LLM") AND "traceability" AND ("VSM" OR "LSI" OR "BM25")
**Database:** OpenAlex
**Bộ lọc:** No filter
**Ngày search:** 2026-07-01 09:42
**Số kết quả:** 37 papers

---

### String B
**Query nguyên văn:**
("GPT-4" OR "zero-shot") AND "traceability" AND ("MAP" OR "Recall") AND ("VSM" OR "LSI" OR "BM25" OR "baseline")
**Database:** OpenAlex
**Bộ lọc:** No filter
**Ngày search:** 2026-07-01 09:50
**Số kết quả:** 29 papers

---

### String C
**Query nguyên văn:**
"GPT-4" AND "traceability" AND ("generalizability" OR "cross-project")
**Database:** OpenAlex
**Bộ lọc:** No filter
**Ngày search:** 2026-07-01 09:52
**Số kết quả:** 6 papers

---

### String D
**Query nguyên văn:**
"GPT-4" AND "traceability" AND ("hallucination" OR "false positive") AND ("zero-shot" OR "few-shot")
**Database:** OpenAlex
**Bộ lọc:** No filter
**Ngày search:** 2026-07-01 09:54
**Số kết quả:** 2 papers

---

### String E
**Query nguyên văn:**
"GPT-4" AND ("source code" OR "requirements") AND ("VSM" OR "LSI" OR "BM25" OR "information retrieval")
**Database:** OpenAlex
**Bộ lọc:** No filter
**Ngày search:** 2026-07-01 09:55
**Số kết quả:** 8 papers

---

# Tổng hợp trước dedup

| Database | String | Kết quả |
| :--- | :--- | :--- |
| OpenAlex | String A | 37 |
| OpenAlex | String B | 29 |
| OpenAlex | String C | 6 |
| OpenAlex | String D | 2 |
| OpenAlex | String E | 8 |
| OpenAlex | String F | 2 |
| OpenAlex | String G | 20 |
| OpenAlex | String H | 3 |
| OpenAlex | String I | 16 |
| **Tổng trước dedup** | | **123** |
| **Sau dedup** | | **91** |
| **Số bị loại (trùng lặp)** | | **32** |

---

## Phần S – Cross-reference Search (Snowballing)

**Phương pháp:** Backward snowballing – đọc reference list của các paper đã pass V2 screen.
**Thực hiện:** Sau khi có `03_final_included.csv`, đọc reference list của từng paper included.
**Công cụ:** CrossRef (crossref.org) để lookup metadata từ DOI; Google Scholar để check formal publication.
**Ngày thực hiện:** YYYY-MM-DD
**Paper included đã scan:** 8 papers
**Paper mới phát hiện:** 0 paper pass IC

---

## Ghi chú

- **Paywalled papers:**
    - ID 64: Machine learning approaches for automated software traceability: A systematic literature review https://doi.org/10.1016/j.jss.2025.112536
    - ID 74: Automated formal-specification-to-code trace links recovery using multi-dimensional similarity measures https://doi.org/10.1016/j.jss.2025.112439
- **Phương pháp thực hiện dedup:** Thực hiện bằng **Excel** (Dựa trên tiêu chí Title, Authors và Year).
- **Phát hiện trùng lặp:** 
    - Paper trùng nhau 32 lần
- **Snowballing:** 0 paper mới tìm được, 0 pass V2