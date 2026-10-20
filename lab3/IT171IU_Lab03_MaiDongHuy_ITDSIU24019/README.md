# IT171IU · Statistical Learning — Lab 3: Classification

**International University – VNU-HCM**  
**School of Computer Science and Engineering**  

---

## 👤 Student Information

* **Full Name:** Mai Dong Huy
* **Student ID:** ITDSIU24019
* **Class / Lab Group:** IT171IU – Lab Group 01
* **Course Instructor:** M.Sc. Son Nguyen (Nguyen Van Son)
* **Completion Date:** October 2026

---

## 📁 Submission Directory Structure

Strictly formatted according to **Section 5 (Submission Instructions)** of the Lab 3 handout:

```text
IT171IU_Lab03_MaiDongHuy_ITDSIU24019/
├── IT171IU_Lab03_MaiDongHuy_ITDSIU24019.ipynb       # Completed Academic English Jupyter Notebook (All 92 code cells executed, 0 errors)
├── IT171IU_Lab03_Report.pdf                        # Comprehensive Academic Lab Report (PDF format)
├── IT171IU_Lab03_Report.docx                       # Original Word Source Document
├── figures/                                        # Standalone publication-grade figures (300 DPI)
│   ├── fig_ex1_volume_time_series.png
│   ├── fig_ex2_model_accuracy_comparison.png
│   ├── fig_ex3_mpg01_boxplots.png
│   ├── fig_ex3_knn_k_errors.png
│   ├── fig_ex4_default_simpson_paradox.png
│   ├── fig_ex5_roc_curves.png
│   ├── fig_ex5_threshold_tuning.png
│   ├── fig_ex6_poisson_bikeshare_effects.png
│   ├── fig_ex7_lda_discriminant_boundary.png
│   └── fig_ex8_wine_lda_projection.png
└── README.md                                       # Reproduction guide, highlight matrix & AI disclosure
```

---

## 🚀 How to Run the Notebook

### 1. Local Environment Setup

#### Step 1: Install Dependencies
Ensure you have **Python 3.10+** installed. Install required scientific packages:

```bash
pip install numpy pandas matplotlib statsmodels scipy scikit-learn ISLP
```

#### Step 2: Launch Jupyter
Navigate to the submission directory and launch Jupyter Notebook / JupyterLab:

```bash
cd lab3/IT171IU_Lab03_MaiDongHuy_ITDSIU24019
jupyter notebook IT171IU_Lab03_MaiDongHuy_ITDSIU24019.ipynb
```

#### Step 3: Execution
* Select **Kernel** $\rightarrow$ **Restart & Run All** (or **Cell** $\rightarrow$ **Run All**).
* All 92 code cells will execute cleanly from top to bottom with zero errors.

---

### 2. Google Colab Environment

