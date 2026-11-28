# COMP3134 Mock Exam B — the curveball paper

> Same format as Mock A: Part A multiple choice (25 marks), Part B True/False (10 marks), Part C short questions (30 marks), Part D long questions (35 marks). Total 100 marks, 3 hours.
> This paper uses the topics that are on the slides but were **never asked as long questions before**: k-means, collaborative filtering, logistic regression, sampling, A/B testing. If the real paper surprises you, it will look like this one. All questions are my own.

**Rules for the practice**

- 3 hours, one sitting. Only your A4 cheat sheet and a calculator.
- Round final answers to 2 decimal places. Keep 3–4 decimals in the middle steps.
- Answers and the marking scheme start after the appendix.

---

## Part A — Multiple choice (25 marks, 1 mark each)

**1.** A subset of a data warehouse that covers one subject area, such as marketing, is called:
A. an operational data store  B. a data mart  C. an enterprise data warehouse  D. a model base

**2.** "Should the company enter a new overseas market?" This decision is best described as:
A. structured, operational control  B. structured, managerial control  C. semi-structured, operational control  D. unstructured, strategic planning

**3.** A system that shows key performance indicators on dashboards for top managers is:
A. an OLTP system  B. a transaction processing system  C. an executive information system (EIS)  D. an expert system

**4.** Which of the following is NOT one of the five key CRM processes?
A. Strategy development  B. Value creation  C. Product manufacturing  D. Multichannel integration

**5.** According to the lecture (Gartner), the single greatest inhibitor of CRM success is:
A. poor data quality  B. high software prices  C. too many channels  D. too few competitors

**6.** Which type of CRM focuses on analysing customer data?
A. Operational CRM  B. Analytical CRM  C. Social CRM  D. Collaborative selling

**7.** Which purchase benefits MOST from relationship marketing?
A. A pair of shoelaces  B. A pack of office paper  C. A season ticket for a sports team  D. A bottle of water

**8.** Giving a price discount to repeat buyers belongs to which level of relationship marketing?
A. Level 1  B. Level 2  C. Level 3  D. None of the levels

**9.** In a market where customers can switch suppliers easily and buy from several of them, the customers are described as:
A. lost-for-good  B. always-a-share  C. niche  D. partners

**10.** A customer designs her own running shoes on the company website. The customer is active. This is:
A. personalisation  B. customisation  C. de-marketing  D. mass marketing

**11.** A music service is free with advertisements, and the company earns from advertising and from users who upgrade. Which digital disruption model is this?
A. Marketplace  B. Free/freemium  C. Hypermarket  D. Pyramid

**12.** "The service is available wherever the user is, at any time." Which attribute of m-commerce is this?
A. Ubiquity  B. Localisation  C. Personalisation  D. Interactivity

**13.** In the data → information → knowledge → expertise → wisdom chain, "causal if–then rules" describes:
A. data  B. information  C. knowledge  D. wisdom

**14.** Temperature in degrees Celsius is measured on which level?
A. Nominal  B. Ordinal  C. Interval  D. Ratio

**15.** An interviewer must interview 480 men and 520 women. She stops whoever is convenient until both numbers are reached. This is:
A. stratified sampling  B. quota sampling  C. cluster sampling  D. simple random sampling

**16.** In Hadoop, which component stores big data in chunks on many machines?
A. MapReduce  B. HDFS  C. OLAP  D. ETL

**17.** The same 20 employees take a product-knowledge test before and after a training course. Which test compares the two sets of scores?
A. One-sample t-test  B. Independent-samples t-test  C. Paired-samples t-test  D. ANOVA

**18.** The power of a hypothesis test equals:
A. α  B. β  C. 1 − α  D. 1 − β

**19.** An A/B test with two million visitors gives p = 0.001 for a conversion uplift of 0.05%. What is the main concern?
A. The result is not statistically significant  B. The result may not be practically significant  C. The sample is too small  D. A Type II error has certainly happened

