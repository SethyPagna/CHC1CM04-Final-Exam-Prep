# BI5 — Data Mining and Their Applications (2): Clustering, Association Rules, Recommender Systems (teaching week 10)

> **Built from:** all 138 slides of "Week 11 - BI&CRM SS-25-26 Lecture BI5.pdf", text and pictures.
> **Exam weight:** very high. The 2025-26 final Q24 (25 marks, the biggest question on the paper) was the **Apriori algorithm**: trace it to 2-itemsets (15), generate the rules (6), give business suggestions (4). The same paper printed the **adjusted cosine similarity** formula in its appendix, so recommender systems were examined too. **K-means** has not yet been a long question — a strong candidate. This year formulas may not be given: put support, confidence, Pearson, adjusted cosine, both prediction formulas and SSE on your A4 sheet.

---

## The lecture in one minute

- **Clustering** is **unsupervised**: find groups with **high similarity inside a cluster and low similarity between clusters**. **K-means**: pick K centroids → assign every point to the nearest centroid → move each centroid to the mean of its points → repeat until nothing changes. Choose K with the **elbow method** (plot SSE against K).
- **Association rule mining** (market basket analysis) finds rules **X → Y** from transactions. **Support** = how often X and Y occur together. **Confidence** = how often Y appears when X appears. Keep rules with support ≥ minsup **and** confidence ≥ minconf.
- **Apriori principle:** *if an itemset is frequent, all its subsets are frequent* — so if a subset is infrequent, skip every superset. Algorithm: frequent 1-itemsets → join to make candidates → prune → count → repeat. Then generate rules from each frequent itemset.
- **Recommender systems** predict items a user may like. Three basic types: **content-based** (more of what I liked), **collaborative filtering** (what similar people liked), **knowledge-based** (what fits my stated needs); **hybrid** mixes them.
- **Collaborative filtering:** **user-based** (find similar users with **Pearson correlation**) or **item-based** (find similar items with **adjusted cosine similarity**). Problems: **sparsity** and **cold start**.

| Topic | You must be able to | Formula |
|---|---|---|
| K-means | Run 1–3 iterations by hand; explain elbow | Euclidean distance; centroid = mean; `SSE = Σ Σ dist(x, c)²` |
| Apriori | Build C1 → L1 → C2 → L2 → …; list rules with confidence | `sup(X) = count(X)/N`; `conf(X→Y) = count(X∪Y)/count(X)` |
| User-based CF | Compute Pearson similarity and a predicted rating | See Part 9 |
| Item-based CF | Compute adjusted cosine similarity and a predicted rating | See Part 10 |

---

## Words you need

| Term | Slide wording | In plain words |
|---|---|---|
| **Clustering** | "an unsupervised learning problem … identify distinct groups (called clusters) based on some notion of similarity" | Grouping without labels |
| **Centroid** | "cluster centers called centroids" | The middle (mean) point of a cluster |
| **K** | "a parameter of the algorithm which specifies the desired number of clusters" | How many groups you ask for |
| **SSE** | "the sum of the squared distance between each member of the cluster and its centroid" | Total tightness of the clusters (smaller = tighter) |
| **Itemset / k-itemset** | "a collection of one or more items" / "an itemset that contains k items" | A set of products |
| **Support count σ** | "frequency of occurrence of an itemset" | Number of transactions containing it |
| **Support s** | "fraction of transactions that contain an itemset" | σ ÷ number of transactions |
| **Frequent itemset** | "an itemset whose support is greater than or equal to a minimal support (minsup) threshold" | An itemset that appears often enough |
| **Association rule** | "an implication expression of the form X → Y, where X and Y are itemsets" | "People who buy X also buy Y" |
| **Confidence c** | "measures how often items in Y appear in transactions that contain X" | Of the baskets with X, the share that also have Y |
| **Anti-monotone property** | "support of an itemset never exceeds the support of its subsets" | Adding items can only lower support |
| **Recommender system** | "predicts and presents items a user may like based on their past interactions and similarities with other users" | A "you may also like" engine |
| **Collaborative filtering** | "the process of information filtering by collecting human judgments (ratings)"; "wisdom of the crowd"; "word of mouth" | Use other people's ratings |
| **Cold start** | "How to recommend new items? What to recommend to new users?" | No ratings yet → nothing to compare |
| **Explicit / implicit ratings** | Stars the user gives / behaviour (buys, clicks, page views, time spent) read as a rating | Asked vs observed |

---

## Part 1 — Clustering and k-means (slides 2–16) ★★

- "Clustering is an **unsupervised** learning problem."
- "The most popularly used clustering techniques are **k-means (divisive)** and **hierarchical (agglomerative)**."
- Objective of k-means: "organize data into clusters such that there is **high intra-cluster similarity and low inter-cluster similarity**".
- "An item will only belong to **one** cluster" — it produces "a specific number of **disjoint, non-hierarchical** clusters".
- K-means "uses the strategy of divide and conquer" and is "a classic example of an **expectation maximization (EM)** algorithm":
  - **E (expectation):** find the expected point associated with a cluster — **assign** points.
  - **M (maximization):** improve the estimate of the cluster — **update** the centroid.
  - Repeat "until **convergence** is reached".

### The algorithm — four steps ★★ (slide 7)

