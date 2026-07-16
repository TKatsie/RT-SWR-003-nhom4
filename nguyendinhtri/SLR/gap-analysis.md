# GAP Analysis – **Intermediate Trace Chain Recovery and Semantic Explanation Depth in Documentation-to-Code Traceability**

**Thành viên:** Nguyễn Đình Trí  
**GAP type:** GAP-T  
**Ngày:** 15/07/2026  
**Evidence table nguồn:** merged-evidence-table.md (N \= 34 papers)

## 1\. Mô tả GAP

Hiện nay, hầu hết các nghiên cứu về truy vết (traceability) sử dụng LLM tập trung vào mối liên kết giữa **Yêu cầu (Requirements) và Mã nguồn (Code)**. Tuy nhiên, việc truy vết từ **Tài liệu kỹ thuật (Documentation)** — đặc biệt là tài liệu dạng tường thuật (narrative) như hướng dẫn sử dụng (tutorials) — sang mã nguồn vẫn còn bị bỏ ngỏ về khía cạnh **độ sâu của giải thích ngữ nghĩa** và **khả năng khôi phục chuỗi truy vết đa bước (multi-step chains)**. LLM có thể xác định các điểm đầu và điểm cuối của liên kết với độ chính xác cao, nhưng thường thất bại trong việc xác định các thành phần trung gian (như phương thức trung gian hoặc thuộc tính bổ trợ) và thiếu độ chính xác tuyệt đối (strict accuracy) khi giải thích kỹ thuật về cách mã nguồn thực thi tài liệu.  
**Bằng chứng từ evidence table:**

* **Hạn chế:** Trong số 34 bài báo, chỉ có **duy nhất 01 bài** (Alor et al., 2025/2026) thực hiện đánh giá chuyên sâu về chuỗi truy vết đa bước và chất lượng giải thích cho tài liệu.  
* **Metric:** "Strict accuracy" (độ chính xác tuyệt đối) cho việc giải thích mối quan hệ chỉ đạt từ **42.9% đến 71.1%**, thấp hơn nhiều so với độ chính xác cơ bản (\>97%).  
* **Pattern quan sát được:** Tỷ lệ khớp hoàn toàn (Complete Match) cho các chuỗi truy vết trong tài liệu dạng hướng dẫn (như bộ dữ liệu Crawl4AI) cực kỳ thấp, chỉ từ **12.8% đến 30.6%**.

## 2\. Kiểm tra phản chứng

| Paper | Đã làm GAP này không? | Chi tiết |
| :---- | :---- | :---- |
| Alor et al. (2025/2026) | Có (một phần) | "Đã xác định được vấn đề nhưng kết quả cho thấy đây vẫn là một rào cản kỹ thuật lớn chưa có lời giải tối ưu." |
| LiSSA (2025) | Không | "Có đề cập đến ""doc-to-code"" nhưng chỉ dừng lại ở phân tích định tính bằng RAG, không đi sâu vào độ chính xác của chuỗi hay giải thích ngữ nghĩa." |
| Các bài về Req-to-Code | Không | "Tập trung vào liên kết nhị phân (có liên kết hay không) giữa yêu cầu và code, không giải quyết bài toán ""chuỗi trung gian"" trong tài liệu." |

**Kết luận:** GAP xác nhận ✅ (Chỉ có một nghiên cứu nền tảng và nghiên cứu đó khẳng định đây là một lỗ hổng lớn về hiệu suất LLM hiện nay).

## 3\. Feasibility Check

| Tiêu chí | Mức | Ghi chú |
| :---- | :---- | :---- |
| Dataset | ✅ | "Có sẵn bộ dữ liệu Crawl4AI và Unity Catalog với ground truth chất lượng cao." |
| API/Tool | ✅ | "Có thể sử dụng Claude 3.5 Sonnet và đặc biệt là o3-mini với khả năng suy luận cao." |
| Tính toán | ✅ | "Chiến lược ""one-to-many"" giúp tối ưu chi phí API mà vẫn giữ được độ chính xác." |
| Ground truth | ✅ | Đã có quy trình xác minh thủ công với độ đồng thuận Cohen’s 𝜅 \= 0.94 14\. |
| Code base | ✅ | Các dự án mã nguồn mở sau tháng 04/2024 giúp tránh hiện tượng rò rỉ dữ liệu (contamination). |
| Kỹ năng | ✅ | "Cần kỹ năng Prompt Engineering nâng cao và quy trình ""LLM-as-a-judge""." |

**Kết quả:** 6/6 ✅ → **An toàn / Khả thi cao**

## 4\. Phát biểu GAP chính thức

**"Hiện đang thiếu các nghiên cứu và công cụ hỗ trợ đạt được 'độ chính xác tuyệt đối' (strict accuracy) trong việc giải thích quan hệ ngữ nghĩa và khả năng xác định tin cậy các 'thành phần trung gian' (intermediate elements) trong chuỗi truy vết từ tài liệu sang mã nguồn, đặc biệt là với các tài liệu kỹ thuật dạng tường thuật không cấu trúc."**.

## 5\. Đề xuất sơ bộ cho nhóm

* **Dataset khả thi:** Tiếp tục khai thác **Crawl4AI** (đối diện với thách thức tài liệu dạng tường thuật) hoặc các dự án OSS mới có tài liệu hướng dẫn phong phú\.  
* **Metric đề xuất:** **Strict Accuracy** (cho giải thích) và **Complete Match Rate** (cho chuỗi truy vết đa bước).  
* **LLM/Tool đề xuất:** **o3-mini (High reasoning effort)** vì mô hình này cho thấy tiềm năng cao nhất trong việc xử lý các tác vụ suy luận phức tạp để khôi phục chuỗi.  
* **Baseline đề xuất:** So sánh với kết quả của chiến lược **One-to-many** trong bài của Alor et al. (2025) và các phương pháp IR truyền thống (TF-IDF, BM25).  
* **Hướng giải pháp:** Kết hợp **Phân tích tĩnh (Static Analysis)** với LLM để cung cấp độ chính xác kỹ thuật cho các bước trung gian trong khi LLM đảm nhận việc hiểu ngữ nghĩa của tài liệu.

