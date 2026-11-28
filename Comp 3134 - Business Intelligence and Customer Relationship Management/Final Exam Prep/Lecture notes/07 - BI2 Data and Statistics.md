# BI2 — Data and Statistics (teaching week 8)

> **Built from:** all 116 slides of "Week 7 P1 - BI&CRM SS-25-26 Lecture BI2.pdf", text and pictures.
> **Exam weight:** very high. The 2025-26 final Q21 (10 marks) was levels of measurement + a frequency table + a cumulative frequency chart. The 2024-25 final Q23 (15 marks) was mean, median, mode, modality, midrange, quartiles, variance and standard deviation. Expect one calculation question from this lecture again, plus MCQ / true-false on sampling and data types.

---

## The lecture in one minute

- Before you analyse data you must **prepare** it: plan → check questionnaires → edit → code → clean → choose the analysis.
- You normally study a **sample**, not the whole **population**. How you pick the sample decides whether you may generalise. **Probability** sampling (everyone has a known chance) lets you generalise; **non-probability** sampling is quicker and cheaper but biased.
- Data has four **levels of measurement**: **nominal → ordinal → interval → ratio**. Numbers are also **discrete** (counted) or **continuous** (measured).
- Machine-learning models need numbers, so categories are **coded**: ordinal encoding for ordered categories, **one-hot encoding** for nominal ones.
- **Descriptive statistics** summarise the data you have (centre and spread). **Inferential statistics** use a sample to say something about the population.
- Centre = **mean, median, mode**. Spread = **range, variance, standard deviation, quartiles, IQR**.
- A **frequency distribution** groups data into classes; from it you get relative frequency, cumulative frequency and a histogram.

| Question the exam asks | Tool from this lecture |
|---|---|
| "What level of measurement? Discrete or continuous?" | Nominal / ordinal / interval / ratio decision steps (Part 3) |
| "Complete the frequency table and sketch the cumulative chart" | Frequency → relative frequency → cumulative frequency (Part 7) |
| "Find the mean / median / mode / midrange" | Part 6 |
| "Find Q1, Q3, variance, standard deviation" | Part 9 |
| "Which sampling method is this?" | Part 2 |

---

## Words you need

| Term | Slide wording | In plain words |
|---|---|---|
| **Population** | "the entire group under study as defined by research objectives" / "all items of interest" | Everybody or everything you want to know about |
| **Census** | "requires information from everyone in the population" | Asking every single member |
| **Sample** | "a subset of the population that should represent the entire group" | The smaller group you actually measure |
| **Sample unit** | "the basic level of investigation" | One member of the sample (a person, a household, a shop) |
| **Sample frame** | "a master list of the entire population" | The list you pick the sample from |
| **Sampling frame error** | "the degree to which the sample frame fails to account for all of the population" | The list is missing some people |
| **Parameter** | "summary measures of a population" | A number describing the whole population (e.g. μ) |
| **Statistic** | "summary measures of a sample" | A number describing the sample (e.g. x̄) |
| **Descriptive statistics** | "summarizing and describing information from data collected" | Describe what you have |
| **Inferential statistics** | "estimating, predicting and making inference about the parameter of a population" from sample statistics | Use the sample to judge the population |
| **Coding** | "assigning a code, usually a number, to each possible response to each question" | Turning answers into numbers |
| **Frequency distribution** | "shows how a data set is partitioned among all categories (or classes)" | A table: class → how many values fall in it |
| **Relative frequency** | "class frequency ÷ total number of observations" | The share of the data in each class |
| **Big Data** | "data that cannot be stored in a single storage unit" | Too much data for one machine |

---

## Part 1 — Data preparation process (slides 2–10)

**Why data and statistics (slide 2):** "Data provides the raw material for analysis. Statistics help in extracting meaningful insights from data."

### The six-stage process ★ (slide 3)

The slide draws the stages as a staircase. In working order:

1. **Preliminary plan of data analysis**
2. **Questionnaire checking**
3. **Editing**
4. **Coding** (and transcribing)
5. **Data cleaning** (and statistically adjusting the data)
6. **Selecting a data analysis strategy**

**Memory hook:** **P**lease **Q**uit **E**ating **C**old **C**hips **S**oon — Plan, Questionnaire check, Edit, Code, Clean, Strategy.

### 1. Preliminary plan (slide 4) — four tasks

- **Define objectives and stakeholders** — "clarify project goals and identify who will use or be affected by the data".
- **Assess data needs and sources** — what data, where from, any access issues.
- **Plan sampling strategy** — is sampling needed, which method, how to make it represent the population.
- **Resource and timeline planning** — resources, timeline, potential challenges.

### 2. Questionnaire checking (slide 5) — six reasons a returned questionnaire is unacceptable ★

