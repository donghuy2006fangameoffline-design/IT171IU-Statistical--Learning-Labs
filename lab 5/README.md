# IT171IU · Statistical Learning — Lab 5: Linear Model Selection & Regularization

**International University – VNU-HCM**  
**School of Computer Science and Engineering**  

---

## 👤 Student Information

* **Full Name:** Mai Dong Huy
* **Student ID:** ITDSIU24019
* **Class / Lab Group:** IT171IU – Lab Group 01
* **Course Instructor:** M.Sc. Son Nguyen (Nguyen Van Son)
* **Academic Term:** Semester I, Academic Year 2026–2027

---

## 📁 Official Submission Package Directory Structure

Strictly formatted according to **Section 5 (Submission Instructions)** of the Lab 5 handout:

```text
IT171IU_Lab05_MaiDongHuy_ITDSIU24019/
├── IT171IU_Lab05_MaiDongHuy_ITDSIU24019.ipynb       # Fully Executed Academic English Jupyter Notebook (All 168 cells executed, 0 errors)
├── IT171IU_Lab05_Report.pdf                        # Comprehensive Academic Lab Report (Compiled via MS Word COM, vector charts)
├── IT171IU_Lab05_Report.docx                       # Original Word Source Document
├── figures/                                        # Standalone publication-grade figures (300 DPI Light Mode)
│   ├── ex1_lasso_cv_curve.png
│   ├── ex2_college_models_comparison.png
│   ├── ex3_train_test_error_curves.png
│   ├── ex4_boston_crime_model_selection.png
│   ├── ex5_diabetes_ridge_lasso_paths.png
│   ├── ex6_standardization_effect.png
│   ├── ex7_closed_form_ridge_shrinkage.png
│   └── ex8_elastic_net_cv_heatmap.png
└── README.md                                       # Reproduction guide, highlight matrix & AI disclosure
```

---

## 🚀 How to Run the Notebook

### 1. Local Environment Setup

#### Step 1: Install Dependencies
Ensure you have **Python 3.10+** installed. Install required scientific packages:

```bash
pip install numpy pandas matplotlib statsmodels scipy scikit-learn ISLP l0bnb
```

#### Step 2: Launch Jupyter
Navigate to the submission directory and launch Jupyter Notebook / JupyterLab:

```bash
cd "lab5/IT171IU_Lab05_MaiDongHuy_ITDSIU24019"
jupyter notebook IT171IU_Lab05_MaiDongHuy_ITDSIU24019.ipynb
```

#### Step 3: Execution
* Select **Kernel** $ightarrow$ **Restart & Run All** (or **Cell** $ightarrow$ **Run All**).
* All 168 cells will execute cleanly from top to bottom with zero errors.

---

### 2. Google Colab Environment

