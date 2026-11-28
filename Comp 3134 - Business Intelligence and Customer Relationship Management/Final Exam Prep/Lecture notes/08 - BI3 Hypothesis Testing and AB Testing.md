# BI3 — Hypothesis Testing and A/B Testing (teaching week 8)

> **Built from:** all 55 slides of "Week 10 - BI&CRM SS-25-26 Lecture BI3.pdf", text and pictures.
> **Exam weight:** high. The 2025-26 final Q22 (10 marks) was a paired-samples t-test: name the test and hypotheses (3), run it with steps (5), explain why a significant result may still disappoint (2). Last year the three t formulas were printed in the appendix. **This year equations may not be provided — put all three on your A4 sheet.** A t-table is likely to be in the appendix ("necessary tables will be provided").

---

## The lecture in one minute

- We measure a **sample**, so there is **sampling error**. A hypothesis test answers: "Is this difference **real**, or just sampling error?"
- Three t-tests: **one-sample** (sample vs a standard), **independent-samples** (two different groups), **paired-samples** (same people measured twice).
- Always start from the **null hypothesis H0: "no difference"** and look for evidence to **reject** it in favour of **H1**.
- Compute **t = difference ÷ standard error**. Compare |t| with the **critical value** from the t-table (significance level α, degrees of freedom df). If |t| is bigger → **reject H0**.
- Two possible mistakes: **Type I** (reject a true H0, probability α) and **Type II** (fail to reject a false H0, probability β). Power = 1 − β.
- **A/B testing** = an independent-samples test on two versions of a web page, e-mail, ad, etc. Six steps in a cycle.
- **Statistically significant ≠ practically important.**

| Test | Compares | H0 | t formula | df |
|---|---|---|---|---|
| One-sample | Sample mean vs reference value μ | Sample mean = reference value | t = (x̄ − μ) / (s / √n) | n − 1 |
| Independent-samples | Means of two separate groups | Means of the two groups are equal | t = (x̄₁ − x̄₂) / √(s₁²/n₁ + s₂²/n₂) | n₁ + n₂ − 2 |
| Paired-samples | Before vs after on the same subjects | Mean of the differences = 0 | t = (x̄d − 0) / (s_d / √n) | n − 1 (n = number of pairs) |

---

## Words you need

| Term | Slide wording | In plain words |
|---|---|---|
| **Hypothesis testing** | "a fundamental statistical method for inferring population parameters based on sample data" | A recipe for deciding if a sample result is real |
| **Sampling error** | "the true population condition may be different from the result obtained from the sample" | The sample is never a perfect copy of the population |
| **Null hypothesis H0** | "says nothing is happening, nothing is different" | The boring default: no effect |
| **Alternative hypothesis H1** | What you accept if you reject H0 | There is an effect / a difference |
| **t-value** | "difference between mean values ÷ standard deviation from the mean (standard error)" | How many standard errors apart the means are |
| **Significance level α** | "the cutoff we can tolerate"; "usually 5% (0.05)" | The risk of a false alarm you accept |
| **Critical t-value** | Read from the table using α and df | The line |t| must cross |
| **Degrees of freedom (df)** | df = n − 1 for one sample | Sample size minus the number of means estimated |
| **p-value** | "how likely it is that your data could have occurred under the null hypothesis" | Small p (< 0.05) → reject H0 |
| **Type I error** | "Rejects a true null hypothesis" | False alarm |
| **Type II error** | "Fails to reject a false null hypothesis" | Missed a real effect |
| **Power** | 1 − β | Chance of detecting a real effect |
| **A/B testing** | "compare two versions (A and B) of a variable … to determine which one performs better in terms of a specified metric" | A controlled experiment on two versions |
| **MDE** | Minimum detectable effect: "how much change from the baseline you want to detect" | The smallest lift you care about |

---

## Part 1 — Why test? (slides 2–4)

- We have hypotheses about the target population, but "instead of asking every one (census), we usually research only **a sample**".
- A **probability sample** is required: only a representative sample "allows us to do inductive reasoning (generalization)".
- "So there is **sampling error**." Statistical testing concludes "what the population characteristics are likely to be".
- The motivating question (slide 4): "Is there a **significant difference** between 2 groups? Or just an error?"