1. Parts are **incomplete**.
2. The pattern of answers shows the respondent **did not understand or follow the instructions**.
3. The responses show **little variance** (e.g. ticking "4" for everything).
4. One or more **pages are missing**.
5. It arrived **after the cut-off date**.
6. It was answered by **someone who does not qualify**.

### 3. Editing (slide 6) — three treatments of unsatisfactory responses ★

| Treatment | What you do |
|---|---|
| **Returning to the field** | Interviewers contact the respondent again |
| **Assigning missing values** | If going back is not feasible, the editor marks the bad answers as missing |
| **Discarding unsatisfactory respondents** | Throw the whole respondent away |

### 4. Coding and transcribing (slides 7–9)

- "Coding means assigning a code, usually a number, to each possible response to each question."
- The code also shows the **column position (field)** and the data record it occupies.
- A **codebook** lists: column number, variable number, variable name, question number, coding instructions (e.g. Preference: "1 = Weak Preference, 7 = Strong Preference").

### 5. Data cleaning and statistical adjustment (slide 10)

- **Data cleaning** — "thorough and extensive checks for consistency and treatment of missing responses or values".
- **Statistically adjusting the data** — "the transformation of data to create new variables or the modification of existing variables … e.g. standardization and re-coding".

---

## Part 2 — Data collection and sampling (slides 11–33) ★★

### Why sample instead of a census? (slide 13)

**In plain words:** a census costs too much money and time, and is often impossible. A well-chosen sample gives nearly the same answer. (The slide asks the question; the answer comes from the sample-size slides: a random sample can be "a tiny percent of the population size and still have a small margin of sample error".)

### Two families of sampling ★★ (slide 14)

| | Probability sampling | Non-probability sampling |
|---|---|---|
| Definition | "Each unit in the target population has a **known probability** (usually equal chance) of being selected" | "The probability of selecting each unit in target population is **unknown**" |
| Example | Simple random sampling | Convenience sampling (intercept at a high-end mall) |
| Advantage | "**Unbiased selection** & proper sample representation of target population" | "Relatively **quicker & lower cost**" |

### Four probability methods ★★ (slides 15–19)

| Method | How it works | Slide example |
|---|---|---|
| **Simple random sampling (SRS)** | Every unit has an **equal** chance. Use a table of random numbers | Random digit dialling, SME business directory, customer list |
| **Systematic random sampling** | From a **list**, pick a random start, then take every k-th unit. **Skip interval = population size ÷ sample size** | Population 100,000, sample 1,000 → interval 100. Random start 23 → 23, 123, 223, 323 … |
| **Stratified random sampling** | Split the population into **strata** that are **homogeneous inside and different from each other**, then random-sample **inside every stratum** | Draw from each stratum in proportion to the population (or weight the results) |
| **Cluster sampling** | The population has a few **similar clusters**, each one a mini-population (**heterogeneous inside**). **Randomly pick a few clusters**, then census or sample inside them. Saves time and cost | Area sampling. Park'n Shop: 30 stores in Central have similar customers → pick 5 stores, interview at each |

**The trap (stratified vs cluster):**

| | Stratified | Cluster |
|---|---|---|
| Inside one group | Members are **alike** (homogeneous) | Members are **mixed** (heterogeneous) |
| Between groups | Groups are **different** | Groups are **similar** |
| What you sample | **Some people from every** group | **Everyone / some people from a few** groups |
| Why | Precision, every sub-group is included | Cheap and easy |

### Four non-probability methods ★★ (slides 20–21)

| Method | How it works | Slide example |
|---|---|---|
| **Convenience** | Respondents "happen to be in the right place at the right time" | Mall intercepts |
| **Quota** | Set quotas so each subgroup has enough respondents | Population 48% male / 52% female → sample of 1,000 = 480 male, 520 female |
| **Purposive / judgment** | Sample chosen by the researcher's judgment to fulfil a purpose | A test market in a city regarded as representative of the country |
| **Referral / snowball** | Recruit through friends' or respondents' referrals | Recruiting people who drink Macallan 18 years |

**Quota vs stratified:** both split by subgroup. Stratified picks **randomly** inside each group (probability). Quota fills each group **any way it can** (non-probability).

### Strengths and weaknesses table ★ (slides 22–24)

