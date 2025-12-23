# Explicit Constructions of Cyclic N-isogenies

This repository contains the **SageMath** implementation accompanying the paper:

> **Explicit Constructions of Cyclic N-isogenies**
> *Daeyeol Jeon and Yongjae Kwon*

This project provides algorithms to explicitly construct cyclic $N$-isogenies for sporadic levels where the modular curve $X_0(N)$ has positive genus. The codebase utilizes **SageMath 10.6** and is organized to demonstrate both the uniform algebraic method (for general levels) and a specialized analytic method (for the exceptional case $N=163$).

## 📂 Repository Structure

The project is organized into three main components:

### 1. `modular_isogeny_lib.sage` (Core Library)
This library contains the backend algorithms and mathematical definitions used to solve the moduli problems. It implements the core logic described in the paper.

#### Key Functions:
* **`get_model_data(N)`**: Returns the defining plane equation $F(x, y) = 0$ for $X_0(N)$ and the $q$-expansions of coordinate generators.
* **`setup_modular_forms(N, prec)`**: Computes high-precision $q$-expansions of Eisenstein series ($E_4, E_6$) and the Fricke-twisted $E_2^{(N)}$.
* **`find_minimal_robust_solution(...)`**: **(Core Solver)** Implements the linear algebra algorithm to express modular invariants ($a_4, a_6$) as rational functions of the curve generators.
* **`analyze_isogenies(...)`**: Constructs explicit elliptic curves over $\mathbb{Q}$ for the identified rational points and verifies the isogeny class (LMFDB label) and twist factors.

---

### 2. `X0_main.ipynb` (General Levels $N \le 67$)
The main interactive notebook for computing isogenies for sporadic levels **$N \in \{11, 14, 15, 17, 19, 21, 27, 37, 43, 67\}$**.

* **Methodology:** Algebraic Approach.
* **Features:**
    * Provides a GUI using `ipywidgets`.
    * Users can select a level $N$ from the dropdown to automatically generate the rational maps and isogeny curves.
    * Relies on `modular_isogeny_lib.sage` for calculations.

### 3. `X_0(163).ipynb` (Special Case $N=163$)
A standalone notebook dedicated to the genus 13 case **$N=163$**.

* **Methodology:** Analytic Approach (Complex Multiplication).
* **Reasoning:** For $N=163$, the algebraic maps involve polynomials with astronomically large coefficients, making the algebraic approach computationally intractable.
* **Key Computations:**
    * **Heegner Point Evaluation:** Evaluates modular forms at $\tau = \frac{-163+\sqrt{-163}}{326}$ with **4000 bits of precision**.
    * **Rational Reconstruction:** analytically recovers the exact rational coefficients of the isogeny $E \to E'$.
    * **Verification:** Confirms the twist relationship $D' = -163D$, consistent with the CM endomorphism.

---

## 🚀 Getting Started

### Prerequisites
* **SageMath 10.6** (or higher)
* Standard SageMath libraries and `ipywidgets` (for the GUI in `X0_main.ipynb`).

### Usage Instructions

1.  **For General Levels ($N \le 67$):**
    * Open **`X0_main.ipynb`**.
    * Ensure `modular_isogeny_lib.sage` is in the same directory.
    * Run all cells and use the interactive dropdown to select $N$ and execute the computation.

2.  **For Level $N=163$:**
    * Open **`X_0(163).ipynb`**.
    * Run the cells to perform the high-precision analytic construction and verification.

## 📜 Citation

If you use this code in your research, please cite the paper:

```bibtex
@article{jeon_kwon_isogenies,
  title={Explicit Constructions of Cyclic N-isogenies},
  author={Jeon, Daeyeol and Kwon, Yongjae},
  journal={To appear},
  year={2026}
}
```

## ⚖️ License
This project is licensed under the MIT License.