1. **Pick K random points** as cluster centres (centroids).
2. **Assign** each point xᵢ to the **nearest** centroid (by distance).
3. **Find the new centre** of each cluster = the **average of its assigned points**.
4. **Repeat steps 2 and 3 until none of the cluster assignments change.**

Distance = **Euclidean**: `d(x, m) = √( Σ (xᵢ − mᵢ)² )`. In 2-D: `√( (x₁ − m₁)² + (x₂ − m₂)² )`. Comparing squared distances gives the same nearest centroid, which saves square roots.

The illustrated slides (9–16) run this on two clusters: iteration 1 → 2 → 3, and at the fourth iteration the centroids stop moving — "Converge!".

### Worked example (extra, not on the slides — same method) ★★

Points A(1,1), B(2,1), C(4,3), D(5,4), E(1,2), F(4,4). K = 2. Initial centroids c1 = A(1,1), c2 = B(2,1).

**Iteration 1 — assign (squared distances):**

| Point | to c1 (1,1) | to c2 (2,1) | Cluster |
|---|---|---|---|
| A(1,1) | 0 | 1 | 1 |
| B(2,1) | 1 | 0 | 2 |
| C(4,3) | 9 + 4 = 13 | 4 + 4 = 8 | 2 |
| D(5,4) | 16 + 9 = 25 | 9 + 9 = 18 | 2 |
| E(1,2) | 0 + 1 = 1 | 1 + 1 = 2 | 1 |
| F(4,4) | 9 + 9 = 18 | 4 + 9 = 13 | 2 |

**Update:** c1 = mean of {A, E} = ((1+1)/2, (1+2)/2) = **(1, 1.5)**. c2 = mean of {B, C, D, F} = ((2+4+5+4)/4, (1+3+4+4)/4) = **(3.75, 3)**.

**Iteration 2 — assign:** A → c1 (0.25 vs 11.56). **B → c1** (1.25 vs 7.06) — it moves. C → c2 (11.25 vs 0.06). D → c2. E → c1. F → c2.
**Update:** c1 = mean of {A, B, E} = (4/3, 4/3) = **(1.33, 1.33)**. c2 = mean of {C, D, F} = (13/3, 11/3) = **(4.33, 3.67)**.

**Iteration 3 — assign:** nobody changes cluster → **converged**. Final clusters {A, B, E} and {C, D, F}.

**SSE** = (0.22 + 0.56 + 0.56) + (0.56 + 0.56 + 0.22) = **2.67**.

**Exam layout:** one distance table per iteration, then the new centroids, then say "assignments unchanged → stop".

## Part 2 — Choosing K, applications, limitations (slides 17–28) ★★

### Customer example (slide 17)

Mall membership data: CustomerID, gender, age, annual income (k$), spending score (1–100). K-means groups "similar customers" — this is **customer segmentation**.

### Elbow method ★★ (slides 18–21)

- Two common ways to choose K: the **Elbow method** and the **Silhouette method** (only the elbow is taught).
- Compute the **SSE** for several values of K:

```
SSE = Σ (over clusters i = 1..K)  Σ (over points x in cluster i)  dist(x, cᵢ)²
```

- Plot K against SSE. "The error **decreases as k gets larger**" because more clusters are smaller, "so distortion is also smaller".
- "Choose the k at which the SSE decreases **abruptly**" — the bend, or "elbow", where adding more clusters stops helping much. In the slide's example **k = 5**.
- Slide 22 plots the five customer clusters (income × spending score) with their centroids.

### Applications (slides 23–27)

Image classification (MNIST handwritten digits), image segmentation (by locality and colour, K = 3), clustering gene data, news article clustering, species clustering, **anomaly detection**, grouping image-search results (real apples vs Apple logos).

### Limitations ★★ (slide 28)

1. "Needs the **number of clusters to be specified**" (the elbow helps, but it also depends on the application).
2. "Has problems if the 'true' clusters are of **differing sizes, densities, and non-globular shapes**."
3. "Presence of **outliers** can skew the results."

---

## Part 3 — Association analysis: the definitions (slides 29–33) ★★

"Association analysis is a data mining technique for discovering relationships and co-occurrence patterns between items in large datasets, commonly known as **market basket analysis**."

Rules "predict the occurrence of an item based on the occurrences of other items in the transaction". **"Implication means co-occurrence, not causality!"**

**The slide data set (5 transactions):**

| TID | Items |
|---|---|
| 1 | Bread, Milk |
| 2 | Bread, Diaper, Beer, Eggs |
| 3 | Milk, Diaper, Beer, Coke |
| 4 | Bread, Milk, Diaper, Beer |
| 5 | Bread, Milk, Diaper, Coke |

```
Support of an itemset      s(X)     = (number of transactions containing X) / (total transactions)
Support of a rule          s(X → Y) = (number of transactions containing both X and Y) / (total transactions)
Confidence of a rule       c(X → Y) = (number containing both X and Y) / (number containing X)
```

- σ({Milk, Bread, Diaper}) = 2 (transactions 4 and 5) → s = 2/5.
- Rule {Milk, Diaper} → {Beer}: s = σ(Milk, Diaper, Beer)/|T| = 2/5 = **0.4**; c = σ(Milk, Diaper, Beer)/σ(Milk, Diaper) = 2/3 = **0.67**.

