# SDK Taxi: painpoint và voucher (tóm tắt)

Tổng hợp ngày 17/11/2026 từ KG `lengoc247/HST-KG`:
- `knowledge/taxi-painpoints.md` (UX, `draft`, kiểm tra 16/11/2026)
- `artifacts/taxi-painpoints.html` (báo cáo cho designer / PO)
- `knowledge/sdk-voucher-research.md` + trang "Voucher xuất hiện ở đâu, lúc nào" (SDK Xe Liên Tỉnh, 16/11/2026)

> **Quyết định 17/11/2026 (chủ dự án):** 6 quy tắc voucher đã duyệt cho SDK Xe Liên Tỉnh **áp dụng cho cả SDK Taxi**. Chưa cập nhật trạng thái này vào KG.

---

## 1. Nguồn số liệu Taxi

- Báo cáo DA "Hành vi người dùng – 12.11.2026": 29.149 phiên SDK Taxi trên VNPAY App, 01–21/10/2026 (bỏ 06/10).
- Màn hình bản cũ: Figma VnTaxi 7.2, Main Flow (có thể lệch app đang chạy).
- Số liệu chỉ tới lúc bấm Đặt xe. Số là tương quan, không phải nhân quả.

## 2. Phễu

| Màn | Phiên | Dừng tại màn | % bấm Đặt xe |
|---|---|---|---|
| Home | 27.512 (94%) | 3.392 (12%) | 52% |
| Tìm điểm | 21.071 (72%) | 1.155 (5%) | 58–59% |
| Xác nhận điểm đón | 21.361 (73%) | 1.287 (6%) | 62% |
| **Báo giá** | 21.674 (74%) | **7.269 (34%)** | 66% |
| Bấm Đặt xe | 15.299 (52%) | — | — |

Sau Đặt xe: 93% có cuốc, 81% ra cuốc thành công (≈ 42% tổng phiên).

## 3. Painpoint

| # | Vấn đề | Số liệu chính | Hướng làm mới | Ưu tiên |
|---|---|---|---|---|
| P1/P3 | Báo giá: phải bấm từng logo hãng để so giá | 7.269 phiên rời (34%); 40% đổi hãng ≥ 3 lần; chọn trong danh sách hãng đặt 74% vs bấm logo 63% | Bỏ thanh logo; một danh sách (hãng + loại xe, giá cuối sau ưu đãi, thời gian đón); chọn sẵn dòng tốt nhất; lọc Rẻ nhất / Nhanh nhất / loại xe | Lên kế hoạch |
| **P2** | **Ưu đãi hứa giảm nhưng không áp được** | 72% phiên mở ưu đãi. Áp được mã → 90% đặt · mở không áp → 38% · không mở → 62%. 56% phiên không đặt ở Báo giá là nhóm mở mà không áp. 33% phiên áp được mã | Tự áp mã tốt nhất, giá sau giảm + gạch ngang, chỉ hiện badge khi chuyến có mã dùng được, chia Dùng được / Chưa đủ điều kiện | **Làm trước** |
| P5 | Hết tài xế: bấm lại đến khi bỏ | 44% phiên bấm Đặt xe ≥ 2 lần; ~390 phiên "không có tài xế gần", ~4 lần/phiên, gần như không ra cuốc | Khoá nút + trạng thái đang tìm; mời hãng / loại xe khác có xe; cho chọn nhiều hãng từ đầu | Làm trước |
| P7/P8 | Lối tắt chuyển đổi cao nhưng khó thấy; Home rơi nhanh | Đặt lại 90% (1,5% phiên), Đặt hộ 83%, Hành trình gợi ý 81%, Nhà/Công ty 73%. 12% rời ở Home, 34% trong 5 giây | Ô "Bạn muốn đến đâu?" lên đầu Home; 3 chuyến gần nhất + Đặt lại; Nhà/Công ty hiện địa chỉ; Đặt hộ, hoá đơn hiện thẳng ở Báo giá | Làm trước |
| P4 | Ghim điểm đón sai chỗ | 26% đổi điểm đón; 45% kéo ghim ≥ 3 lần; ra cuốc: giữ nguyên 52%, kéo ghim 39%, kéo + chọn cổng 32% | Ghim mặc định ở cổng gần GPS; bản đồ lớn, cổng là điểm chạm có nhãn gợi ý; ghim hút về cổng | Lên kế hoạch |
| P9 | Tìm điểm phải làm lại | 38% quay lại màn; 17% gõ ≥ 3 lần | Hiện Gần đây + Đã lưu trước khi gõ | Nhỏ |
| P6 | Liên kết thẻ giữa luồng | 385 phiên → 9% ra cuốc | Liên kết xong quay về đúng Báo giá, giữ lựa chọn | Nhỏ |
| P10 | Tuỳ chọn, hoá đơn ít dùng | Tuỳ chọn 686 phiên; hoá đơn 42 phiên | Đưa ra khỏi menu ⋮ | Nhỏ |