| Technique | Strengths | Weaknesses |
|---|---|---|
| Convenience | Least expensive; least time-consuming; most convenient | Selection bias; not representative; not recommended for descriptive or causal research |
| Judgmental | Low cost; convenient; not time-consuming | No generalization; subjective |
| Quota | Sample can be controlled for certain characteristics | Selection bias; no assurance of representativeness |
| Snowball | Can estimate rare characteristics | Time-consuming |
| Simple random | Easily understood; results projectable | Difficult to construct sampling frame; expensive; lower precision; no assurance of representativeness |
| Systematic | Can increase representativeness; easier than SRS; sampling frame not needed | Can decrease representativeness |
| Stratified | Includes all important subpopulations; precision | Difficult to select stratification variables; not feasible on many variables; expensive |
| Cluster | Easy to implement; cost-effective | Imprecise; difficult to compute and interpret results |

### Which family to choose? (slide 25)

| Factor | Favours non-probability | Favours probability |
|---|---|---|
| Nature of research | **Exploratory** | **Conclusive** |
| Sampling vs non-sampling errors | Non-sampling errors are larger | Sampling errors are larger |
| Variability in the population | Homogeneous (low) | Heterogeneous (high) |
| Statistical considerations | Unfavourable | Favourable |
| Operational considerations | Favourable | Unfavourable |

### Factors for determining sample design (slide 26)

Research objectives (exploratory / descriptive / causal; need to generalise) · degree of accuracy · resources (time and cost) · knowledge of the target population · scope of the research · statistical analysis needs.

### Online sampling techniques (slide 27)

- **Online panels** — "large numbers of individuals who have agreed to participate in online surveys".
- **River samples** — "created via the use of banners, pop-ups, or other online devices that invite website visitors".
- **E-mail list samples** — purchased or procured lists of opt-in e-mail addresses.

### Develop a sample plan — six steps ★ (slide 28)

1. Define the population → 2. Obtain a sample frame → 3. Decide on the sample method → 4. Decide on the sample size → 5. Draw the sample → 6. Validate the sample.

### Sample size and accuracy ★ (slides 29–33)

**Eight axioms (slide 29, picture table).** The ones worth remembering:

1. The only perfectly accurate sample is a **census**.
2. A random sample always has some inaccuracy = **margin of sample error**.
3. **The larger a random sample, the more accurate** (less margin of error).
4. Margin of error can be calculated and written as ±%.
5. Repeat the survey with the same sample size and you will "very likely" find the same result within the ±% range.
6. In almost all cases the margin of error is **independent of the size of the population**.
7. A sample can be a **tiny percent** of the population and still have a small margin of error.
8. Sample size depends on the client's desired accuracy **balanced against the cost** of data collection.

**Sample size → margin of error (slide 31):** 10 → ±31.0% · 50 → ±13.9% · 100 → ±9.8% · 200 → ±6.9% · 400 → ±4.9% · 500 → ±4.4% · 750 → ±3.6% · 1,000 → ±3.1% · 1,500 → ±2.5% · 2,000 → ±2.2% · 5,000 → ±1.4% · 10,000 → ±1.0%.

**In plain words:** going from 100 to 1,000 people cuts the error from about ±10% to ±3%. Going from 1,000 to 10,000 only cuts it to ±1%. Bigger helps, but less and less.

**Confidence interval / Central Limit Theorem (slide 32):** "If we conducted our study over and over with a certain sample size, we would expect our result to fall within a known range. If we conduct the study with a larger sample size, this range will shrink, so the error is smaller." The picture shows **95% of a normal curve lies within ±1.96 standard deviations**.

**Other ways to set sample size (slide 33):**

| Method | Idea |
|---|---|
| Arbitrary "percent rule of thumb" | Unscientific: "sample 10% of the population" |
| Conventional | Follow field / industry norms |
| Statistical analysis requirements | Some tests need a minimum number of observations |
| Cost basis | Whatever the budget allows |

---

## Part 3 — Types of data and data coding (slides 34–53) ★★

### The four scales of measurement ★★ (slides 35–41)

| Level | Type | What you can do | Slide example |
|---|---|---|---|
| **Nominal** | Qualitative | Only **classify**. No order. No arithmetic | Colour (red, green, blue, yellow) |
| **Ordinal** | Qualitative | Classify **and rank**. Gaps between ranks are not equal | Strongly agree … strongly disagree (Likert scale); grades A, B+, D |
| **Interval** | Quantitative | Order + **differences are meaningful**. **No natural zero**, so ratios make no sense | Years 1000, 2000, 1776, 1492; temperature in °C |
| **Ratio** | Quantitative | Interval + a **natural zero** (zero = none of the quantity). Differences **and ratios** are meaningful | Prices of textbooks ($0 = no cost; $100 is twice $50) |

**How to decide in the exam — ask four questions in order:**

1. Are the values just **names/labels**? → **Nominal**.
2. Can I put them **in order**, but the gaps are not measurable? → **Ordinal**.
3. Are they numbers where **differences** make sense but **zero does not mean "nothing"**? → **Interval**.
4. Does **zero mean "none"**, so "twice as much" makes sense? → **Ratio**.