**20.** In the regression line y = b0 + b1x, b1 is:
A. the value of y when x is 0  B. the change in y when x increases by one unit  C. the error of the prediction  D. the mean of y

**21.** A model is 99% accurate on the training data and 60% accurate on new data. The model is:
A. underfitting  B. overfitting  C. unsupervised  D. pruned too much

**22.** In logistic regression, when z = b0 + b1x = 0, the predicted probability P(Y = 1) is:
A. 0  B. 0.25  C. 0.5  D. 1

**23.** In the elbow method for k-means, which quantity is plotted against K?
A. The number of iterations  B. The sum of squared errors (SSE)  C. The confidence  D. The entropy

**24.** A recommender suggests films that are similar, by genre and actors, to films the user liked before. It does not use other users' ratings. This is:
A. collaborative filtering  B. content-based filtering  C. knowledge-based recommendation  D. non-personalised recommendation

**25.** How many association rules can be generated from ONE frequent 3-itemset?
A. 3  B. 6  C. 8  D. 9

---

## Part B — True or False (10 marks, 1 mark each)

**1.** A data warehouse is volatile: its data are changed all the time by daily operations.

**2.** Primary data are data that are collected for the first time.

**3.** Cluster sampling works best when each cluster is mixed inside and the clusters are similar to each other.

**4.** Interval data have a natural zero point.

**5.** With the same sample size, lowering α from 0.05 to 0.01 reduces the chance of a Type I error but increases the chance of a Type II error.

**6.** A/B testing can show the causal impact of a change.

**7.** Post-pruning removes parts of a decision tree after the full tree has been built.

**8.** K-means is a supervised learning method.

**9.** The confidence of the rule X → Y is always equal to the confidence of the rule Y → X.

**10.** In a lost-for-good market, switching costs are low.

---

## Part C — Short questions (30 marks)

### C1. Hypothesis test (6 marks)

A call centre trains 36 agents in a new CRM system. The customer-satisfaction score of each agent is measured before and after the training. The differences (after − before) have a mean of 1.8 and a standard deviation of 3.6.

At the 5% significance level, has the training increased the scores?

(a) State the hypotheses. (1 mark)
(b) Name the correct t-test and say why. (1 mark)
(c) Calculate the t statistic. (2 marks)
(d) State the degrees of freedom and the critical value. (1 mark)
(e) State your decision and your conclusion. (1 mark)

### C2. Logistic regression (5 marks)

A shop predicts whether a website visitor will buy (Y = 1) from the number of minutes on the site (x). The fitted model is z = −4 + 0.1x.

(a) Calculate the probability of buying for a visitor who stays 50 minutes. (2 marks)
(b) Calculate the probability for a visitor who stays 30 minutes. (1 mark)
(c) Classify both visitors with a threshold of 0.5. (1 mark)
(d) At how many minutes is the probability exactly 0.5? (1 mark)

### C3. Association rules (7 marks)

| TID | Items |
|---|---|
| T1 | A, B, D |
| T2 | A, C, E |
| T3 | A, B, C, E |
| T4 | C, E |
| T5 | B, D |

Minimum support = 40%. Minimum confidence = 70%.

(a) Find all frequent itemsets with the Apriori algorithm. Show the candidate sets and the counts. (4 marks)
(b) Generate the rules from the frequent 3-itemset and say which ones pass. (2 marks)
(c) Explain why {A, B, C} does not need to be counted. (1 mark)

### C4. Sampling (4 marks)

Name the sampling method in each case. (1 mark each)

(a) A university takes a random sample of 50 students from every faculty.
(b) A supermarket chain randomly chooses 5 of its 30 stores and surveys every customer in those 5 stores.
(c) An interviewer stops shoppers at the entrance of one mall.
(d) A researcher of rare-coin collectors asks each respondent to give the names of other collectors.

### C5. A/B testing (4 marks)

(a) Which TWO values must you decide before you can calculate the sample size of an A/B test? (2 marks)
(b) Give TWO things to beware of when you read the result of an A/B test. (2 marks)

