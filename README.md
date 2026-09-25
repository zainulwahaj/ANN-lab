# ANN Lab

Lab work for the **Artificial Neural Networks** course.

| | |
|---|---|
| **Name** | Zain Ul Wahaj |
| **Roll Number** | FA23-BAI-058 |
| **Course** | Artificial Neural Networks |

---

## Labs

| # | Lab | Notebook |
|---|-----|----------|
| 01 | Python Fundamentals | [`Lab01_Python_Fundamentals.ipynb`](Lab01_Python_Fundamentals.ipynb) |
| 02 | NumPy Essentials | [`Lab02_NumPy_Essentials.ipynb`](Lab02_NumPy_Essentials.ipynb) |
| 03 | Perceptron and Weight Initialization | [`Lab03_Perceptron_and_Weight_Initialization.ipynb`](Lab03_Perceptron_and_Weight_Initialization.ipynb) |

Every lab is a fully executed Jupyter notebook. Each lettered part is solved in its own
code cell, directly under the question it answers, with its output saved — so the results
and plots are visible on GitHub without running anything.

---

## Lab 01 — Python Fundamentals

| # | Task | Topics Covered |
|---|------|----------------|
| 1 | Variables and Basic Operators | Python syntax basics |
| 2 | Working with Lists | Data types (list) |
| 3 | Tuples and Dictionaries | Data types (tuple, dictionary) |
| 4 | Indexing and Slicing Practice | Indexing and slicing |
| 5 | String Processing | Strings |
| 6 | Conditional Statements | Flow control (`if` / `elif` / `else`) |
| 7 | Loops with Break and Continue | Flow control (`for` / `while` / `break` / `continue`) |
| 8 | Functions — Basics | Functions |
| 9 | Classes and Inheritance | Classes (OOP basics) |

Variables and operators, the core built-in containers and how mutability differs between
them, indexing and slicing, string handling, conditionals and loops, functions with
default arguments and reference semantics, and OOP with inheritance and method overriding.

## Lab 02 — NumPy Essentials

| # | Task | Topics Covered |
|---|------|----------------|
| 1 | Vectors | 1-D arrays, shape, dtype, broadcasting |
| 2 | Matrices | 2-D arrays, `zeros_like()`, row assignment |
| 3 | Addition & Subtraction | Element-wise arithmetic, `sum(axis=)`, `argmax()` |
| 4 | Dot Product | `np.dot()`, shape alignment rules |
| 5 | Reshaping | `reshape()`, valid vs invalid shapes |
| 6 | Indexing | Element access, negative indexing, in-place updates |
| 7 | Slicing | Sub-matrices, step slicing |
| 8 | Random Matrices | Seeding, `rand()`, `randint()`, `randn()` |
| 9 | Transpose | `.T`, shape verification, enabling a dot product |

Vector and matrix creation, element-wise arithmetic, dot products and why array shapes
have to align, reshaping rules, indexing and slicing of sub-matrices, reproducible random
generation with seeds, and transposition.

## Lab 03 — Perceptron and Weight Initialization

| # | Task | Topics Covered |
|---|------|----------------|
| 1 | Dataset Loading and Visualization | Data inspection, class distribution plots, train/test split, scaling |
| 2 | Basic Perceptron Implementation | Perceptron written from scratch with NumPy |
| 3 | Learning Curve and Weight Visualization | Per-epoch error tracking, decision boundary |
| 4 | Gaussian Weight Initialization | Normal initialisation and convergence |
| 5 | Xavier/Glorot Initialization | `sqrt(2 / (fan_in + fan_out))` scaling |
| 6 | He/Kaiming Initialization | `sqrt(2 / fan_in)` scaling |
| 7 | Orthogonal Initialization | QR decomposition |
| 8 | Comparative Analysis | All four strategies side by side |
| 9 | Experimental Study | Second dataset, 10 random seeds per strategy |

A perceptron built from scratch — no `sklearn.linear_model.Perceptron` — then used to
study how weight initialisation affects training.

**Datasets.** Breast Cancer Wisconsin (Diagnostic) for Tasks 1–8 and Wine for Task 9, both
from the UCI ML Repository and bundled with scikit-learn, so the notebook runs offline and
reproduces exactly.

**A note on convergence.** Breast Cancer is not linearly separable, so the perceptron never
reaches zero training error and the convergence theorem does not apply. The notebook
reports both the textbook criterion and a practical 3% training-error threshold, and
explains the difference. Wine (cultivar 0 vs the rest) *is* separable, so all 40 runs in
Task 9 genuinely converge.

**Headline result.** Averaged over 10 seeds on Wine, mean epochs to convergence order
exactly by starting weight norm — Gaussian 3.4, Orthogonal 7.9, Xavier 9.8, He 10.4 —
while mean test accuracy varies by less than 0.01. Initialisation changed how *fast*
training got there, not *where* it ended up. Within-strategy accuracy variance across
seeds is larger than the between-strategy spread, so no method is meaningfully more
accurate than another on this problem.

---

## Requirements

| Lab | Needs |
|---|---|
| 01 | Python standard library only |
| 02 | NumPy |
| 03 | NumPy, Matplotlib, scikit-learn, pandas |

```bash
pip install numpy matplotlib scikit-learn pandas
```

## Running

```bash
git clone https://github.com/zainulwahaj/ANN-lab.git
cd ANN-lab
jupyter notebook
```

Open any notebook and run all cells with **Cell → Run All**, or read the saved outputs
straight from GitHub.
