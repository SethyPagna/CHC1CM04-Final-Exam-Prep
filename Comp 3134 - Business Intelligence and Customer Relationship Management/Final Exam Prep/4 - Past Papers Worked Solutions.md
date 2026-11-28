# COMP3134 Past Papers — Worked Solutions

> Every long question from the 2025-26 final, the 2024-25 final and the 2024 mid-term, with the data, the answer and the marks.
> The official marking scheme exists only for the mid-term. For the two finals the answers are mine: every number was recomputed by program, and the mark splits are estimates.
> How to use this file: cover the answer, do the question on paper with only your cheat sheet, then compare line by line.

Where the past MCQs are: each lecture note lists the past MCQs for that lecture in its section "How this lecture is examined".

## Contents

1. 2025-26 final — Q21 measurement and frequency table · Q22 paired t-test · Q23 ID3 tree · Q24 Apriori · Q25 customer segments
2. 2024-25 final — Q21 when CRM is not worthwhile · Q22 CRM architecture · Q23 descriptive statistics · Q24 ID3 tree
3. Mid-term 2024 — B1 to B4 with the official marking scheme
4. 2023-24 final (older syllabus) — what is still useful

---

## 1. 2025-26 final (3 hours, 20 MCQ + 5 long questions = 80 marks)

The paper said: round to 2 decimal places. Appendix I gave the t-test formulas, entropy and information gain, adjusted cosine similarity, support and confidence. This year the formulas may not be given.

### Q21 (10 marks) — levels of measurement and a frequency table

**(a) (4 marks) Give the level of measurement. If the data are quantitative, say discrete or continuous.**

| Item | Level | Discrete / continuous | Reason |
|---|---|---|---|
| Eye colours of students in your class | Nominal | Not applicable (qualitative) | Names only, no order |
| Pulse rates of male students | Ratio | Discrete | Beats are counted. Zero means no pulse. |
| Body temperatures (in degrees) | Interval | Continuous | Measured. Zero degrees does not mean "no temperature". |
| Ages (in years) of homes sold | Ratio | Continuous | Time is measured. A 20-year-old home is twice as old as a 10-year-old home. |
| Age brackets (under 30, 30–49, 50–64, over 64) | Ordinal | Not applicable | Ordered categories |

**(b) (5 marks) Waiting times in minutes of 20 patients. Complete the table and sketch the cumulative frequency chart.**

Data: 2, 10, 4, 5, 11, 9, 12, 6, 7, 18, 5, 12, 4, 17, 8, 8, 21, 8, 13, 3.

| Class (minutes) | Values | Frequency | Relative frequency | Cumulative frequency |
|---|---|---|---|---|
| 0–4 | 2, 4, 4, 3 | 4 | 4/20 = 0.20 | 4 |
| 5–9 | 5, 9, 6, 7, 5, 8, 8, 8 | 8 | 0.40 | 12 |
| 10–14 | 10, 11, 12, 12, 13 | 5 | 0.25 | 17 |
| 15–19 | 18, 17 | 2 | 0.10 | 19 |
| 20–24 | 21 | 1 | 0.05 | 20 |
| Total | | 20 | 1.00 | |

The chart: x-axis = waiting time (upper class limits 4, 9, 14, 19, 24). y-axis = cumulative frequency. Plot (4, 4), (9, 12), (14, 17), (19, 19), (24, 20) and join the points. The line never goes down. Label both axes.

**(c) (1 mark) How many patients waited 14 minutes or less?** The cumulative frequency of the class 10–14 = **17 patients**.

Full teaching: [note 07](Lecture%20notes/07%20-%20BI2%20Data%20and%20Statistics.md), Parts 3 and 7.

### Q22 (10 marks) — paired t-test

30 students take a standardised exam before an online study-skills workshop and a similar exam 8 weeks later. Mean difference (after − before) = 2 points. Standard deviation of the differences = 1 point. Critical value at 0.05 = 1.699. Is there a significant increase?