Đối thủ tham khảo: Grab, Gojek, Bolt, Uber, Lyft (Mobbin). Gojek tự áp mã phù hợp nhất và ẩn mã không dùng được; Bolt hiện "10% promo applied", mọi giá đã trừ sẵn. Grab Philippines: đặt nhiều loại xe cùng lúc giảm thời gian tìm xe 20–30%.

## 4. Quy tắc voucher (áp dụng cho Xe Liên Tỉnh và Taxi)

| Quy tắc | Nội dung | Áp vào Taxi |
|---|---|---|
| `voucher-auto-apply-best` | Tự áp voucher giảm nhiều nhất; dòng Ưu đãi thấy ngay; giá gạch ngang + "Tiết kiệm X"; tôn trọng "Không dùng ưu đãi"; bằng nhau ưu tiên hết hạn sớm | Báo giá tự áp mã cho dòng đang chọn, tính lại khi đổi hãng / loại xe |
| `voucher-eligible-split-reason` | Ô nhập mã ở đầu; nhóm Dùng được (sắp theo tiền tiết kiệm) / Chưa đủ điều kiện (lý do, số tiền thiếu) | Lý do: hãng / loại xe không áp dụng, chưa đủ đơn tối thiểu, sai nguồn tiền |
| `voucher-ticket-card` | Card dạng vé, giá trị giảm lớn nhất, điều kiện 1 dòng, badge Tốt nhất / Sắp hết hạn | Giữ nguyên |
| `voucher-post-purchase` | Màn thành công "Bạn đã tiết kiệm X" + voucher lần sau | Kết thúc chuyến: "Đã tiết kiệm X" + đặt lại / chiều ngược |
| `voucher-price-in-results` | Giá sau voucher tốt nhất trên từng lựa chọn, giá gốc gạch ngang, lọc "Có ưu đãi" | Mỗi dòng hãng / loại xe ở Báo giá là giá đã trừ ưu đãi |
| `voucher-display-frequency` | Hiện theo sự kiện; tối đa 1 lớp nổi khuyến mại / phiên; không chồng popup host; không gamification | Chỉ hiện badge khi chuyến có mã dùng được (bỏ kiểu "Ưu đãi −50%" chung chung) |

### Khi nào hiện / im

- **Hiện:** có voucher mới (1 lần); voucher áp được cho chuyến đang xem; thiếu ít để đủ điều kiện; sắp hết hạn (≤ 2 ngày); vừa hoàn tất đơn.
- **Im:** host vừa hiện popup; user đã chọn "Không dùng ưu đãi" (chỉ nhắc nhỏ "đang bỏ lỡ X"); voucher không áp được cho chuyến đang xem.

### 8 chặng voucher (nghiên cứu Xe Liên Tỉnh) và tương ứng ở Taxi