1. Upload `IT171IU_Lab05_MaiDongHuy_ITDSIU24019.ipynb` to Google Drive or open directly in [Google Colab](https://colab.research.google.com/).
2. Execute **Cell 10 (Setup cell)**: Automatically verifies and installs missing libraries (`ISLP`, `l0bnb`).
3. Select **Runtime** $ightarrow$ **Run all** (or press `Ctrl + F9`).

---

## 📬 Submission via Google Form

Submit your repository link or shared Google Drive folder through the official course Google Form:

| Submission Item | Link / Instructions |
| :--- | :--- |
| **Lab 5 Submission Form (Pre-selected)** | [Open the Lab 5 submission form](https://docs.google.com/forms/d/e/1FAIpQLSeM7zOP9JarqtfBxE2RpljzppuZEfMPfygg7_k96zD5VlgZfQ/viewform?usp=pp_url&entry.1104082638=Lab+5:+Linear+Model+Selection+%26+Regularization+(Ch.+6)) |
| **General Form Link (Short URL)** | [https://forms.gle/pUebamKV64bYB6KHA](https://forms.gle/pUebamKV64bYB6KHA) – choose **Lab 5: Linear Model Selection & Regularization (Ch. 6)** |
| **Required Fields to Fill In** | **Full Name:** Mai Dong Huy<br>**Student ID:** ITDSIU24019<br>**Class/Group:** IT171IU – Lab Group 01<br>**Lab Number:** Lab 5: Linear Model Selection & Regularization (Ch. 6)<br>**Submission Link/File:** Link to your GitHub repo or Google Drive folder |

---

## 📊 Summary of Exercise Highlights & Empirical Metrics

| Exercise | Main Objective & Topic | Key Models & Noteworthy Results |
| :--- | :--- | :--- |
| **Exercise 1** | Polynomial Model Selection ($n=100$) | Forward Stepwise selects $\{X^1, X^2, X^3, X^{10}\}$. 5-Fold CV Lasso ($\lambda^* = 0.12613$) sets all 7 noise terms ($X^4 \dots X^{10}$) strictly to 0, recovering true signal without false positives. For $Y = 3 + 7X^7 + arepsilon$, Lasso concentrates weight on $X^7$ ($\hat{eta}_7 = 692.89$). |
| **Exercise 2** | Predicting Applications on `College` ($n=777, p=17$) | Test MSE: OLS ($1,659,682, R^2 = 90.87\%$), Ridge ($1,734,094, R^2 = 90.46\%$), Lasso ($1,753,284, R^2 = 90.36\%$, 14 non-zero), PCR ($M=17, 1,659,682$), PLS ($M=10, 1,671,280, R^2 = 90.81\%$). Supervised PLS achieves full accuracy with 41% dimension reduction. |
| **Exercise 3** | Train vs. Test Error as Model Grows ($n=1000, p=20$) | Training MSE decreases strictly monotonically ($29.839 	o 0.607$). Test MSE follows classic U-curve with global minimum at $d^* = 14$ ($	ext{MSE} = 1.0823$), remarkably recovering the true underlying sparsity of 13 signal variables. |
| **Exercise 4** | Boston Crime Rate `crim` ($n=506$) | 10-Fold CV MSE: OLS ($42.019$), Ridge ($42.028$), Lasso ($42.034$), PCR ($42.019$), Forward Selection ($42.905$, 4 variables: `rad`, `lstat`, `medv`, `ptratio`). Proposed 4-factor model is within 2.1% of full model error while discarding 8 irrelevant features. |
| **Exercise 5** | Regularization Paths on `diabetes` ($p=10$) | Ridge shrinks asymptotically toward 0; Lasso drives coefficients exactly to 0. Variable entrance order in Lasso: `bmi` ($\lambda=40.37$), `s5` ($40.37$), `bp` ($20.09$) — perfectly replicating the exact variable ranking found in Lab 2 Exercise 7! |
| **Exercise 6** | Necessity of Feature Standardization (`Hitters`) | Scale sensitivity in Ridge: unstandardized ridge flips `Runs` coefficient from $+29.66$ to $-2.16$! Scaling response $Y$ (`Salary` / 1000) uniformly scales all coefficients down by exactly 1,000 without altering relative importance or rank. |
| **Exercise 7** | Closed-Form Analytical Solution of Ridge | $\hat{eta}^R_\lambda = (X^	op X + \lambda I)^{-1} X^	op y$ matches `skl.Ridge` to floating-point precision ($10^{-12}$). SVD proof confirms $\|\hat{eta}^R_\lambda\|_2 = \sqrt{\sum [d_j/(d_j^2+\lambda)]^2 (u_j^	op y)^2}$ decreases strictly monotonically: $651.04 	o 173.86 	o 93.88$. |
| **Exercise 8** | Elastic Net Regularization on `Hitters` | 5-Fold CV 2D grid search over $ho \in [0.1, 1.0]$ and $lpha$ selects optimal $ho^* = 1.0$ (pure Lasso), $lpha^* = 3.14724$, CV MSE = $114,690.73$, retaining 13 features and eliminating 6 collinear career totals. |

---

## 🤖 AI Assistant Statement & Academic Integrity

In compliance with the course policy of **IT171IU · Statistical Learning**, artificial intelligence assistance (Google Antigravity / Gemini 2.5 Pro) was utilized strictly for script automation, figure styling (300 DPI Light Mode), and LaTeX typesetting. All analytical derivations, statistical interpretations, model diagnoses, and mathematical proofs were authored, reviewed, and verified independently by the student.