**(a) (3 marks) Test and hypotheses**

1. Paired-samples t-test, because the same 30 students are measured twice. (1)
2. H0: the mean difference is zero (μd = 0). (1)
3. H1: the mean difference is greater than zero (μd > 0). One-tailed, because the question says "increase". (1)

**(b) (5 marks) Carry out the test**

1. α = 0.05, df = n − 1 = 29, critical value = 1.699 (one-tailed). (1)
2. Standard error = sd / √n = 1 / √30 = 0.1826. (1)
3. t = (x̄d − 0) / (sd / √n) = 2 / 0.1826 = **10.95**. (1)
4. 10.95 > 1.699, so reject H0. (1)
5. Conclusion: there is a significant increase in the exam scores after the workshop. (1)

**(c) (2 marks) The result is significant, but the university is still not happy. Why?**

1. Statistical significance is not practical significance. The gain is only 2 points, which may be too small to matter or to justify the cost of the workshop. (1)
2. There is no control group, so the gain may come from 8 more weeks of normal study or from practice with a similar exam. (1)

Full teaching: [note 08](Lecture%20notes/08%20-%20BI3%20Hypothesis%20Testing%20and%20AB%20Testing.md).

### Q23 (20 marks) — ID3 decision tree

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

**(a) (10 marks) Information gain of Temperature**

1. The whole set has 4 Yes and 4 No. H(S) = −(4/8)log₂(4/8) − (4/8)log₂(4/8) = **1**.
2. The subsets:

| Temperature | IDs | Yes | No | Entropy |
|---|---|---|---|---|
| Hot | 1, 2, 3 | 1 | 2 | −(1/3)log₂(1/3) − (2/3)log₂(2/3) = 0.918 |
| Mild | 4, 8 | 1 | 1 | 1 |
| Cool | 5, 6, 7 | 2 | 1 | 0.918 |

3. Weighted entropy = (3/8)(0.918) + (2/8)(1) + (3/8)(0.918) = 0.344 + 0.250 + 0.344 = 0.939.
4. **Gain(Temperature) = 1 − 0.939 = 0.06.**

**(b) (6 marks) Root and first split.** The paper gave Gain(Weather) = 0.656 and Gain(Humidity) = 0.046. Weather is the largest, so Weather is the root.

```
                    Weather
        ┌──────────────┼──────────────┐
      Sunny         Overcast         Rainy
    IDs 1, 2, 8     IDs 3, 7      IDs 4, 5, 6
    all No → leaf  all Yes → leaf  2 Yes, 1 No → split again
```

Note: Gain(Humidity) is 0.049 when you compute it. The paper printed 0.046. When a paper gives a value, use the paper's value.

**(c) (4 marks) Training accuracy 90%, test accuracy 60%. Explain and give two fixes.**

1. The tree is overfitting: it has learned the training data too well, including the noise, so it does not work on new data. (1)
2. Cause: ID3 grows every branch until the training examples are classified perfectly. A deeper tree overfits more. (1)
3. Fix 1, pre-pruning: stop growing early, for example a maximum depth or a minimum number of instances in a subset. (1)
4. Fix 2, post-pruning: build the full tree, then replace a subtree by a leaf when the accuracy is not worse (subtree replacement), or use subtree raising. (1)

Full teaching: [note 09](Lecture%20notes/09%20-%20BI4%20Data%20Mining%201%20-%20Regression%20Classification%20Decision%20Trees.md).

### Q24 (25 marks) — Apriori

| TID | Items |
|---|---|
| T1 | Laptop, Headphones, T-shirt |
| T2 | Laptop, Headphones, Coffee |
| T3 | Laptop, Smartphone, Headphones |
| T4 | Headphones, Jeans, Coffee |
| T5 | Laptop, Headphones, Jeans |

Minimum support = 60% (a count of at least 3). Minimum confidence = 90%.

