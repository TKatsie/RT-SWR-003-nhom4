### PRISMA Flow Diagram — Software Traceability Link Recovery: GPT-4 vs. IR Methods

[**Records từ database searching (N = 123)**]  
← Tổng số bản ghi thu được từ 9 chuỗi tìm kiếm (A-I)  
↓  
[**Sau khi xóa duplicate (N = 91)**]  
← Số lượng bản ghi duy nhất trong `01_all_records.csv`  
↓  
┌───────────────────────────────────────────────────┐  
│ **Screened title + abstract (N = 91)**            │  
│  └─ **Excluded (N = 56):**                        │  
│     Vi phạm các tiêu chí sàng lọc sơ bộ (Phase 1) │  
│     chủ yếu là EC-Dom (Sai lĩnh vực) và           │  
│     EC-O (Sai mục tiêu kỹ thuật).                 │  
└───────────────────────────────────────────────────┘  
↓  
**35 papers pass**  
← Tổng số bài (INCLUDE + UNSURE) từ `02_after_screening_v1.csv`  
↓  
┌────────────────────────────────────────────────┐  
│ **Full-text assessed (N = 35)**                │  
│  └─ **Excluded (N = 27):**                     │  
│     - EC-A (16 bài): 13 bài không tìm thấy tài │  
│       liệu, 2 bài dính Paywall (64, 74), và    │  
│       1 bài thiếu nội dung (65).               │  
│     - Vi phạm ie_criteria (11 bài): EC-Dom,    │  
│       EC-O (Survey), EC-N.                     │  
└────────────────────────────────────────────────┘  
↓  
[**Final included (N = 8)**]  
← Các bài báo đáp ứng đủ tiêu chí IC-L đến IC-E trong `03_final_included_v2.csv`  

---

##### Kiểm tra nhất quán (Self-check):

*   **N sau dedup:** 91 (Số lượng bản ghi thực tế trong tệp 01).
*   **Excluded vòng 1:** 56 (Loại bỏ các bài về y tế, luật, robot, hoặc không tập trung vào TLR phần mềm).
*   **Full-text assessed:** 35 (Bao gồm các bài được đánh dấu INCLUDE và UNSURE từ Phase 1).
*   **Excluded vòng 2:** 27 (Trong đó 15 bài do thiếu tài liệu/Paywall theo danh sách thủ công, 12 bài còn lại vi phạm tiêu chí về nội dung sau khi quét PDF).
*   **Final included:** 8 (Gồm các ID: 2, 12, 33, 34, 66, 68, 72 và 80).