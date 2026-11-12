# **Bài tập: Data Masking (che mờ PII) cho email khiếu nại**

## **Phần A: Masking Table**

| Thông tin PII thật | Nhãn che mờ | Loại dữ liệu |
| ----- | ----- | ----- |
| Phạm Minh C | \[TÊN\_KH\] | Họ tên |
| 0988.111.222 | \[SĐT\_KH\] | Số điện thoại |
| minhc@gmail.com | \[EMAIL\_KH\] | Email |
| Căn hộ 502 Chung cư Sunrise, Q7 | \[ĐỊA\_CHỈ\_KH\] | Địa chỉ cư trú |

Giữ nguyên thông tin không phải PII: ngày 20/09, 2kg thịt bò Wagyu, 4.500.000 VNĐ, MartX District 7, giao chậm 3 tiếng. Đây là ngữ cảnh để AI soạn thư đúng nội dung.

## **Phần B: Masked Input**

*Tôi là \[TÊN\_KH\] (SĐT: \[SĐT\_KH\], Email: \[EMAIL\_KH\], ở \[ĐỊA\_CHỈ\_KH\]). Ngày 20/09 tôi mua 2kg thịt bò Wagyu giá 4.500.000 VNĐ tại MartX District 7 nhưng bị giao chậm 3 tiếng làm hỏng tiệc gia đình. Tôi yêu cầu bồi thường 100%\!*

## **Phần C: Prompt gửi AI**

*Bạn là nhân viên CSKH chuyên nghiệp của siêu thị MartX. Hãy soạn email xin lỗi khách VIP dựa trên nội dung khiếu nại bên dưới. Giữ nguyên các nhãn dạng \[TÊN\_KH\], \[EMAIL\_KH\]... không tự đoán thông tin thật. Giọng điệu chân thành, lịch sự, xưng "chúng tôi" và gọi khách là "quý khách". Không hứa bồi thường 100%, chỉ nói sẽ xem xét và phản hồi sớm. Dưới 150 từ.*

*\[Dán Masked Input vào đây\]*

## **Phần D: Văn bản De-mask Kính gửi anh Phạm Minh C,**

MartX chân thành xin lỗi quý khách về việc đơn hàng 2kg thịt bò Wagyu (4.500.000 VNĐ) ngày 20/09 tại MartX District 7 bị giao chậm 3 tiếng, làm ảnh hưởng đến bữa tiệc gia đình của quý khách.

Chúng tôi đã ghi nhận phản hồi và đang xem xét phương án bồi thường phù hợp. Nhân viên CSKH sẽ liên hệ quý khách qua số 0988.111.222 trong thời gian sớm nhất.

Một lần nữa, MartX xin lỗi vì sự bất tiện này.

Trân trọng,  
Bộ phận CSKH MartX

**Luồng De-mask:** bảng ở Phần A được lưu nội bộ, không gửi ra ngoài. Sau khi AI trả thư, nhân viên thay ngược từng nhãn bằng thông tin thật rồi mới gửi cho khách.

