# Track 1 - Day 24 — AI Product Financial Model & Unit Economics

## Thông tin học viên

- **Họ và tên:** Huỳnh Thị Hải Châu
- **Mã học viên:** 2A202601912

## 00 — Mô hình Kinh doanh

1. **Dự án:** P-053 — ViVi AI Agent, tập trung vào use case hỗ trợ khách chọn xe và đặt lịch lái thử VinFast.
2. **Target Customer / Persona:** Showroom hoặc đại lý ô tô là bên trả tiền, bắt đầu từ mạng lưới VinFast; khách đang cân nhắc mua xe và muốn đặt lịch lái thử là người dùng trực tiếp.
3. **Revenue Model:** Hybrid B2B — phí nền tảng hằng tháng cộng phí theo usage. Ở kịch bản Base, mô hình dùng mức phí nền tảng 9 triệu đồng/showroom/tháng và usage trung bình 1,5 triệu đồng, tương đương ARPU 10,5 triệu đồng/tháng.
4. **TAM:** 10.000 điểm bán ô tô tại Đông Nam Á. Đây là planning assumption ở cận dưới của dải TAM trong brief Day 24, không phải số liệu đã kiểm toán. Mốc 394 showroom VinFast trên toàn cầu tại ngày 30/06/2025 trong [báo cáo kết quả kinh doanh quý II/2025 của VinFast](https://vinfastauto.com/vn_en/vinfast-reports-unaudited-second-quarter-2025-financial-results) được dùng làm beachhead ban đầu, không đại diện cho toàn bộ TAM.

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
| Adoption/tháng | 0,5% | 0,3% | 0,1% |
| TAM | 10.000 | 10.000 | 10.000 |
| Gross Margin | 70,8% | 61,9% | 37,5% |
| LTV/CAC | 10,63x | **4,81x** | 0,99x |
| CAC Payback | 4,7 tháng | **6,9 tháng** | 22,5 tháng |
| Churn/tháng | 2,0% | 3,0% | **4,5%** |
| CAC | 40,0 triệu | 45,0 triệu | **67,5 triệu** |

- **Base:** NPV khoảng **+6,382 tỷ VND**, IRR **115,2%**, project payback **18 tháng**.
- **Pessimistic:** Churn và CAC đều bằng **1,5x Base**; runway còn **14 tháng**.
- **AI hidden costs Base:** 1,3 triệu/showroom/tháng, bằng **86,7% API cost**.

## Kiểm chứng Unit Economics — Base

Tôi kiểm tra lại theo đúng thứ tự của Tab 2, không nhìn mỗi ô `HEALTHY`:

- Gross profit mỗi showroom mỗi tháng: `10,5 - 4,0 = 6,5 triệu đồng`.
- Gross margin: `6,5 / 10,5 = 61,9%`, cao hơn ngưỡng an toàn 50%–60%.
- Thời gian ở lại trung bình: `1 / 3% = 33,3 tháng`.
- LTV: `6,5 × 33,3 = 216,67 triệu đồng`. Phép tính dùng gross profit sau COGS, không dùng revenue thô.
- LTV/CAC: `216,67 / 45 = 4,81x`, lớn hơn 3,0x.
- CAC payback: `45 / 6,5 = 6,92 tháng`, thấp hơn 12 tháng.

Vì cả hai điều kiện vàng đều đạt, cột Base trả về **`HEALTHY`**. Tôi giữ nguyên giả định thay vì tiếp tục tăng ARPU hoặc giảm CAC chỉ để chỉ số đẹp hơn.

## Kiểm chứng ROI và Stress-test — Tab 3

Tôi chạy Tab 3 theo hai bước, không dùng chung một kết quả cho cả hai kịch bản:

- **Base:** NPV đạt **+6,382 tỷ đồng**, IRR năm **115,2%** và project payback ở **tháng 18**. Cả ba điều kiện NPV dương, IRR trên 20% và hoàn vốn trước tháng 24 đều đạt; kết luận của mô hình là `GO`.
- **Pessimistic:** tiền mặt cuối tháng 12 còn khoảng **1,414 tỷ đồng**, cuối tháng 14 còn khoảng **401 triệu đồng** và bắt đầu âm ở tháng 15. Vì doanh nghiệp sống hết 14 tháng trước khi tiền mặt xuống dưới 0, runway của kịch bản này là **14 tháng**, cao hơn ngưỡng 12 tháng.

Kịch bản Pessimistic có NPV âm và kết luận `NO-GO`; đây là tín hiệu stress-test cần giữ nguyên, không phải lỗi công thức. Gate 3 chỉ yêu cầu Base đáng đầu tư và Pessimistic đủ tiền để xử lý biến cố ít nhất 12 tháng. File được lưu với ô chọn scenario ở `Pessimistic`, đúng trạng thái cuối sau khi thực hiện hai bước kiểm tra.

## Decision Note

ViVi dùng hybrid B2B: 9 triệu đồng phí nền tảng/showroom/tháng cộng 1,5 triệu đồng usage, nên ARPU Base là 10,5 triệu đồng. Cách thu này bám logic [Intercom](https://www.intercom.com/ai-chatbot): gói nền tảng từ 29 USD/seat/tháng và Fin AI Agent thêm 0,99 USD cho mỗi outcome. Với ViVi, phí nền tảng chi trả cho tích hợp dữ liệu xe, lịch lái thử và dashboard; phần usage hấp thụ biến động hội thoại. CAC Base 45 triệu đồng được ước tính bottom-up từ demo, tích hợp, onboarding và hỗ trợ bán hàng B2B. Kết quả payback 6,9 tháng, thấp hơn mốc 12 tháng dành cho SMB theo Bessemer.

Ngoài API 1,5 triệu và hạ tầng 1,2 triệu đồng/showroom/tháng, tôi dành 1,3 triệu đồng cho AI hidden costs, bằng 86,7% API cost. Mỗi tuần nhóm lấy mẫu lỗi và gắn nhãn lại intent; mỗi tháng cập nhật knowledge base; mỗi quý chạy regression test rồi chỉnh prompt hoặc retrain. PM giữ rubric, kỹ sư vận hành pipeline, còn sales ops kiểm tra thủ công các ca có giá, khuyến mại hoặc booking bất thường. Khoản này gắn với công việc cụ thể, không phải buffer chung.

Ở Base, gross margin là 61,9%, LTV/CAC đạt 4,81x, CAC payback là 6,9 tháng, NPV dương và dự án hoàn vốn ở tháng 18. Pessimistic hạ ARPU còn 8 triệu đồng, adoption còn 0,1%, churn lên 4,5% và CAC lên 67,5 triệu đồng; NPV khi đó âm. Với 10 tỷ đồng tiền mặt, runway vẫn đạt 14 tháng. Nếu kết quả thực tế bám kịch bản này ba tháng liên tiếp, nhóm sẽ dừng rollout mới, đặt trần usage, dùng model rẻ hơn cho tác vụ ít rủi ro, giữ human QA cho ca quan trọng và chốt vốn trước khi runway xuống dưới 12 tháng.

## Nguồn và benchmark

- [Intercom — gói từ 29 USD/seat/tháng và Fin AI Agent 0,99 USD/outcome](https://www.intercom.com/ai-chatbot)
- [VinFast Q2/2025 — 394 showrooms toàn cầu tại 30/06/2025](https://vinfastauto.com/vn_en/vinfast-reports-unaudited-second-quarter-2025-financial-results)
- [Bessemer — CLTV/CAC từ 3x và CAC payback theo phân khúc](https://www.bvp.com/assets/uploads/2021/09/scaling-to-100-million-by-mary-d-onofrio.pdf)
- [a16z — AI businesses có cloud, data labeling và human-in-the-loop costs](https://a16z.com/the-new-business-of-ai-and-how-its-different-from-traditional-software/)
- [OpenAI API Pricing](https://platform.openai.com/pricing)
- `Day24-AI-Product-Handbook.pdf` trong repository.

## Tự kiểm trước khi nộp

- [x] File Excel đúng tên `2A202601912_HuynhThiHaiChau_Day24.xlsx`.
- [x] Tất cả ô màu vàng ở Tab 1 đã có dữ liệu cho ba kịch bản.
- [x] Adoption của ba kịch bản nằm trong dải 0,1%–0,5%/tháng; TAM là 10.000 khách hàng.
- [x] AI hidden costs lớn hơn 30% API cost.
- [x] Pessimistic Churn và CAC đều đạt shock 1,5x Base.
- [x] Base LTV/CAC > 3 và CAC Payback < 12 tháng.
- [x] Base NPV > 0, IRR > WACC và project payback < 24 tháng.
- [x] Pessimistic runway đạt 14 tháng, cao hơn ngưỡng 12 tháng.
- [x] Có bảng sensitivity ARPU × Churn và khối kiểm tra `MODEL STATUS: PASS`.

## AI Support Disclosure

AI được dùng để rà công thức, gợi ý cách stress-test và kiểm tra xem các gate có tính được hay không. Các giả định vẫn được ghi rõ là planning assumptions; bài không sử dụng số liệu người dùng hoặc doanh thu thật của VinFast và không trình bày các con số mô phỏng như kết quả đã xảy ra.