### C6. Business intelligence (4 marks)

Name the four types of analytics. For each, give the question it answers. (4 marks)

---

## Part D — Long questions (35 marks)

### D1. K-means clustering (11 marks)

A shop wants to put six customers into two groups. x = visits per month, y = spending per month (in hundreds of dollars).

| Customer | A | B | C | D | E | F |
|---|---|---|---|---|---|---|
| x | 1 | 2 | 4 | 5 | 1 | 4 |
| y | 1 | 1 | 3 | 4 | 2 | 4 |

Use k-means with K = 2 and Euclidean distance. The initial centroids are c1 = A (1, 1) and c2 = B (2, 1).

(a) Iteration 1: calculate the distance from every point to both centroids and assign every point to a cluster. (4 marks)
(b) Calculate the new centroids. (2 marks)
(c) Iteration 2: assign the points again and calculate the new centroids. (3 marks)
(d) Show that the algorithm has converged and state the final clusters. (1 mark)
(e) State ONE limitation of k-means. (1 mark)

### D2. Collaborative filtering (12 marks)

Four users rated four items from 1 to 5. Amy has not rated Item 4.

| | Item 1 | Item 2 | Item 3 | Item 4 |
|---|---|---|---|---|
| Amy | 5 | 3 | 4 | ? |
| Ben | 4 | 2 | 3 | 4 |
| Cat | 2 | 5 | 1 | 2 |
| Dan | 5 | 4 | 4 | 5 |

(a) Calculate the Pearson similarity between Amy and each of the other three users, over the items that both have rated. (6 marks)
(b) Use the two most similar users to predict Amy's rating of Item 4 with user-based collaborative filtering. (3 marks)
(c) Should the system recommend Item 4 to Amy? Why? (1 mark)
(d) Calculate the adjusted cosine similarity between Item 1 and Item 4. (2 marks)

### D3. CRM architecture (12 marks)

(a) Describe the five major components of a CRM system architecture. For each, give its main objective or function. (10 marks)
(b) Choose ONE customer touch point of an online retailer. Explain ONE way CRM technology can improve the customer experience at that touch point. (2 marks)

---

## Appendix — critical values of t

| df | One-tailed α = 0.05 | Two-tailed α = 0.05 | Two-tailed α = 0.01 |
|---|---|---|---|
| 9 | 1.833 | 2.262 | 3.250 |
| 10 | 1.812 | 2.228 | 3.169 |
| 15 | 1.753 | 2.131 | 2.947 |
| 20 | 1.725 | 2.086 | 2.845 |
| 25 | 1.708 | 2.060 | 2.787 |
| 29 | 1.699 | 2.045 | 2.756 |
| 30 | 1.697 | 2.042 | 2.750 |
| 35 | 1.690 | 2.030 | 2.724 |
| 40 | 1.684 | 2.021 | 2.704 |
| 60 | 1.671 | 2.000 | 2.660 |
| 80 | 1.664 | 1.990 | 2.639 |
| 120 | 1.658 | 1.980 | 2.617 |
| ∞ | 1.645 | 1.960 | 2.576 |

---

---

# Answers and marking scheme

## Part A answers