**(a) (15 marks) Trace Apriori to the 2-itemsets**

Step 1, C1:

| Item | Count | Support | Frequent? |
|---|---|---|---|
| Laptop | 4 | 80% | Yes |
| Headphones | 5 | 100% | Yes |
| T-shirt | 1 | 20% | No |
| Coffee | 2 | 40% | No |
| Smartphone | 1 | 20% | No |
| Jeans | 2 | 40% | No |

Step 2, L1 = {Laptop}, {Headphones}.

Step 3, C2 = {Laptop, Headphones}. No pair with T-shirt, Coffee, Smartphone or Jeans is generated, because an itemset with an infrequent subset cannot be frequent (Apriori principle).

Step 4, count: {Laptop, Headphones} is in T1, T2, T3, T5 → count 4 → support 80% → frequent.

Step 5, L2 = {Laptop, Headphones}. No 3-itemset can be formed. Stop.

**(b) (6 marks) Rules**

| Rule | Support | Confidence | Passes 90%? |
|---|---|---|---|
| Laptop → Headphones | 4/5 = 80% | 4/4 = 100% | Yes |
| Headphones → Laptop | 4/5 = 80% | 4/5 = 80% | No |

Only **Laptop → Headphones** passes.

**(c) (4 marks) Suggestions** (any four)

1. Cross-sell: when a customer puts a laptop in the cart, recommend headphones.
2. Bundle: sell a laptop + headphones set, or give a headphone discount with a laptop.
3. Direction matters: do not push laptops to every headphone buyer. That rule has only 80% confidence.
4. Follow-up: send a headphone offer by e-mail or app after a laptop purchase.
5. Use more data or a lower minimum support to find rules for the less frequent items. A rule shows co-occurrence, not causality.

Full teaching: [note 10](Lecture%20notes/10%20-%20BI5%20Data%20Mining%202%20-%20Clustering%20Association%20Rules%20Recommenders.md).

### Q25 (15 marks) — customer segments and CRM

| Segment | Customers | Average annual revenue (HKD) | Average annual cost to serve (HKD) | Retention |
|---|---|---|---|---|
| VIP Premium | 3,000 | 8,500 | 1,200 | 92% |
| Regular Online Shoppers | 45,000 | 2,800 | 450 | 65% |
| Social Media Buyers | 52,000 | 1,200 | 380 | 42% |
| Occasional Bargain Hunters | 35,000 | 650 | 420 | 25% |
| One-time Purchasers | 15,000 | 380 | 350 | 8% |
| Total | 150,000 | | | |

**(a) (4 marks) Annual profit contribution of each segment**

| Segment | Profit per customer | Segment profit (HKD) | Share of profit | Share of customers |
|---|---|---|---|---|
| VIP Premium | 8,500 − 1,200 = 7,300 | 3,000 × 7,300 = 21,900,000 | 12.2% | 2.0% |
| Regular Online Shoppers | 2,800 − 450 = 2,350 | 45,000 × 2,350 = 105,750,000 | 59.1% | 30.0% |
| Social Media Buyers | 1,200 − 380 = 820 | 52,000 × 820 = 42,640,000 | 23.8% | 34.7% |
| Occasional Bargain Hunters | 650 − 420 = 230 | 35,000 × 230 = 8,050,000 | 4.5% | 23.3% |
| One-time Purchasers | 380 − 350 = 30 | 15,000 × 30 = 450,000 | 0.3% | 10.0% |
| Total | | **178,790,000** | 100% | 100% |

**(b) (4 marks) Pareto: which segments are the "top 20%"? Justify with lifetime value and differential treatment.**

- 20% of 150,000 = 30,000 customers. Rank by profit per customer: all 3,000 VIP Premium, then 27,000 Regular Online Shoppers.
- Their profit = 21,900,000 + 27,000 × 2,350 = 85,350,000 = 47.7% of the total.