### Quantitative data: discrete or continuous ★★ (slide 38)

| | Discrete | Continuous |
|---|---|---|
| Comes from | **Counting** | **Measuring** |
| Slide example | Number of customers arriving in 2 minutes | Elapsed time of a production run; your height |

Nominal and ordinal data are qualitative, so discrete/continuous is **not applicable (N/A)**.

### Other types (slide 42)

- **Time series data** — "recorded in a regular successive interval of time" (closing price of one stock over a month).
- **Cross-sectional data** — "measured at the same or approximately the same point of time" (closing prices of 20 stocks on one day).

### Worked classification — 2025-26 final Q21(a) ★★

| Item | Level | Discrete / continuous / N/A | Why |
|---|---|---|---|
| Eye colours of students in your class | **Nominal** | N/A | Names only, no order |
| Pulse rates of male students | **Ratio** | **Discrete** | Beats are **counted** per minute; 0 = no pulse |
| Body temperatures (in degrees) | **Interval** | **Continuous** | Measured; 0° does not mean "no temperature" |
| Ages (in years) of homes sold | **Ratio** | **Continuous** | Time is measured; age 0 = brand new; 20 years is twice 10 years |
| Age brackets (under 30, 30–49, 50–64, over 64) | **Ordinal** | N/A | Ordered categories |

More practice: phone number → nominal · class rank → ordinal · IQ score or calendar year → interval · weight, income, number of children → ratio (children: discrete; weight: continuous) · satisfaction "poor/fair/good" → ordinal.

### Coding ★ (slides 43–49)

- **Coding** = "translating data from questionnaires or other sources into other representation easy for further analysis", e.g. to feed machine-learning models. It also removes inconsistency (Male / Female / M / F).
- **Dichotomous** (two-value) variables: 0 = No, 1 = Yes (or 1 = No, 2 = Yes). Either is fine "as long as it is clear how the data are coded" → keep a **data dictionary**.
- **Labels** can be attached to the values so the output is readable (0 → "Male", 1 → "Female").
- **Ordinal variables:** the numbers must follow the order. Good: 0 Primary, 1 Secondary, 2 University, 3 Graduate school (reverse order is also fine). **Bad:** 0 University, 1 Graduate, 2 Secondary, 3 Primary — "data has an inherent order but coding does not follow that order".
- **Nominal variables:** "order makes no difference" (1 Apple, 2 Orange, 3 Mango, 4 Banana).
- **Continuous → categories:** age → AGECAT (1 = 0–9, 2 = 10–19, 3 = 20–39, 4 = 40–59, 5 = 60+). This creates an **ordinal** categorical variable.

### Encoding for machine learning ★★ (slides 50–53)

| | Ordinal (label) encoding | One-hot encoding |
|---|---|---|
| What | One number per category: 0, 1, 2, 3 | One 0/1 column per category |
| Use for | **Ordinal** data (education level) | **Nominal** data (fruit) |
| Example | Primary 0, Secondary 1, University 2, Graduate 3 | Apple 1000, Orange 0100, Mango 0010, Banana 0001 |
| Problem | For nominal data the numbers suggest an order that is not real and "may confuse ML models" | See disadvantages |

**One-hot advantages (slide 52):** (1) can improve model performance by giving more information about the categorical variable; (2) "avoids the problem of ordinality".

**One-hot disadvantages (slide 53):** (1) **increased dimensionality** — a column for every category → more complex, slower to train, **easily overfits if the sample is small**; (2) **sparse data and large data size** — mostly zeros.

---

## Part 4 — Big Data (slides 54–56)

- Definition: "data that cannot be stored in a single storage unit". Forms: **structured** and **unstructured**.
- Characteristics — the **3 Vs**: **volume, velocity, variety**.
- Two problems at this scale:

| Problem | Old way | Big-data way |
|---|---|---|
| **Storing** | One extremely expensive storage solution | Store data in **chunks on different machines** on a network: **Hadoop Distributed File System (HDFS)** keeps a copy or two of each chunk in different places |
| **Processing** | One powerful computer | A **parallel distributed algorithm on a cluster**: the **MapReduce** programming paradigm |

**In plain words:** Hadoop = HDFS (storage) + MapReduce (processing).

---

## Part 5 — What statistics is (slides 57–71) ★

- "Statistics is the study of the **collection, organization, presentation and interpretation (analysis)** of data."
- Four key terms (slide 59): **Population** (all items of interest) · **Sample** (a portion of the population) · **Parameter** (summary measure of a **p**opulation) · **Statistic** (summary measure of a **s**ample). **P goes with P, S goes with S.**

**Green Phone example (slide 61) ★★** — 500 randomly chosen smartphone owners; 175 use Green Phone.