| Q | Answer | Why | Note |
|---|---|---|---|
| 1 | B | Data mart = subset, single subject. ODS = customer file updated during operations. EDW = whole enterprise. | 01 |
| 2 | D | No standard method = unstructured. Long-term direction = strategic planning. | 01 |
| 3 | C | EIS = dashboards and KPIs for executives. | 01 |
| 4 | C | The five are strategy development, value creation, multichannel integration, information management, performance assessment. | 02 |
| 5 | A | Poor data quality. Contact data erodes about 33% a year. | 02 |
| 6 | B | Operational = transactions and data collection. Analytical = analysis. Social = relationships and engagement. | 02 |
| 7 | C | Continuous, relational, emotional exchanges benefit most. The others are discrete and functional. | 03 |
| 8 | A | Level 1 = pricing incentives. Level 2 = social bonds. Level 3 = structural solutions. | 03 |
| 9 | B | Always-a-share = easy switching. Lost-for-good = high switching cost. | 04 |
| 10 | B | Customer active = customisation. Customer passive = personalisation. | 04 |
| 11 | B | Free/freemium earns from data, advertising "eyeballs" and upgrades. | 05 |
| 12 | A | Ubiquity = anywhere, any time. Localisation = based on where the user is. | 05 |
| 13 | C | Knowledge = causal if–then rules. | 06 |
| 14 | C | Differences have meaning but there is no natural zero. 0 °C does not mean "no temperature". | 07 |
| 15 | B | Fixed proportions but the people are not chosen at random = quota. | 07 |
| 16 | B | HDFS stores. MapReduce processes. | 07 |
| 17 | C | The same people are measured twice. | 08 |
| 18 | D | Power = 1 − β. | 08 |
| 19 | B | With a huge sample, a tiny effect becomes statistically significant. It may be too small to matter. | 08 |
| 20 | B | b1 is the slope. Option A is b0, the intercept. | 09 |
| 21 | B | High on training, low on test = overfitting. | 09 |
| 22 | C | 1/(1 + e⁰) = 1/2. | 09 |
| 23 | B | SSE falls as K rises. Choose K at the bend. | 10 |
| 24 | B | Item features + the user's own history = content-based. | 10 |
| 25 | B | 2³ − 2 = 6. | 10 |

## Part B answers

| Q | Answer | Why |
|---|---|---|
| 1 | F | A data warehouse is non-volatile. Data are loaded and kept, not changed by daily operations. |
| 2 | T | Secondary data already exist. |
| 3 | T | Then a few clusters represent the whole population well. (Strata are the opposite: similar inside, different between.) |
| 4 | F | Ratio data have a natural zero. Interval data do not. |
| 5 | T | α and β move in opposite directions when n is fixed. |
| 6 | T | Random assignment of visitors lets it show the causal impact. |
| 7 | T | Pre-pruning stops early. Post-pruning cuts afterwards (subtree replacement or raising). |
| 8 | F | It is unsupervised. It uses no class labels. |
| 9 | F | The numerator is the same but the denominators are count(X) and count(Y). |
| 10 | F | Switching costs are high in lost-for-good markets. |

## Part C answers

### C1 (6 marks)

(a) H0: the mean difference is zero (μd = 0), the training has no effect. H1: the mean difference is greater than zero (μd > 0), the scores increased. One-tailed, because the question says "increased". (1)

(b) **Paired-samples t-test**, because the same 36 agents are measured twice (before and after). (1)

(c)

```
t = (x̄d − 0) / (sd / √n)
  = 1.8 / (3.6 / √36)
  = 1.8 / 0.6
  = 3.00
```

Formula and substitution (1). Answer 3.00 (1).

(d) df = n − 1 = 35. One-tailed, α = 0.05: critical value = **1.690**. (1)

(e) 3.00 > 1.690, so **reject H0**. At the 5% level there is significant evidence that the CRM training increased the customer-satisfaction scores. (1)

### C2 (5 marks)

P(Y = 1) = 1 / (1 + e^(−z))

(a) x = 50: z = −4 + 0.1 × 50 = 1 (1). P = 1 / (1 + e^(−1)) = 1 / (1 + 0.3679) = **0.73** (1).

(b) x = 30: z = −4 + 0.1 × 30 = −1. P = 1 / (1 + e^(1)) = 1 / (1 + 2.7183) = **0.27** (1).

(c) 0.73 ≥ 0.5 → the 50-minute visitor is classified as **buy**. 0.27 < 0.5 → the 30-minute visitor is classified as **not buy**. (1)

(d) P = 0.5 when z = 0: −4 + 0.1x = 0 → x = **40 minutes**. (1)

### C3 (7 marks)

Minimum support 40% of 5 transactions = a count of at least 2.

(a) (4 marks)

C1: A 3, B 3, C 3, D 2, E 3. All are frequent. **L1 = {A}, {B}, {C}, {D}, {E}** (1)

