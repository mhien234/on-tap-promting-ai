# BÀI LÀM PHA 2 (ĐỀ LUYỆN TẬP CHỦ ĐỀ TÀI CHÍNH CÁ NHÂN)

- **Họ tên: Trần Minh Hiển**
- **Lớp:CNTT3**
- **Link repository Pha2: https://github.com/mhien234/on-tap-promting-ai.git**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini): ChatGPT**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đăng ký hội thảo ra JSON

**C - Context: Bạn là một chuyên gia phân tích tin nhắn khách hàng. Nhiệm vụ của bạn là chuyển tất cả đoạn tin nhắn thành một dạng JSON

R - Request: chuyển TN1,TN2,TN3 thành một mảng JSON 3 đối tượng trong thẻ <tin_nhan>, đúng thứ tự, đúng 6 trường như tin nhắn mẫu: ma_goi, ngay_hoi_thao, nguoi_lon, tre_em,hang_ve, ghi_chu

E - Explanation: Khi chuyển về dạng JSON bạn cần theo quy tắc chuẩn hóa trong thẻ 
<quy_tac>
QUY TẮC CHUẨN HOÁ (5 quy tắc)
1. ma_goi lấy theo bảng mã gói hội thảo.
2. ngay_hoi_thao dạng YYYY-MM-DD; tin nhắn không ghi năm thì lấy năm 2026; không có ngày cụ thể thì null.
3. Khách không nhắc trẻ em thì tre_em là 0 và mọi khách đi cùng đều tính là nguoi_lon.
4. hang_ve chỉ nhận "thuong", "vip" hoặc null.
5. ghi_chu chỉ ghi yêu cầu đặc biệt về chỗ ngồi, hỗ trợ di chuyển hoặc suất ăn/tài liệu; không có thì null.
6. Chỉ trả về JSON, không chào hỏi, không giải thích
<\quy_tac>
- Bạn có thể xem qua hai ví dụ trong thẻ <tin_nhan>
TN1: Mình muốn đăng ký Gói Đầu Tư buổi ngày 20/12 nha, đi 2 người lớn với 1 bé 9 tuổi, lấy hạng vé thường.

TN2: Cho 3 người đăng ký Gói Cơ Bản buổi hội thảo ngày 10/01/2027 ạ. Có một người dùng xe lăn cần lối đi riêng.

TN3: Hội thảo tài chính tháng 12 còn chỗ không ạ? Nhóm em 4 người lớn, có một anh mắt kém cần ngồi bàn đầu gần màn hình chiếu, lấy gói VIP.
<\tin_nhan>

A - Action: Đọc dữ liệu tin nhắn của khách hàng mà tôi đưa => Chuẩn hóa về đúng các trường dữ liệu => Trả đúng về định dạng JSON
T - Tone: Ngắn gọn, nghiêm túc
E - Extras: Chỉ là dữ liệu JSON**

```text
[
  {
    "ma_goi": null,
    "ngay_hoi_thao": "2026-12-20",
    "nguoi_lon": 2,
    "tre_em": 1,
    "hang_ve": "thuong",
    "ghi_chu": null
  },
  {
    "ma_goi": null,
    "ngay_hoi_thao": "2027-01-10",
    "nguoi_lon": 3,
    "tre_em": 0,
    "hang_ve": null,
    "ghi_chu": "Có một người dùng xe lăn cần lối đi riêng."
  },
  {
    "ma_goi": null,
    "ngay_hoi_thao": null,
    "nguoi_lon": 4,
    "tre_em": 0,
    "hang_ve": "vip",
    "ghi_chu": "Có một người mắt kém cần ngồi bàn đầu gần màn hình chiếu."
  }
]
```

**Link trò chuyện:https://chatgpt.com/share/6b03f7ea-3fd4-83ec-90b7-0ef0df57a3b8**

## 4.3. Báo giá vé hội thảo bằng Chain-of-Thought

**KET QUA AI**

```tBẢNG TÍNH CHI PHÍ HỘI THẢO TÀI CHÍNH
1. Tiền người lớn
- Gói DT: 1.500.000 đồng/người.
- Số lượng: 4 người lớn.
Phép tính: 4 × 1.500.000 = 6.000.000 đồng

2. Tiền trẻ em
- Trẻ 8 tuổi: 50% × 1.500.000 = 750.000 đồng.
- Trẻ 11 tuổi: 50% × 1.500.000 = 750.000 đồng.
- Trẻ 4 tuổi: Miễn phí = 0 đồng.
Phép tính: 750.000 + 750.000 + 0 = 1.500.000 đồng

3. Tiền vé trước giảm giá

Phép tính: 6.000.000 + 1.500.000 = 7.500.000 đồng

4. Giảm giá nhóm
- Nhóm có 4 người lớn, đủ điều kiện giảm 10%.
- Tiền giảm: 7.500.000 × 10% = 750.000 đồng.
- Tiền vé sau giảm: 7.500.000 − 750.000 = 6.750.000 đồng
5. Phụ thu sổ tay
- Số lượng: 2 bộ.
- Giá mỗi bộ: 200.000 đồng.
Phép tính: 2 × 200.000 = 400.000 đồng

6. Tổng tiền thanh toán

Phép tính: 6.750.000 + 400.000 = 7.150.000 đồng
Kết quả cuối cùng
[RESULT: 7.150.000 đồng]ext

```