**In plain words:** support asks "is this common enough to matter?"; confidence asks "how reliable is the 'if … then'?". Support is the same in both directions; **confidence changes with the direction** because the denominator is the left-hand side.

## Part 4 — The mining task and why it is hard (slides 34–40) ★

- **Task:** given transactions T, find all rules with **support ≥ minsup** and **confidence ≥ minconf**.
- **Brute force:** list all possible rules, compute support and confidence for each, prune those failing the thresholds → "**computationally prohibitive!**"
- Six rules from the itemset {Milk, Diaper, Beer} (slide 35):

| Rule | s | c |
|---|---|---|
| {Milk, Diaper} → {Beer} | 0.4 | 0.67 |
| {Milk, Beer} → {Diaper} | 0.4 | 1.0 |
| {Diaper, Beer} → {Milk} | 0.4 | 0.67 |
| {Beer} → {Milk, Diaper} | 0.4 | 0.67 |
| {Diaper} → {Milk, Beer} | 0.4 | 0.5 |
| {Milk} → {Diaper, Beer} | 0.4 | 0.5 |

  "Rules originating from the same itemset have **identical support** but can have **different confidence**. Thus, we may **decouple** the support and confidence requirements."
- **Two-step approach ★★:**
  1. **Frequent itemset generation** — all itemsets with support ≥ minsup.
  2. **Rule generation** — high-confidence rules from each frequent itemset; each rule is a binary partitioning of a frequent itemset.
- Size of the problem: d items → **2^d** possible itemsets, and `R = 3^d − 2^(d+1) + 1` possible rules (**d = 6 → 602 rules**). Brute-force counting costs about O(N·M·w) with M = 2^d candidates.
- **Three strategies (slide 40):** reduce the number of **candidates (M)** by pruning; reduce the number of **transactions (N)** as itemsets grow (DHP, vertical-based mining); reduce the number of **comparisons (NM)** with efficient data structures (hash tree).

## Part 5 — The Apriori principle and algorithm (slides 41–48) ★★

### Apriori principle

> "If an itemset is frequent, then all of its subsets must also be frequent."
> Equivalently: "If any subset of an itemset is infrequent, then the itemset itself cannot be frequent."

It holds because of the **anti-monotone property of support**: for X ⊆ Y, s(X) ≥ s(Y). So once {A, B} is found infrequent, every superset (ABC, ABD, ABCD …) is **pruned** without counting.

**Illustration (slide 43), minimum support count = 3:**

| Items (1-itemsets) | Count | | Pairs (2-itemsets) | Count |
|---|---|---|---|---|
| Bread | 4 | | {Bread, Milk} | 3 |
| Coke | 2 ✗ | | {Bread, Beer} | 2 ✗ |
| Milk | 4 | | {Bread, Diaper} | 3 |
| Beer | 3 | | {Milk, Beer} | 2 ✗ |
| Diaper | 4 | | {Milk, Diaper} | 3 |
| Eggs | 1 ✗ | | {Beer, Diaper} | 3 |

No pair containing Coke or Eggs is generated. Triplet candidate: {Bread, Milk, Diaper}. Without pruning: 6C1 + 6C2 + 6C3 = 6 + 15 + 20 = **41** candidates. With support-based pruning: 6 + 6 + 1 = **13**. (The slide prints a count of 3 for the triplet; counting the table gives 2, as slide 32 says. Either way the point is the saving from 41 to 13.)

### The algorithm ★★ (slide 45)

```
k = 1.  Generate frequent itemsets of length 1.
Repeat until no new frequent itemsets are identified:
   1. Generate candidate (k+1)-itemsets from the frequent k-itemsets     (self-join  Lk * Lk)
   2. Prune candidates that contain an infrequent k-itemset              (Apriori principle)
   3. Count the support of each candidate by scanning the database
   4. Eliminate infrequent candidates, leaving only the frequent ones
```

Notation: **Ck** = candidate k-itemsets; **Lk** = frequent k-itemsets.

**Self-join rule (slide 46):** two frequent k-itemsets are joined when their **first k − 1 items are the same**. From L2 = {AB, AC, AE, CE}: AB + AC → ABC; AB + AE → ABE; AC + AE → ACE.

### Full worked example ★★ (slides 44, 46–48), minimum support count = 2

| Tid | Items |
|---|---|
| 10 | A, B, D |
| 20 | A, C, E |
| 30 | A, B, C, E |
| 40 | C, E |

| Step | Result |
|---|---|
| **1st scan → C1** | {A} 3, {B} 2, {C} 3, {D} 1, {E} 3 |
| **L1** | {A} 3, {B} 2, {C} 3, {E} 3 (D dropped) |
| **C2** (join L1) | {A,B}, {A,C}, {A,E}, {B,C}, {B,E}, {C,E} |
| **2nd scan** | {A,B} 2, {A,C} 2, {A,E} 2, {B,C} 1, {B,E} 1, {C,E} 3 |
| **L2** | {A,B} 2, {A,C} 2, {A,E} 2, {C,E} 3 |
| **C3** (join L2) | ABC, ABE, ACE → **prune ABC** (BC not frequent) and **ABE** (BE not frequent) → {A,C,E} |
| **3rd scan → L3** | {A,C,E} 2 |

