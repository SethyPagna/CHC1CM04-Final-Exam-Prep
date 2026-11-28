# BI4 — Data Mining and Their Applications (1): Regression, Classification, Decision Trees (teaching week 9)

> **Built from:** all 125 slides of "Week 8&9 - BI&CRM SS-25-26 Lecture BI4.pdf", text and pictures.
> **Exam weight:** the highest of any lecture. An **ID3 decision-tree** question appeared in the last two finals: 2024-25 Q24 (20 marks, choose the root for the 14-record buys_computer table) and 2025-26 Q23 (20 marks: information gain of one attribute, choose the root and draw the first split, explain overfitting and two fixes). Linear regression and logistic regression have **not** yet been set as long questions, so they are strong candidates for a short question this year.

---

## The lecture in one minute

- **Data mining** = finding patterns in large data with statistical, mathematical and computational techniques. Four types: **classification, regression, clustering, association**.
- **Regression** predicts a **number**. **Classification** predicts a **category**. Both learn from labelled data (supervised). **Clustering** has no labels (unsupervised).
- **Simple linear regression** fits a straight line `y = b0 + b1·x` by **least squares**: `b1 = Sxy / Sxx`, `b0 = ȳ − b1·x̄`. Put time on the x-axis and the same line gives a **forecast**.
- **Logistic regression** is a **classifier**. It pushes the linear score through the **sigmoid** `1 / (1 + e^(−z))` to get a probability between 0 and 1, then rounds at 0.5.
- A **decision tree** asks one attribute question per node. **ID3** picks, at every node, the attribute with the **highest information gain** (biggest drop in **entropy**).
- Trees **overfit**. Fix by **pruning**: pre-pruning (stop early) or post-pruning (subtree replacement, subtree raising).

| Technique | Predicts | Supervised? | Key formula |
|---|---|---|---|
| Linear regression | Continuous value | Yes | `b1 = Sxy/Sxx`, `b0 = ȳ − b1x̄` |
| Logistic regression | Class (via probability) | Yes | `P(Y=1|X) = 1/(1 + e^−(b0 + b1x))` |
| Decision tree (ID3) | Class | Yes | `H = −Σ p·log2 p`, `Gain = H(parent) − Σ (|Ci|/|C|)·H(Ci)` |
| Clustering (lecture BI5) | Groups | No | Distance to centroid |

---

## Words you need

| Term | Slide wording | In plain words |
|---|---|---|
| **Data mining** | "the process of discovering patterns, trends, and useful information from large sets of data using statistical, mathematical, and computational techniques" | Digging useful patterns out of big data |
| **Classification** | "predicts discrete labels or categories (e.g., yes/no, spam/not spam)" | Put each case into a class |
| **Regression** | "predicts continuous values (e.g., price, temperature)" | Predict a number |
| **Clustering** | "group similar data points together into clusters"; "does not use predefined labels"; "a method of unsupervised learning" | Find natural groups |
| **Dependent variable (y)** | "the response variable or the predicted variable" | What you want to predict |
| **Independent variable (x)** | "the explanatory variable or the predictor variable" | What you use to predict |
| **Residual eᵢ** | "distance of points from line" | Actual y minus predicted y |
| **Least squares** | "minimizes sum of square residuals" | The line with the smallest total squared error |
| **Overfitting** | "we model the training data too well … modelling noise" | Memorising instead of learning |
| **Underfitting** | "the model is too general" | Too simple to capture the pattern |
| **Sigmoid / logistic function** | "S-shaped curve that can take any real-valued number and map it into a value between 0 and 1, but never exactly at those limits" | Squashes any number into a probability |
| **Entropy** | "the measure of disinformation" | How mixed-up the classes are (0 = pure) |
| **Information gain** | "the expected reduction in entropy caused by partitioning on this attribute" | How much an attribute tidies the classes |
| **Pruning** | "identify and remove branches that reflect noise or outliers" | Cutting a tree back so it generalises |

---

## Part 1 — Data mining and its four techniques (slides 2–5) ★

- **Classification and regression** "aim to make predictions based on input features".
- **Clustering** "finds hidden patterns or groupings, whereas classification and regression make predictions based on known outcomes".
- **Association and correlation analysis:** frequent patterns — "what items are frequently purchased together in your Walmart?" A typical rule: **Diaper → Beer [0.5%, 75%]** = (support, confidence). The slide warns about **association, correlation vs. causality**.

**The 2023-24 final Q6 asked "how can data mining be applied to …" — match the task to the technique:**

| Business question | Technique |
|---|---|
| Which items do customers tend to purchase together? | **Association rule mining** (market basket analysis) |
| Frequent-flier incentives for groups of passengers | **Clustering** (segment passengers), then target each cluster |
| Approve / reject a loan application | **Classification** (decision tree, logistic regression) |
| Sales forecasting from time-based patterns | **Regression / time-series forecasting** |
| Charts, plots and graphs for data presentation | **Data visualization / descriptive analytics** (dashboards) |

