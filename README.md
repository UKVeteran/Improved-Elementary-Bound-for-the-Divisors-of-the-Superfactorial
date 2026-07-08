<div align="center">
  <img src="https://img.shields.io/badge/Mathematics-Number%20Theory-blueviolet?style=for-the-badge" alt="Math Field">
  <img src="https://img.shields.io/badge/LaTeX-Typeset-emerald?style=for-the-badge" alt="LaTeX Ready">
  <img src="https://img.shields.io/badge/Status-Verified-success?style=for-the-badge" alt="Status">

  <h1 align="center">📐 Superfactorial Divisor Bounds</h1>
  <p align="center"><strong>An Improved Elementary Bound for the Divisors of the Superfactorial ($S_n$)</strong></p>
  
  <p align="center">
    <a href="\#-key-results">Key Results</a> •
    <a href="\#-mathematical-framework">Mathematical Framework</a> •
    <a href="\#-asymptotic-scaling">Asymptotic Analysis</a> •
    <a href="\#%EF%B8%8F-verification">Verification</a>
  </p>
</div>

## 📑 Abstract
Let $S_n = \prod_{k=1}^n k!$ denote the superfactorial of $n$, and let $d(k)$ count the positive divisors of $k$. This repository presents a streamlined proof of the lower bound:

$$\boxed{ d(S_n) \ge \frac{n^n}{n!} }$$

for all $n \ge 1$, completely characterizing the equality cases and providing algorithmic verification for small intervals.



## 🎯 Key Results

### 🔹 Theorem 1 (Main Bound)
For every positive integer $n \ge 1$:
$$d(1! \, 2! \cdots n!) \ge \frac{n^n}{n!}$$
* **Equality** holds if and only if $n \in \{1, 2\}$.
* For $n \ge 3$, the inequality is **strictly dominant**.

### 🔹 Lemma 2 (Combinatorial Valuation Bound)
For any prime $p \le n$, letting $e_p = v_p(S_n)$, the $p$-adic valuation satisfies:
$$e_p + 1 \ge \frac{n(n + 2 - p)}{2p}$$



## 📊 Analytical Domain Breakdown

For lower intervals ($1 \le n \le 5$), the theorem is explicitly verified below. For $n \ge 6$, the intermediate prime product bound permanently overtakes the target threshold, establishing global asymptotic divergence.

<div align="center">

| $n$ | $S_n$ | $d(S_n)$ | $n^n / n!$ | Strict Equality Case? |
| :---: | :---: | :---: | :---: | :---: |
| **1** | $1$ | $1$ | $1.00$ | 🟢 **Yes** |
| **2** | $2$ | $2$ | $2.00$ | 🟢 **Yes** |
| **3** | $12$ | $6$ | $4.50$ | ❌ No ($6 > 4.50$) |
| **4** | $288$ | $18$ | $10.67$ | ❌ No ($18 > 10.67$) |
| **5** | $34560$ | $72$ | $26.04$ | ❌ No ($72 > 26.04$) |

</div>


## 📈 Asymptotic Scaling Behavior

By pairing the **Prime Number Theorem** with standard estimates on the first Chebyshev function $\theta(n)$, the logarithmic expansion yields:

$$\log B_n = n + (1 - \log 2)\frac{n}{\log n} + O\left(\frac{n}{\log^2 n}\right)$$

In contrast, **Stirling’s approximation** for the target lower bound scales at a much slower rate:

$$\log\left(\frac{n^n}{n!}\right) = n - \frac{1}{2}\log n - \frac{1}{2}\log(2\pi) + O\left(\frac{1}{n}\right)$$

> 💡 **Asymptotic Takeaway:** Because $1 - \log 2 \approx 0.3069 > 0$, the secondary term of our bound grows positive-dominantly at $O(n/\log n)$, while the Stirling threshold decays. Thus, the bound becomes progressively sharper as $n \to \infty$.


---

## 📈 Computational Analysis and Asymptotic Scaling

To validate the analytical sharpness of these bounds, a high-precision numeric script was executed across the interval $1 \le n \le 150$. The resulting values are presented using a logarithmic scale ($\log_{10}$) to manage the hyper-exponential divergence of the sequences.

<div align="center">
  <img src="superfactorial_bound_plot.jpg" alt="Superfactorial Divisor Growth vs. Lower Bounds Plot" width="85%">
  
  <p><em>Figure 1: Comparison of the exact divisor function $\log_{10} d(S_n)$, the analytical intermediate bound $\log_{10} B_n$, and the target Stirling bound $\log_{10}(n^n / n!)$.</em></p>
</div>

Three critical behaviors emerge from the empirical data:
* **Asymptotic Divergence:** The exact divisor curve $\log_{10} d(S_n)$ scales cleanly above the target Stirling bound. At $n = 100$, $d(S_{100}) \approx 8.51 \times 10^{46}$ while the target bound yields $\approx 1.07 \times 10^{42}$, illustrating that $\frac{n^n}{n!}$ serves as a conservative but valid global lower bound.
* **The Lower Interval Domain:** The intermediate prime product bound $B_n$ drops temporarily below the target bound $\frac{n^n}{n!}$ during the local initial values ($3 \le n \le 5$). However, at exactly $n = 6$, $B_n$ permanently overtakes the target threshold ($B_6 = 81.0 > 64.8$), justifying the split-domain framework used in the proof.
* **Boundary Cases:** Exact integer evaluation confirms $d(S_1) = 1$ and $d(S_2) = 2$, matching the algebraic values of $\frac{1^1}{1!}$ and $\frac{2^2}{2!}$ respectively. This completely characterizes the necessary and sufficient conditions for equality.


## 🛠️ Verification & Build Instructions

The companion verification scripts evaluate exact integer boundaries across the domain $6 \le n < 150$.

### Prerequisites
* A standard LaTeX environment (`pdflatex`)
* Python 3.x (Optional, for computing localized validation arrays)