## Part 6 — Counting with a hash tree (slides 49–57)

- To cut comparisons, "store the candidates in a **hash structure**"; a transaction is matched only against candidates in the buckets it hashes to.
- Example: 15 candidate 3-itemsets; hash function **1,4,7 / 2,5,8 / 3,6,9** (three branches); hash on the 1st item at level 1, the 2nd at level 2, the 3rd at level 3. You need a hash function, a **max leaf size** (split the node when exceeded) and an **order on the items**.
- Transaction {1, 2, 3, 5, 6} has ten 3-item subsets; using the tree it is matched against only **9 of the 15** candidates.

**In plain words:** know *why* (fewer comparisons) and the numbers 15 and 9. Building the tree by hand is unlikely to be asked.

## Part 7 — Rule generation; pros and cons (slides 58–62) ★★

- From a frequent itemset L, find every non-empty subset f such that **f → L − f** meets minconf.
- "If |L| = k, there are **2^k − 2** candidate association rules" (ignoring L → ∅ and ∅ → L). {A,B,C,D} → 14 rules.
- Confidence in general is **not** anti-monotone: c(ABC → D) can be larger or smaller than c(AB → D).
- But for rules **from the same itemset** it is anti-monotone with respect to the size of the **right-hand side**: `c(ABC → D) ≥ c(AB → CD) ≥ c(A → BCD)`, because confidence = σ(itemset)/σ(LHS). So if a rule fails minconf, every rule made by moving more items to the right-hand side is pruned.
- Bottom-up generation: merge two rules that share the same prefix in the consequent (A ⇒ B,C and A ⇒ B,D give A ⇒ B,C,D).

| Advantages of Apriori | Disadvantages of Apriori |
|---|---|
| **Simple and easy to understand** and implement | **High computational cost** — many candidate itemsets, especially with many items or a low minsup |
| **Uses the Apriori principle for pruning** — avoids unnecessary computation | **Inefficient for dense data** — candidates grow exponentially |

**Rule-generation method for the exam:** for each frequent itemset with 2 or more items, list every way to split it into left → right, compute `conf = count(whole itemset) / count(left side)`, and keep the rules ≥ minconf. A k-itemset gives 2^k − 2 rules (pair → 2 rules; triple → 6 rules).

---

## Part 8 — Recommender systems: the big picture (slides 63–78) ★★

**Definition (slide 64):** "A recommender system predicts and presents items a user may like based on their past interactions and similarities with other users." It helps people make decisions; recommendations are based on the preferences of **an individual** or **a group or community**. Used in e-commerce (items), e-learning/streaming (content), search and navigation (links).

### Value (slides 65–66)

| Provider's point of view | User's point of view |
|---|---|
| Sell more items | Find some good items |
| Sell more **diverse** items (**long tail**) | Understand what items are popular |
| Increase user satisfaction, fidelity | Get a recommended sequence or bundle |
| Better understand what users want | Explore something new |

Numbers: **Netflix — 2/3 of the movies watched**; **Amazon — 35% of sales**; **Google News — 38% more click-through**. Side-effects for users: easily influenced by others; may buy something not useful.

### Types ★★ (slides 67–73)

| Type | Slide slogan | Uses | Example |
|---|---|---|---|
| **Collaborative filtering (CF)** | "Tell me what's popular among my peers" | User profile + **community data** | Two people with similar taste recommend items to each other |
| **Content-based (CB)** | "Show me more of the same what I've liked" | User profile + **product features** (title, genre, actors) | "What sort of books do I like?" |
| **Knowledge-based (KB)** | "Tell me what fits based on my needs" | User requirements + product features + **knowledge models** (rules, constraints) | Cameras by price, resolution, brand |
| **Hybrid** | "Combinations of various inputs and/or composition of different mechanism" | All of the above | — |

"Recommender systems reduce **information overload** by estimating **relevance**."

### Non-personalized recommendation (slides 74–77)

- Simplest idea: recommend the "most popular items" — the highest average rating.
- Problems with averages: **uncertainty and size of data** (average 5 from 3 ratings vs 4.9 from 100 ratings); **bias** (some users always rate higher). Fix: combine the average with **uncertainty** (e.g. standard deviation); example **TrueSkill** (Bayesian ranking of players).
- **Exploitation vs exploration ★:** pure exploitation always shows the top items; exploration shows other items to gather data. Too much exploitation → "we may omit some very good items"; too much exploration → "we present poor items needlessly".

### CF vs CB vs KB ★★ (slide 78)

| | CF | CB | KB |
|---|---|---|---|
| **Compares** | Users' interests | Item information | With a knowledge base |
| **Similarity** | Set of users; user profile | Item info; text documents | Rules or logic instead of similarity |
| **Shortcomings** | Other users' feedback matters; **sparsity of ratings; cold start** | Features matter; **over-specialization**; eliciting user feedback | Requires explicit **knowledge engineering**; hard to scale and maintain |

---

## Part 9 — User-based collaborative filtering (slides 79–96) ★★

