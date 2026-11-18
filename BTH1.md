# Hệ thống Prompt CREATE & Kế hoạch Tài chính Cá nhân

Tài liệu này tổng hợp toàn bộ cấu trúc Prompt chuẩn hóa theo mô hình **CREATE** (tích hợp tư duy chuỗi **Chain-of-Thought** và các ràng buộc kiểm soát logic chặt chẽ) dành cho việc quản lý dòng tiền biến động, trả nợ và tiết kiệm.

## I. Khung Prompt Mẫu (CREATE Framework)

Bạn có thể sao chép toàn bộ nội dung dưới đây và điền số liệu thực tế của mình vào phần **Dữ liệu đầu vào** để yêu cầu AI lập kế hoạch hàng tháng:

```
### C - Context (Bối cảnh)
Tôi là một cá nhân có thu nhập biến động mỗi tháng và đang có một số khoản nợ cần thanh toán. Tôi cần một trợ lý AI thông minh lập kế hoạch tài chính chi tiết, tối ưu hóa dòng tiền và đưa ra đề xuất phân bổ ngân sách chi tiêu hợp lý.

### R - Request (Yêu cầu cốt lõi)
- **Yêu cầu cốt lõi:** Thiết kế kế hoạch tài chính hàng tháng từ dữ liệu đầu vào gồm: Thu nhập, Chi phí cố định, Các khoản nợ, Mục tiêu tiết kiệm. Đảm bảo các nguyên tắc: **tiết kiệm tối thiểu 20%, trả nợ đúng hạn, và trích lập quỹ dự phòng**.
- **Kỹ thuật xử lý:** Thực hiện suy luận từng bước (Chain-of-Thought) để tính toán ngân sách trước khi xuất kết quả cuối cùng.

### E - Explanation (Giải thích & Cấu trúc đầu ra)
Cấu trúc phản hồi bắt buộc chia làm 2 phần rõ rệt để giải thích cặn kẽ cách tính toán:
- **Phần 1: Nhật ký suy luận logic (Reasoning Steps)** chỉ ra công thức tính toán và số liệu trung gian.
- **Phần 2: Bảng phân bổ ngân sách cuối cùng** bằng Markdown Table với các cột: `Hạng mục`, `Số tiền`, `Tỷ lệ %`, `Ghi chú`.

### A - Action (Hành động từng bước)
- **Bước 1:** Tính toán tổng thu nhập khả dụng sau khi trừ thuế và chi phí cố định bắt buộc.
- **Bước 2:** Phân bổ khoản tiền trả nợ tối thiểu.
- **Bước 3:** Trích lập quỹ tiết kiệm theo tỷ lệ cam kết.
- **Bước 4:** Chia phần còn lại cho chi tiêu linh hoạt theo quy tắc 50/30/20 cải tiến.

### T - Tone (Giọng điệu)
Thực tế, logic, minh bạch, khách quan và mang tính định hướng hành động cao.

### E - Extras & Negative Prompt (Ràng buộc bổ sung & Nghiêm cấm)
- Bắt buộc hiển thị đầy đủ phép tính cộng trừ nhân chia trung gian, không nhảy cóc ra kết quả.
- Đảm bảo tổng tỷ lệ phần trăm phân bổ ngân sách phải bằng chính xác 100%.
- Không dùng Pydantic hay code Python, thực hiện hoàn toàn bằng kỹ năng Prompting logic.

---
### Dữ liệu đầu vào của tôi tháng này:
- **Thu nhập dự kiến:** [Nhập số tiền, ví dụ: 15.000.000 VNĐ]
- **Chi phí cố định bắt buộc:** [Nhập số tiền, ví dụ: 6.000.000 VNĐ]
- **Các khoản nợ cần trả tháng này:** [Nhập số tiền, ví dụ: 3.000.000 VNĐ]
- **Mục tiêu tiết kiệm & dự phòng:** Tối thiểu 20% tổng thu nhập
```

## II. Bản Kế hoạch Tài chính Mẫu (Kết quả thực thi từ Prompt)

*Giả định mức thu nhập mẫu hàng tháng là **15.000.000 VNĐ**.*

### Phần 1: Nhật ký suy luận logic (Reasoning Steps & Calculations)

1. **Bước 1: Tính toán Chi phí Cố định & Sinh hoạt**
   * **Công thức:** $\text{Số tiền} = \text{Tổng thu nhập} \times \text{Tỷ lệ \% mục tiêu}$
   * **Tính toán:** $15.000.000 \times 40\% = 15.000.000 \times 0.40 = 6.000.000 \text{ VNĐ}$
   * **Kiểm tra tỷ lệ:** $(6.000.000 / 15.000.000) \times 100 = 40\%$

