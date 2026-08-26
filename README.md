# Track 1 - Day 24 — AI Product Financial Model & Unit Economics

## Thông tin bài làm

- **Họ và tên:** Huỳnh Thị Hải Châu
- **Mã học viên:** 2A202601912
- **Dự án nhóm Day 16–17:** P-053 — ViVi AI Agent
- **Use case:** ViVi hỗ trợ khách chọn xe và đặt lịch lái thử VinFast
- **Đơn vị khách hàng trong mô hình:** Một showroom/đại lý sử dụng ViVi
- **Mô hình doanh thu:** Hybrid B2B — phí nền tảng hằng tháng cộng phí usage

## File nộp bài

[Mở file Excel tài chính hoàn chỉnh](2A202601912_HuynhThiHaiChau_Day24.xlsx)

Workbook giữ đúng ba tab của template:

1. `1. Assumptions` — giả định Optimistic, Base và Pessimistic.
2. `2. Unit Economics` — LTV, CAC, gross margin, payback, sensitivity và model checks.
3. `3. P&L & ROI` — P&L 24 tháng, NPV, IRR, project payback và runway.

## Kết quả chính

| Chỉ số | Optimistic | Base | Pessimistic |
|---|---:|---:|---:|
| ARPU/tháng | 12,0 triệu | 10,5 triệu | 8,0 triệu |
| Gross Margin | 70,8% | 61,9% | 37,5% |
| LTV/CAC | 10,63x | **4,81x** | 0,99x |
| CAC Payback | 4,7 tháng | **6,9 tháng** | 22,5 tháng |
| Churn/tháng | 2,0% | 3,0% | **4,5%** |
| CAC | 40,0 triệu | 45,0 triệu | **67,5 triệu** |

- **Base:** NPV khoảng **+1,394 tỷ VND**, IRR **53,9%**, project payback **21 tháng**.
- **Pessimistic:** Churn và CAC đều bằng **1,5x Base**; runway còn **12 tháng**.
- **AI hidden costs Base:** 1,3 triệu/showroom/tháng, bằng **86,7% API cost**.

## Decision Note

Trong mô hình này, tôi không thu phí trực tiếp từ người đặt lịch lái thử. Khách hàng trả tiền là showroom hoặc đại lý, còn người dùng cuối vẫn sử dụng ViVi miễn phí. Tôi chọn hybrid pricing gồm 9 triệu đồng phí nền tảng mỗi tháng và phần usage trung bình 1,5 triệu đồng, nên ARPU Base là 10,5 triệu đồng/showroom/tháng. Cách thu này giúp doanh thu có phần cố định nhưng vẫn bảo vệ biên lợi nhuận khi một địa điểm có lượng hội thoại và booking tăng mạnh.

TAM 500 địa điểm là mức planning làm tròn, neo theo báo cáo VinFast có 394 showroom toàn cầu vào ngày 30/06/2025 và khả năng mở rộng mạng lưới. CAC Base 45 triệu đồng phản ánh cách bán B2B có mục tiêu qua hệ thống đại lý hiện hữu, gồm demo, tích hợp và hỗ trợ ban đầu. Với gross margin 61,9%, LTV/CAC đạt 4,81x và CAC payback là 6,9 tháng; cả hai vượt ngưỡng 3x và dưới 12 tháng mà bài lab yêu cầu. Tôi tính LTV trên gross profit, không dùng doanh thu thuần.

Pessimistic không sao chép Base: ARPU giảm còn 8 triệu, adoption giảm từ 3,0% xuống 0,8%, churn tăng đúng 1,5x và CAC cũng tăng 1,5x. Kịch bản này chỉ còn runway 12 tháng và NPV âm, nên Plan B được kích hoạt ngay: dừng rollout địa điểm mới, giới hạn usage trong gói, chuyển phần lớn request sang model rẻ hơn, chỉ giữ human QA cho trường hợp rủi ro và cắt chi phí vận hành không thiết yếu. Nếu cash position đi đúng đường Pessimistic trong ba tháng liên tiếp, nhóm phải chốt thêm ngân sách trước tháng 10 thay vì chờ tiền mặt gần cạn.

## Nguồn và benchmark

- [VinFast Q2/2025 — 394 showrooms toàn cầu tại 30/06/2025](https://vinfastauto.com/vn_en/vinfast-reports-unaudited-second-quarter-2025-financial-results)
- [Bessemer — CLTV/CAC từ 3x và CAC payback theo phân khúc](https://www.bvp.com/assets/uploads/2021/09/scaling-to-100-million-by-mary-d-onofrio.pdf)
- [a16z — AI businesses có cloud, data labeling và human-in-the-loop costs](https://a16z.com/the-new-business-of-ai-and-how-its-different-from-traditional-software/)
- [OpenAI API Pricing](https://platform.openai.com/pricing)
- `Day24-AI-Product-Handbook.pdf` trong repository.

## Tự kiểm trước khi nộp

- [x] File Excel đúng tên `2A202601912_HuynhThiHaiChau_Day24.xlsx`.
- [x] Tất cả ô màu vàng ở Tab 1 đã có dữ liệu cho ba kịch bản.
- [x] AI hidden costs lớn hơn 30% API cost.
- [x] Pessimistic Churn và CAC đều đạt shock 1,5x Base.
- [x] Base LTV/CAC > 3 và CAC Payback < 12 tháng.
- [x] Base NPV > 0, IRR > WACC và project payback < 24 tháng.
- [x] Pessimistic runway đạt 12 tháng.
- [x] Có bảng sensitivity ARPU × Churn và khối kiểm tra `MODEL STATUS: PASS`.

## AI Support Disclosure

AI được dùng để rà công thức, gợi ý cách stress-test và kiểm tra xem các gate có tính được hay không. Các giả định vẫn được ghi rõ là planning assumptions; bài không sử dụng số liệu người dùng hoặc doanh thu thật của VinFast và không trình bày các con số mô phỏng như kết quả đã xảy ra.