## Part 2 — The three types of test ★★ (slides 5–9)

| Type | Slide description | Slide example |
|---|---|---|
| **One-sample test** | "compare your data with a gold standard" | Tissue packets claimed to weigh **100 g**; a sample of **30** packets has mean **97 g**. Is 97 significantly different from 100? |
| **Independent-samples test** | "compare two groups" | Drug A vs drug B: **60** subjects randomly split into two groups; is pain relief different? |
| **Paired-samples test** | "compare two readings from same individuals (usually at two different times)" | Weigh the **same 30 people** before and after a diet (a "dependent t-test") |

- "The t-test is a statistical test for comparing the means of two samples."
- The **Z-test** is "used for larger sample and known variance".

**How to choose in the exam — two questions:**

1. Is there **one** group compared with a **fixed number** (a claim, a target, a standard)? → **one-sample**.
2. Two sets of numbers: do they come from the **same subjects** (before/after, matched pairs)? → **paired**. From **different subjects**? → **independent**.

## Part 3 — What makes a hypothesis (slides 10–15) ★

- **Scientific statements** "can be verified and tested with reference to empirical evidence". "Cats are better than dogs" is not testable; "cats are better than dogs **at climbing trees**" is.
- "A good hypothesis is a **falsifiable** hypothesis." "All horses are white" can never be proved by looking (some horse may be hidden) — "the absence of evidence is not evidence of absence". But **one** black horse rejects it.
- So we set up the **null hypothesis** ("nothing is happening") and look for evidence to **reject** it. "Our work is easier and concrete when going to reject the null hypothesis."

**Hypotheses for each test (slides 13–15) — write them exactly like this:**

| Test | H0 | H1 |
|---|---|---|
| One-sample | The sample mean **is equal** to the reference value (no difference) | The sample mean **is not equal** to the reference value |
| Independent | The means in the two groups **are equal** | The means in the two groups **are not equal** |
| Paired | The mean of the differences between the pairs **is zero** | The mean of the differences **is non-zero** |

In symbols: one-sample H0: μ = μ₀; independent H0: μ₁ = μ₂; paired H0: μd = 0.

**One-tailed or two-tailed? (extra, not on the slides, but used in the 2025-26 paper)** The slides write every H1 as "not equal" (two-tailed). If the question asks about a **direction** ("significant **increase**", "better", "lower") write H1 with > or < and use the **one-tailed** critical value. The 2025-26 paper asked for "a significant increase" and gave the one-tailed value 1.699.

## Part 4 — Computing and reading t ★★ (slides 16–25)

**The idea (slides 16–20).** Every sample varies, so the difference is almost never exactly zero. The t-test measures "at what difference level we can say there is a significant difference".

```
        difference between mean values
t  =  ----------------------------------
        standard error (spread of the mean)
```

- t gets **larger** when the difference between the means is larger.
- t gets **smaller** when the data are more spread out: "the greater the scatter of the data, the less a given mean difference matters".

**The three formulas (slides 19, 25) — memorise or put on the sheet:**

```
One-sample          t = ( x̄ − μ ) / ( s / √n )                   df = n − 1

Independent samples t = ( x̄₁ − x̄₂ ) / √( s₁²/n₁ + s₂²/n₂ )       df = n₁ + n₂ − 2

Paired samples      t = ( x̄d − 0 ) / ( s_d / √n )                df = n − 1
                        x̄d = mean of the differences, s_d = SD of the differences, n = number of pairs
```

**Decision (slides 21–23).** Compare the calculated t with the **critical t-value** from the table.

- Need two things to read the table: the **significance level** (usually 0.05) and the **degrees of freedom**.
- Slide example: α = 5%, df = 9 → critical t = **2.262**. A calculated t of 2.5 > 2.262, so "the two means are so far apart that we can reject the null hypothesis".
- **Rule: if |t calculated| > t critical → reject H0. Otherwise → do not reject H0.**

