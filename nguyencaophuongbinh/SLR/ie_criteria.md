# IE Criteria — Software Traceability Link Recovery: GPT-4 vs. IR Methods

**Thành viên:** Nguyễn Cao Phương Bình
**RQ:** "How effectively does GPT-4 zero-shot prompting generate class-level requirement-to-source-code traceability links in software projects, compared to IR-based automated methods (VSM, LSI, BM25) on CoEST public benchmark datasets?"
**PICO:** - **P (Population):** Các dự án phần mềm / Bộ dữ liệu mẫu công khai CoEST (eTour, iTrust, SMOS) ở mức độ chi tiết lớp (class-level granularity).
- **I (Intervention):** Kỹ thuật tạo liên kết vết bằng GPT-4 sử dụng zero-shot prompting (và few-shot prompting cho phân tích hallucination).
- **C (Comparison):** Các phương pháp tìm kiếm thông tin truyền thống dựa trên IR (VSM, LSI, BM25).
- **O (Outcome):** Hiệu suất sinh liên kết vết được đo lường qua các chỉ số: MAP@10, Recall, độ biến thiên hiệu suất giữa các dự án (variance), và tỷ lệ ảo tưởng (hallucination rate).

---

## Inclusion Criteria (IC) — Bản nghiên cứu PHẢI đáp ứng đầy đủ các điều kiện sau:

| Mã | Tiêu chí | Chi tiết |
| :--- | :--- | :--- |
| **IC-L** | Ngôn ngữ | Viết bằng tiếng Anh. |
| **IC-Y** | Năm xuất bản | Xuất bản từ năm **2020 đến nay**. <br>*Lý do:* Đây là giai đoạn các mô hình ngôn ngữ lớn (LLM) đột phá và bắt đầu được áp dụng mạnh mẽ vào Kỹ thuật phần mềm; các nghiên cứu trước mốc này không mang tính thời sự cho cấu trúc GPT-4. |
| **IC-T** | Loại hình công bố | Đăng trên các hội nghị (conference) hoặc tạp chí (journal) có quy trình phản biện độc lập (Peer-reviewed). |
| **IC-P** | Phạm vi bài toán (Task) | Nghiên cứu về việc **tự động lập vết yêu cầu phần mềm (Traceability Link Recovery - TLR)**, cụ thể là thiết lập mối liên kết giữa tài liệu yêu cầu (requirements) và mã nguồn (source code) hoặc ngược lại (PICO.P). |
| **IC-I** | Kỹ thuật áp dụng | Sử dụng mô hình ngôn ngữ lớn (đặc biệt là dòng mô hình GPT/LLM prompting) hoặc các phương pháp Information Retrieval truyền thống (VSM, LSI, BM25) để xử lý bài toán liên kết vết (PICO.I & PICO.C). |
| **IC-E** | Minh chứng thực nghiệm | Có ít nhất 1 bảng số liệu hoặc biểu đồ kết quả thực nghiệm định lượng về hiệu suất lập vết (ví dụ: MAP, Recall, Precision, hoặc Hallucination Rate) trong bài báo gốc. |

---

## Exclusion Criteria (EC) — Loại bỏ bài báo nếu vướng phải BẤT KỲ điều kiện nào dưới đây:

| Mã | Tiêu chí | Chi tiết |
| :--- | :--- | :--- |
| **EC-D** | Trùng lặp | Bài báo bị trùng lặp nội dung với nghiên cứu khác đã có trong danh sách lựa chọn (Deduplication). |
| **EC-A** | Không thể truy cập | Không thể tiếp cận bản full-text (bị dính Paywall hoặc không tìm thấy bất kỳ nguồn lưu trữ PDF/Text hợp pháp nào công khai). |
| **EC-S** | Dung lượng ngắn | Bài báo có độ dài dưới 4 trang (thuộc dạng extended abstract, poster, sơ lược workshop, hoặc ghi chú tóm tắt). |
| **EC-N** | Thiếu thực nghiệm | Không có dữ liệu đánh giá thực nghiệm định lượng (các bài báo dạng định hướng phát triển - vision paper, khảo sát thuần lý thuyết - position paper, bài hướng dẫn - tutorial, hoặc bài nêu quan điểm cá nhân). |
| **EC-O** | Sai mục tiêu kỹ thuật | Bài báo không tập trung vào Traceability: Chỉ tập trung thuần túy vào sinh mã nguồn tự động (Code Generation), sửa lỗi tự động (Bug Fixing), hoặc sinh ca kiểm thử (Test Case Generation) mà không đánh giá hay liên kết ngược lại tài liệu yêu cầu. |
| **EC-Dom**| Sai lĩnh vực (Domain) | Nghiên cứu áp dụng kỹ thuật lập vết trong các lĩnh vực ngoài công nghệ phần mềm như: chuỗi cung ứng vật lý (supply chain traceability), theo dõi sản xuất phần cứng (hardware design), hoặc y tế. |