1. The top 20% are VIP Premium plus the best part of Regular Online Shoppers. These two segments get the priority. (1)
2. Pareto holds roughly, not exactly: the two segments are 32% of the customers and give 71.4% of the profit. The bottom two segments are 33.3% of the customers and give 4.8%. (1)
3. Lifetime value: the two segments have the highest profit per customer (7,300 and 2,350) and the highest retention (92% and 65%), so the profit repeats for more years. (1)
4. Differential treatment (tiered servicing): high-cost, personal methods for them (VIP status, relationships, "surprises"). Low-cost methods for the others (automation, AI, self-service). (1)

**(c) (4 marks) Two touch points and how CRM technology improves each**

1. Browsing the website or app (1). Personalisation: recommendations and offers from the customer's own history (1).
2. Post-purchase service (1). Integrated service tools: the agent or chatbot sees the full customer profile and the order, so the customer does not repeat the story (1).

**(d) (3 marks) Occasional Bargain Hunters: de-marketing or migration?**

1. De-marketing = weaken or extinguish demand when customers are unprofitable (minimum order size, extra charges). (1)
2. This segment is still profitable: HKD 230 each, 8.05 million in total. But the cost to serve takes about 65% of the revenue, and retention is only 25%. (1)
3. So recommend migration first: move them to low-cost self-service channels and move the better ones up to Regular Online Shoppers. Keep de-marketing for those who stay unprofitable. Sudden de-marketing risks negative word-of-mouth. (1)

Full teaching: [note 04](Lecture%20notes/04%20-%20CRM3%20Segmentation%20Targeting%20and%20Customer%20Value.md).

---

## 2. 2024-25 final (2 hours, 20 MCQ = 40% + 4 long questions = 60%)

### Q21 (10 marks) — four business situations where heavy CRM investment is not worthwhile

The slides have no list with this title. This answer is built from slide points. Estimate: 2.5 marks per situation (name it, say why, give an example).

1. **The exchange is only a transaction.** The product is discrete and functional (shoelaces, office supplies). The customer does not value a relationship, so a better 4 Ps mix is enough.
2. **The company has no contact with the final customer.** A manufacturer sells through middlemen. There are no touch points, so there is no customer data to collect and nobody to personalise for.
3. **There is no competition and no segmentation.** A monopoly such as water or electricity. Loyalty is a defence against competitors. If the customer cannot leave, retention spending brings little.
4. **Every customer gives about the same profit (shallow value skew).** CRM works by separating profitable from unprofitable customers. If all are worth the same, there is no key group to find. Cutting costs with automation is better.

Spare situations: always-a-share products where switching is easy · the organisation is not ready (culture, no plan, no metrics, the system is not used) · the customer data are poor.

### Q22 (15 marks) — the basic architecture of a CRM system

3 marks per component. This is the same answer as Mock Exam B, question D3.

1. **Integrated front office**: marketing, sales and service with engagement centres, sales force automation and the Internet. It provides complete customer profiles to all customer-facing persons.
2. **Business intelligence system**: captures information from all touch points. Data warehouses and data marts store it. Data mining segments the customer base, attaches a value to each segment and differentiates the messages.
3. **Workflow and business rules**: transmit BI to the front-office personnel, so they understand the value they can give each customer.
4. **Physical links to the back office**: inventory control, accounts receivable. Front-office staff can make fulfilment promises that the company can keep.
5. **Performance metrics**: show the success of the CRM efforts and the value of each customer.

Full model answer with all 15 points: [note 02](Lecture%20notes/02%20-%20CRM1%20CRM%20Strategy%20Processes%20and%20Technology.md).

### Q23 (15 marks) — descriptive statistics of 27 ages

Sorted data (n = 27): 13, 15, 16, 16, 19, 20, 20, 21, 22, 22, 25, 25, 25, 25, 30, 33, 33, 35, 35, 35, 35, 36, 40, 45, 46, 52, 70.