**Reading the t-table (the slide shows a "two-tailed" table).** Rows = df. Columns = α. Useful values:

| df | Two-tailed α = 0.05 | One-tailed α = 0.05 (= two-tailed column 0.10) |
|---|---|---|
| 9 | 2.262 | 1.833 |
| 17 | 2.110 | 1.740 |
| 20 | 2.086 | 1.725 |
| 29 | 2.045 | 1.699 |

If your df is not in the table, use the nearest **smaller** df (safer). For large df the two-tailed 0.05 value approaches **1.96**.

**The p-value (slide 24).** "Tells you how likely it is that your data could have occurred under the null hypothesis." If p is small enough — "usually **p < 0.05** (same as significance level)" — reject H0. It is calculated from the t-value and df (by software).

## Part 5 — Full worked example: independent samples (slides 26–30) ★★

**Caffeine and a mouse-tracking task.** Half the people get caffeine, half a placebo; "nobody knows who got what".

| | Experimental (caffeine) | Control (no caffeine) |
|---|---|---|
| n | N₁ = 9 | N₂ = 10 |
| Mean | M₁ = 9.778 | M₂ = 15.1 |
| SD | SD₁ = 4.1164 | SD₂ = 4.2805 |

1. **Set the significance level:** α = 0.05.
2. **State the hypotheses:** H0: μ₁ = μ₂ (caffeine has no effect). H1: μ₁ ≠ μ₂.
3. **Calculate the test statistic:**
   SE = √(4.1164²/9 + 4.2805²/10) = √(1.8827 + 1.8323) = **1.93**
   t = (9.778 − 15.1) / 1.93 = −5.322 / 1.93 = **−2.758**
4. **Critical value:** α = 0.05, two tails, df = 9 + 10 − 2 = **17** → **2.11**.
5. **Decision rule:** if |−2.758| > 2.11, reject the null.
6. **Conclusion:** Reject H0. The population means are different: caffeine has an effect on the motor pursuit task.

**Copy this six-step layout in the exam.** Marks are given for hypotheses, formula, substitution, df/critical value, decision, and a conclusion **in words about the context**.

### The eight-step summary (slide 31, flow chart)

1. Formulate H0 and H1.
2. Select an appropriate test.
3. Choose the level of significance α.
4. Collect data and calculate the test statistic.
5. Either (a) determine the **probability** (p-value) of the test statistic, or (b) determine the **critical value**.
6. Either (a) compare the probability with α, or (b) see whether the test statistic falls in the rejection region.
7. Reject or do not reject H0.
8. Draw a marketing research conclusion.

## Part 6 — Errors in decisions ★★ (slides 32–34)

| | H0 is really **true** | H0 is really **false** |
|---|---|---|
| **Do not reject H0** | Correct (probability 1 − α) | **Type II error (β)** |
| **Reject H0** | **Type I error (α)** | Correct — **power (1 − β)** |

- **Type I error (α):** "rejects a true null hypothesis". Its probability α is the **level of significance**, "set by researcher".
- **Type II error (β):** "fails to reject a false null hypothesis". "The power of the test is (1 − β)."
- "The two probabilities are **inversely related**. Decreasing one increases the other, for a fixed sample size."

**Jury analogy (slide 33):** H0 = innocent. Convicting an innocent person = Type I. Letting a guilty person go = Type II.

**Choosing (slide 34):** depends on the **cost** of each error. "Choose smaller Type I error when the cost of committing a Type I error is high" (criminal trial). In practice Type II is more complex, "so we would only focus on the manipulation of the Type I error, α".

**Limitations (slide 35):** the t-test or z-test "can only compare **two** groups/conditions" and "can only use **one** independent variable". **ANOVA** (analysis of variance, by Fisher) overcomes this: it compares **multiple groups at the same time**.

---

## Part 7 — A/B testing ★★ (slides 36–54)

**Definition (slide 37).** "A/B testing is primarily used in marketing, product development, and user experience research. Its purpose is to compare two versions (A and B) of a variable (e.g., a webpage, an ad, a product feature) to determine which one performs better in terms of a specified metric (e.g., click-through rate, conversion rate)."

