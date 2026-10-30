# IT171IU · Statistical Learning — Lab 4: Resampling Methods

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

## 📁 Official Submission Package Directory Structure

Strictly formatted according to **Section 5 (Submission Instructions)** of the Lab 4 handout:

```text
IT171IU_Lab04_MaiDongHuy_ITDSIU24019/
├── IT171IU_Lab04_MaiDongHuy_ITDSIU24019.ipynb       # Fully Executed Academic English Jupyter Notebook (All 101 cells executed, 0 errors)
├── IT171IU_Lab04_Report.pdf                        # Comprehensive Academic Lab Report (Compiled via MS Word COM, vector charts)
├── IT171IU_Lab04_Report.docx                       # Original Word Source Document
├── figures/                                        # Standalone publication-grade figures (300 DPI Light Mode)
│   ├── ex1_valset_variability.png
│   ├── ex2_bootstrap_vs_analytic_se.png
│   ├── ex3_loocv_vs_null_baseline.png
│   ├── ex4_polynomial_loocv_curve.png
│   ├── ex5_bootstrap_boston_distributions.png
│   ├── ex6_diabetes_cv_curves_1se_rule.png
│   ├── ex7_bootstrap_probability_convergence.png
│   └── ex8_cv_vs_true_test_mse.png
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
cd "lab 4/IT171IU_Lab04_MaiDongHuy_ITDSIU24019"
jupyter notebook IT171IU_Lab04_MaiDongHuy_ITDSIU24019.ipynb
```

#### Step 3: Execution
* Select **Kernel** $\rightarrow$ **Restart & Run All** (or **Cell** $\rightarrow$ **Run All**).
* All 101 cells will execute cleanly from top to bottom with zero errors.

---

### 2. Google Colab Environment