- Assumption: "users with **similar taste in the past will have similar taste in the future**"; preferences stay stable. Needs only the **matrix of ratings**.
- **Input:** user–item rating matrix (with missing values, "often very sparse"). **Output:** predictions for the missing values. (Netflix Prize: US$1 million for a 10% improvement.)
- **Two families:** **memory-based** (find similar users/items — nearest neighbours — and use the rating matrix directly; "does not scale for most real-world scenarios") and **model-based** (learn a model offline: latent factors, matrix factorization, machine learning; only the model is used at run time).
- **kNN** = the memory-based approach: "utilizes the entire user-item database to generate predictions directly, i.e., there is no model building". It has user-based and item-based methods.

**Technique:** for active user Alice and an unseen item i: (1) find users who rated like Alice in the past and who rated i; (2) combine their ratings of i; (3) do this for all unseen items and recommend the best.

### Pearson correlation ★★ (slide 91)

```
                 Σp∈P ( r(a,p) − r̄a ) ( r(b,p) − r̄b )
sim(a, b) = ───────────────────────────────────────────────────
             √Σp∈P ( r(a,p) − r̄a )²  ·  √Σp∈P ( r(b,p) − r̄b )²

a, b = users;   r(a,p) = rating of user a for item p;   P = items rated by BOTH a and b;   value between −1 and +1
```

Pearson "takes differences in rating behavior into account" (a harsh rater and a generous rater can still be similar) and works better than plain cosine similarity for users.

### The Alice example ★★ (slides 89–92)

| | Item1 | Item2 | Item3 | Item4 | Item5 | sim with Alice |
|---|---|---|---|---|---|---|
| Alice | 5 | 3 | 4 | 4 | ? | — |
| User1 | 3 | 1 | 2 | 3 | 3 | **0.85** |
| User2 | 4 | 3 | 4 | 3 | 5 | **0.70** |
| User3 | 3 | 3 | 1 | 5 | 4 | **0.00** |
| User4 | 1 | 5 | 5 | 2 | 1 | **−0.79** |

**Working for sim(Alice, User1)** over Item1–Item4. Means on those items: Alice 4; User1 (3 + 1 + 2 + 3)/4 = 2.25.

| | Item1 | Item2 | Item3 | Item4 |
|---|---|---|---|---|
| Alice − 4 | 1 | −1 | 0 | 0 |
| User1 − 2.25 | 0.75 | −1.25 | −0.25 | 0.75 |
| Product | 0.75 | 1.25 | 0 | 0 |

Numerator = 2.0. Denominator = √(1 + 1 + 0 + 0) × √(0.5625 + 1.5625 + 0.0625 + 0.5625) = 1.414 × 1.658 = 2.345. **sim = 2.0 / 2.345 = 0.85.**

### Prediction ★★ (slide 94)

```
pred(a, p) = r̄a +  Σb∈N  sim(a,b) · ( r(b,p) − r̄b )   /   Σb∈N  sim(a,b)

N = the chosen neighbours;  r̄b = neighbour b's average rating
```

**In plain words:** start from Alice's own average; add the neighbours' "how much above or below *their* average did they rate this item", weighted by how similar they are to Alice.

**Worked (extra — the slides give the formula but not the number).** Neighbours User1 (0.85) and User2 (0.70). Their averages over all five items: User1 = 12/5 = 2.4; User2 = 19/5 = 3.8.
pred(Alice, Item5) = 4 + [0.85 × (3 − 2.4) + 0.70 × (5 − 3.8)] / (0.85 + 0.70) = 4 + (0.51 + 0.84)/1.55 = **4.87** → Alice will probably like Item5.

**Improving the prediction (slide 95):** give more weight to items with **higher variance** (agreement on controversial items is more informative); **significance weighting** (reduce weight when few items are co-rated); **case amplification** (more weight to very similar neighbours); **neighbourhood selection** (similarity threshold or fixed number of neighbours).

---

## Part 10 — Item-based collaborative filtering (slides 97–106) ★★

**Idea:** "use the similarity between **items** (and not users)". To predict Alice's rating for Item5, find items similar to Item5 and use **Alice's own ratings** of those items. The slides call item-based CF "an example for model-based approaches" because item similarities can be computed offline.

```
Cosine similarity            sim(a, b) = (a · b) / ( |a| · |b| )          ratings as vectors; angle between them

Adjusted cosine similarity
                 Σu∈U ( r(u,a) − r̄u ) ( r(u,b) − r̄u )
sim(a, b) = ───────────────────────────────────────────────────
             √Σu∈U ( r(u,a) − r̄u )²  ·  √Σu∈U ( r(u,b) − r̄u )²

a, b = items;   U = users who rated BOTH items;   r̄u = average rating of USER u

Prediction     pred(u, p) = Σi∈ratedItems(u)  sim(i,p) · r(u,i)   /   Σi∈ratedItems(u)  sim(i,p)
```