---

## Part 2 — Regression (slides 6–34) ★★

### What regression is (slides 7–11)

- Correlation tells you variables are related. Regression gives "a mathematical model": **y = F(x)**, like the physical law F = ma.
- **y** = dependent / response / predicted variable. **x** = independent / explanatory / predictor variable. "Usually we take the variable which we can control more easily as the independent variable."
- **Fitting** = "find the parameters in the model". A linear function has **2 parameters**.
- Slide examples (y is a function of x): time to fill a vending machine ← number of cases; mean piglet weight ← piglet (litter) size; tractor maintenance cost ← age of tractor.

### Simple linear regression and least squares ★★ (slides 10, 15–18)

```
Model:        y  = b0 + b1·x              b0 = intercept, b1 = slope
One point:    yᵢ = b0 + b1·xᵢ + eᵢ        eᵢ = residual (random error)
Goal:         choose b0, b1 to minimise  Σ eᵢ²  =  Σ ( yᵢ − (b0 + b1·xᵢ) )²

Solution:     b1 = Sxy / Sxx          b0 = ȳ − b1·x̄

              Sxx = Σ (xᵢ − x̄)²          =  Σx²  − (Σx)² / n       "sums of squares of x"
              Sxy = Σ (xᵢ − x̄)(yᵢ − ȳ)   =  Σxy  − (Σx)(Σy) / n    "sums of cross products of x and y"
```

- Method: "take the derivative with respect to b0 and with respect to b1, set the two resulting equations equal to zero and solve". The slides skip the derivation.
- Simplest assumption: residuals are independent and `eᵢ ~ N(0, σ²)`.

**In plain words:** b1 says "when x goes up by 1, y changes by b1". b0 is the value of y when x = 0. The least-squares line always passes through the point (x̄, ȳ).

### Slide example (slides 19–20)

Repair time y (minutes) vs number of components x for 14 computers → **b1 = 15.20, b0 = 7.71**, so `y = 7.71 + 15.20x`. Each extra component adds about 15.2 minutes; a repair with 5 components should take 7.71 + 15.20 × 5 = 83.7 minutes.

### Steps in a regression analysis ★ (slide 21)

1. **Examine the scatterplot.** Does it look linear? Any outliers? Need a transformation?
2. If a line looks right, **estimate the parameters** (method of least squares).
3. **Validate** the line. Examine the residuals: is there evidence of a more complicated relationship (say a polynomial)?

### Validation (slide 22) ★

"We need to know how well our models will perform." **Split** the data into **training data** (build the model) and **test data** (pass through the model). "We should **never test a model on the same data that was used to build it** — this would be confirming a hypothesis with the same hypothesis."

### Curve fitting (slides 23–25)

"A more general term than regression": fitting different types of curve.

| Type | Form |
|---|---|
| Polynomial | `y = b0 + b1x + b2x²` (b2 = quadratic coefficient) |
| Sinusoidal (nonlinear) | `y = b0·sin(b1x + b2x²)` |
| Exponential (nonlinear) | `y = b0·b1^x` |

### Using regression for decisions and forecasting ★★ (slides 26–34)

- Knowing the relationship supports better decisions: an electricity provider adjusts generation from the **temperature** → "better utilize the resources, maximize profit".
- If one variable is **time** (usually x), regression finds the trend = **forecasting**.
- **Time series** data are common: finance (stock prices), e-commerce (page views, new users, searches), business (transactions, revenue, inventory).
- Aim of forecasting: "make the best possible predictions for future events, minimise errors, and provide the most reliable information possible". "There is no single best way of forecasting." It "does not (necessarily) use the most sophisticated and obscure mathematics".

**Worked forecast (slides 31–34) — do this by hand:**

| Month x | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| Price y | 5.3 | 6.4 | 7.5 | 5.6 | 9.7 | 10.2 |

1. n = 6; Σx = 21; Σy = 44.7; x̄ = 3.5; ȳ = 7.45.
2. Σx² = 1 + 4 + 9 + 16 + 25 + 36 = 91 → Sxx = 91 − 21²/6 = 91 − 73.5 = **17.5**.
3. Σxy = 5.3 + 12.8 + 22.5 + 22.4 + 48.5 + 61.2 = 172.7 → Sxy = 172.7 − (21 × 44.7)/6 = 172.7 − 156.45 = **16.25**.
4. b1 = 16.25 / 17.5 = **0.9286**. b0 = 7.45 − 0.9286 × 3.5 = **4.20**.
5. Line: `price = 4.20 + 0.93 × month`. Month 7: 4.20 + 0.9286 × 7 = **10.7** — the slide's answer ("the estimated price should be around 10.7").