| Part | Working | Answer |
|---|---|---|
| Mean | Σx = 809. 809 / 27 | 29.96 |
| Median | (27 + 1)/2 = 14th value | 25 |
| Mode | 25 appears 4 times and 35 appears 4 times | 25 and 35 |
| Modality | Two modes | Bimodal |
| Midrange | (13 + 70)/2 | 41.5 |
| Q1 and Q3 | Q1 = (27 + 1)/4 = 7th value. Q3 = 3 × 28/4 = 21st value | Q1 = 20, Q3 = 35 |
| Variance and SD | Σx² = 28,595. Σ(x − x̄)² = 28,595 − 809²/27 = 4,354.96. s² = 4,354.96 / 26 | s² = 167.50, s = 12.94 |

Extra line worth a mark: mean (29.96) > median (25), so the data are positively skewed (the value 70 pulls the mean up).

Trap: dividing by n gives 12.70. The slides use n − 1.

### Q24 (20 marks) — ID3 on the buys_computer table

| RID | age | income | student | credit_rating | buys_computer |
|---|---|---|---|---|---|
| 1 | ≤30 | high | no | fair | no |
| 2 | ≤30 | high | no | excellent | no |
| 3 | 31…40 | high | no | fair | yes |
| 4 | >40 | medium | no | fair | yes |
| 5 | >40 | low | yes | fair | yes |
| 6 | >40 | low | yes | excellent | no |
| 7 | 31…40 | low | yes | excellent | yes |
| 8 | ≤30 | medium | no | fair | no |
| 9 | ≤30 | low | yes | fair | yes |
| 10 | >40 | medium | yes | fair | yes |
| 11 | ≤30 | medium | yes | excellent | yes |
| 12 | 31…40 | medium | no | excellent | yes |
| 13 | 31…40 | high | yes | fair | yes |
| 14 | >40 | medium | no | excellent | no |

(This is the standard 14-record table from the lecture. The class has 9 yes and 5 no.)

H(S) = −(9/14)log₂(9/14) − (5/14)log₂(5/14) = 0.410 + 0.530 = **0.940**

| Attribute | Value: (yes, no) → entropy | Weighted entropy | Gain |
|---|---|---|---|
| age | ≤30: (2, 3) → 0.971 · 31…40: (4, 0) → 0 · >40: (3, 2) → 0.971 | (5/14)(0.971) + (4/14)(0) + (5/14)(0.971) = 0.694 | **0.25** |
| income | high: (2, 2) → 1 · medium: (4, 2) → 0.918 · low: (3, 1) → 0.811 | (4/14)(1) + (6/14)(0.918) + (4/14)(0.811) = 0.911 | 0.03 |
| student | no: (3, 4) → 0.985 · yes: (6, 1) → 0.592 | (7/14)(0.985) + (7/14)(0.592) = 0.788 | 0.15 |
| credit_rating | fair: (6, 2) → 0.811 · excellent: (3, 3) → 1 | (8/14)(0.811) + (6/14)(1) = 0.892 | 0.05 |

**age has the highest gain, so age is the root.** The branch 31…40 is pure (all yes) and becomes a leaf. The branches ≤30 and >40 are split again.

---

## 3. Mid-term 2024 (10 MCQ + 4 questions, official marking scheme)

The scheme gives one mark per correct point.

### B1 (10 marks)

**(a) Define CRM (3)**

1. A strategic approach concerned with creating improved shareholder value (1)
2. through the development of appropriate relationships with key customers and customer segments. (1)
3. CRM unites relationship marketing strategies and IT to create profitable, long-term relationships. (1)

**(b) Five key processes (5)**: strategy development · value creation · multichannel integration · information management · performance assessment. One mark each with a short explanation.

**(c) Why cross-functional integration is essential (2)**: seamless coordination between marketing, sales and customer service (1). A consistent customer experience across all departments and channels (1).

### B2 (10 marks)