**The difference from Pearson:** Pearson (user-based) subtracts each **user's** mean while comparing two **users** across items. Adjusted cosine compares two **items** across users but still subtracts each **user's** mean (not the item's mean).

### Slide example ★★ (slides 100–103)

| User | Item a | Item b | User average | a adjusted | b adjusted |
|---|---|---|---|---|---|
| Alice | 4 | 5 | 4.5 | −0.5 | +0.5 |
| Bob | 3 | 2 | 2.5 | +0.5 | −0.5 |
| Candy | 5 | 4 | 4.5 | +0.5 | −0.5 |

- Numerator = (−0.5 × 0.5) + (0.5 × −0.5) + (0.5 × −0.5) = **−0.75**.
- Item a: √(0.25 + 0.25 + 0.25) = √0.75 = 0.866. Item b: √0.75 = 0.866.
- **sim(a, b) = −0.75 / (0.866 × 0.866) = −1** — "perfect negative correlation".

**Neighbourhood size:** "in most real-world situations, a neighborhood of **20 to 50** neighbors seems reasonable" (MovieLens analysis).

**Which similarity measure?** "No fundamental reason for the choice of one metric" — "mostly based on practical experiences".

### Pre-processing for item-based filtering (slide 106)

- Item-based filtering "does not solve the scalability problem itself".
- **Amazon.com (2003):** calculate **all pair-wise item similarities in advance**. At run time the neighbourhood is small (only items the user has rated). "Item similarities are supposed to be **more stable** than user similarities."
- Memory: up to **N²** pair-wise similarities in theory (N = number of items); less in practice. Reduce further with a minimum threshold for co-ratings or a limit on neighbourhood size.

---

## Part 11 — Ratings, sparsity, models, evaluation, issues (slides 107–137) ★

### Explicit vs implicit ratings ★★ (slides 107–108)

| | Explicit ratings | Implicit ratings |
|---|---|---|
| What | The user gives a rating (1–5 or 1–7 Likert scales) | Collected from behaviour: purchases, clicks, page views, time on page, demo downloads |
| Good | "Probably the **most precise** ratings" | Collected constantly; **no extra effort** from the user |
| Bad | Users are not always willing to rate → **sparse** matrices → poor recommendations | "One cannot be sure whether the user behavior is **correctly interpreted**" (a book bought as a gift) |

### Data sparsity and cold start ★★ (slides 109–110)

- **Cold start:** how to recommend **new items**; what to recommend to **new users**.
- Straightforward fixes: **ask/force users to rate** a set of items; use **another method** (content-based, demographic, non-personalized) in the initial phase; **default voting** (give default values to items only one of the two users has rated).
- Alternative: better algorithms, e.g. **recursive CF** — if a very close neighbour has not rated the item, predict that neighbour's rating first and use it (assume "transitivity" of neighbourhoods).

### Model-based approaches (slides 111–130)

- Techniques: matrix factorization (singular value decomposition, principal component analysis), **association rule mining**, probabilistic models (clustering, Bayesian networks, pLSA), other machine learning.
- **Restricted Boltzmann Machine (RBM):** "a kind of autoencoder"; a shallow **two-layer** neural net — a **visible (input)** layer and a **hidden** layer; building block of deep-belief networks. Nodes connect **across** layers but **not within** a layer ("no intra-layer communication — this is the **restriction**"). It is a **symmetrical bipartite graph**. Each input is multiplied by a weight, a bias is added, and the result passes through an activation (sigmoid) function. **Reconstruction:** hidden activations go backward through the same weights to rebuild the input; the **reconstruction error** (input − reconstruction) is used to update the weights again and again.
- **Movie example:** 6 visible units (Harry Potter, Avatar, LOTR 3, Gladiator, Titanic, Glitter), **2 hidden units**. After training, hidden unit 1 reacts to **Sci-Fi/Fantasy** films and hidden unit 2 to **Oscar winners** — these are **latent factors**. A new user who likes Gladiator and Titanic (input [0 0 0 1 1 0]) activates **Hidden 2**, so the system recommends the Oscar-winning film they have not seen: **LOTR 3**.

### CF pros and cons ★ (slide 131)

- **Pros:** well understood; works well in some domains; **no knowledge engineering** required.
- **Cons:** requires a **user community**; **sparsity** problems; no integration of other knowledge sources; **no explanation** of results.

### Evaluation metrics ★ (slides 132–134)

| Metric | Meaning |
|---|---|
| **Predict accuracy** | Ability to predict a user's rating — **MAE / RMSE** |
| **Rank accuracy** | How well the system orders recommendations — **precision** (share of the list the user finds useful), **half-life utility** (emphasises getting the top of the list right) |
| **Novelty** | Recommending items the user was **not already aware of** |
| **Serendipity** | Items that are **unexpected and pleasantly surprising** |
| **Coverage** | Percentage of items for which the system can generate predictions |
| **Learning rate** | How quickly the system becomes effective as data arrive |
| **Confidence** | Ability to judge the likely quality of its own predictions |
| **User satisfaction** | From surveys, or retention and use statistics |

### Privacy, trust and interfaces (slides 135–137)

- **User profiling and inference:** systems may infer sensitive attributes (political views, health); risk of over-personalization and "**filter bubbles**".
- **Third-party sharing** without clear consent. **Regulatory compliance:** GDPR, CCPA.
- **Explanation:** where, how and from whom recommendations come — but not too much.
- **Social navigation:** make the community's behaviour visible ("footprints": read-wear / edit-wear), mimicking word-of-mouth (Epinions.com).

---

## How this lecture is examined

### 2025-26 final Q24 (25 marks) — full model answer ★★

| TID | Items |
|---|---|
| T1 | Laptop, Headphones, T-shirt |
| T2 | Laptop, Headphones, Coffee |
| T3 | Laptop, Smartphone, Headphones |
| T4 | Headphones, Jeans, Coffee |
| T5 | Laptop, Headphones, Jeans |

Minimum support = 60% → an itemset must be in at least 0.6 × 5 = **3 transactions**. Minimum confidence = 90%.

**(a) Trace Apriori to 2-itemsets (15 marks)**

*Step 1 — candidate 1-itemsets C1 (scan the database):*

| Item | Count | Support | Frequent? |
|---|---|---|---|
| Laptop | 4 | 80% | Yes |
| Headphones | 5 | 100% | Yes |
| T-shirt | 1 | 20% | No |
| Coffee | 2 | 40% | No |
| Smartphone | 1 | 20% | No |
| Jeans | 2 | 40% | No |

*Step 2 — frequent 1-itemsets L1:* {Laptop}, {Headphones}.

*Step 3 — candidate 2-itemsets C2 (join L1 with itself):* {Laptop, Headphones}. By the Apriori principle, no pair containing T-shirt, Coffee, Smartphone or Jeans is generated, because an itemset with an infrequent subset cannot be frequent.

*Step 4 — scan:* {Laptop, Headphones} is in T1, T2, T3, T5 → count 4 → support 80% ≥ 60% → frequent.

*Step 5 — L2:* {Laptop, Headphones}. No 3-itemset can be formed, so the algorithm stops.

**All frequent itemsets:** {Laptop} (80%), {Headphones} (100%), {Laptop, Headphones} (80%).

**(b) Association rules (6 marks)** — from {Laptop, Headphones}:

| Rule | Support | Confidence | ≥ 90%? |
|---|---|---|---|
| Laptop → Headphones | 4/5 = 80% | count(Laptop, Headphones)/count(Laptop) = 4/4 = **100%** | **Yes** |
| Headphones → Laptop | 4/5 = 80% | 4/5 = **80%** | No |

**Only Laptop → Headphones** meets both thresholds.

**(c) Suggestions (4 marks)** — any four well-explained points:
1. **Cross-sell:** when a customer views or adds a laptop to the cart, recommend headphones ("frequently bought together"), because every laptop buyer also bought headphones.
2. **Bundle / promotion:** offer a laptop + headphones bundle or a discount on headphones with a laptop; place them together on the page.
3. **Direction matters:** do not push laptops to every headphone buyer — that rule has only 80% confidence, below the threshold.
4. **Follow-up marketing:** personalised e-mail or app notification with headphone offers after a laptop purchase.
5. **Improve the mining:** lower minsup or use more data to find rules for less frequent items (coffee, jeans — the long tail); combine the rules with collaborative filtering or content-based methods, and remember a rule shows co-occurrence, not causality.

### Model answers for other likely questions

**Q (4 marks). State the Apriori principle and explain how it reduces computation.**
1. If an itemset is frequent, then all of its subsets must also be frequent. (1)
2. Equivalently, if any subset is infrequent, the itemset itself cannot be frequent. (1)
3. This holds because support is anti-monotone: an itemset's support never exceeds the support of its subsets. (1)
4. So candidates containing an infrequent subset are pruned without counting, reducing the number of candidates (e.g. 41 → 13). (1)

**Q (4 marks). Describe the k-means algorithm.** The four steps on slide 7, one mark each.

**Q (3 marks). Give three limitations of k-means.** K must be specified; struggles with clusters of differing sizes, densities and non-globular shapes; outliers skew the result.

**Q (4 marks). Explain the cold-start problem and two ways to handle it.**
1. Collaborative filtering needs ratings; a new user or a new item has none, so no similar users/items can be found. (1)
2. It is part of the data sparsity problem. (1)
3. Ask or force new users to rate a set of items. (1)
4. Use another method at first — content-based, demographic or non-personalized (most popular) recommendations; or default voting. (1)

**Q (6 marks). Compare collaborative, content-based and knowledge-based recommenders.** Use the slide-78 table: what each compares (2), one example each (2), one shortcoming each (2).

**Q (4 marks). Explicit vs implicit ratings: one advantage and one problem of each.** From the table in Part 11.

---

## Easy to mix up

| A | B | How to tell them apart |
|---|---|---|
| Support | Confidence | ÷ all transactions vs ÷ transactions containing the left-hand side |
| Ck | Lk | Candidates (before counting) vs frequent itemsets (after counting) |
| Frequent itemset | Association rule | A set that is common vs an if-then made from it |
| Apriori principle | Anti-monotone property | The pruning rule vs the reason it works |
| Clustering | Classification | No labels vs labels |
| K-means | Hierarchical | Divisive, K fixed, disjoint clusters vs agglomerative |
| E step | M step | Assign points vs update centroids |
| User-based CF | Item-based CF | Similar **users** (Pearson) vs similar **items** (adjusted cosine) |
| Pearson | Adjusted cosine | Both subtract the **user's** mean; Pearson sums over items for two users, adjusted cosine sums over users for two items |
| Memory-based | Model-based | Uses the rating matrix directly vs learns a model offline |
| Content-based | Collaborative | Item features vs other users' ratings |
| Explicit | Implicit | Stars given vs behaviour observed |
| Novelty | Serendipity | Not known before vs unexpected **and** pleasant |
| Exploitation | Exploration | Show known top items vs try others to learn |

## Memory hooks

- K-means: **"Pick, Assign, Average, Repeat."**
- Elbow: **"more K → less SSE; stop at the bend."**
- Apriori loop: **"Join, Prune, Count, Eliminate."**
- Confidence: **"both over left."** Support: **"both over all."**
- A k-itemset gives **2^k − 2** rules.
- Recommender slogans: CF = **peers**, CB = **more of the same**, KB = **fits my needs**.
- CF weaknesses: **"sparse and cold"**. CB weakness: **over-specialised**. KB weakness: **knowledge engineering**.
- RBM: **two layers, no links inside a layer**.

---

## Test yourself

**Multiple choice**

1. K-means is an example of: A) supervised learning B) an expectation maximization algorithm C) association mining D) hierarchical clustering
2. In the elbow method, as K increases the SSE: A) increases B) stays the same C) decreases D) first rises then falls
3. In 5 transactions, {Milk, Diaper} appears in 3 and {Milk, Diaper, Beer} in 2. Confidence of {Milk, Diaper} → {Beer} is: A) 0.4 B) 0.6 C) 0.67 D) 1.5
4. The Apriori principle allows us to: A) raise the confidence B) prune supersets of infrequent itemsets C) remove transactions D) avoid scanning the database
5. A frequent 3-itemset can generate how many candidate rules? A) 3 B) 6 C) 7 D) 8
6. "Show me more of the same what I've liked" describes: A) collaborative B) content-based C) knowledge-based D) hybrid
7. Which similarity measure is popular in user-based CF? A) Euclidean distance B) Pearson correlation C) SSE D) entropy
8. Which is a shortcoming of collaborative filtering? A) knowledge engineering B) over-specialization C) cold start D) needs product features
9. Interpreting a purchase as a positive rating is an example of: A) explicit rating B) implicit rating C) default voting D) serendipity
10. In an RBM, nodes are connected: A) only within a layer B) across layers but not within a layer C) to every other node D) only to the bias