**Table layout that earns the method marks:** make columns x, y, x², xy (or x − x̄, y − ȳ, their product, and (x − x̄)²), total each column, then substitute.

---

## Part 3 — Classification basics (slides 35–40) ★

- "Trying to predict a 'class' (categorical data) given historical training data." The class labels in the training data act "as a teacher". The classifier then predicts the class of an **unseen sample**; it must **generalize**.
- Evaluate by **accuracy**; "false negative and false positive rates are vital".
- Class labels usually come from an expert. Some data are "kept back as test/validation data".
- "**Imbalanced classes cause problems**" (fraud detection: few fraudsters, many normal cases).

**Overfitting vs underfitting ★★ (slides 39–40)**

| | Underfitting | Appropriate fitting | Overfitting |
|---|---|---|---|
| Picture | A straight line through a curved boundary | A smooth curve | A wiggly line around every point |
| Slide caption | "too simple to explain the variance" | — | "force-fitting — too good to be true" |
| Training accuracy | Low | Good | Very high |
| Test accuracy | Low | Good | **Low** |

---

## Part 4 — Logistic regression (slides 41–68) ★★

### What it is

- "A **classification** approach." Linear regression predicts a continuous value; logistic regression "predicts a class (e.g. disease or healthy) or binary outcome ('Y/N', '1/0')".
- Both belong to the family "**general linear model**".
- Relationship between "one dependent **binary** variable and one or more nominal, ordinal, interval or ratio-level independent variables".
- "Remember: though the name of the algorithm carries regression, it is used for classification."

### Three types (slide 44)

| Type | Response | Example |
|---|---|---|
| **Binary** | Two outcomes | Spam or not |
| **Multinomial** | Three or more categories **without** ordering | Preferred food: veg, non-veg, vegan |
| **Ordinal** | Three or more categories **with** ordering | Movie rating 1 to 5 |

### From linear to logistic (slides 49–55)

A company e-mails a discount offer; the outcome is Action (Y/N) against Age. A straight line through 0/1 data gives predictions **below 0 and above 1**, which cannot be probabilities. "It is necessary to restrict the value range for the prediction between 0 and 1" → use the logistic function.

```
Linear score:      z  = b0 + b1·x1 + … + bk·xk
Sigmoid:           f(z) = 1 / (1 + e^(−z))
Probability:       P(Y = 1 | X) = 1 / (1 + e^(−(b0 + b1·x1)))
                   P(Y = 0 | X) = 1 − P(Y = 1 | X)
Same thing as:     ln( p / (1 − p) ) = b0 + b1·x          (log-odds are linear in x)
Classify:          p ≥ 0.5 → class 1,   p < 0.5 → class 0
```

The S-curve passes through **0.5 when z = 0**, approaches 1 as z → +∞ and 0 as z → −∞.

**Probability reading (slides 56–63):** P(gender = male | height = 160) = 0.8 → "very likely to be male" → round to 1. P(male | height = 130) = 0.4 → "not likely". On the age example the curve gives p̂ = 0.7%, 23%, 85%, 99.4% for ages 20, 30, 40, 50 → predictions 0, 0, 1, 1.

### Worked example ★★ (slides 64–65)

Coefficients b0 = −100, b1 = 0.6. Is a person of height 150 cm male?

1. z = −100 + 0.6 × 150 = **−10**.
2. p = e^(−10) / (1 + e^(−10)) = 1 / (1 + e^(10)) = **0.0000454**.
3. p < 0.5 → **not male** ("a probability of near zero that the person is a male").

The two forms `e^z / (1 + e^z)` and `1 / (1 + e^(−z))` are the same function.

**Calculator:** compute z first. Then `1 ÷ (1 + e^(−z))` using the `eˣ` key (SHIFT + ln). Quick checks: z = 0 → 0.5; z = 1 → 0.731; z = −1 → 0.269; z = 2 → 0.881.

### Preparing data (slide 66)

- **Binary output variable** — it predicts the probability of the default class, snapped to 0 or 1.
- **Remove noise** — logistic regression "assumes no error in the output variable (y)"; remove outliers and possibly misclassified instances.

### Advantages and disadvantages ★ (slides 67–68)

| Advantages | Disadvantages |
|---|---|
| Performs well when the dataset is **linearly separable** | Assumes **linearity** between the independent variables and the **log-odds** of the dependent variable |
| **Less prone to over-fitting** (but can overfit in high-dimensional datasets) | If **observations < features**, it should not be used — may overfit |
| Gives how relevant a predictor is (**coefficient size**) and its **direction** (positive or negative) | Can only predict **discrete** functions: the dependent variable is restricted to a discrete set |
| **Easier to implement, interpret, very efficient to train** | |