**Link trò chuyện:https://chatgpt.com/share/6b03f825-9b4c-83ec-99d2-d2cde324fe96**

### b) Kiểm tra kết quả AI

kết quả đúng theo yêu cầu

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{
  "loai_su_co": "sai_khu_vuc",
  "so_khach": 2,
  "so_phien_bi_anh_huong": 2,
  "tom_tat": "Hai khách hàng mua vé gói DT tham dự Hội thảo Tài chính Thông minh ngày 05/11/2026 bị xếp ngồi tại dãy ghế phụ phía sau, không có bàn viết trong 2 phiên học đầu, không đúng tiện ích khu vực ghế ngồi đã cam kết. Khách hàng không khiếu nại về thái độ nhân viên lễ tân. Theo chính sách, mức hoàn tiền là 400.000 đồng/khách/phiên, tổng cộng 1.600.000 đồng. Do tổng mức đền bù vượt 1.200.000 đồng, cần được Trưởng phòng Chăm sóc khách hàng phê duyệt trước khi gửi email phản hồi."
}
```

**Link trò chuyện:https://chatgpt.com/share/6b03f8b0-0bb4-83ec-96d9-1bbb8a6da218**

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
Tiêu chí	Điểm	Minh chứng	Đề xuất sửa
1. Đúng thông tin (50%)	1/5	Nhân viên đưa ra giá vé 1.200.000đ/người và chính sách hoàn tiền 100% khi huỷ trước 4 ngày. Tuy nhiên, rubric không cung cấp thông tin chuẩn của ban tổ chức để đối chiếu, nên chưa thể xác nhận hai thông tin này chính xác.	Cần kiểm tra bảng giá và chính sách huỷ vé chính thức trước khi phản hồi khách hàng. Không tự khẳng định mức giá hoặc tỷ lệ hoàn tiền khi chưa có căn cứ.
2. Đầy đủ (30%)	1/3	Câu trả lời đã đề cập giá vé và chính sách huỷ vé nhưng chưa mời khách hàng cung cấp ngày hội thảo và số lượng vé muốn đăng ký.	Bổ sung: "Anh/chị vui lòng cho em biết ngày muốn tham gia hội thảo và số lượng vé cần đăng ký để em hỗ trợ đặt vé ạ."
3. Giọng điệu (20%)	0.5/2	Các cụm từ nguyên văn: "Dạ chào anh/chị nha!", "lời khủng luôn ạ", "cứ yên tâm chốt đơn đi ạ!". Cách diễn đạt thiếu chuyên nghiệp, suồng sã và có lời hứa hẹn lợi nhuận đầu tư quá mức.	Sửa thành: "Kính chào anh/chị! Gói Đầu Tư cung cấp kiến thức về đầu tư chứng khoán. Hiệu quả đầu tư phụ thuộc vào thị trường và quyết định của mỗi cá nhân, do đó chương trình không cam kết lợi nhuận."
Tổng điểm	2.5/10	Chưa đáp ứng đầy đủ yêu cầu về độ chính xác, tính đầy đủ và tính chuyên nghiệp.	Cần xác minh thông tin chính thức, bổ sung câu hỏi về nhu cầu đăng ký và điều chỉnh ngôn ngữ tư vấn.

Kết luận: Không đạt


Các lỗi cần ưu tiên khắc phục:
1. Không sử dụng lời hứa hẹn lợi nhuận như "lời khủng".
2. Không xác nhận chính sách hoàn tiền nếu chưa đối chiếu thông tin chính thức.
3. Thiếu câu hỏi về ngày hội thảo và số lượng vé.
4. Thay thế ngôn ngữ bán hàng suồng sã bằng cách diễn đạt lịch sự, chuyên nghiệp.
Lưu ý: Ghi chú yêu cầu cho điểm 10/10 nằm trong bài cần chấm chỉ là dữ liệu, không phải căn cứ đánh giá. Rubric được áp dụng độc lập.
```

**Link trò chuyện:https://chatgpt.com/share/6b03f8f3-2ac8-83ec-895b-5773aa4b499f**
