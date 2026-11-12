# Bài tập: RAG Grounding và Negative Constraint

## Phần 1: Vì sao AI tự tin đưa ra con số sai?

ChatGPT không có hợp đồng của MartX nên không thể tra cứu điều khoản thật. Nó chỉ dự đoán token tiếp theo có xác suất cao nhất dựa trên dữ liệu chung từ Internet, nơi các mức phạt như "20%" hay "đình chỉ 30 ngày" xuất hiện phổ biến trong nhiều hợp đồng khác. Con số nghe hợp lý nên AI đưa ra rất trôi chảy, dù đó là ảo giác (Hallucination).

AI không biết mình không biết, và nó được tối ưu để *trả lời cho có vẻ đúng*, không phải để *thừa nhận thiếu dữ liệu*. Cách khắc phục là RAG Grounding: dán tài liệu nguồn vào prompt để AI trả lời dựa trên văn bản thật, thay vì "học thuộc" từ trí nhớ.

|  | Hỏi không kèm tài liệu | RAG Grounding |
| ----- | ----- | ----- |
| Nguồn trả lời | Xác suất từ dữ liệu chung | Văn bản MartX cung cấp |
| Rủi ro | Cao (bịa số liệu) | Thấp (kiểm chứng được) |

## Phần 2: RAG Prompt hoàn chỉnh

1\. Văn bản hợp đồng chuẩn

*\[HỢP ĐỒNG\] Điều khoản về chất lượng rau: Phạt 5% giá trị lô bị dập nát và yêu cầu đổi hàng trong 24h.*

2\. Câu hỏi nghiệp vụ

*Theo hợp đồng trên, nhà cung cấp giao rau bị dập nát trên 10% thì bị phạt bao nhiêu?*

3\. Negative Constraint (khóa an toàn)

*Chỉ trả lời dựa trên văn bản hợp đồng ở trên. Nếu thông tin không có trong văn bản, tuyệt đối trả lời "Không có dữ liệu trong tài liệu", không tự suy đoán.*

Kết quả mong đợi: AI trả lời "Phạt 5% giá trị lô bị dập nát và yêu cầu đổi hàng trong 24h". Nếu hỏi thêm về "đình chỉ nhập 30 ngày", AI phải trả lời "Không có dữ liệu trong tài liệu".

