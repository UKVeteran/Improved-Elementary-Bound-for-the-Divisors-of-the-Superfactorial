<div align="center">
  <img src="https://img.shields.io/badge/Mathematics-Number%20Theory-blueviolet?style=for-the-badge" alt="Math Field">
  <img src="https://img.shields.io/badge/LaTeX-Typeset-emerald?style=for-the-badge" alt="LaTeX Ready">
  <img src="https://img.shields.io/badge/Status-Verified-success?style=for-the-badge" alt="Status">

  <h1 align="center">📐 Superfactorial Divisor Bounds</h1>
  <p align="center"><strong>An Improved Elementary Bound for the Divisors of the Superfactorial ($S_n$)</strong></p>
  
  <p align="center">
    <a href="#-key-results">Key Results</a> •
    <a href="#-mathematical-framework">Mathematical Framework</a> •
    <a href="#-asymptotic-scaling">Asymptotic Analysis</a> •
    <a href="#%EF%B8%8F-verification">Verification</a>
  </p>
</div>
---

## 📑 Abstract
Let $S_n = \prod_{k=1}^n k!$ denote the superfactorial of $n$, and let $d(k)$ count the positive divisors of $k$. This repository presents a streamlined proof of the lower bound:

$$\bbox[10px,border:2px solid #2563eb,text-align:center]{d(S_n) \ge \frac{n^n}{n!}}$$

for all $n \ge 1$, completely characterizing the equality cases and providing algorithmic verification for small intervals.

---

## 🎯 Key Results

### 🔹 Theorem 1 (Main Bound)
For every positive integer $n \ge 1$:
$$d(1! \, 2! \cdots n!) \ge \frac{n^n}{n!}$$
* **Equality** holds if and only if $n \in \{1, 2\}$.
* For $n \ge 3$, the inequality is **strictly dominant**.

### 🔹 Lemma 2 (Combinatorial Valuation Bound)
For any prime $p \le n$, letting $e_p = v_p(S_n)$, the $p$-adic valuation satisfies:
$$e_p + 1 \ge \frac{n(n + 2 - p)}{2p}$$

---

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

---

## 📈 Asymptotic Scaling Behavior

By pairing the **Prime Number Theorem** with standard estimates on the first Chebyshev function $\theta(n)$, the logarithmic expansion yields:

$$\log B_n = n + (1 - \log 2)\frac{n}{\log n} + O\left(\frac{n}{\log^2 n}\right)$$

In contrast, **Stirling’s approximation** for the target lower bound scales at a much slower rate:

$$\log\left(\frac{n^n}{n!}\right) = n - \frac{1}{2}\log n - \frac{1}{2}\log(2\pi) + O\left(\frac{1}{n}\right)$$

> 💡 **Asymptotic Takeaway:** Because $1 - \log 2 \approx 0.3069 > 0$, the secondary term of our bound grows positive-dominantly at $O(n/\log n)$, while the Stirling threshold decays. Thus, the bound becomes progressively sharper as $n \to \infty$.

---

## 🛠️ Verification & Build Instructions

The companion verification scripts evaluate exact integer boundaries across the domain $6 \le n < 150$.

### Prerequisites
* A standard LaTeX environment (`pdflatex`)
* Python 3.x (Optional, for computing localized validation arrays)

### Compile the Manuscript
```bash
pdflatex superfactorial_bounds.tex