---

## Part 5 — Decision trees (slides 69–86) ★★

### Structure (slides 70–71)

"A flow-chart-like tree structure":

- **Internal node** = a **test on an attribute**.
- **Branch** = an **outcome** of the test (one branch per value).
- **Leaf node** = a **class label** (or class distribution).

"Decision trees represent rules, which can be understood by humans." Classify by "starting at the root of the tree and moving through it until a leaf node".

### Key requirements (slide 72)

1. **Attribute-value description** — each case is described by a fixed set of attributes (hot, mild, cold).
2. **Predefined classes** — the target has discrete/categorical values.
3. **Sufficient data** — enough training cases.

### Two phases (slide 73) ★

1. **Tree construction** — all training examples start at the root; partition them recursively on selected attributes.
2. **Tree pruning** — "identify and remove branches that reflect noise or outliers".

### The credit-risk example (slides 74–80)

14 loan records. Attributes: credit history (bad / unknown / good), debt (high / low), collateral (none / adequate), income ($0–15k / $15–35k / over $35k). Class: **risk** (high / moderate / low).

| No. | Risk | Credit history | Debt | Collateral | Income |
|---|---|---|---|---|---|
| 1 | high | bad | high | none | $0–15k |
| 2 | high | unknown | high | none | $15–35k |
| 3 | moderate | unknown | low | none | $15–35k |
| 4 | high | unknown | low | none | $0–15k |
| 5 | low | unknown | low | none | over $35k |
| 6 | low | unknown | low | adequate | over $35k |
| 7 | high | bad | low | none | $0–15k |
| 8 | moderate | bad | low | adequate | over $35k |
| 9 | low | good | low | none | over $35k |
| 10 | low | good | high | adequate | over $35k |
| 11 | high | good | high | none | $0–15k |
| 12 | moderate | good | high | none | $15–35k |
| 13 | low | good | high | none | over $35k |
| 14 | high | bad | high | none | $15–35k |

- A random choice of splitting attributes makes a **huge tree**: "hard to understand" and "larger trees are typically less accurate than smaller trees".
- The good tree uses only 3 of the 4 attributes; "'Collateral' is not a discriminating attribute".
- **Occam's Razor:** "Given a number of competing hypotheses, the simplest one is preferable."

### ID3 ★★ (slides 81–86)

- **ID3** (the slide expands it as "Interactive Dichotomize 3"), by **Ross Quinlan, 1979**. All tree algorithms share a structure; "the difference lies in how we select the attributes".
- **Basic idea (slide 82):**
  1. Choose the **best attribute** to split the remaining instances; make it a decision node.
  2. **Repeat recursively** for each child.
  3. **Stop when:** (a) all the instances have the **same target value**; (b) there are **no more attributes**; (c) there are **no more instances**.
- **Pseudocode (slide 83):** if all entries are in the same class → return a leaf with that class; else if no properties are left → return a leaf labelled with the disjunction of the classes; else select a property P, make it the root, delete P from the properties, and for each value V of P create a branch and call the function again on the examples with that value.
- "Finding the **minimal** decision tree consistent with the data is **NP-hard**." The recursive algorithm is "a **greedy heuristic** search for a simple tree, but **cannot guarantee optimality**".
- "ID3 splits attributes based on their **entropy**."

---

## Part 6 — Entropy and information gain (slides 87–111) ★★

### Entropy (slides 88–97)

- Symbol probability: `P(sᵢ) = mᵢ / M` (count of the symbol ÷ message length).
- **Self-information** of an event A: `−log2 P(A)`. Rarer symbol → more information. Independent symbols add.
- **Entropy** = average self-information:

```
H = Σ P(sᵢ)·log2( 1 / P(sᵢ) ) = − Σ P(sᵢ)·log2 P(sᵢ)        (bits)
```

- Entropy is "the lower bound on the average number of bits needed to code a symbol": H ≤ average code length.

| Slide example | Entropy |
|---|---|
| Fair coin {0.5, 0.5} | −(½ × −1 + ½ × −1) = **1 bit** |
| {0.25, 0.75} | 0.25 × 2 + 0.75 × 0.415 = **0.811** |
| {0.25, 0.25, 0.25, 0.25} | **2** |
| {1, 0, 0, 0} | **0** |
| {0.25, 0.25, 0.5, 0} | **1.5** |
| {0.125, 0.125, 0.25, 0.5} | **1.75** |

**In plain words:** entropy is **0** when everything is one class (no surprise), and **largest** when the classes are evenly mixed (1 bit for two classes, log2 k for k classes). Treat `0 × log2 0` as 0.