**Why (slide 38).** It lets you understand the **causal impact** of a product change; it gives data and empirical evidence to refine performance; continuous optimisation → more effective marketing → higher ROI and revenue.

**What can be tested (slide 39):** e-mails, newsletters, advertisements, text messages, website pages, components on web pages, mobile apps.

**When to use it (slide 41) — three conditions ★:**
1. You have a **clear hypothesis**.
2. You can obtain a **sufficient sample size**.
3. You can test within a **reasonable timeframe**.

**Just-for-fun slide (40):** NVIDIA's Jensen Huang tried different clothing styles "using an A/B testing approach" before settling on the leather jacket.

### The six-step cycle ★★ (slide 42)

**Observe & metrics design → Construct hypothesis → Determine sample size → Run experiment → Analyze test results → Take action** (then back to the start).

| Step | What the slides say |
|---|---|
| **1. Observe & metrics design** (slide 43) | Study visitor behaviour (visitor records, heatmaps). Decide what to improve. Choose metrics that fit your goals. E-commerce examples: **conversion rate, average order value, subscription rate, click-through rate** |
| **2. Construct hypothesis** (slide 44) | "A/B test is an **independent samples test**." Example: enlarging the button makes it more prominent. **H0: versions A and B have the same conversion rate. H1: versions A and B have different conversion rates** |
| **3. Determine sample size** (slides 45–46) | Affects how long the test runs. "Usually has to be as large as **thousands** or more" because you need hundreds of conversions. Use an online calculator with the **baseline conversion rate** (current rate) and the **minimum detectable effect (MDE)**. Example: baseline 20%, MDE 5% → the test can detect, 80% of the time, a true rate of **19% or 21%** (20% ± 5% × 20%). Trying to detect smaller differences → the test is **underpowered** |
| **4. Run experiment** (slide 47) | **Randomly** divide users: 50% see A, 50% see B. Run for a predetermined period (say 30 days) and collect the metrics for both groups |
| **5. Analyze test results** (slides 48–49) | Does conversion differ? "Pay attention to **statistical significance**." A calculator takes **inputs**: visitors and conversions for A and B, one-sided vs two-sided hypothesis, confidence. **Outputs**: significance level / **p-value**, **relative uplift** in conversion, **observed power** ("the probability that the test correctly rejected the null hypothesis") |
| **6. Take action** (slide 50) | Clear winner → implement it. Inconclusive → "go back and rework your hypothesis" and start the next experiment |

**MDE arithmetic:** the MDE is **relative**. Baseline 20%, MDE 5% → 5% of 20% = 1 percentage point → detect 19% or 21%. (Not 15% or 25%.)

### Four considerations ★★ (slides 51–54)

| # | Consideration | Meaning |
|---|---|---|
| 1 | **Statistical vs practical significance** | Statistical: "observed mean differences are not likely due to sampling error". Practical: "difference is **large enough to actually matter**". Slide example: an experiment with **+0.1% conversion rate** can be significant yet unimportant |
| 2 | **Downstream metrics** | The change may hurt other metrics. Example: variant A raises the upgrade rate by **10%** (the target) but lowers LTV by **30%** because of excessive monetisation prompts |
| 3 | **Local maximum** | Testing one variable at a time for a long time makes it "impossible for you to arrive at a much better design" |
| 4 | **Other problems that invalidate the experiment** | Insufficient sample size; insufficient time; outlier events (holidays); incorrect instrumentation; bugs |

---

## How this lecture is examined

### 2025-26 final Q22 (10 marks) — full model answer ★★

*A university gives 30 students a standardized exam before an online study-skills workshop and a similar exam after 8 weeks. Is there a significant increase?* Given: mean difference (after − before) = 2 points; SD of the differences = 1 point; n = 30; critical value at 0.05 = 1.699.

**(a) Test and hypotheses (3 marks)**
1. **Paired-samples t-test**, because the same 30 students are measured twice (before and after), so the two sets of scores are dependent. (1)
2. **H0:** the mean of the differences (after − before) is zero — the workshop does not change the average score (μd = 0). (1)
3. **H1:** the mean of the differences is greater than zero — the average score increases after the workshop (μd > 0). (1)