1. Upload `IT171IU_Lab04_MaiDongHuy_ITDSIU24019.ipynb` to Google Drive or open directly in [Google Colab](https://colab.research.google.com/).
2. Execute **Cell 10 (Setup cell)**: Automatically verifies and installs missing libraries (`ISLP`, `statsmodels`).
3. Select **Runtime** $\rightarrow$ **Run all** (or press `Ctrl + F9`).

---

## 📬 Submission via Google Form

Submit your repository link or shared Google Drive folder through the official course Google Form:

| Submission Item | Link / Instructions |
| :--- | :--- |
| **Lab 4 Submission Form (Pre-selected)** | [Open the Lab 4 submission form](https://docs.google.com/forms/d/e/1FAIpQLSeM7zOP9JarqtfBxE2RpljzppuZEfMPfygg7_k96zD5VlgZfQ/viewform?usp=pp_url&entry.1104082638=Lab+4:+Resampling+Methods+(Ch.+5)) |
| **General Form Link (Short URL)** | [https://forms.gle/pUebamKV64bYB6KHA](https://forms.gle/pUebamKV64bYB6KHA) – choose **Lab 4: Resampling Methods (Ch. 5)** |
| **Required Fields to Fill In** | **Full Name:** Mai Dong Huy<br>**Student ID:** ITDSIU24019<br>**Class/Group:** IT171IU – Lab Group 01<br>**Lab Number:** Lab 4: Resampling Methods (Ch. 5)<br>**Submission Link/File:** Link to your GitHub repo or Google Drive folder |

---

## 📊 Summary of Exercise Highlights & Empirical Metrics

| Exercise | Main Objective & Topic | Key Models & Noteworthy Results |
| :--- | :--- | :--- |
| **Exercise 1** | Validation-Set Error on `Default` ($n=10,000$) | Base validation error fluctuates between $2.480\%$ and $2.900\%$ across seeds (Mean: **$2.627\%$**). Adding `student` yields **$2.693\%$** ($+0.067\%$). Does not improve out-of-sample accuracy due to collinearity with `balance`. |
| **Exercise 2** | Bootstrap Standard Errors on `Default` | Asymptotic Fisher Information SEs match empirical Bootstrap SEs ($B=1000$) within **$0.21\% - 2.38\%$** (Intercept: $0.4348$ vs $0.4357$, Income: $4.985 \times 10^{-6}$ vs $4.866 \times 10^{-6}$, Balance: $2.274 \times 10^{-4}$ vs $2.298 \times 10^{-4}$). Validates large-sample MLE normality. |
| **Exercise 3** | Explicit LOOCV Loop on `Weekly` ($n=1,089$) | LOOCV Error Rate = **$44.995\%$** (Accuracy = $55.005\%$). Naive baseline blindly forecasting majority class `Up` achieves **$44.444\%$** error. Logistic regression performs worse than trivial guessing, confirming **Weak-Form Efficient Market Hypothesis (EMH)**. |
| **Exercise 4** | Cross-Validation on Simulated Nonlinear Data ($n=100$) | Demonstrates **strict seed invariance** of LOOCV on fixed data. Degree 2 drops test MSE dramatically from **$6.6330$** to **$1.1229$**, perfectly matching true quadratic generating equation $Y = X - 2X^2 + \varepsilon$ and OLS $p$-values ($p < 10^{-18}$). |
| **Exercise 5** | Bootstrap Inference on `Boston` Housing (`medv`, $n=506$) | Population mean $\hat{\mu} = 22.533$, formula $\mathrm{SE} = 0.409$, bootstrap $\mathrm{SE} = 0.413$. 95% Bootstrap CI $[21.707, 23.358]$ matches Student's $t$ $[21.730, 23.336]$. Non-parametric bootstrap provides valid SE for median ($\hat{\mu}_{\text{med}} = 21.20$, $\mathrm{SE} = 0.370$) and 10th percentile ($\hat{\mu}_{0.1} = 12.75$, $\mathrm{SE} = 0.504$). |
| **Exercise 6** | Model Flexibility & One-Standard-Error Rule on `diabetes` | 10-Fold CV reaches minimum at Degree 1 ($\text{MSE} = 3915.86$, $\mathrm{SE} = 227.10$). One-Standard-Error threshold ($4142.96$) encompasses all degrees; by the parsimony principle, the **Degree 1 (Linear Model)** is selected. 10-Fold CV exhibits slight seed shift ($\approx 42.7$) while LOOCV is stationary ($3922.99$). |
| **Exercise 7 (Bonus)** | Analytical Proof of Bootstrap Sample Composition | Proves $P(\text{obs } j \notin \text{sample}) = (1 - 1/n)^n \to 1/e \approx 36.79\%$, and inclusion probability $P(\text{in}) \to 1 - 1/e \approx \mathbf{63.21\%}$. Convergence verified for $n=1$ to $100,000$. 10,000 Monte Carlo bootstrap draws for $n=100$ yield **$63.62\%$** ($6,362 / 10,000$). |
| **Exercise 8 (Bonus)** | Cross-Validation Accuracy & Bias Simulation (50 Trials) | Evaluates degree-5 polynomial 10-fold CV against gold-standard population test MSE ($N=10,000$). Mean CV MSE = **$0.30623$**, Mean True Test MSE = **$0.29917$**. Empirical Bias = **$+0.00706$** ($+2.36\%$). Proves 10-fold CV is nearly unbiased in expectation, though subject to moderate single-sample variance. |

---

## ⚖️ Academic Integrity & AI Assistance Disclosure

In accordance with course guidelines and the CSE academic integrity policy, this assignment was developed with the assistance of **Antigravity** (Google DeepMind advanced agentic coding assistant) for:
1. Automated execution verification and top-level import hoisting.
2. Generating 300 DPI Light Mode visualizations and LaTeX mathematical typography.
3. Automated compilation of the final publication-grade academic report (`.pdf`) via headless Microsoft Word COM automation.
4. All conceptual analyses, empirical evaluations, mathematical derivations, and code implementations were audited, executed, and verified by the student.