| Term | In the example |
|---|---|
| Population | All smartphone owners |
| Parameter | The proportion of **all** smartphone owners using Green Phone |
| Sample | The 500 owners surveyed |
| Statistic | The proportion of the 500 using Green Phone (175/500 = 35%) |

Saying "the market share is about 35%" generalises from sample to population = **statistical inference**.

**Shuttlecock activity (slide 63) — answers:** population = all shuttlecocks the manufacturer produces; sample = the 60 shuttlecocks in the five tubes; 5 g = **parameter** (the claimed population mean); 4.83 g = **statistic** (the sample mean).

| | Descriptive statistics | Inferential statistics |
|---|---|---|
| Does | Collect, summarise, present data | Estimate, predict, test |
| Tools | Central tendency (mean, mode, median); dispersion (standard deviation, variance, interquartile range) | Estimation of parameters (point estimate, interval estimate); hypothesis testing (p-value) |
| Scope | The data you have | "Generalization of data in a wider scope" |

---

## Part 6 — Measures of central tendency (slides 72–79, 100–101) ★★

| Measure | How | Notes from the slides |
|---|---|---|
| **Mean** x̄ = Σx / n | Add everything, divide by how many | "Most popular and useful". **A single outlier can skew it** in small samples |
| **Median** | Sort, take the **middle** value. If n is even, **average the two middle values** | "Not affected by any extreme observations" |
| **Mode** | The value that occurs **most often** | "Especially useful in describing nominal and ordinal" data. Less used |

**Slide examples.**

- Mean of 7, 3, 9, −2, 4, 6 = 27 / 6 = **4.5**.
- Median of 19, 20, 18, 18, 58 → sorted 18, 18, 19, 20, 58 → **19** (the mean would be 26.6, pulled up by 58).
- Salaries 28, 100, 26, 32, 30, 26, 29 → sorted 26, 26, 28, **29**, 30, 32, 100 → median **29**. Add 31 → 26, 26, 28, **29, 30**, 31, 32, 100 → median (29 + 30)/2 = **29.5**.
- Mode of 31, 34, 36, 33, 28, 34, 30, 34, 32, 40 = **34**.

**City vs highway (slides 100–101):** City: mean 20.14, median 20.3, mode 19.9. Highway: mean 24.62, median 24.45, mode 24.2. All three are higher on the highway.