**(b) Perform the test (5 marks)**
1. Significance level α = 0.05; df = n − 1 = 29. (1)
2. Formula: t = (x̄d − 0) / (s_d / √n). (1)
3. Standard error = 1 / √30 = 0.1826; t = 2 / 0.1826 = **10.95**. (1)
4. Critical value = 1.699. Since 10.95 > 1.699, t falls in the rejection region → **reject H0**. (1)
5. Conclusion: at the 5% level there is a statistically significant increase in average test scores after the workshop. (1)

**(c) Why might the university still be unhappy? (2 marks)**
1. **Statistical significance is not practical significance.** The result only shows the difference is unlikely to be sampling error. (1)
2. The actual improvement is only **2 points** on average — possibly too small to matter for students' performance or to justify the cost and 8 weeks of the workshop. (1)
   Also acceptable: no control group, so the gain may come from practice with a "similar" exam or 8 more weeks of normal study; only 30 students; other outcomes (downstream metrics) were not measured.

### Model answers for other likely questions

**Q (6 marks). Tissue packets are claimed to weigh 100 g. A sample of 30 has mean 97 g and standard deviation 6 g. Test at α = 0.05 (two-tailed critical value for df = 29 is 2.045).**
1. One-sample t-test (one sample against a claimed standard). (1)
2. H0: the mean weight equals 100 g. H1: the mean weight is not equal to 100 g. (1)
3. t = (x̄ − μ)/(s/√n) = (97 − 100)/(6/√30). (1)
4. = −3 / 1.0954 = **−2.74**. (1)
5. df = 29; |−2.74| > 2.045 → reject H0. (1)
6. The mean packet weight is significantly different from (lower than) the claimed 100 g. (1)

**Q (3 marks). Explain Type I error, Type II error and power.**
1. Type I: rejecting a true H0; probability α = significance level, set by the researcher. (1)
2. Type II: failing to reject a false H0; probability β. (1)
3. Power = 1 − β, the probability of correctly rejecting a false H0; α and β are inversely related for a fixed sample size. (1)

**Q (6 marks). List the steps to set up an A/B test.** The six steps in the table above, one mark each with a short description.

**Q (4 marks). An A/B test of a new checkout button gives p = 0.01 and a conversion uplift of 0.1%. Should the company launch? Give two considerations.**
1. p = 0.01 < 0.05 → the difference is statistically significant (not likely due to sampling error). (1)
2. But a 0.1% uplift may not be practically significant: it may be too small to matter or to cover the cost of the change. (1)
3. Check downstream metrics (e.g. average order value, LTV, refunds) — the change could hurt them. (1)
4. Check validity: enough sample and time, no holiday/outlier events, correct instrumentation, no bugs. (1)

---

## Easy to mix up

| A | B | How to tell them apart |
|---|---|---|
| Paired | Independent | Same subjects twice vs two different groups |
| One-sample | Paired | Both use (mean − value)/(s/√n). One-sample compares raw data with a standard; paired compares the **differences** with 0 |
| Type I | Type II | I = false alarm (reject a true H0). II = miss (keep a false H0) |
| α | β | α = P(Type I) = significance level. β = P(Type II). Power = 1 − **β** |
| Statistical significance | Practical significance | Real vs big enough to matter |
| Critical value | Calculated t | From the table vs from your data |
| p-value | α | p comes from the data; α is chosen beforehand. Reject when **p < α** |
| t-test | ANOVA | Two groups vs more than two groups |
| t-test | Z-test | Z for large samples and known variance |
| Baseline conversion rate | MDE | Current rate vs smallest relative change you want to detect |

## Memory hooks

- **"Same people? Paired. Different people? Independent. One group and a claim? One-sample."**
- t = **signal ÷ noise** (difference ÷ standard error).
- Decision: **"big t, small p → reject H0"**.
- Type **I** = **I**nnocent convicted. Type **II** = guilty goes free.
- A/B cycle: **O-H-S-R-A-T** = **O**bserve, **H**ypothesis, **S**ample size, **R**un, **A**nalyze, **T**ake action.
- A/B warnings: **P-D-L-O** = **P**ractical significance, **D**ownstream metrics, **L**ocal maximum, **O**ther problems.