| Chặng | Xe Liên Tỉnh | Taxi |
|---|---|---|
| 1. Vào SDK | Bottom sheet "Bạn có N ưu đãi" 1 lần | Như vậy, phối hợp với popup host |
| 2. Màn tìm chuyến | Dải mini-ticket ưu đãi | Home: ưu đãi gắn với chuyến đặt lại |
| 3. Kết quả tìm kiếm | Giá sau voucher từng chuyến | Gộp vào Báo giá |
| 4. Chọn ghế | Gợi ý khứ hồi / thêm ghế | Gần như không áp dụng |
| 5. Xác nhận thanh toán | Tự áp tốt nhất | Gộp vào Báo giá |
| 6. Phương thức TT (host) | Ưu đãi theo nguồn tiền, "Trả bằng thẻ X để giảm thêm" | Giữ nguyên, cần host |
| 7. Sau thanh toán | "Đã tiết kiệm X" + voucher chiều về | Sau chuyến: đã tiết kiệm + đặt lại |
| 8. Quay lại | Badge số ưu đãi, nhắc hết hạn, đặt lại | Giữ nguyên; push qua host |

Lộ trình gốc: giai đoạn 1 SDK tự làm (chặng 5, 7, 8 ví) → giai đoạn 2 cần backend (3, 2, 4) → giai đoạn 3 cần host (6, 1, push).

### Câu hỏi mở về voucher

- Q1: Backend có tính được voucher tốt nhất theo từng đơn / từng lựa chọn không?
- Q2: Host cho SDK tự áp không cần xác nhận, hiện bottom sheet, push nhắc hạn, đọc ưu đãi theo nguồn tiền?
- Q4: Voucher thuộc host, hãng xe hay cả hai?
- Ngân sách: tự áp làm tăng chi phí khuyến mãi / cuốc.

## 5. Đối thủ và flow đề xuất (17/11/2026)

Canvas: https://claude.ai/artifact/U8PAGcW5pqj1tAVqX56ui8 (trang v1: 8 màn bản đầu + bảng đối thủ).

**Thị trường:** Green SM (tên cũ Xanh SM, đổi tên 13/04/2026) 54,51% thị phần taxi công nghệ quý I/2026 (Mordor); Grab vẫn được 68% người khảo sát chọn là app số 1 (5/2026); Be 5,86% quý IV/2025. Gojek rời VN 10/2024. Số thị phần bị các hãng phản bác lẫn nhau.

**Đối thủ cùng mô hình cần theo dõi:** MoMo × Green SM ký hợp tác, dự kiến đưa đặt xe Green SM vào app MoMo từ 2026. Hiện MoMo chỉ là nguồn tiền (tạm giữ khi đặt, trừ khi xong chuyến, huỷ thì hoàn).

**Lợi thế riêng VNPAY Taxi:** so giá nhiều hãng trong một danh sách (gần 200 hãng, 2024) + ưu đãi theo nguồn tiền ngân hàng.

**Giả định cần xác nhận:** SDK được tạm giữ tiền khi đặt (thay vì trả sau chuyến); backend gọi song song nhiều hãng và tự huỷ yêu cầu thừa; host trả về ưu đãi theo nguồn tiền (Q2).

## 6. Thiết kế lại v2 – hệ UI mới (17/11/2026)

Canvas trang **v2 · Thiết kế lại** (mặc định mở) + trang demo HTML bấm được: https://claude.ai/artifact/5GsxX2f717Ev24w9ZiwvWP

**Quan sát màn iOS thật trên Mobbin (17/11/2026):**
- Uber: Plan your ride có chip "Pickup now ▾" / "For me ▾"; Choose a ride: thẻ lớn viền đen cho lựa chọn đang chọn, badge "Faster"; thanh dưới 2 tầng (dòng nguồn tiền + nút "Choose UberX" cạnh ô hẹn giờ).
- Grab: tab Recent / Suggested / Saved; nhãn "Preferred pickup (56% of users)"; mọi dòng xe có giá gạch ngang; thanh dưới "Cash | ✓ 1 applied | •••" + "Book with cash"; lúc tìm xe hỏi "Add more ride types? You'll get the first available driver".
- Lyft: dải "You're saving 50%… + 1 more" đầu sheet; sheet thu gọn chỉ 1 lựa chọn; "Lyft Cash + Promo | Schedule" + "Select Standard"; "Add note for driver" + "Change rider" ở màn xác nhận điểm đón.
- Green SM: không có trên Mobbin; báo chí: tối giản, màu dịu, gợi ý chuyến theo thói quen. Nên chụp màn thật.