**Calculator:** `log2 x = log x ÷ log 2` (or `ln x ÷ ln 2`). Keep 3–4 decimals while working; round the final answer to 2 or 3 decimals as the paper asks.

**Two-class entropy table (put it on your A4 sheet):**

| Split | H | Split | H | Split | H |
|---|---|---|---|---|---|
| 1 : 1 | 1.000 | 1 : 5 | 0.650 | 3 : 5 | 0.954 |
| 1 : 2 | 0.918 | 1 : 6 | 0.592 | 3 : 7 | 0.881 |
| 1 : 3 | 0.811 | 1 : 7 | 0.544 | 4 : 5 | 0.991 |
| 1 : 4 | 0.722 | 2 : 5 | 0.863 | 5 : 9 | 0.940 |
| 2 : 3 | 0.971 | 3 : 4 | 0.985 | pure | 0 |

### Information gain (slides 98–100)

Let C be the set of examples at a node. An attribute with n values splits C into subsets C₁ … Cₙ.

```
Expected information still needed after the split  =  Σ ( |Cᵢ| / |C| ) · H(Cᵢ)       (weighted average entropy)

Gain(A) = H(C) − Σ ( |Cᵢ| / |C| ) · H(Cᵢ)
```

"Partitions with **low entropy** lead to **high gain**." **ID3 chooses the attribute with the highest gain.**

### The slide example: root attribute ★★ (slides 101–105)

1. **Entropy of the whole table.** High 6, moderate 3, low 5 of 14:
   H = −(6/14)log2(6/14) − (3/14)log2(3/14) − (5/14)log2(5/14) = 0.524 + 0.476 + 0.531 = **1.531 bits**.
2. **Split on income.** C1 ($0–15k) = {1, 4, 7, 11} = {h, h, h, h}; C2 ($15–35k) = {2, 3, 12, 14} = {h, m, m, h}; C3 (over $35k) = {5, 6, 8, 9, 10, 13} = {l, l, m, l, l, l}.
   H(C1) = 0; H(C2) = 1.0; H(C3) = −(5/6)log2(5/6) − (1/6)log2(1/6) = 0.65.
   Weighted = (4/14)(0) + (4/14)(1.0) + (6/14)(0.65) = **0.564 bits**.
3. **Gain(income)** = 1.531 − 0.564 = **0.967 bits**.
4. Slide values for the others: gain(credit history) = 0.266, gain(debt) = 0.581, gain(collateral) = 0.756.
5. **Income has the greatest gain → ID3 selects it as the root.**

> **Check on the slide numbers.** Recomputing from the table gives gain(credit history) = 0.266 ✔, gain(debt) = **0.063** and gain(collateral) = **0.206**. The slide's 0.581 and 0.756 are misprints carried over from the source textbook. The conclusion (income is the root) does not change. In an exam, **use whatever values the paper gives you**; if you must compute them yourself, trust your own working.

### Internal nodes (slides 106–111)

- **Branch $0–15k:** {1, 4, 7, 11} are all high → make it a **leaf: high risk**.
- **Branch $15–35k:** {2, 3, 12, 14}, H = 1.0. Try credit history: unknown = {2, 3} (h, m → H = 1.0), bad = {14} (H = 0), good = {12} (H = 0) → weighted = (2/4)(1.0) = 0.5 → **gain = 0.5**. Debt: 1.0 − (3/4)(0.92) − (1/4)(0) = **0.31**. Collateral: 1.0 − 1.0 = **0**. → choose **credit history**.
- Loop over the remaining branches to finish.

**Final tree:**

```
income?
├─ $0–15k ────────► HIGH risk
├─ $15–35k ───────► credit history?
│                    ├─ unknown ► debt?
│                    │              ├─ high ► HIGH risk
│                    │              └─ low  ► MODERATE risk
│                    ├─ bad ─────► HIGH risk
│                    └─ good ────► MODERATE risk
└─ over $35k ─────► credit history?
                     ├─ unknown ► LOW risk
                     ├─ bad ─────► MODERATE risk
                     └─ good ────► LOW risk
```

New applicant: income $0–15k, credit history bad, debt low, collateral adequate → follow the first branch → **high risk**.

**Tree → rule (slide 123):** "If income is between $0 to $15k then it is high risk."

---

## Part 7 — Continuous attributes, overfitting and pruning (slides 112–124) ★★

### Continuous attributes (slide 112)

Discretise with **thresholds**. Method: sort the examples by the attribute; the **candidate thresholds are the mid-points between neighbouring values where the class label changes**.

| Temperature | 40 | 48 | 60 | 72 | 80 | 90 |
|---|---|---|---|---|---|---|
| PlayTennis | No | No | Yes | Yes | Yes | No |

Label changes between 48 and 60 → (48 + 60)/2 = **54**; and between 80 and 90 → **85**. Add the tests (Temperature < 54), (Temperature > 54), … to the attribute set.