---

## Test yourself

**Multiple choice**

1. Thirty employees' typing speed is measured before and after training. Which test? A) one-sample B) independent-samples C) paired-samples D) ANOVA
2. In an independent-samples t-test with n₁ = 12 and n₂ = 15, df = A) 25 B) 26 C) 27 D) 13
3. A Type I error is: A) failing to reject a false H0 B) rejecting a true H0 C) accepting a true H0 D) rejecting a false H0
4. The t-value becomes larger when: A) the data are more scattered B) the sample is smaller C) the difference between the means is greater D) α is smaller
5. In A/B testing, a baseline conversion rate of 10% with MDE 10% means the test is designed to detect rates of: A) 0% or 20% B) 9% or 11% C) 9.9% or 10.1% D) 5% or 15%
6. Which is NOT one of the conditions for using A/B testing? A) a clear hypothesis B) sufficient sample size C) reasonable timeframe D) more than two versions to compare
7. "Observed power" in an A/B calculator is: A) the probability H0 is true B) the probability that the test correctly rejected H0 C) the relative uplift D) the baseline rate
8. Which test compares three or more groups at once? A) Z-test B) paired t-test C) ANOVA D) one-sample t-test
9. With α = 0.05 a p-value of 0.20 means: A) reject H0 B) do not reject H0 C) H0 is proved true D) the test is invalid
10. Optimising one variable at a time for a long period risks: A) a Type I error B) a local maximum C) outlier events D) sampling frame error

**True / false**

1. The null hypothesis for a paired-samples test states that the mean of the differences is zero.
2. Decreasing the probability of a Type I error also decreases the probability of a Type II error for a fixed sample size.
3. An A/B test is a paired-samples test.
4. The power of a test is 1 − α.
5. A statistically significant result is always practically significant.
6. The greater the scatter of the data, the less a given mean difference matters.
7. A Z-test is used for larger samples with known variance.
8. In an A/B test, users choose which version they want to see.

**Short questions**

1. Version A: 50 users, mean order value $200, SD $40. Version B: 50 users, mean $218, SD $50. Test at α = 0.05 (two-tailed critical value for df = 98 ≈ 1.984).
2. Twelve customers rate a service before and after a redesign. The mean difference (after − before) is 0.9 and the SD of the differences is 1.2. Test for an improvement at α = 0.05 (one-tailed critical value for df = 11 is 1.796).
3. Give two reasons an A/B experiment can be invalid.

### Answers

**Multiple choice:** 1 **C** (same employees twice). 2 **A** (12 + 15 − 2). 3 **B** (A is Type II). 4 **C** (more scatter makes t smaller). 5 **B** (MDE is relative: 10% of 10% = 1 point). 6 **D**. 7 **B**. 8 **C**. 9 **B** (p > α; we never "prove" H0). 10 **B**.

**True / false:** 1 **T**. 2 **F** (they are inversely related). 3 **F** (independent-samples: different users see A and B). 4 **F** (1 − β). 5 **F**. 6 **T**. 7 **T**. 8 **F** (users are **randomly** divided 50/50).

**Short questions**

1. Independent-samples t-test. H0: mean order values are equal; H1: not equal. SE = √(40²/50 + 50²/50) = √(32 + 50) = √82 = 9.055. t = (200 − 218)/9.055 = **−1.99**. df = 98. |−1.99| > 1.984 → reject H0 (only just): the mean order values differ, B is higher. Comment: borderline; check practical significance.
2. Paired-samples t-test. H0: μd = 0; H1: μd > 0. t = 0.9 / (1.2/√12) = 0.9 / 0.3464 = **2.60**. df = 11. 2.60 > 1.796 → reject H0: ratings improved significantly after the redesign.
3. Any two: insufficient sample size; insufficient time; outlier events such as holidays; incorrect instrumentation; bugs.