**(a) Pareto principle (2)**: the top 20% of customers account for 80% of profits (1). It is also called the iceberg principle (1).

**(b) 150–20 rule (2)**: the 20% most profitable customers generate up to 150% of profits (1). The 20% least profitable customers lose 100% of profits (1).

**(c) Three tiered-servicing strategies (3)**: different service levels, low-cost methods for the 80% low-profit customers and high-cost personal service for the 20% (1). VIP status and strong relationships when the base has a steep value skew (1). Cost reduction through automation and AI when the base has a shallow value skew (1).

**(d) De-marketing (3)**: attempts to weaken or extinguish demand when customers are unprofitable (1). Examples: minimum order sizes (1), high admittance charges or extra charges for unprofitable usage (1).

### B3 (10 marks) — LUX Bank

**(a) Three service tiers (6)**: Tier 1 premium, the top 20%: VIP treatment, a relationship manager. Tier 2 standard, the middle 30%: balanced service, cross-selling. Tier 3 basic, the bottom 50%: chatbots and self-service. Two marks per tier (who + how they are served).

**(b) Two strategies to prevent downward migration (4)**: proactive monitoring, BI gives an early warning when a customer's activity falls (2). Relationship strengthening: a personal banker, priority service, fee waivers, exclusive events (2).

### B4 (10 marks)

**(a) Five BI steps for CPV analysis (5)**: (1) ask customers and collect data on the attributes and performance levels they look for. (2) classify and cluster the importance of the attributes. (3) assess the company and its competitors on the attributes against their importance. (4) analyse the segments. (5) repeat periodically, because customer values change.

**(b) CPV and sustainable competitive advantage (2)**: understanding CPV (total customer benefit − total customer cost) helps a company differentiate its offering against the competitive alternatives (1). By delivering superior perceived value, the company achieves a sustainable competitive advantage in its target markets (1).

**(c) Place Divine, Green & Black's and Kinder on a quality × price map (3, one per brand)**: Green & Black's = premium brand, high quality and high price (upper right) (1). Divine = premium, ethical brand, high quality and high price (upper right) (1). Kinder = mass snack for children, lower price and lower quality (lower left) (1). Write the reason next to each dot. More in [note 04](Lecture%20notes/04%20-%20CRM3%20Segmentation%20Targeting%20and%20Customer%20Value.md).

Mid-term MCQ answers that are worth remembering: de-marketing → reduce demand from unprofitable customers · humanistic bonds → personal service for profitable customers · a stable relationship → relational · evaluating changing preferences over time → longitudinal studies · the model that creates consumer dependency on a suite of products → ecosystem · Pareto → 80% of profits from 20% of customers.

---

## 4. 2023-24 final (older syllabus, another lecturer)

Most of this paper is outside this year's slides (star schema, cluster profiling, loyalty dimensions, SEO). Do not spend time on those. The items below still match this year's slides.

| Item on the 2023-24 paper | Short answer from this year's slides | Note |
|---|---|---|
| Three types of CRM | Operational (transactions, data collection), analytical (analysis), social (relationships, engagement) | 02 |
| Primary data and secondary data | Primary = collected for the first time. Secondary = already collected for another purpose. | 06 |
| OLAP | Analysis of data in the data warehouse, with queries and reports. OLTP = routine transactions. | 01 |
| Applications of data mining | Classification (approve a loan), regression (forecast sales), clustering (segment customers), association (items bought together), recommendation | 09, 10 |
| Social media strategy against social CRM strategy | Social media strategy uses the channels for promotion and awareness. Social CRM uses the interactions and the data to build relationships with individual customers. | 05 |
| Where to get customer data for analytical CRM | All customer touch points: transactions, website and app, engagement centre, sales staff, surveys, social media, secondary sources | 02, 06 |
| CRM project against CRM process | Process = the five ongoing key processes. Project = the six-step timeline to build the CRM programme. (My own synthesis; the slides do not compare them.) | 02 |