C2, ten pairs (1½):

| Pair | Count | Frequent? | Pair | Count | Frequent? |
|---|---|---|---|---|---|
| AB | 2 (T1, T3) | Yes | BD | 2 (T1, T5) | Yes |
| AC | 2 (T2, T3) | Yes | BE | 1 | No |
| AD | 1 | No | CD | 0 | No |
| AE | 2 (T2, T3) | Yes | CE | 3 (T2, T3, T4) | Yes |
| BC | 1 | No | DE | 0 | No |

**L2 = {A,B}, {A,C}, {A,E}, {B,D}, {C,E}** (½)

C3, join the pairs of L2 that share the first item (1):

- AB + AC → ABC. Subset BC is not frequent → pruned.
- AB + AE → ABE. Subset BE is not frequent → pruned.
- AC + AE → ACE. Subsets AC, AE, CE are all frequent → keep.

Count ACE = 2 (T2, T3) → **L3 = {A, C, E}**. C4 is empty. Stop.

(b) (2 marks) Rules from {A, C, E}, where count = 2:

| Rule | Confidence | Pass (≥ 70%)? |
|---|---|---|
| {A, C} → E | 2/2 = 100% | Yes |
| {A, E} → C | 2/2 = 100% | Yes |
| {C, E} → A | 2/3 = 67% | No |
| A → {C, E} | 2/3 = 67% | No |
| C → {A, E} | 2/3 = 67% | No |
| E → {A, C} | 2/3 = 67% | No |

Two rules pass. (All six have the same support, 40%, because they come from the same itemset.)

(c) (1 mark) By the Apriori principle, if an itemset is frequent then all its subsets are frequent. {B, C} is a subset of {A, B, C} and it is not frequent (count 1), so {A, B, C} cannot be frequent. It is pruned without scanning the database.

### C4 (4 marks)

(a) **Stratified sampling**: the faculties are the strata, and a random sample is taken from every one. (1)
(b) **Cluster sampling**: the stores are the clusters, a few are chosen at random, and everyone in them is surveyed. (1)
(c) **Convenience sampling** (mall intercept). (1)
(d) **Snowball (referral) sampling**: used for rare groups. (1)

### C5 (4 marks)

(a) (1 mark each)

1. The **baseline conversion rate**: the conversion rate of the current (control) version.
2. The **minimum detectable effect (MDE)**: the smallest change from the baseline that you want to detect. A smaller MDE needs a larger sample.

(b) Any two (1 mark each):

- Statistical significance is not practical significance. A very small uplift can be significant and still not be worth the cost.
- Downstream metrics. The tested metric can go up while a later metric goes down (upgrades +10% but lifetime value −30%).
- Local maximum. Testing one small variable at a time can miss a much better design.
- Not enough sample or time, outlier events such as holidays, wrong instrumentation or bugs.

### C6 (4 marks)

One mark each (name + question):

1. **Descriptive** analytics: what happened?
2. **Diagnostic** analytics: where and why did it happen?
3. **Predictive** analytics: what might happen?
4. **Prescriptive** analytics: what should we do?

## Part D answers

### D1 (11 marks)

Distance: d = √((x − cx)² + (y − cy)²)

**(a) Iteration 1, centroids c1 = (1, 1), c2 = (2, 1) (4 marks)**

| Point | Distance to c1 | Distance to c2 | Cluster |
|---|---|---|---|
| A (1, 1) | 0 | 1.00 | 1 |
| B (2, 1) | 1.00 | 0 | 2 |
| C (4, 3) | √(9 + 4) = 3.61 | √(4 + 4) = 2.83 | 2 |
| D (5, 4) | √(16 + 9) = 5.00 | √(9 + 9) = 4.24 | 2 |
| E (1, 2) | √(0 + 1) = 1.00 | √(1 + 1) = 1.41 | 1 |
| F (4, 4) | √(9 + 9) = 4.24 | √(4 + 9) = 3.61 | 2 |