### Overfitting in trees ★★ (slides 113–114)

- "ID3 grows each branch of the tree just deeply enough to **perfectly classify the training examples**."
- Trouble when (1) there is **noise** in the data; (2) the **number of training examples is too small** to be representative.
- "A **deeper tree** is more likely to have overfit." The graph: as the number of nodes grows, accuracy on **training** data keeps rising (to about 0.87) while accuracy on **test** data peaks early (about 0.75) and then falls (to about 0.69).

### Pruning ★★ (slides 115–121)

| | Pre-pruning (forward pruning) | Post-pruning (backward pruning) |
|---|---|---|
| When | **During** building: decide when to stop adding attributes (possibly from their information gain) | **After** the full tree is built |
| How | Fix the **depth** of the tree; check the **number of instances** in a subset | **Subtree replacement**; **subtree raising** |
| Problem | "Sometimes attributes individually do not contribute much to a decision, but combined, they may have a significant impact" — you may stop too early | More computation |

- **Subtree replacement:** "entire subtree is replaced by a single leaf node". Done when there are few instances or noise. "Generalizes the tree a little more, but may increase accuracy." In practice: test the accuracy with the subtree replaced and keep the replacement "when the accuracy is not worse than before".
- **Subtree raising:** "entire subtree is raised onto another node". Not discussed in detail — "not clear whether this is really worthwhile (as it is very time consuming)".

### Decision boundaries (slide 122)

"Decision trees divide the feature space into **axis-parallel rectangles**, and label each rectangle with one of the classes."

### Strengths and weaknesses ★ (slides 123–124)

| Strengths | Weaknesses |
|---|---|
| Generate **understandable rules** | **Not suitable for prediction of continuous attributes** |
| Classify **without much computation** | Perform poorly with **many classes and small data** |
| Handle **continuous and categorical** independent variables | **Computationally expensive to train** (sorting every candidate field at each node; searching combinations; pruning compares many sub-trees) |
| Show clearly **which fields are most important** | Do not treat **non-rectangular regions** well |

---

## How this lecture is examined

### The ID3 method — seven steps to copy

1. Count the classes in the whole set S. Compute **H(S)**.
2. For the attribute, list each value with its class counts (a small table).
3. Compute the entropy of **each** subset.
4. **Weighted average** = Σ (subset size / total) × subset entropy.
5. **Gain = H(S) − weighted average.**
6. Repeat for every attribute (or use the gains given). **Largest gain = root.**
7. Draw the root, one branch per value, and write the instance IDs under each branch. A pure branch becomes a leaf.

### 2025-26 final Q23 (20 marks) — full model answer ★★

| ID | Weather | Temperature | Humidity | Go hiking |
|---|---|---|---|---|
| 1 | Sunny | Hot | High | No |
| 2 | Sunny | Hot | High | No |
| 3 | Overcast | Hot | High | Yes |
| 4 | Rainy | Mild | High | Yes |
| 5 | Rainy | Cool | Normal | Yes |
| 6 | Rainy | Cool | Normal | No |
| 7 | Overcast | Cool | Normal | Yes |
| 8 | Sunny | Mild | High | No |

**(a) Information gain of Temperature (10 marks)**

1. Whole set: 4 Yes, 4 No. H(S) = −(4/8)log2(4/8) − (4/8)log2(4/8) = **1**.
2. Subsets:

| Temperature | IDs | Yes | No | Entropy |
|---|---|---|---|---|
| Hot | 1, 2, 3 | 1 | 2 | −(1/3)log2(1/3) − (2/3)log2(2/3) = 0.918 |
| Mild | 4, 8 | 1 | 1 | 1 |
| Cool | 5, 6, 7 | 2 | 1 | 0.918 |

3. Weighted entropy = (3/8)(0.918) + (2/8)(1) + (3/8)(0.918) = 0.344 + 0.250 + 0.344 = **0.939**.
4. **Gain(S, Temperature) = 1 − 0.939 = 0.061 ≈ 0.06.**

**(b) Root and first split (6 marks).** Given Gain(Weather) = 0.656 and Gain(Humidity) = 0.046; Temperature = 0.06. The largest is **Weather** → root.

```
                 Attribute: Weather
        ┌───────────────┼───────────────┐
   (Value: Sunny)  (Value: Overcast)  (Value: Rainy)
  Instance IDs:     Instance IDs:     Instance IDs:
    1, 2, 8            3, 7             4, 5, 6
  (all No → leaf)   (all Yes → leaf)  (2 Yes, 1 No → split again)
```

Check: Sunny {No, No, No} H = 0; Overcast {Yes, Yes} H = 0; Rainy {Yes, Yes, No} H = 0.918 → weighted = (3/8)(0.918) = 0.344 → gain = 0.656 ✔.

