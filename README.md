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

Every lab is a fully executed Jupyter notebook. Each lettered part is solved in its own
code cell, directly under the question it answers, with its output saved — so the results
are visible on GitHub without running anything.

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

Covers variables and operators, the core built-in containers and how mutability differs
between them, indexing and slicing, string handling, conditionals and loops, functions
with default arguments and reference semantics, and object-oriented programming with
inheritance and method overriding.

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

Covers vector and matrix creation, element-wise arithmetic, dot products and why array
shapes have to align, reshaping rules, indexing and slicing of sub-matrices, reproducible
random generation with seeds, and transposition.

Random results are seeded so the saved outputs reproduce exactly on a re-run.

---

## Requirements

Lab 01 uses only the Python standard library. Lab 02 additionally needs NumPy:

```bash
pip install numpy
```

## Running

```bash
git clone https://github.com/zainulwahaj/ANN-lab.git
cd ANN-lab
jupyter notebook
```

Open either notebook and run all cells with **Cell → Run All**, or read the saved outputs
straight from GitHub.
