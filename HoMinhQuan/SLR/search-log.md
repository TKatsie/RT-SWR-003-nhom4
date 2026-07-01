# Search Log — GPT-4 Zero-Shot for Requirement-to-Source-Code Traceability Link Recovery (vs. IR-based methods)
Thành viên: Hồ Minh Quân
Ngày thực hiện: 2026-06 – 2026-07-01

---

## Chuỗi tìm kiếm (Query Strings)

### String A
Query nguyên văn: `("GPT-4" OR "GPT4" OR "large language model" OR "LLM" OR "prompting") AND ("traceability link" OR "software traceability" OR "traceability recovery" OR "requirement-to-source-code") AND ("information retrieval" OR "VSM" OR "LSI" OR "BM25" OR "vector space model")`
Database: IEEE Xplore
Bộ lọc: Không có bộ lọc
Ngày search: 2026-06
Số kết quả: 7

---

### String B
Query nguyên văn: `("GPT-4" OR "zero-shot") AND ("traceability" OR "traceability link") AND ("CoEST" OR "benchmark") AND ("MAP" OR "MAP@10" OR "Recall" OR "VSM" OR "LSI" OR "BM25")`
Database: IEEE Xplore
Bộ lọc: Không có bộ lọc
Ngày search: 2026-06
Số kết quả: 1

---

### String C
Query nguyên văn: `("GPT-4" OR "large language model" OR "zero-shot") AND ("traceability" OR "traceability link") AND ("generalize" OR "generalizability" OR "cross-project" OR "variance" OR "retuning" OR "prompt engineering")`
Database: IEEE Xplore
Bộ lọc: Không có bộ lọc
Ngày search: 2026-06
Số kết quả: 6

---

### String D
Query nguyên văn: `("GPT-4" OR "large language model" OR "LLM") AND ("traceability" OR "traceability link") AND ("hallucination" OR "false positive" OR "non-existent") AND ("few-shot" OR "zero-shot")`
Database: IEEE Xplore
Bộ lọc: Không có bộ lọc
Ngày search: 2026-06
Số kết quả: 2

---

### String E
Query nguyên văn: `("LLM" OR "ChatGPT" OR "GPT" OR "large language model") AND ("traceability link" OR "trace link recovery" OR "traceability recovery") AND ("source code" OR "requirement*")`
Database: IEEE Xplore (chạy trực tiếp trên Advanced Search, export CSV)
Bộ lọc: Không có bộ lọc
Ngày search: 2026-07-01
Số kết quả: 7 (6/7 trùng với String A/C/D, 1 record mới)

---

## Tổng hợp trước dedup

| Database | String | Kết quả |
| :---- | :---- | :---- |
| IEEE Xplore | String A | 7 |
| IEEE Xplore | String B | 1 |
| IEEE Xplore | String C | 6 |
| IEEE Xplore | String D | 2 |
| IEEE Xplore | String E | 7 |
| Tổng trước dedup | | 23 |
| Sau dedup (Thực tế) | | 15 |
| Số bị loại (Trùng lặp) | | 8 |

*(1 bài "Prompts Matter: Insights and Strategies for Prompt Engineering in Automated Software Traceability" xuất hiện ở cả String A, C, D → gộp còn 1, loại 2 trùng lặp; 6/7 kết quả của String E trùng với các bài đã có ở String A/C/D → loại tiếp 6 trùng lặp. Tổng loại: 2 + 6 = 8.)*

---

## Danh sách tài liệu và Liên kết tải về

### Toàn bộ 8 bài báo đều bị Paywall (IEEE Xplore — không phải Open Access)

Khác với đợt search "LLM for Acceptance Test Automation", không có bài nào trong 8 bài dưới đây thuộc diện IEEE Access/Open Access. Tất cả đều nằm trong các proceedings hội nghị (RE, REW, ICSE, ICSA, APSEC, CASCON) yêu cầu **subscription cá nhân/tổ chức hoặc mua lẻ (pay-per-view)** để tải PDF. Link `stamp.jsp` dưới đây sẽ chỉ hiện được PDF nếu tài khoản IEEE Xplore đang truy cập có quyền (qua thư viện trường/viện, VPN institutional, hoặc đã mua bài).

| ID | Authors | Title | Year | Venue | DOI | PDF Link |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| 1 | D. Fuchß; S. Schwedt; J. Keim; T. Hey | Beyond Retrieval: A Study of Using LLM Ensembles for Candidate Filtering in Requirements Traceability | 2025 | 2025 IEEE 33rd International Requirements Engineering Conference Workshops (REW) | 10.1109/REW66121.2025.00006 | https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=11190238 |
| 2 | T. Hey; J. Keim; S. Corallo | Requirements Classification for Traceability Link Recovery | 2024 | 2024 IEEE 32nd International Requirements Engineering Conference (RE) | 10.1109/RE59067.2024.00024 | https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10628507 |
| 3 | W. Wang; Y. Wang; L. Zhao; Q. Huang; B. Jiang | Enhancing Requirement-to-Code Traceability via Chain-of-Thought Prompting in Large Language Models | 2025 | 2025 32nd Asia-Pacific Software Engineering Conference (APSEC) | 10.1109/APSEC66846.2025.00083 | https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=11396549 |
| 4 | D. Fuchß; T. Hey; J. Keim; H. Liu; N. Ewald; T. Thirolf; A. Koziolek | LiSSA: Toward Generic Traceability Link Recovery Through Retrieval-Augmented Generation | 2025 | 2025 IEEE/ACM 47th International Conference on Software Engineering (ICSE) | 10.1109/ICSE55347.2025.00186 | https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=11029919 |
| 5 | A. D. Rodriguez; K. R. Dearstyne; J. Cleland-Huang | Prompts Matter: Insights and Strategies for Prompt Engineering in Automated Software Traceability | 2023 | 2023 IEEE 31st International Requirements Engineering Conference Workshops (REW) | 10.1109/REW57809.2023.00087 | https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10260721 |
| 6 | D. Fuchß; H. Liu; T. Hey; J. Keim; A. Koziolek | Enabling Architecture Traceability by LLM-based Architecture Component Name Extraction | 2025 | 2025 IEEE 22nd International Conference on Software Architecture (ICSA) | 10.1109/ICSA65012.2025.00011 | https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10978943 |
| 7 | S. S. Nath; B. Roy; M. Jahan | Establishing Traceability Between Release Notes & Software Artifacts: Practitioners' Perspectives | 2025 | 2025 IEEE International Conference on Collaborative Advances in Software and COmputiNg (CASCON) | 10.1109/CASCON66301.2025.00067 | https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=11344146 |
| 15 | H. Jin; Y. Yuan; B. Wang; H. Wan; Z. Zou | HGTRTracer: Advancing Requirements-Code Traceability with LLM-Augmented Attribution Reasoning and Heterogeneous Graph Transformer | 2025 | 2025 32nd Asia-Pacific Software Engineering Conference (APSEC) | 10.1109/APSEC66846.2025.00070 | https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=11396602 |