**(c) Training accuracy 90%, test accuracy 60% (4 marks)**
1. The tree is **overfitting**: it has modelled the training data too well, including noise, so it does not generalise to unseen data. (1)
2. Cause: ID3 grows each branch deep enough to classify the training examples perfectly; this happens with noisy data or too few training examples (a deeper tree is more likely to overfit). (1)
3. Fix 1 — **pre-pruning**: stop growing early, e.g. fix the maximum depth or require a minimum number of instances in a subset. (1)
4. Fix 2 — **post-pruning**: build the full tree, then apply subtree replacement (replace a subtree by a leaf when accuracy is not worse) or subtree raising. (1)

### 2024-25 final Q24 (20 marks) — full model answer ★★

14 records, class buys_computer: 9 yes, 5 no.

**H(S)** = −(9/14)log2(9/14) − (5/14)log2(5/14) = 0.410 + 0.530 = **0.940**.

| Attribute | Value: (yes, no) → entropy | Weighted entropy | Gain |
|---|---|---|---|
| **age** | ≤30: (2, 3) → 0.971; 31…40: (4, 0) → 0; >40: (3, 2) → 0.971 | (5/14)(0.971) + (4/14)(0) + (5/14)(0.971) = 0.694 | **0.246** |
| income | high: (2, 2) → 1; medium: (4, 2) → 0.918; low: (3, 1) → 0.811 | (4/14)(1) + (6/14)(0.918) + (4/14)(0.811) = 0.911 | 0.029 |
| student | no: (3, 4) → 0.985; yes: (6, 1) → 0.592 | (7/14)(0.985) + (7/14)(0.592) = 0.788 | 0.151 |
| credit_rating | fair: (6, 2) → 0.811; excellent: (3, 3) → 1 | (8/14)(0.811) + (6/14)(1) = 0.892 | 0.048 |

**age has the highest information gain (0.246) → age is the root.** Branch 31…40 is pure (all yes) → leaf "yes". Branches ≤30 and >40 are split again.

(With more decimals the gains are 0.2467, 0.0292, 0.1518, 0.0481. Small rounding differences are fine.)

### Other likely questions

**Q (6 marks). Sales y (units) for advertising spend x (HK$'000): (1, 3), (2, 5), (3, 4), (4, 7), (5, 8). Fit the least-squares line and predict sales for x = 6.**
1. x̄ = 3, ȳ = 5.4. (1)
2. Sxx = (−2)² + (−1)² + 0² + 1² + 2² = 10. (1)
3. Sxy = (−2)(−2.4) + (−1)(−0.4) + (0)(−1.4) + (1)(1.6) + (2)(2.6) = 12. (1)
4. b1 = 12/10 = 1.2. (1)
5. b0 = 5.4 − 1.2 × 3 = 1.8 → y = 1.8 + 1.2x. (1)
6. x = 6 → y = 1.8 + 7.2 = 9.0 units. (1)

**Q (4 marks). A logistic model has b0 = −4 and b1 = 0.1 (x = age). Find P(buy) for a 50-year-old and classify.**
1. z = −4 + 0.1 × 50 = 1. (1)
2. P = 1 / (1 + e^(−1)). (1)
3. = 1 / 1.3679 = 0.73. (1)
4. 0.73 ≥ 0.5 → predict "buy" (class 1). (1)

**Q (4 marks). Compare linear and logistic regression.**
1. Linear predicts a continuous numeric value; logistic predicts a class / binary outcome. (1)
2. Linear output is unbounded; logistic uses the sigmoid to keep the output between 0 and 1 (a probability). (1)
3. Linear is a regression technique; logistic, despite its name, is a classification technique. (1)
4. Both are part of the general linear model family and combine inputs linearly with coefficients. (1)

**Q (3 marks). State the three stopping conditions of the basic decision-tree algorithm.** All instances have the same target value; no more attributes; no more instances.

---

## Easy to mix up

| A | B | How to tell them apart |
|---|---|---|
| Classification | Regression | Category vs number |
| Classification | Clustering | Labels given (supervised) vs no labels (unsupervised) |
| Linear regression | Logistic regression | Predicts a value vs predicts a class through a probability |
| b0 | b1 | Intercept vs slope |
| Sxx | Sxy | Squares of x vs cross products of x and y |
| Entropy | Information gain | Messiness of one set vs **reduction** in messiness after a split |
| Weighted entropy | Gain | Gain = H(parent) **minus** weighted entropy. Do not stop at the weighted entropy |
| High entropy | High gain | You want **low** entropy in the children → **high** gain |
| Pre-pruning | Post-pruning | Stop early while building vs cut back after building |
| Subtree replacement | Subtree raising | Subtree → one leaf vs subtree moved up onto another node |
| Overfitting | Underfitting | Train high / test low vs both low |
| Multinomial logistic | Ordinal logistic | Unordered categories vs ordered categories |

## Memory hooks

- Regression: "**b1 = Sxy over Sxx; b0 = y-bar minus b1 x-bar**". The line passes through (x̄, ȳ).
- Sigmoid: **z = 0 → 0.5**. Positive z → class 1. Negative z → class 0.
- Entropy: **pure = 0, fifty-fifty = 1**. Thirds (1 : 2) = 0.918. Quarters (1 : 3) = 0.811.
- ID3 loop: **"Entropy of all → entropy of each branch → weight → subtract → biggest wins."**
- ID3 stops on **"same class, no attributes, no instances"**.
- Pruning: **pre = stop early (depth, minimum instances); post = replace or raise**.
- Tree weaknesses: **C-M-E-R** = Continuous targets, Many classes/small data, Expensive training, Rectangles only.

---

## Test yourself

**Multiple choice**

1. Which technique is unsupervised? A) classification B) regression C) clustering D) logistic regression
2. In `y = b0 + b1x`, b1 is: A) the intercept B) the slope C) the residual D) the response
3. The least-squares line minimises: A) the sum of residuals B) the sum of squared residuals C) the largest residual D) Sxx
4. Logistic regression with z = 0 gives a probability of: A) 0 B) 0.27 C) 0.5 D) 1
5. A node contains 8 "yes" and 0 "no". Its entropy is: A) 0 B) 0.5 C) 1 D) 8
6. ID3 selects the attribute with: A) the highest entropy B) the lowest information gain C) the highest information gain D) the most values
7. Which is a post-pruning technique? A) fixing the tree depth B) checking the number of instances in a subset C) subtree replacement D) Occam's Razor
8. Training accuracy 95%, test accuracy 62% suggests: A) underfitting B) overfitting C) imbalanced classes D) a Type II error
9. Predicting a movie rating from 1 to 5 uses which type of logistic regression? A) binary B) multinomial C) ordinal D) linear
10. Candidate thresholds for a continuous attribute are placed: A) at the mean B) at every value C) at mid-points where the class label changes D) at the quartiles

