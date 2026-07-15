### GAP Analysis – **Thiếu sự đa dạng trong tập dữ liệu kiểm chứng và tính tổng quát hóa của các mô hình phục hồi truy vết**

**Thành viên:** Nguyễn Cao Phương Bình
**GAP type:** GAP-M
**Ngày:** 15/07/2026
**Evidence table nguồn:** evidence-table-merged.md (N = 34 papers)

#### 1. Mô tả GAP
Phần lớn các nghiên cứu hiện nay về phục hồi liên kết truy vết (TLR) đều tập trung vào các kho lưu trữ mã nguồn mở (OSS) phổ biến trên GitHub hoặc Jira. Sự tập trung quá mức này dẫn đến việc thiếu đa dạng về loại hình dự án (ví dụ: dự án thương mại, hệ thống nhúng, hệ thống an toàn cao) và các tham số đặc thù của Kỹ thuật yêu cầu (RE). Các mô hình có thể đạt hiệu suất cao trên các tập dữ liệu OSS chuẩn nhưng thường gặp khó khăn khi áp dụng vào các môi trường công nghiệp thực tế nơi dữ liệu nhiễu hơn, quy trình gán nhãn không nhất quán và cấu trúc tài liệu khác biệt.

**Bằng chứng từ các nguồn tài liệu:**
*   **Hạn chế về tính tổng quát hóa:** Nghiên cứu của Dharmaraj (2026) thừa nhận rằng các kết quả thực nghiệm không nên được tổng quát hóa cho tất cả các kho lưu trữ vì tập dữ liệu chỉ bao gồm một số dự án Python cụ thể.
*   **Phụ thuộc vào mã nguồn mở:** Morgan và cộng sự (2026) lưu trữ dữ liệu từ các dự án Apache lớn (Spark, Hive, Kafka, v.v.) và thừa nhận "tính hợp lệ bên ngoài" là một mối đe dọa vì nghiên cứu chỉ tập trung vào mã nguồn mở.
*   **Khoảng cách ngữ nghĩa giữa các loại Artifact:** Zou và cộng sự (2025) chỉ ra rằng hiệu suất mô hình thay đổi đáng kể giữa các cặp artifact khác nhau (ví dụ: Test-Code đạt F1 cao hơn nhiều so với Requirements-Code), cho thấy kết quả từ một loại dự án không thể phản ánh khả năng của mô hình trên toàn bộ miền ST.
*   **Sự đơn nhất về ngôn ngữ:** Nghiên cứu của Lin và cộng sự (2021) chỉ giới hạn ở các dự án Python, điều này làm hạn chế khả năng áp dụng cho các ngôn ngữ lập trình khác hoặc các dự án đa ngôn ngữ.

#### 2. Kiểm tra phản chứng
| Paper | Đã làm GAP này không? | Chi tiết |
| ------ | ------ | ------ |
| Morgan et al. (2026) | Không | Mặc dù sử dụng tập dữ liệu lớn (130k issues) nhưng vẫn chỉ giới hạn trong hệ sinh thái mã nguồn mở Apache và Jira. |
| Zou et al. (2025) | Có (một phần) | Đã cố gắng đa dạng hóa với 12 dự án Java khác nhau, nhưng vẫn thừa nhận chưa đại diện được toàn bộ sự đa dạng của các dự án kỹ thuật phần mềm. |
| Dharmaraj (2026) | Không | Chỉ thử nghiệm trên 3 dự án Python OSS và liệt kê sự thiếu đa dạng của tập dữ liệu là một hạn chế chính. |
| Lin et al. (2021) | Không | Tập trung vào việc chứng minh hiệu quả của T-BERT trên 3 dự án OSS cụ thể, không giải quyết vấn đề tổng quát hóa đa miền. |

**Kết luận:** GAP xác nhận ✅ (Dữ liệu kiểm chứng hiện tại đang bị "bão hòa" bởi các dự án OSS lớn, thiếu sự hiện diện của các dự án đặc thù và hệ thống thương mại).

#### 3. Feasibility Check (Đánh giá khả năng thực hiện)
| Tiêu chí | Mức | Ghi chú |
| ------ | ------ | ------ |
| **Dataset** | ⚠️ | Cần thu thập thêm các bộ dữ liệu từ CoEST (iTrust, eTour) để bổ sung cho các dự án GitHub nhằm tăng tính đa dạng. |
| **API/Tool** | ✅ | Có thể sử dụng Gemini 2.5 Pro hoặc Code Llama 7B đã được chứng minh là có khả năng zero-shot tốt trên nhiều loại dữ liệu. |
| **Tính toán** | ✅ | Sử dụng GPU Google Colab T4 hoặc Kaggle là đủ để chạy suy luận (inference) cho các mô hình SLM. |
| **Ground truth** | ⚠️ | Việc xác minh thủ công cho các dự án mới cần khoảng 5-10 giờ làm việc nhóm để đảm bảo độ tin cậy (Cohen’s $\kappa$). |
| **Code base** | ✅ | Có sẵn các framework như T-BERT hoặc RAG pipeline từ các nghiên cứu trước để adapt. |
| **Kỹ năng** | ✅ | Nhóm có khả năng thực hiện các pipeline IR và Prompt Engineering cơ bản. |

**Kết quả:** 4/6 ✅, 2/6 ⚠️ → **An toàn để thực hiện nếu có kế hoạch thu thập dữ liệu kỹ lưỡng.**

#### 4. Phát biểu GAP chính thức
**"Hiện nay đang thiếu các nghiên cứu TLR có tính tổng quát hóa cao, do các tập dữ liệu kiểm chứng chủ yếu tập trung vào các dự án mã nguồn mở Python/Java phổ biến, dẫn đến sự thiếu hụt bằng chứng về hiệu quả của các mô hình LLM trên các hệ thống có cấu trúc yêu cầu phức tạp, dự án thương mại hoặc các miền kỹ thuật chuyên biệt."**

#### 5. Đề xuất sơ bộ cho nhóm
*   **Dataset khả thi:** Kết hợp các dự án OSS hiện đại từ **Apache Dataset** (Morgan et al.) với các bộ dữ liệu RE kinh điển từ **CoEST** như **iTrust** (hệ thống y tế) và **Dronology** (hệ thống UAV) để kiểm chứng tính đa miền.
*   **Metric đề xuất:** Sử dụng **Difference Ratio** để đánh giá độ khó của tập dữ liệu trước khi chạy mô hình và các metric xếp hạng như **MAP@3**, **MRR** để so sánh hiệu quả.
*   **LLM/Tool đề xuất:** **Gemini 2.5 Pro** kết hợp với chiến lược **Multi-strategy integration** (tích hợp phụ thuộc mã nguồn và phản hồi người dùng) vì nó cho thấy khả năng thích nghi tốt nhất với dữ liệu đa dạng.
*   **Baseline đề xuất:** So sánh trực tiếp giữa **T-BERT** (đại diện encoder-only) và **RAG-based SLM** (đại diện generative) trên ít nhất 3 miền dự án khác nhau.
*   **Hướng giải pháp:** Xây dựng một **Cross-project evaluation framework** (khung đánh giá xuyên dự án) để đo lường mức độ sụt giảm hiệu suất khi mô hình được huấn luyện trên miền này nhưng kiểm chứng trên miền khác.