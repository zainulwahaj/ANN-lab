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
| 04 | Self-Organizing Map (SOM) | [`Lab04_Self_Organizing_Map.ipynb`](Lab04_Self_Organizing_Map.ipynb) |
| 05 | Learning Vector Quantization (LVQ) | [`Lab05_Learning_Vector_Quantization.ipynb`](Lab05_Learning_Vector_Quantization.ipynb) |

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

## Lab 04 — Self-Organizing Map (SOM)

| # | Task | Topics Covered |
|---|------|----------------|
| 1 | Data and Weight Setup | 200 random colours, 10 x 10 grid of 3-value weight vectors, `plt.imshow()` |
| 2 | Distance Calculation | `euclidean_distance()`, vectorized distance to every neuron (no loops) |
| 3 | Finding the Winner (BMU) | `find_bmu()`, marking the BMU, hit map of all samples |
| 4 | Neighborhood Function | Gaussian and bubble neighbourhoods for different radii |
| 5 | One Weight Update Step | `update_weights()`, before/after maps, change in weights |
| 6 | Training Loop | `train_som()` with exponentially decaying learning rate and radius |
| 7 | Measuring Training Quality | Quantization error recorded during training |
| 8 | Parameter Experiments | Iterations, grid size and learning rate compared |
| 9 | Mini Project with Your Own Data | Red / green / blue clusters, grouping samples by BMU |

A SOM written from scratch with NumPy: find the best matching unit for a random colour, pull
it and its neighbours towards the colour, and shrink the learning rate and neighbourhood
radius as training goes on. The trained 10 x 10 map turns random noise into smooth colour
gradients. `task6_result.png` (initial vs trained map) is saved by the notebook.

**A note on quantization error.** On the uniformly random colours of Tasks 1-8 the error
*rises* slightly after training (0.066 to 0.088), because 100 random neurons already cover the
RGB cube well and a SOM deliberately trades some accuracy for an ordered map. On the clustered
red/green/blue data in Task 9 the error falls by about 95%, and the hit map shows three
separate groups.

---

---

## Lab 05 - Learning Vector Quantization (LVQ)

| # | Task | Topics Covered |
|---|------|----------------|
| 1 | The LVQ Algorithm from the Lab Manual | The manual's solved activity, run and debugged |
| 2 | Dataset Loading and Preprocessing | Wine (UCI), stratified split, `StandardScaler` |
| 3 | Distance and the Winning Prototype | `euclidean_distance()`, `find_winner()`, checked against a plain loop |
| 4 | Prototype Initialization | First-sample, class-mean and random-per-class schemes on a PCA plot |
| 5 | The LVQ1 Update Rule | Reward and punish, step size against alpha, movement traced in 2-D |
| 6 | Training Loop | `train_lvq()` with linear learning-rate decay and per-epoch shuffling |
| 7 | Classification and Evaluation | Accuracy, classification report, confusion matrix, 1-NN baseline |
| 8 | Hyperparameter Experiments | Learning rate, epochs, prototypes per class, and a grid heatmap |
| 9 | Mini Project with Your Own Data | UCI Handwritten Digits, prototypes shown as images, summary report |

LVQ written from scratch with NumPy. Prototype vectors compete to be nearest to each
training sample; the winner is pulled towards the sample when their labels agree and
pushed away when they do not, with the learning rate decaying to zero over training.

**Datasets.** Wine for Tasks 2-8 and Optical Recognition of Handwritten Digits for
Task 9, both from the UCI ML Repository and bundled with scikit-learn, so the notebook
runs offline and reproduces exactly.

**A note on the lab manual's listing.** The solved activity printed in the manual does
not run. Task 1 reproduces it with three bugs fixed. `winner()` compares `D0 > D1` and
so returns the *farther* prototype. `update()` tests `if actual -- j:`, which is two
unary minus signs rather than a comparison, and refers to a lower-case `j` that is never
defined. The update loop runs over `range(len(weights))`, the number of prototypes,
instead of the number of features, so two of the four weights never move. Each fix is
explained in the cell next to it.

**Headline result.** On Wine, three prototypes - one per class - reach 94.44% test
accuracy against 96.30% for 1-NN, while storing 3 vectors instead of 124. The
hyperparameter grid in Task 8 peaks at 100% with 3 prototypes per class at alpha 0.3. On
Digits, 30 prototypes reach 96.30% against 98.89% for 1-NN while storing 42x less.
Trading a couple of points of accuracy for a 40x smaller model is the whole argument for
LVQ, and because every prototype is a point in the original feature space, the Digits
prototypes fold back into 8x8 images and read as averaged handwritten digits.

## Requirements

| Lab | Needs |
|---|---|
| 01 | Python standard library only |
| 02 | NumPy |
| 03 | NumPy, Matplotlib, scikit-learn, pandas |
| 04 | NumPy, Matplotlib |
| 05 | NumPy, Matplotlib, scikit-learn |

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