**Two more words the 2024-25 paper used (not defined on this year's slides, but asked):**

- **Midrange** = (smallest + largest) / 2.
- **Modality** = how many modes: one = **unimodal**, two = **bimodal**, three = trimodal, more = multimodal.

---

## Part 7 — Frequency distributions (slides 80–93) ★★

### Vocabulary (slides 82–86, pulse rates of females: classes 60–69, 70–79, …, 120–129)

| Term | Meaning | In the example |
|---|---|---|
| **Frequency** | "the number of original values that fall into that class" | 12, 14, 11, 1, 1, 0, 1 |
| **Lower class limits** | Smallest numbers that can belong to each class | 60, 70, 80 … |
| **Upper class limits** | Largest numbers that can belong to each class | 69, 79, 89 … |
| **Class midpoint** | (lower limit + upper limit) / 2 | 64.5, 74.5, 84.5 … |
| **Class width** | Difference between two consecutive **lower** class limits | 70 − 60 = 10 |

### How many classes? (slide 87)

| Observations | Classes |
|---|---|
| Less than 50 | 5–7 |
| 50–200 | 7–9 |
| 200–500 | 9–10 |
| 500–1,000 | 10–11 |

**Class width = range ÷ number of classes**, rounded up. Telephone bills: (119.63 − 0) / 8 = 14.95 → **15**.

### Relative and cumulative frequency ★★ (slides 91–93)

```
relative frequency   = class frequency / total number of observations
cumulative frequency = running total of the frequencies
cumulative relative  = cumulative frequency / total
```

Telephone bills (n = 200): frequencies 71, 37, 13, 9, 10, 18, 28, 14 → cumulative 71, 108, 121, 130, 140, 158, 186, 200 → cumulative relative .355, .540, .605, .650, .700, .790, .930, 1.000.

"Relative frequency is useful in comparing distributions while the number of observations of them are different."

**Reading a histogram (slide 90):** about half the bills are small (71 + 37 = 108), a few are in the middle (32), and there are relatively many large bills (60). **In plain words:** two humps.

### Worked exam answer — 2025-26 final Q21(b), (c) ★★

Data (waiting minutes, n = 20): 2, 10, 4, 5, 11, 9, 12, 6, 7, 18, 5, 12, 4, 17, 8, 8, 21, 8, 13, 3.

**Step 1 — tally each value into its class** (cross values off as you go so none is missed).

| Class (min) | Values | Frequency | Relative frequency | Cumulative frequency |
|---|---|---|---|---|
| 0–4 | 2, 4, 4, 3 | 4 | 4/20 = 0.20 | 4 |
| 5–9 | 5, 9, 6, 7, 5, 8, 8, 8 | 8 | 0.40 | 12 |
| 10–14 | 10, 11, 12, 12, 13 | 5 | 0.25 | 17 |
| 15–19 | 18, 17 | 2 | 0.10 | 19 |
| 20–24 | 21 | 1 | 0.05 | 20 |
| **Total** | | **20** | **1.00** | |

**Step 2 — check:** frequencies add to 20; relative frequencies add to 1.00; the last cumulative value equals n.

**Step 3 — sketch the cumulative chart (ogive).** x-axis = waiting time (upper class limits 4, 9, 14, 19, 24). y-axis = cumulative frequency. Plot (4, 4), (9, 12), (14, 17), (19, 19), (24, 20), join with straight lines, and start the line at 0 on the left. Label both axes and give a title. The line **never goes down**. (A cumulative bar chart with the same heights is also acceptable as a "chart".)

**(c) Waiting 14 minutes or less** = cumulative frequency of the 10–14 class = **17 patients**.

---

## Part 8 — Shapes of distributions (slides 94–99) ★

| Shape | Looks like | Order of the three centres |
|---|---|---|
| **Symmetric** | Left half mirrors right half | Mean = median = mode |
| **Positively skewed (skewed to the right)** | Long tail on the **right** | **Mode < Median < Mean** |
| **Negatively skewed (skewed to the left)** | Long tail on the **left** | **Mean < Median < Mode** |

**In plain words:** the **mean is pulled toward the tail**. The name of the skew is the side of the **tail**, not the side of the hump.

**Normal distribution (slides 96–98):** bell-shaped, symmetric around the middle (unimodal), short tails. "The mean, mode, median should all have similar values."

- **±1 standard deviation covers 68.27%** of the data.
- **±2 standard deviations cover 95.44%**.
- This is "the basis on which parametric statistical tests such as t-test, anova and linear correlation operate".

---

## Part 9 — Measures of dispersion (slides 102–115) ★★

Two basketball teams can have the same mean, mode and median height but very different spread — "measures of central location fail to tell the whole story".

### Formulas

```
Range              = largest − smallest
Sample variance    s² = Σ(x − x̄)² / (n − 1)
Standard deviation s  = √s²
Quartile positions Q1 = (n + 1)/4 th     Q2 = (n + 1)/2 th     Q3 = 3(n + 1)/4 th   (in the SORTED data)
Inter-quartile range IQR = Q3 − Q1
```

- Divide by **n − 1** (not n). This is the **sample** variance, the only one on the slides.
- Range: easy to compute, but tells you nothing about the values between the two ends.
- **If the quartile position is not a whole number, the slides average the two neighbouring values** (slide 114: position 2.75 → average of the 2nd and 3rd values; position 8.25 → average of the 8th and 9th).

### Worked examples from the slides

**Variance (slide 105):** 3.4, 2.5, 4.1, 1.2, 2.8, 3.7 → x̄ = 17.7 / 6 = 2.95 → Σ(x − x̄)² = 5.375 → s² = 5.375 / 5 = **1.075 years²**.

**Risk (slides 107–108):** Fund A: mean 16, standard deviation 16.74. Fund B: mean 12, standard deviation 9.969. **Fund A is more risky because its standard deviation is larger.**

**Quartiles (slides 111–112):** sorted 2, 4, 4, 5, 7, 8, 10, 12, 17, 18, 18, 21, 27, 29, 30 (n = 15). Q1 at (15 + 1)/4 = 4th → **5**. Q2 at 8th → **12**. Q3 at 12th → **21**.

**Sick leave (slides 113–115):**

| | Sorted data | Range | Q1 | Q3 | IQR | Mean | Variance | SD |
|---|---|---|---|---|---|---|---|---|
| Summer | 12, 15, 16, 16, 18, 19, 20, 20, 20, 21 | 21 − 12 = 9 | 2.75th → (15 + 16)/2 = 15.5 | 8.25th → (20 + 20)/2 = 20 | 4.5 | 17.7 | 8.2333 | 2.8694 |
| Winter | 18, 18, 18, 23, 24, 28, 28, 29, 32, 38 | 38 − 18 = 20 | (18 + 18)/2 = 18 | (29 + 32)/2 = 30.5 | 12.5 | 25.6 | 44.4889 | 6.6700 |

### Worked exam answer — 2024-25 final Q23 (15 marks) ★★

Ages (already sorted, n = 27): 13, 15, 16, 16, 19, 20, 20, 21, 22, 22, 25, 25, 25, 25, 30, 33, 33, 35, 35, 35, 35, 36, 40, 45, 46, 52, 70.

| Part | Working | Answer |
|---|---|---|
| a) Mean | Σx = 809; 809 / 27 | **29.96** |
| b) Median | (27 + 1)/2 = 14th value | **25** |
| c) Mode | 25 appears 4 times, 35 appears 4 times | **25 and 35** |
| d) Modality | Two modes | **Bimodal** |
| e) Midrange | (13 + 70)/2 | **41.5** |
| f) Q1, Q3 | Q1 at (27 + 1)/4 = 7th → 20. Q3 at 3 × 28/4 = 21st → 35 | **Q1 = 20, Q3 = 35** (IQR = 15) |
| g) Variance, SD | Σx² = 28,595. Σ(x − x̄)² = 28,595 − 809²/27 = 28,595 − 24,240.04 = 4,354.96. s² = 4,354.96 / 26 | **s² = 167.50, s = 12.94** |

