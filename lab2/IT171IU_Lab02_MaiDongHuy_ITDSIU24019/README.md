# IT171IU · Statistical Learning — Lab 2: Linear Regression

**Trường Đại học Quốc Tế – ĐHQG-HCM**  
**Khoa Khoa học và Kỹ thuật Máy tính (School of Computer Science and Engineering)**  

---

## 👤 Thông tin sinh viên (Student Information)

* **Họ và tên (Full Name):** Mai Dong Huy
* **Mã số sinh viên (Student ID):** ITDSIU24019
* **Lớp học phần / Nhóm (Class/Group):** IT171IU – Lab Group 01
* **Giảng viên hướng dẫn (Instructor):** ThS. Nguyễn Văn Sơn (Son Nguyen)
* **Thời gian hoàn thành:** Tháng 10/2026

---

## 📁 Cấu trúc thư mục nộp bài (Submission Structure)

Cấu trúc thư mục tuân thủ tuyệt đối quy định tại **Mục 5 (Submission Instructions)** của Lab Handout:

```text
IT171IU_Lab02_MaiDongHuy_ITDSIU24019/
├── IT171IU_Lab02_MaiDongHuy_ITDSIU24019.ipynb    # Jupyter Notebook hoàn chỉnh, đã chạy đủ kết quả và biểu đồ
├── IT171IU_Lab02_Report.pdf                     # Báo cáo học thuật định dạng PDF hoàn chỉnh
├── IT171IU_Lab02_Report.docx                    # File Word gốc phục vụ rà soát và chỉnh sửa
├── figures/                                     # Thư mục chứa 10 biểu đồ chẩn đoán độ phân giải cao (300 DPI)
│   ├── fig_ex1_fit.png
│   ├── fig_ex1_residuals.png
│   ├── fig_ex2_corr.png
│   ├── fig_ex2_residuals.png
│   ├── fig_ex2_leverage.png
│   ├── fig_ex3_residuals_comparison.png
│   ├── fig_ex4_sales_fit.png
│   ├── fig_ex5_simulation_fits.png
│   ├── fig_ex6_collinearity_scatter.png
│   └── fig_ex7_diabetes_models.png
└── README.md                                    # Tài liệu hướng dẫn thực thi và ghi chú sử dụng AI
```

---

## 🚀 Hướng dẫn chạy Notebook (How to Run the Notebook)

### 1. Chạy trên môi trường máy cá nhân (Local Environment)

#### Bước 1: Cài đặt các thư viện phụ thuộc
Đảm bảo máy đã cài đặt **Python 3.10+**. Cài đặt các thư viện cần thiết thông qua `pip`:

```bash
pip install numpy pandas matplotlib statsmodels scipy scikit-learn ISLP
```

#### Bước 2: Khởi động Jupyter Notebook / JupyterLab
Di chuyển vào thư mục bài làm và mở file notebook:

```bash
cd lab2/IT171IU_Lab02_MaiDongHuy_ITDSIU24019
jupyter notebook IT171IU_Lab02_MaiDongHuy_ITDSIU24019.ipynb
```

#### Bước 3: Thực thi
* Trên thanh menu chọn **Cell** $\rightarrow$ **Run All** (hoặc **Kernel** $\rightarrow$ **Restart & Run All**).
* Toàn bộ các cell mã nguồn và ô bài tập sẽ được thực thi tuần tự từ trên xuống dưới mà không phát sinh lỗi.

---

### 2. Chạy trên Google Colab (Google Colab Environment)