**True / false**

1. In k-means an item can belong to several clusters.
2. Rules generated from the same itemset have identical support but may have different confidence.
3. An association rule X → Y proves that buying X causes buying Y.
4. Support of an itemset never exceeds the support of its subsets.
5. Adjusted cosine similarity subtracts the item's average rating from each rating.
6. Item similarities are supposed to be more stable than user similarities.
7. Explicit ratings can be collected without any extra effort from the user.
8. Outliers can skew the result of k-means.

**Short questions**

1. Transactions: {A,B,D}, {A,C,E}, {A,B,C,E}, {C,E}, {B,D}. Minimum support 40%, minimum confidence 70%. Find all frequent itemsets and the rules that qualify.
2. Ratings — Amy: I1 = 5, I2 = 3, I3 = 4; Ben: I1 = 4, I2 = 2, I3 = 3, I4 = 4. Compute the Pearson similarity between Amy and Ben over I1–I3.
3. One-dimensional points 2, 4, 10, 12, 3, 11 with K = 2 and initial centroids 2 and 4. Run k-means to convergence.

### Answers

**Multiple choice:** 1 **B**. 2 **C**. 3 **C** (2/3; 0.4 is the support). 4 **B**. 5 **B** (2³ − 2). 6 **B**. 7 **B**. 8 **C** (A is KB, B and D are CB). 9 **B**. 10 **B**.