Cluster 1 = {A, E}. Cluster 2 = {B, C, D, F}. Distances (3), assignment (1).

**(b) New centroids (2 marks)**

- c1 = mean of A and E = ((1 + 1)/2, (1 + 2)/2) = **(1, 1.5)** (1)
- c2 = mean of B, C, D, F = ((2 + 4 + 5 + 4)/4, (1 + 3 + 4 + 4)/4) = **(3.75, 3)** (1)

**(c) Iteration 2 (3 marks)**

| Point | Distance to c1 (1, 1.5) | Distance to c2 (3.75, 3) | Cluster |
|---|---|---|---|
| A (1, 1) | 0.50 | 3.40 | 1 |
| B (2, 1) | √(1 + 0.25) = 1.12 | √(3.0625 + 4) = 2.66 | **1** (moved) |
| C (4, 3) | 3.35 | 0.25 | 2 |
| D (5, 4) | 4.72 | 1.60 | 2 |
| E (1, 2) | 0.50 | 2.93 | 1 |
| F (4, 4) | 3.91 | 1.03 | 2 |

Cluster 1 = {A, B, E}. Cluster 2 = {C, D, F}. (2)

New centroids: c1 = ((1 + 2 + 1)/3, (1 + 1 + 2)/3) = **(1.33, 1.33)**. c2 = ((4 + 5 + 4)/3, (3 + 4 + 4)/3) = **(4.33, 3.67)**. (1)

**(d) Convergence (1 mark)**

Iteration 3 with the new centroids:

| Point | Distance to c1 | Distance to c2 | Cluster |
|---|---|---|---|
| A | 0.47 | 4.27 | 1 |
| B | 0.75 | 3.54 | 1 |
| C | 3.14 | 0.75 | 2 |
| D | 4.53 | 0.75 | 2 |
| E | 0.75 | 3.73 | 1 |
| F | 3.77 | 0.47 | 2 |

No point changes cluster, so the algorithm has converged. **Final clusters: {A, B, E} (few visits, low spending) and {C, D, F} (many visits, high spending).**

Extra (not asked): SSE = 0.22 + 0.56 + 0.56 + 0.56 + 0.56 + 0.22 = 2.67.

**(e) One limitation (1 mark)** Any one:

- K must be chosen before the algorithm runs.
- It has problems when the clusters have different sizes, different densities or non-globular shapes.
- Outliers pull the centroids.
- The result depends on the initial centroids.

### D2 (12 marks)

**(a) Pearson similarity (6 marks, 2 per pair)**

sim(a, b) = Σ(ra − r̄a)(rb − r̄b) / [√Σ(ra − r̄a)² × √Σ(rb − r̄b)²], over the items that both users rated (Items 1, 2, 3).

Amy: mean of (5, 3, 4) = 4. Deviations: (1, −1, 0). √Σ² = √2 = 1.414.

**Ben:** mean of (4, 2, 3) = 3. Deviations: (1, −1, 0).

- Numerator = (1)(1) + (−1)(−1) + (0)(0) = 2
- Denominator = √2 × √2 = 2
- **sim(Amy, Ben) = 1.00**

**Cat:** mean of (2, 5, 1) = 2.667. Deviations: (−0.667, 2.333, −1.667).

- Numerator = (1)(−0.667) + (−1)(2.333) + (0)(−1.667) = −3.00
- Denominator = √2 × √(0.444 + 5.444 + 2.778) = 1.414 × 2.944 = 4.163
- **sim(Amy, Cat) = −0.72**

**Dan:** mean of (5, 4, 4) = 4.333. Deviations: (0.667, −0.333, −0.333).

- Numerator = (1)(0.667) + (−1)(−0.333) + 0 = 1.00
- Denominator = √2 × √(0.444 + 0.111 + 0.111) = 1.414 × 0.816 = 1.155
- **sim(Amy, Dan) = 0.87**

**(b) Prediction (3 marks)**

The two most similar users are Ben (1.00) and Dan (0.87). Cat has the opposite taste (negative similarity) and is left out. (1)