1. Tải file `IT171IU_Lab02_MaiDongHuy_ITDSIU24019.ipynb` lên Google Drive hoặc mở trực tiếp trên [Google Colab](https://colab.research.google.com/).
2. Chạy **Cell 0 (Setup cell)** đầu tiên: Cell này đã được thiết kế tự động kiểm tra và `pip install` các thư viện còn thiếu (`ISLP`, `statsmodels`) và tải các bộ dữ liệu phụ trợ (`additional-data/diabetes.csv`).
3. Chọn **Runtime** $\rightarrow$ **Run all** (hoặc nhấn phím tắt `Ctrl + F9`).

---

## 📊 Tóm tắt kết quả các bài tập (Exercise Highlights)

| Bài tập | Nội dung chính | Mô hình & Kết quả nổi bật |
| :--- | :--- | :--- |
| **Exercise 1** | Hồi quy đơn trên `Auto` (`mpg ~ horsepower`) | $R^2 = 0.6059$, $\hat{\beta}_1 = -0.1578$ ($p < 0.0001$). Dự báo tại $hp=98$: $\hat{y} \approx 24.47$; 95% CI: $[23.97, 24.96]$; 95% PI: $[14.81, 34.12]$. Biểu đồ phần dư cho thấy độ cong chữ U phi tuyến. |
| **Exercise 2** | Hồi quy bội trên `Auto` (7 biến định lượng) | $R^2 = 0.8215$, $F = 252.4$. Biến `year` có $\hat{\beta} \approx +0.75$ ($p < 0.0001$). VIF chỉ rõ đa cộng tuyến nặng ở `displacement` ($21.8$), `weight` ($10.8$), `cylinders` ($10.7$). Quan sát #13 có leverage cao nhất ($h \approx 0.198$). |
| **Exercise 3** | Tương tác & Biến đổi phi tuyến | Chọn **Interaction Model** (`weight + year + horsepower + hp × weight`): SSR thấp nhất ($3397.74$), $R^2 = 0.8581$, ANOVA $F = 133.02$ ($p < 10^{-26}$). Triệt tiêu hoàn toàn độ cong trên biểu đồ phần dư. |
| **Exercise 4** | Biến định tính trên `Carseats` | `Urban` không có ý nghĩa ($p = 0.936$). Rút gọn còn `Sales ~ Price + US`: $R^2 = 0.2393$, RSE $= 2.4694$. Tăng giá \$1 giảm 54.5 chiếc; cửa hàng tại Mỹ bán nhiều hơn 1,201 chiếc. |
| **Exercise 5** | Mô phỏng tác động của nhiễu | Kiểm chứng tính không chệch của OLS. Khi $\sigma^2$ tăng từ $0.05 \to 1.0$, sai số chuẩn tăng từ $0.023 \to 0.103$, khoảng tin cậy giãn rộng gấp 4.4 lần. Thêm số hạng bậc hai $x^2$ không có ý nghĩa ($p = 0.164$). |
| **Exercise 6** | Đa cộng tuyến giữa $x_1$ và $x_2$ | $r(x_1, x_2) = 0.8351$, VIF $\approx 3.3$. Mô hình đồng thời khiến cả 2 biến mất ý nghĩa ($p > 0.3$), nhưng mô hình đơn lẻ đều đạt $p < 0.0001$. Minh họa hiện tượng chia sẻ phương sai của đa cộng tuyến. |
| **Exercise 7** | Tiến triển tiểu đường (`diabetes`) | $m_1$ (`bmi`): $R^2 = 0.344$; $m_2$ (`bmi + bp + s5`): $R^2 = 0.480$; $m_3$ (full): $R^2 = 0.518$. Bảng VIF phát hiện các chỉ số lipid máu ($s_1, s_2, s_5$) bị cộng tuyến cực nặng. Đề xuất 3 biến cho bác sĩ: `bmi`, `s5`, `bp`. |
| **Exercise 8 (Bonus)** | Hàm OLS tự viết bằng NumPy | Thuật toán đại số ma trận OLS $\hat{\beta} = (X^T X)^{-1} X^T y$ cho kết quả trùng khớp chính xác 100% đến từng chữ số thập phân với `statsmodels.OLS`. |
| **Exercise 9 (Bonus)** | Hồi quy qua gốc tọa độ | Chứng minh toán học công thức thống kê $t$ đối xứng hoàn toàn giữa $x$ và $y$. Thực nghiệm khẳng định cả 2 mô hình $y \sim x$ và $x \sim y$ đều cho $t = 18.730349$ (chênh lệch tuyệt đối = 0). |

---

## 🤖 Ghi chú về việc sử dụng Trợ lý AI (Note on AI-Assistant Use)

Tuân thủ nghiêm ngặt theo **Chính sách sử dụng AI của Khóa học (Course AI Policy)**:
* **Mục đích hỗ trợ:** Trợ lý AI (Antigravity / Gemini) được sử dụng như một cộng sự lập trình (pair-programming assistant) để hỗ trợ:
  1. Kiểm tra cú pháp mã nguồn Python và tối ưu hóa việc xuất biểu đồ matplotlib với độ phân giải cao (300 DPI, Light Mode).
  2. Hỗ trợ định dạng thẩm mỹ báo cáo văn bản (`.docx`) và xuất tài liệu PDF chuẩn học thuật.
  3. Rà soát định dạng công thức toán học LaTeX và cấu trúc bảng biểu.
* **Cam kết độc lập học thuật:** Toàn bộ quá trình tư duy giải bài tập, lập luận suy diễn thống kê, phân tích ý nghĩa số liệu thực nghiệm, và các kết luận lựa chọn mô hình đều do chính sinh viên trực tiếp thực hiện, kiểm chứng và chịu trách nhiệm toàn diện về tính chính xác học thuật.