**7 nguyên tắc:** (1) bản đồ + một bottom sheet; (2) nền đơn sắc, xanh VNPAY chỉ cho nút chính, xanh lá chỉ cho tiền tiết kiệm; (3) ưu đãi nói một lần ở đầu sheet, giá trừ sẵn trên từng dòng; (4) thanh dưới đúng 2 tầng: nguồn tiền | ưu đãi | ••• + nút "Chọn …"; (5) việc nào ở đúng bước: Đặt hộ ở bước chọn điểm, ghi chú ở bước điểm đón, gọi thêm hãng ở bước tìm xe, hoá đơn trong •••; (6) gợi ý trước khi gõ + nhãn điểm đón nhiều người chọn; (7) đọc được khi chữ to (chạm ≥ 44, tương phản 4.5:1).

**Token:** Be Vietnam Pro; Ink #0F1A2A, Muted #5B6675, Soft #F2F4F7, Line #E3E7EC, Accent #0B5CD5, Save #0A7A3E, Warn #B45309, Danger #B42318; chữ 28/20/16/14/12; lưới 4px; nút 52; bo dòng 14, sheet 20.

**9 màn v2:** Home → Tìm điểm → Điểm đón → Báo giá thu gọn → Báo giá mở rộng → Ưu đãi → Xác nhận (sheet) → Đang tìm xe (thêm hãng) → Hoàn tất. Màn Báo giá: thanh dưới từ 5 tầng xuống 2.

## 7. Concept v7 – Grab / DiDi (17/11/2026)

Demo bấm được: https://claude.ai/artifact/To5batU5xPWgab1yXwDecG (artifact "VNPAY Taxi concept", bản v7).

- Home: hero thành phố + lời chào; ô "Bạn muốn đến đâu?" nổi lên trên hero kèm chip Nhà / Công ty / Sân bay (kiểu DiDi); lưới 8 dịch vụ icon 3D; thẻ "Cần xe gấp?" (gọi nhiều hãng); thẻ đặt lại kéo ngang có giá đã trừ mã; banner ưu đãi bằng ảnh (kiểu Grab).
- Báo giá: khung tải giá (skeleton) ~0,7 giây trong lúc so 5 hãng; dòng chọn viền xanh 2px.
- Tìm xe và Hoàn tất có minh hoạ 3D (ghim radar, heo tiết kiệm).
- Asset: 18 ảnh tạo bằng Figma AI (8 xe 3D, 4 icon dịch vụ, hero, 3 banner, 2 minh hoạ) ở file Figma `[SDK] Vector Graphics`, Page 3, frame "VNPAY Taxi · Asset v7": https://www.figma.com/design/drYqcpUjIPAWKYZVcZns8k/-SDK--Vector-Graphics?node-id=2003-288
- Xe là màu chung (xanh ngọc, vàng, trắng sọc xanh…), không có logo hãng.

## 8. Tài liệu liên quan

- KG: https://kg.prisma-ui.com (repo `lengoc247/HST-KG`)
- Báo cáo Taxi: `artifacts/taxi-painpoints.html`
- Trang 8 chặng voucher: `artifacts/sdk-voucher-touchpoints.html` · https://claude.ai/artifact/FNAgjkaxA9VMDWFQQhkg55
- Prototype thanh toán: https://claude.ai/artifact/RFELWfXPXnkyyWL51jyjck
- Doc đề xuất voucher: https://claude.ai/artifact/J4kyaavGY8Rm29eQwh9teQ
- Canvas flow SDK Taxi (v2 + v1): https://claude.ai/artifact/U8PAGcW5pqj1tAVqX56ui8
- Demo HTML hệ UI v2: https://claude.ai/artifact/5GsxX2f717Ev24w9ZiwvWP
- Concept v7 Grab/DiDi: https://claude.ai/artifact/To5batU5xPWgab1yXwDecG