2. **Bước 2: Phân bổ khoản tiền trả nợ đúng hạn**
   * **Công thức:** $\text{Số tiền} = \text{Tổng thu nhập} \times \text{Tỷ lệ \% trả nợ}$
   * **Tính toán:** $15.000.000 \times 20\% = 15.000.000 \times 0.20 = 3.000.000 \text{ VNĐ}$
   * **Kiểm tra tỷ lệ:** $(3.000.000 / 15.000.000) \times 100 = 20\%$

3. **Bước 3: Trích lập quỹ tiết kiệm theo tỷ lệ cam kết**
   * **Công thức:** $\text{Số tiền} = \text{Tổng thu nhập} \times \text{Tỷ lệ \% tiết kiệm}$
   * **Tính toán:** $15.000.000 \times 20\% = 15.000.000 \times 0.20 = 3.000.000 \text{ VNĐ}$
   * *(Chi tiết phân bổ: 10% Tiết kiệm dài hạn = $1.500.000 \text{ VNĐ}$; 10% Quỹ dự phòng khẩn cấp = $1.500.000 \text{ VNĐ}$)*
   * **Kiểm tra tỷ lệ:** $(3.000.000 / 15.000.000) \times 100 = 20\%$

4. **Bước 4: Chia phần còn lại cho chi tiêu linh hoạt (Quy tắc 50/30/20 cải tiến)**
   * **Công thức tính số dư trung gian:** $\text{Số dư} = \text{Tổng thu nhập} - (\text{Chi phí cố định} + \text{Trả nợ} + \text{Tiết kiệm})$
   * **Tính toán:** $15.000.000 - (6.000.000 + 3.000.000 + 3.000.000) = 15.000.000 - 12.000.000 = 3.000.000 \text{ VNĐ}$
   * **Kiểm tra tỷ lệ chi tiêu linh hoạt:** $(3.000.000 / 15.000.000) \times 100 = 20\%$

5. **Bước 5: Kiểm tra tổng tỷ lệ % phân bổ ngân sách**
   * $\text{Tổng tỷ lệ} = 40\% (\text{Cố định}) + 20\% (\text{Trả nợ}) + 20\% (\text{Tiết kiệm}) + 20\% (\text{Linh hoạt}) = 100\%$ *(Khớp hoàn toàn)*.

### Phần 2: Bảng phân bổ ngân sách cuối cùng

| Hạng mục | Số tiền (VNĐ) | Tỷ lệ % | Ghi chú | 
| :--- | :---: | :---: | :--- | 
| **1. Chi phí Cố định & Sinh hoạt** | 6.000.000 | 40% | Nhà ở, điện nước, ăn uống tối thiểu ($15.000.000 \times 40\%$) | 
| **2. Trả nợ Đúng hạn** | 3.000.000 | 20% | Thanh toán nợ gốc và lãi định kỳ ($15.000.000 \times 20\%$) | 
| **3. Tiết kiệm & Dự phòng** | 3.000.000 | 20% | Gồm 10% tiết kiệm và 10% quỹ dự phòng ($15.000.000 \times 20\%$) | 
| **4. Chi tiêu Linh hoạt** | 3.000.000 | 20% | Giải trí, phát sinh cá nhân ($15.000.000 - 12.000.000$) | 
| **Tổng cộng** | **15.000.000** | **100%** | **Cân đối hoàn hảo dòng tiền** | 

## III. Nguyên tắc Vận hành Dòng tiền Biến động

* **Trong tháng thu nhập cao:** Tuyệt đối không nâng mức sống ngay lập tức. Giữ nguyên chi phí cố định và chi tiêu linh hoạt ở mức sàn, dùng toàn bộ phần tiền dôi dư để **trả bớt gốc khoản nợ có lãi suất cao nhất** hoặc **bơm nhanh vào quỹ dự phòng** (mục tiêu tích lũy đủ 3–6 tháng chi phí sinh hoạt).
* **Trong tháng thu nhập thấp:** Cắt giảm triệt để mục *Chi tiêu linh hoạt*, siết chặt chi phí sinh hoạt cốt lõi để bảo vệ tuyệt đối nghĩa vụ **Trả nợ đúng hạn** và **Tiết kiệm tối thiểu 20%**.