**True / false:** 1 **F** (only one — disjoint clusters). 2 **T**. 3 **F** (co-occurrence, not causality). 4 **T** (anti-monotone). 5 **F** (the **user's** average). 6 **T**. 7 **F** (that is implicit ratings). 8 **T**.

**Short questions**

1. Minimum count = 0.4 × 5 = 2. C1: A 3, B 3, C 3, D 2, E 3 → all frequent. C2 counts: AB 2, AC 2, AD 1, AE 2, BC 1, BD 2, BE 1, CD 0, CE 3, DE 0 → L2 = {AB, AC, AE, BD, CE}. C3: join gives ABC, ABE, ACE; prune ABC (BC infrequent) and ABE (BE infrequent) → ACE, count 2 → L3 = {ACE}. Rules ≥ 70%: **D → B** (2/2 = 100%), **C → E** (3/3 = 100%), **E → C** (3/3 = 100%), **AC → E** (2/2 = 100%), **AE → C** (2/2 = 100%). All others are 2/3 = 67% and fail (e.g. A → B, B → D, CE → A).
2. Means: Amy 4, Ben (4 + 2 + 3)/3 = 3. Deviations — Amy: 1, −1, 0; Ben: 1, −1, 0. Numerator = 1 + 1 + 0 = 2. Denominator = √2 × √2 = 2. **sim = 1.0** (Ben rates one point lower every time, but the pattern is identical).
3. Iteration 1: 2 → c1; 3 is 1 from both → tie, assign to the first (c1); 4, 10, 11, 12 → c2. New centroids: c1 = 2.5, c2 = (4 + 10 + 11 + 12)/4 = 9.25. Iteration 2: 2, 3, 4 → c1 (4 is 1.5 from 2.5 and 5.25 from 9.25); 10, 11, 12 → c2. New centroids: c1 = 3, c2 = 11. Iteration 3: no change → clusters **{2, 3, 4}** and **{10, 11, 12}**, centroids 3 and 11.