1. Upload `IT171IU_Lab03_MaiDongHuy_ITDSIU24019.ipynb` to Google Drive or open directly in [Google Colab](https://colab.research.google.com/).
2. Execute **Cell 0 (Setup cell)**: The setup cell automatically verifies and installs missing libraries (`ISLP`, `statsmodels`) and downloads supplementary datasets (`additional-data/breast_cancer.csv`, `wine.csv`).
3. Select **Runtime** $\rightarrow$ **Run all** (or press `Ctrl + F9`).

---

## 📊 Summary of Exercise Highlights

| Exercise | Main Objective & Topic | Key Models & Noteworthy Results |
| :--- | :--- | :--- |
| **Exercise 1** | Logistic Regression on `Weekly` ($n=1,089$, 1990–2010) | Only `Lag2` is statistically significant ($p = 0.0296 < 0.05$). Overall Accuracy = $56.11\%$. Model exhibits heavy upward bias (Sensitivity = $92.07\%$, Specificity = $11.16\%$). |
| **Exercise 2** | Out-of-Sample Holdout Testing on `Weekly` ($n=104$, 2009–2010) | **Logistic Regression** and **LDA** tie as top performers with **62.50%** Accuracy (Test Error = $37.50\%$). QDA and Naive Bayes degenerate to predicting 100% "Up" ($58.65\%$). KNN ($K=1$) suffers from noise overfitting ($50.00\%$). |
| **Exercise 3** | Predicting Mileage Classification on `Auto` (`mpg01`) | Median cut-off = $22.75$ MPG. Four strongest negative correlates: `displacement` ($-0.75$), `cylinders` ($-0.76$), `weight` ($-0.76$), `horsepower` ($-0.67$). **LDA** and **Logistic** achieve lowest test error (**10.17%**, Accuracy = **89.83%**). KNN optimal at $K = 7$ (Error = **11.86%**). |
| **Exercise 4** | Validation-Set Stability on `Default` & Simpson's Paradox | Validation error stable at $2.36\% - 2.86\%$. Adding `student` provides negligible improvement. Odds Ratio $\exp(\hat{\beta}_{\text{student}}) \approx 0.49 - 0.52$: At fixed balance, students have $50\%$ lower default odds; but aggregate default is higher ($4.31\%$ vs $2.93\%$) due to higher mean debt (\$987.80 vs \$771.78) — classic confounding. |
| **Exercise 5** | Cancer Diagnosis on `breast_cancer` ($n=569$) | Malignancy rate = $37.26\%$. Threshold tuning from 0.50 down to $\tau^* \approx 0.165$ achieves **Sensitivity $\ge 98.44\%$** (only 1 false negative out of 64), preserving Specificity at $92.5\% - 95.3\%$. AUC reaches **0.9950** (Logistic) and **0.9922** (LDA). |
| **Exercise 6** | Poisson GLM for Count Data on `Bikeshare` | Multiplicative factors $\exp(\hat{\beta})$: Working days multiply expected ridership by $1.326$ ($+32.6\%$), temperature multiplies by $2.270$ ($+127\%$). At 8am in June, OLS predicts 118 riders, Poisson predicts 141. OLS produces 1,090 nonsensical negative counts; Poisson guarantees $100\%$ strictly positive predictions ($\hat{Y} > 0$). |
| **Exercise 7 (Bonus)** | Mathematical Derivation of Scratch LDA vs Scikit-Learn | Analytical calculation of prior $\hat{\pi}_k$, mean $\hat{\mu}_k$, pooled unbiased variance $\hat{\sigma}^2 = 5.3621$, and decision boundary $x^* = 0.1265\%$. Test predictions across all 104 holdout weeks match Scikit-Learn **100% IDENTICALLY** (0 discrepancies). |
| **Exercise 8 (Bonus)** | Multiclass Classification of `Wine` Cultivars (3 Classes) | 5-Fold Stratified Cross-Validation with `StandardScaler` Pipeline: **LDA** achieves highest accuracy (**99.44%**, Error = $0.56\%$), followed by Multinomial Logistic and QDA ($98.87\%$). LDA 2D projection ($\text{LD}_1, \text{LD}_2$) cleanly separates the three cultivars into non-overlapping clusters. |

---

## 🤖 Note on AI-Assistant Use

In strict adherence to the **Course AI Policy**:
* **Role of AI:** Generative AI tools (Antigravity / Gemini) were utilized strictly as a technical pair-programming assistant to:
  1. Inspect syntax, verify statistical module calls, and enforce centralized top-level imports in setup cells.
  2. Assist in automating high-resolution chart exports (300 DPI, Light Mode) and Word COM layout formatting (`<w:cantSplit/>`, `<w:tblHeader/>`).
  3. Validate mathematical formulas and verify LaTeX equation notation.
* **Academic Integrity Statement:** All analytical model interpretations, statistical reasoning, diagnostic conclusions, and comparative evaluations were performed, verified, and approved by the student, who assumes full academic responsibility for the submitted work.