pred(Amy, Item 4) = r̄Amy + Σ sim(Amy, b)(r(b, Item 4) − r̄b) / Σ sim(Amy, b)

- r̄Amy = 4. r̄Ben = (4 + 2 + 3 + 4)/4 = 3.25. r̄Dan = (5 + 4 + 4 + 5)/4 = 4.5. (1)
- pred = 4 + [1.00 × (4 − 3.25) + 0.866 × (5 − 4.5)] / (1.00 + 0.866)
- = 4 + (0.75 + 0.433) / 1.866
- = 4 + 0.634 = **4.63** (1)

The slides use each neighbour's average over all of that neighbour's ratings in this step (in the Alice example, User1's 2.4 and User2's 3.8). Follow the slides.

**(c) Recommend? (1 mark)**

Yes. The predicted rating (4.63) is higher than Amy's own average (4) and near the top of the scale, so Item 4 should be recommended.

**(d) Adjusted cosine (2 marks)**

sim(i, j) = Σu (r(u,i) − r̄u)(r(u,j) − r̄u) / [√Σ(r(u,i) − r̄u)² × √Σ(r(u,j) − r̄u)²], over the users who rated both items (Ben, Cat, Dan). r̄u is the **user's** average.

| User | r̄u | Item 1 − r̄u | Item 4 − r̄u |
|---|---|---|---|
| Ben | 3.25 | 0.75 | 0.75 |
| Cat | 2.5 | −0.5 | −0.5 |
| Dan | 4.5 | 0.5 | 0.5 |

- Numerator = 0.5625 + 0.25 + 0.25 = 1.0625 (1)
- Denominator = √1.0625 × √1.0625 = 1.0625
- **sim(Item 1, Item 4) = 1.00** (1)

The two columns of deviations are identical: every user rated Item 1 and Item 4 the same way compared with his own average. So an item-based system would also predict a high rating, because Amy gave Item 1 a 5.

### D3 (12 marks)

**(a) Five components (10 marks: 2 per component, 1 for what it is, 1 for its objective or function)**

1. **Integrated front office.** The customer-facing part: marketing, sales and customer service, supported by customer engagement centres, sales force automation and the Internet (1). Objective: it provides complete customer profiles to all customer-facing persons, so every employee sees the same full picture of the customer (1).
2. **Business intelligence (BI) system.** It captures information from all customer touch points and stores it in data warehouses and data marts (1). Function: data mining and analytic tools let the company segment its customer base, attach a value to each segment, and differentiate its service and messages for each group (1).
3. **Workflow and business rules.** They sit between the BI system and the front office and transmit the business intelligence to front-office personnel (1). Objective: the staff understand the value they can give each customer when they answer a request or try to retain the customer (1).
4. **Physical links to the back office and external systems.** They connect the front office to systems such as inventory control and accounts receivable (1). Objective: front-office staff can make fulfilment promises that the company can keep, for example a delivery date (1).
5. **Performance metrics.** A set of measures over the whole system (1). Objective: they let the company determine the success of its CRM efforts and the value of each customer, for example acquisition, retention, satisfaction and profit (1).

**(b) Touch point (2 marks)** One mark for the touch point, one for the improvement. Examples:

- Browsing the website (1). Personalisation: the BI system uses past views and purchases to show recommendations and offers that fit this customer (1).
- Post-purchase service (1). Integrated service tools: the agent or chatbot sees the 360-degree view of the customer and the order status, so the customer does not need to repeat the story and gets a correct answer at once (1).
- Purchase (1). Automation: a saved profile and one-click checkout, then automatic order and delivery updates (1).

---

## Your score

| Part | Your marks | Out of |
|---|---|---|
| A | | 25 |
| B | | 10 |
| C | | 30 |
| D | | 35 |
| Total | | 100 |

Compare with Mock A. If Part D was much weaker here, spend the last day on note 10 (k-means and collaborative filtering) and redo D1 and D2 from a blank page.
