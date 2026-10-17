# matrix-factorizations-parallelization
Showcasing different ways of how we can use parallelization in order to speed up crucial algorithms in modern computing - matrix factorizations.

# Parallel Cholesky Matrix Factorization on Multi-Core CPU

This repository contains the sequential and parallel CPU implementations of the **Cholesky Decomposition** algorithm for symmetric positive-definite matrices ($A = L \cdot L^T$). 

The project focuses on leveraging multi-core CPU architectures using **OpenMP in C/C++** to optimize memory access patterns, reduce execution time, and evaluate parallel scalability (Speedup and Efficiency).

---

## 📌 Theoretical Background

For a real, symmetric, and positive-definite matrix $A \in \mathbb{R}^{n \times n}$, the Cholesky decomposition computes a lower triangular matrix $L$ with strictly positive diagonal entries such that:

$$A = L \cdot L^T$$

The elements of $L$ are computed using:
* **Diagonal entries:**  
  $$L_{j,j} = \sqrt{A_{j,j} - \sum_{k=0}^{j-1} L_{j,k}^2}$$
* **Non-diagonal entries ($i > j$):**  
  $$L_{i,j} = \frac{1}{L_{j,j}} \left( A_{i,j} - \sum_{k=0}^{j-1} L_{i,k} L_{j,k} \right)$$

---

## 🚀 Key Features

* **Sequential Baseline:** Reference standard implementation for numerical validation and runtime baseline.
* **OpenMP Parallelization:** Multi-threaded parallel loops (`#pragma omp parallel for`) utilizing dynamic/static scheduling to balance load across cores.
* **Performance Benchmarking:** Execution time measurements across varying:
  * Matrix dimensions ($N \times N$, e.g., $500, 1000, 2000, 4000$)
  * Thread counts ($1, 2, 4, 8, \dots$)
* **Scalability Metrics:** Calculation of Speedup ($S = \frac{T_{seq}}{T_{par}}$) and Parallel Efficiency ($E = \frac{S}{p}$).

---

## 🛠️ Tech Stack & Requirements

* **Language:** C / C++
* **Parallel API:** OpenMP
* **Compiler:** GCC (`gcc` / `g++`) or Clang with OpenMP support
* **OS:** Linux / macOS / Windows (via MinGW or WSL)

---

## ⚙️ Compilation & Execution

### 1. Clone the repository and switch to the Cholesky branch:
```bash
git clone https://github.com/etirak1/matrix-factorizations-parallelization-cpu.git
cd matrix-factorizations-parallelization-cpu
git checkout Cholesky