Extra comment worth a mark: mean (29.96) > median (25) → the data are **positively skewed** (pulled right by 70).

**Calculator shortcut:** in STAT / SD mode enter the values, then read x̄, **sx** (or σn−1) for the sample standard deviation, and square it for the variance. Do **not** use σx (σn): that divides by n and gives 12.70. Without STAT mode use `Σ(x − x̄)² = Σx² − (Σx)²/n`.

---

## How this lecture is examined

**Past questions**

- 2025-26 final Q21 (10 marks): (a) level of measurement + discrete/continuous for five items (4); (b) complete frequency / relative frequency / cumulative frequency table and sketch the cumulative chart (5); (c) read a value from it (1). Full answers in Parts 3 and 7.
- 2024-25 final Q23 (15 marks): mean, median, mode, modality, midrange, Q1/Q3, variance and standard deviation. Full answer in Part 9.
- Mid-term and finals: MCQ on sampling and data types.

**Model answers for likely short questions**

**Q (4 marks). Distinguish probability from non-probability sampling and give one advantage of each.**
1. Probability sampling: each unit in the target population has a known (usually equal) chance of being selected. (1)
2. Advantage: unbiased selection and a representative sample, so results can be generalised. (1)
3. Non-probability sampling: the probability of selecting each unit is unknown. (1)
4. Advantage: relatively quicker and lower cost. (1)

**Q (4 marks). A chain has 200 similar stores. It randomly picks 10 stores and surveys every customer in them. Name the method and justify. How would stratified sampling differ?**
1. Cluster sampling. (1)
2. Each store is a cluster that is similar to the others and mixed inside, so a few clusters represent the population at lower cost. (1)
3. Stratified sampling would divide customers into homogeneous strata (e.g. by age group). (1)
4. It would then randomly sample from **every** stratum, not from a few. (1)

**Q (4 marks). Why is one-hot encoding used for nominal variables? Give two disadvantages.**
1. Nominal categories have no order; ordinal codes 0–3 would suggest an order and confuse ML models. (1)
2. One-hot gives each category its own 0/1 column, avoiding the problem of ordinality. (1)
3. Disadvantage: increased dimensionality → more complex, slower, can overfit with small samples. (1)
4. Disadvantage: sparse data and large data size (many zeros). (1)

**Q (3 marks). Mean 52, median 45, mode 40. Describe the shape and say which measure best represents a typical value.**
1. Mode < median < mean → positively skewed (skewed to the right). (1)
2. The mean is pulled up by a few large values (outliers). (1)
3. The median is the better typical value because it is not affected by extreme observations. (1)

**Q (3 marks). List three reasons a returned questionnaire may be unacceptable.** Any three of the six in Part 1.

---

## Easy to mix up

| A | B | How to tell them apart |
|---|---|---|
| Parameter | Statistic | **P**arameter ↔ **P**opulation; **S**tatistic ↔ **S**ample |
| Stratified | Cluster | Stratified: alike inside, sample from **all** groups. Cluster: mixed inside, sample **a few whole** groups |
| Stratified | Quota | Stratified is random inside groups; quota is not |
| Systematic | Simple random | Systematic uses a list + skip interval; SRS uses random numbers for every pick |
| Interval | Ratio | Ratio has a true zero ("twice as much" works) |
| Ordinal | Interval | Ordinal: order only. Interval: equal, measurable gaps |
| Discrete | Continuous | Counted vs measured |
| Positive skew | Negative skew | Named after the side of the **tail**; mean sits on the tail side |
| Relative frequency | Cumulative frequency | Share of one class vs running total |
| Variance | Standard deviation | SD = √variance; SD is in the original units |
| Ordinal encoding | One-hot encoding | Ordered categories vs unordered categories |
| Time series | Cross-sectional | One thing over time vs many things at one time |
| Data cleaning | Editing | Editing treats unsatisfactory questionnaires; cleaning checks consistency and missing values in the coded data |