**True / false**

1. Logistic regression is used to predict continuous values.
2. A model should be tested on the same data that was used to build it.
3. Entropy is highest when the classes are evenly mixed.
4. The recursive decision-tree algorithm guarantees the smallest possible tree.
5. In pre-pruning, the full tree is built first and then cut back.
6. Decision trees divide the feature space into axis-parallel rectangles.
7. A deeper tree is more likely to overfit.
8. Logistic regression assumes a linear relationship between the independent variables and the log-odds.

**Short questions**

1. A node has 6 "buy" and 2 "not buy". Attribute Gender splits it into Male (4 buy, 0 not) and Female (2 buy, 2 not). Compute the information gain.
2. Fit a least-squares line to (2, 11), (4, 14), (6, 20), (8, 23), (10, 27) and predict y for x = 12.
3. Give two strengths and two weaknesses of decision trees.

### Answers

**Multiple choice:** 1 **C**. 2 **B**. 3 **B** (the plain sum of residuals is always zero for the least-squares line, so it cannot be the criterion). 4 **C**. 5 **A** (pure). 6 **C**. 7 **C** (A and B are pre-pruning). 8 **B**. 9 **C** (ordered categories). 10 **C**.

**True / false:** 1 **F** (it predicts a class). 2 **F** ("never"). 3 **T**. 4 **F** (greedy heuristic; minimal tree is NP-hard; no guarantee). 5 **F** (that is post-pruning). 6 **T**. 7 **T**. 8 **T**.

**Short questions**

1. H(parent) = −(6/8)log2(6/8) − (2/8)log2(2/8) = 0.311 + 0.500 = 0.811. H(Male) = 0. H(Female) = 1. Weighted = (4/8)(0) + (4/8)(1) = 0.5. **Gain = 0.811 − 0.5 = 0.311.**
2. x̄ = 6, ȳ = 19. Sxx = 16 + 4 + 0 + 4 + 16 = 40. Sxy = (−4)(−8) + (−2)(−5) + 0 + (2)(4) + (4)(8) = 32 + 10 + 8 + 32 = 82. b1 = 82/40 = **2.05**; b0 = 19 − 2.05 × 6 = **6.7**. y = 6.7 + 2.05x. x = 12 → **31.3**.
3. Strengths (any two): understandable rules; little computation to classify; handles continuous and categorical inputs; shows which fields matter most. Weaknesses (any two): not suitable for predicting continuous attributes; poor with many classes and small data; computationally expensive to train; poor on non-rectangular regions.