## Memory hooks

- **N-O-I-R** ("noir") = Nominal, Ordinal, Interval, Ratio, from weakest to strongest.
- Probability methods: **S-S-S-C** = Simple, Systematic, Stratified, Cluster. Non-probability: **C-Q-J-S** = Convenience, Quota, Judgment, Snowball.
- Big Data **3 Vs**: Volume, Velocity, Variety.
- Normal curve: **68 – 95** for 1 and 2 standard deviations (exactly 68.27% and 95.44%); **1.96** standard deviations for 95%.
- Skew: "the **mean** chases the **tail**".
- Quartile positions: **(n + 1)/4, (n + 1)/2, 3(n + 1)/4**.

---

## Test yourself

**Multiple choice**

1. A researcher picks every 50th name from a customer list after a random start. This is: A) simple random B) systematic C) stratified D) quota
2. Which is a non-probability method? A) cluster B) stratified C) snowball D) systematic
3. "Body temperature in °C" is measured on which scale? A) nominal B) ordinal C) interval D) ratio
4. Which statement about one-hot encoding is correct? A) it reduces dimensionality B) it is best for ordinal data C) it avoids implying an order among categories D) it produces dense data
5. In a positively skewed distribution: A) mean < median < mode B) mode < median < mean C) mean = median = mode D) median < mode < mean
6. The sample variance divides the sum of squared deviations by: A) n B) n + 1 C) n − 1 D) √n
7. Which treatment of unsatisfactory responses re-contacts respondents? A) discarding B) assigning missing values C) returning to the field D) coding
8. For 300 observations the slides suggest how many classes? A) 5–7 B) 7–9 C) 9–10 D) 10–11
9. In almost all cases, the margin of sample error of a random sample is: A) proportional to population size B) independent of population size C) zero for samples over 1,000 D) larger for larger samples
10. Which pair is correct for Hadoop? A) HDFS processes, MapReduce stores B) HDFS stores, MapReduce processes C) both store D) both process

**True / false**

1. A statistic is a summary measure of a population.
2. In stratified sampling the elements inside each stratum are homogeneous.
3. Quota sampling is a probability sampling technique.
4. The median is not affected by extreme observations.
5. For ordinal variables the order of the codes does not matter.
6. About 95.44% of normally distributed data lie within two standard deviations of the mean.
7. A larger probability sample has a larger margin of sample error.
8. Cross-sectional data are recorded at regular successive intervals of time.

**Short questions**

1. Data: 4, 8, 6, 5, 3, 8, 9, 5, 8 . Find the mean, median, mode, range, Q1, Q3 and IQR.
2. A population of 12,000 members; a sample of 400 is wanted by systematic sampling. What is the skip interval? If the random start is 7, list the first four selected members.
3. Classify: (a) T-shirt size S/M/L; (b) number of complaints per day; (c) year of birth; (d) delivery distance in km; (e) payment method.

### Answers

**Multiple choice:** 1 **B** (list + skip interval; not SRS because later picks are fixed by the start). 2 **C** (cluster, stratified, systematic are probability methods). 3 **C** (0 °C does not mean no temperature; ratio would need a true zero). 4 **C** (it increases dimensionality and gives sparse data; ordinal data use ordinal encoding). 5 **B** (the mean is pulled to the right tail). 6 **C**. 7 **C**. 8 **C** (200–500 → 9–10). 9 **B** (axiom 6). 10 **B**.

**True / false:** 1 **F** (that is a parameter; a statistic describes a sample). 2 **T**. 3 **F** (non-probability). 4 **T**. 5 **F** (true for nominal; ordinal codes must follow the order). 6 **T**. 7 **F** (larger sample → smaller error). 8 **F** (that is time series; cross-sectional = same point in time).

**Short questions**

1. Sorted: 3, 4, 5, 5, 6, 8, 8, 8, 9 (n = 9). Mean = 56/9 = **6.22**. Median = 5th = **6**. Mode = **8**. Range = 9 − 3 = **6**. Q1 at (9 + 1)/4 = 2.5th → (4 + 5)/2 = **4.5**. Q3 at 7.5th → (8 + 8)/2 = **8**. IQR = **3.5**.
2. Skip interval = 12,000 / 400 = **30**. Members **7, 37, 67, 97**.
3. (a) ordinal, N/A; (b) ratio, discrete; (c) interval, discrete as recorded in whole years (calendar year has no true zero); (d) ratio, continuous; (e) nominal, N/A.
