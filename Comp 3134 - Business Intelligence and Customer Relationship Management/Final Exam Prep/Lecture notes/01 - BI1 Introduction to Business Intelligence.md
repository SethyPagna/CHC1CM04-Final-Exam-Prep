# BI1 — Introduction of BI (teaching week 1)

> **Built from:** all 79 slides of "Week 1 - BI&CRM SS-25-26 Lecture BI1.pdf", text and pictures.
> **Exam weight:** The mid-term past paper took three multiple-choice questions from this lecture (DSS components, OLTP vs OLAP, data mining) and the 2023-24 final had an "OLAP" matching item. The 2024-25 and 2025-26 finals had 20 multiple-choice questions over all lectures (text not released), so the many lists in this lecture are prime multiple-choice and true/false material.

---

## The lecture in one minute

- BI means deciding "By Objective Data", not "By Subjective Opinion". "BI is an umbrella term that combines architectures, tools, databases, analytical tools, applications, and methodologies."
- A decision follows Simon's four phases: Intelligence → Design → Choice → Implementation.
- A DSS (Decision Support System) has four subsystems: data management, model management, user interface, knowledge-based management.
- Computer support for decisions grew in this order: MIS (reports) → DSS → EIS (dashboards for executives) → BI → Analytics → Big Data → Automation.
- BI has four major components: DW, business analytics, BPM, user interface. The DW (data warehouse) is the foundation: "subject-oriented, integrated, time-variant, nonvolatile".
- OLTP runs the daily transactions. OLAP analyses the data stored in the DW.
- Data analytics has four types: descriptive, diagnostic, predictive, prescriptive. Value and difficulty both rise in that order.
- AI tries to "mimic the manner in which people think". Analytics computes on historical data. Each has limits alone, so they are combined. AI is now used widely in marketing and CRM (example: Salesforce Einstein).

| Topic | What to memorise | Slides |
|---|---|---|
| Two ways to decide | Subjective opinion vs objective data (3 steps each) | 3 |
| Simon's process | Intelligence, Design, Choice, Implementation | 9–10 |
| DSS framework | 2 dimensions: degree of structure (3) x type of control (3) | 11–12 |
| DSS characteristics | 14 characteristics | 13 |
| DSS components | 4 subsystems, with 4 and 5 sub-elements | 14–18 |
| Evolution | MIS → DSS → EIS; eras DSS → Enterprise/Executive IS → BI → Analytics → Big Data → Automation | 19–20 |
| BI | Umbrella term; data → information → decisions → actions; 3 objectives; 4 components | 22–24 |
| DW | Definition (4 words); DM, ODS, EDW; ETL | 25–26 |
| OLTP vs OLAP | Transactions vs analysis | 27 |
| BI trends | 6 key trends | 28 |
| Analytics | Definition; 4 primary focuses; 6-step life cycle; 5-step pipeline | 29–33 |
| 4 types of analytics | Question, tools, popularity, value vs difficulty | 35–42 |
| Case studies | Humana, retail, Facebook, Uber, AXA Hong Kong, HKTVmall | 43–58 |
| AI | 6 signs of intelligence; intelligent agent; AI in decisions | 60–66 |
| AI + analytics | Differences; 5 reasons to combine; Big Data; IoT | 67–72 |
| AI in marketing / CRM | 14 examples; Salesforce Einstein; 3-stage sales pipeline | 73–78 |

## Words you need

| Term | Slide wording | In plain words |
|---|---|---|
| BI (Business Intelligence) | "an umbrella term that combines architectures, tools, databases, analytical tools, applications, and methodologies" | Everything a company uses to turn data into better decisions. |
| DSS (Decision Support System) | "combination of individuals intellectual resources with the capabilities of the computer to improve the quality of decisions" | A computer system that helps a person decide. The person still decides. |
| MIS (Management Information Systems) | "a variety of reports used to understand and address the changing business needs and challenges" | Regular reports for managers. |
| EIS (Executive Information Systems) | "DSS designed and developed specifically for executives and their decision-making needs" | A dashboard for top managers to watch KPIs. |
| Intelligence (Simon's phase) | "The decision maker examines reality, identifies and defines the problem" | Find out what the problem is. |
| Design (Simon's phase) | "A model representing the system is constructed ... and then validated" | Build a simple model of the problem and list options. |
| Choice (Simon's phase) | "Selection of a proposed solution to the model" | Pick one option and test it. |
| Implementation (Simon's phase) | "Successful implementation results in solving the real problem" | Do it in the real world. |
| Structured problem | "Routine/repetitive problems for which standard solution methods exist" | A problem with a known recipe. |
| Unstructured problem | "Complex problems where there are no clear, standard solution methods" | A problem with no recipe. |
| DW (Data Warehouse) | "a subject-oriented, integrated, time-variant, nonvolatile collection of data in support of management's decision-making process" | One big, clean store of history data, built for analysis. |
| DM (Data Mart) | "a subset of a DW, typically consisting of a single subject area" | A small warehouse for one topic or one department. |
| ODS (Operational Data Store) | "provides a form of customer information file whose contents are updated throughout the course of business operations" | A store of current customer data that keeps changing during the day. |
| EDW (Enterprise Data Warehouse) | "a large-scale data warehouse used across the enterprise for decision support" | The warehouse for the whole company. |
| ETL | "extracted, transformed, and loaded" (slide 26); "extract, transform, load" (slide 32) | Take data out of the sources, clean it, put it into the DW. |
| OLTP | "OnLine Transaction Processing"; "handle a company's routine ongoing business, where the computer responds immediately to user requests" | The system that records each sale or payment, right now. |
| OLAP | "OnLine Analytical Processing"; analyses data stored in the DW | The system that asks questions about many past records. |
| BPM | "Business Process Management (BPM) (for monitoring & analyzing performance)" | The part of BI that checks how well the business is doing. |
| Data analytics | "the process of examining data to uncover useful information and support decision-making" | Looking into data to find something useful. |
| Descriptive analytics | "aims to provide insight into what has happened" | What happened? |
| Diagnostic analytics | "focuses on analysis of data to find out the causes of the event" | Where and why did it happen? |
| Predictive analytics | "helps model and forecast what might happen" | What will probably happen? |
| Prescriptive analytics | "seeks to determine the best solution or outcome among various choices, given the known parameters" | What should we do? |
| Intelligent agent (IA) | "a small computer software program that observes and acts upon changes in its environment by running specific tasks autonomously" | A small program that watches, acts by itself, and learns. |
| Analytics (vs AI) | "processes historical data using statistical, management science and other computational tools" | Calculation on past data. |
| AI | "AI's major objective is to mimic the manner in which people think, learn, reason, make decisions, and solve problems" | A machine that copies human thinking. |
| IoT | "collects a large amount of data from sensors and other 'things.'" | Devices with sensors that send data. |
| Salesforce Einstein | "an AI set of technologies used for enhancing customer interactions and supporting sales" | The AI layer inside the Salesforce CRM product. |

## Part 1 — Why BI: opinion versus data (slides 1–8)

**Slides 1–2 (title and textbook).** Lecture BI-1, "INTRODUCTION OF BI". Textbook: "Business Intelligence, Analytics, Data Science, and AI, 5th edition", Pearson, authors Ramesh Sharda and Efraim Turban. The figure numbers in these notes (Figure 1.1 and so on) are the textbook figures shown on the slides.

**Slide 3 — two "Ways of Solving Problem or Making Decision".** The slide examples: "How many stock we should prepare?" and "Which PolyU restaurant we should go?"

| Step | "By Subjective Opinion" | "By Objective Data" |
|---|---|---|
| 1 | "Describe problem to target person (friend, boss…)" | "Find data related to the problem" |
| 2 | "Collect Suggestion from target person" | "Analyze the data to find insight and solution" |
| 3 | "Action base on Suggestion" | "Action base on insight" |

**In plain words:** BI is the right-hand column. You act on what the data shows, not on what somebody feels.

**Slide 4 — "Why Business Intelligence?" (four reasons).**
1. "Business cycle times are extremely compressed; faster, and more informed."
2. "Managers need the right information at the right time and in the right place (core of the modern approaches to BI)."
3. "Organizations are being driven to capture, understand, and harness their data to support decision making and improve business operations."
4. "Legislation/regulations require leaders to document their business processes and sign off on the validity of the information they report to stakeholders."

**In plain words:** business moves faster, managers need the right information, companies must use their data, and the law makes leaders responsible for the numbers they report.

**Slide 5 — "Data and Its Analysis in Decision Making".**
- "The amount of data doubles every two years."
- "Decision making process requires an organization to collect and analyze vast stores of data."
- "Computer applications have moved from transaction-processing and monitoring activities => to problem analysis and solution applications."
- "These activities are done with cloud-based technologies, mostly accessed through mobile devices."

**In plain words:** computers used to only record things. Now they also help to analyse problems and find solutions.

**Slide 6 — video placeholder.** "A Case Study : The Power of Data" (YouTube). Topic: a case study of a company that uses data to make decisions. Its lessons are listed on slide 7.

**Slide 7 — "Takeaways from this case study" (five points).**
1. "You can use data to make decisions"
2. "The decisions ma[y] be complex – with tradeoffs because of capacity – which is why you may need to automate the decisions"
3. "The rules you use will evolve over time, be refined"
4. "You can measure the consequences of decisions – good vs. bad"
5. "You can tie decisions to business goals"

**Slide 8.** "The foundation of modern management lies in analytics and BI tools such as data warehousing, data mining, online analytical processing (OLAP), dashboards, and the use of cloud-based systems for decision support."

**In plain words:** remember the five named tools: data warehousing, data mining, OLAP, dashboards, cloud-based systems.

## Part 2 — Simon's decision-making process (slides 9–10)

★ The four phases are a short, fixed list. They are prime multiple-choice and true/false material (design/choice swap).

**Slide 9 — "Simon's Process: Intelligence, Design, and Choice". "Decision-making process phases":**

| No. | Phase | Slide wording | In plain words |
|---|---|---|---|
| 1 | Intelligence | "The decision maker examines reality, identifies and defines the problem" | Look at the real world. Say clearly what the problem is. |
| 2 | Design | "A model representing the system is constructed" by "making assumptions to simplify reality" and "identifying relationships between variables", "and then validated" | Build a simple model. List the possible solutions. |
| 3 | Choice | "Selection of a proposed solution to the model. This solution is tested to determine its viability." | Pick one solution. Test if it works. |
| 4 | Implementation | "Successful implementation results in solving the real problem. Failure leads to a return to an earlier phase of the process." | Do it for real. If it fails, go back. |

Note: the slide title names only three phases (Intelligence, Design, Choice), but the list has four. Implementation is the fourth.

**Slide 10 — Figure 1.1 "The Decision-Making/Modeling Process" (picture).**

| Phase | Activities listed in the figure | Output |
|---|---|---|
| Intelligence | "Organization objectives; Search and scanning procedures; Data collection; Problem identification; Problem ownership; Problem classification; Problem statement" | "Problem Statement" |
| Design | "Formulate a model; Set criteria for choice; Search for alternatives; Predict and measure outcomes" | "Alternatives" |
| Choice | "Solution to the model; Sensitivity analysis; Selection to the best (good) alternative(s); Plan for implementation" | goes to "Implementation of the solution" |
| Implementation | "Implementation of the solution" | "Success" or "Failure" |

Other labels in the figure:
- "Reality" enters Intelligence through "Simplification" and "Assumptions".
- Design is checked against reality by "Validation of the Model".
- Choice is checked against reality by "Verification, Testing of the Proposed Solution".
- "Success" goes back to reality. "Failure" (dotted line) goes back to Intelligence, Design or Choice.

**Example (extra, not on the slides):** A Mong Kok bubble-tea shop sells out every Saturday. Intelligence: find that the problem is not enough pearls on Saturday. Design: model demand by weekday and list options (order more, limit sales). Choice: pick "order 30% more on Friday" and test it on paper. Implementation: do it; if pearls are wasted, go back.

## Part 3 — The classical DSS framework and DSS characteristics (slides 11–13)

★ The two dimensions and their six terms are easy multiple-choice material.

**Slide 11 — "The Classical Decision Support System (DSS) Framework".** "The framework for computerized decision support can be represented [in] the following 2 dimensions":

| Dimension | Level | Slide wording |
|---|---|---|
| 1. "Degrees of structure" | Structured | "Routine/repetitive problems for which standard solution methods exist" |
| | Semi structured | "Fall between structured and unstructured problems" |
| | Unstructured | "Complex problems where there are no clear, standard solution methods" |
| 2. "Types of controls" | Strategic planning | "Defining long-range goals/policies for resource allocation" |
| | Management control | "The efficient use of resources in the accomplishment of organizational goals" |
| | Operational control | "the efficient and effective execution of specific tasks" |

**In plain words:** dimension 1 asks "is there a recipe for this problem?". Dimension 2 asks "how high in the company is this decision?" (top = strategic, middle = management, daily work = operational).

**Slide 12 — Figure 1.2 "Decision Support Frameworks" (picture, 3 x 3 table, cells numbered 1–9).** The figure calls the middle column "Managerial Control"; slide 11 calls it "Management control".

| "Type of Decision" | "Operational Control" | "Managerial Control" | "Strategic Planning" |
|---|---|---|---|
| Structured | Cell 1: "Monitoring accounts receivable; Monitoring accounts payable; Placing order entries" | Cell 2: "Analyzing budget; Forecasting short-term; Reporting on personnel; Making or buying" | Cell 3: "Managing finances; Monitoring investment portfolio; Locating warehouse; Monitoring distribution systems" |
| Semistructured | Cell 4: "Scheduling production; Controlling inventory" | Cell 5: "Evaluating credit; Preparing budget; Laying out plant; Scheduling project; Designing reward system; Categorizing inventory" | Cell 6: "Building a new plant; Planning mergers and acquisitions; Planning new products; Planning compensation; Providing quality assurance; Establishing human resources policies; Planning inventory" |
| Unstructured | Cell 7: "Buying software; Approving loans; Operating a help desk; Selecting a cover for a magazine" | Cell 8: "Negotiating; Recruiting an executive; Buying hardware; Lobbying" | Cell 9: "Planning research and development; Developing new technologies; Planning social responsibility" |

**Slide 13 — Figure 1.3 "Key Characteristics and Capabilities of DSS" (picture, 14 items).**
1. "Provides support for semistructured or unstructured problems"
2. "Supports managers at all levels"
3. "Supports individuals and groups"
4. "Supports interdependent or sequential decisions"
5. "Supports intelligence, design, choice, and implementation"
6. "Support variety of decision processes and styles"
7. "Is adaptable and flexible"
8. "Provides interactivity, ease of use"
9. "Improves effectiveness and efficiency"
10. "Provides complete human control of the process"
11. "Provides ease of development by end users"
12. "Provides models and analysis"
13. "Provides data access"
14. "Can be stand-alone, integrated, and Web-based tool"

**In plain words:** a DSS is for hard (semi-structured or unstructured) problems, for any manager, for all four Simon phases, and the human stays in control (item 10). Note item 1: a DSS is not mainly for structured problems.

## Part 4 — The four components of a DSS (slides 14–18)

★★ Asked in the mid-term past paper (multiple choice: which is NOT a component of a DSS; the wrong one was "Network management subsystem").

**Slide 14 — "A DSS can be composed of":**
1. "Data management subsystem"
2. "Model management subsystem"
3. "User interface subsystem"
4. "Knowledge-based management subsystem"

Figure 1.4 "Schematic View of DSS" (on slides 14–18) shows these boxes: "Data: internal and/or external" ("ERP/POS", "Legacy", "Web, etc.") → "Data Management", "Model Management", "External Models", "Knowledge-Based Subsystems", "User Interface", "Manager (user)", "Organizational Knowledgebase", "Other Computer-Based Systems", "Internet, Intranet, Extranet".

| Subsystem | Slide wording | Sub-elements on the slide | In plain words |
|---|---|---|---|
| 1. Data management (slide 15) | "It can be interconnected with the corporate data warehouse (a repository for corporate relevant decision-making data)" | 1. "DSS database" 2. "Database management system" 3. "Data directory" 4. "Query facility" | Stores and finds the data. |
| 2. Model management (slide 16) | "a component that includes quantitative models that provide the system's analytical capabilities and appropriate software management" | 1. "Model base" 2. "MBMS (Model Base Management System)" 3. "Modeling language" 4. "Model directory" 5. "Model execution, integration, and command processor" | Stores and runs the calculation models. |
| 3. User interface (slide 17) | "The user communicates with and commands the DSS through the user interface subsystem." | (no numbered list) | The screen the user works with. |
| 4. Knowledge-based management (slide 18) | "provides intelligence to augment the decision maker's own intelligence" and "to help understand a user's query and provide a consistent answer" | (no numbered list) | Adds expert knowledge (AI) to help the user. |

**Slide 17 — more on the user interface.**
- "The user is considered part of the system."
- "The Web browser has been recognized as an effective DSS GUI because it is flexible, user-friendly, and a gateway to almost all sources of necessary information and data."
- "Web browsers have led to the development of portals and dashboards (front end of many DSS)."

**Slide 18 — more on the knowledge-based management subsystem.**
- "Interconnected with the organization's knowledge repository or connected to thousands of external knowledge sources."
- "User interface developments are closely tied to the major new advances in their knowledge-based systems."

**Watch out:** the data management list and the model management list look alike. "Data directory" and "Query facility" belong to data management. "Model directory" and "Modeling language" belong to model management.

## Part 5 — Evolution: from MIS to DSS to EIS to BI (slides 19–20)

★ The order MIS → DSS → EIS and the three definitions are likely multiple-choice material.

**Slide 19 — Figure 1.5 "Evolution of Decision Support, Business Intelligence, Analytics, and AI" (picture).**

| Decade | Items on the timeline |
|---|---|
| 1970s | "Routine Reporting"; "AI/Expert Systems"; "Decision Support Systems" |
| 1980s | "Relational DBMS"; "On-Demand Static Reporting"; "Enterprise Resource Planning" |
| 1990s | "Data Warehousing"; "Dashboards, Scorecards"; "Executive Information Systems" |
| 2000s | "Software as a Service"; "Data/Text/Web Mining"; "Business Intelligence, BPM" |
| 2010s | "Cloud, Big Data Analytics"; "In-Memory/In-Database/MPP"; "Social Network/Media Analytics" |
| 2020s | "Automated Analytics"; "AI/Deep Learning, IoT/Sensors"; "Robotics, Smart Robo-Assistants" |

The band of arrows under the timeline reads, in order: "Decision Support Systems" → "Enterprise/Executive IS" → "Business Intelligence" → "Analytics" → "Big Data" → "Automation".

**Slide 20 — "Evolution Of Computerized Decision Support (cont.)".**
1. "Management Information Systems (MIS): a variety of reports used to understand and address the changing business needs and challenges."
2. "Decision Support Systems (DSS): combination of individuals intellectual resources with the capabilities of the computer to improve the quality of decisions."
3. "Executive Information Systems (EIS): the need for more versatile reporting leads to the development of EISs";
   - "DSS designed and developed specifically for executives and their decision-making needs"
   - "These systems were designed as graphical dashboards that allow decision makers to keep track of the key performance indicators."

**In plain words:** MIS = reports. DSS = person + computer deciding together. EIS = a DSS for executives, shown as a graphical dashboard of KPIs.

## Part 6 — BI: framework and architecture (slides 21–24)

★ The BI definition, the chain data → information → decisions → actions, the three objectives and the four components are all short lists.

**Slide 21.** Section title: "BI and Analytics".

**Slide 22 — "A Framework for Business Intelligence (BI)".**
- "BI is an umbrella term that combines architectures, tools, databases, analytical tools, applications, and methodologies."
- "BI process is based on the transformation of data -> information -> decisions -> actions"
- "BI's major objective is to enable":
  1. "interactive access to data (in real time),"
  2. "data manipulation, and"
  3. "appropriate analyses."
- "By analyzing historical and current data, situations, and performances, decision makers [are] able to make more informed and better decisions."

Figure 1.6 "Evolution of Business Intelligence (BI)" shows these tools all feeding into "Business Intelligence": "Querying and Reporting", "ETL", "Metadata", "Data Warehouse", "Data Marts", "DSS", "Spreadsheets (MS Excel)", "EIS/ESS", "Financial Reporting", "OLAP", "Digital Cockpits and Dashboards", "Scorecards and Dashboards", "Workflow", "Alerts and Notifications", "Data and Text Mining", "Predictive Analytics", "Broadcasting Tools", "Portals".

**In plain words:** BI is not one product. It is the name for the whole set of tools. Raw data becomes information, information leads to a decision, and the decision leads to action.

**Slide 23 — "Architecture of BI". "BI has four major components":**

| No. | Component | Slide wording |
|---|---|---|
| 1 | DW | "DW (with its source data)" |
| 2 | Business analytics | "a collection of tools for manipulating, mining, and analyzing the data in the DW" |
| 3 | BPM | "Business Process Management (BPM) (for monitoring & analyzing performance)" |
| 4 | User interface | "User interface", with sub-bullet "Dashboard" |

**Slide 24 — "Architecture of BI (cont')" (picture).**

| Area in the figure | Who | What they do |
|---|---|---|
| "Data Warehouse Environment" | "Technical staff" | "Build the data warehouse": "Organizing", "Summarizing", "Standardizing" data from the "Data Sources" |
| "Business Analytics Environment" | "Business users" | "Access" the "Data warehouse"; "Manipulation, results" |
| "Performance and Strategy" | "Managers/executives" | "BPM strategies" |
| "User interface" | all users | "Browser", "Portal", "Dashboard" |
| "Future component: Intelligent systems" | — | Drawn with a dotted line as a future part |

**In plain words:** technical staff build the warehouse, business users analyse it, managers use the results to steer performance, and everybody sees it through a browser, portal or dashboard.

## Part 7 — Data warehouse, OLTP versus OLAP, six BI trends (slides 25–28)

★★ OLTP vs OLAP was a mid-term multiple-choice question, and "OLAP" was a matching item in the 2023-24 final ("Online analysis of warehoused data"). ★ The DW definition and DM / ODS / EDW are standard multiple-choice items.

**Slide 25 — "Data Warehouse (DW) as a Foundation for BI".**
- "BI systems rely on DWs as the information source for creating insight and supporting managerial decisions."
- "DW is a subject-oriented, integrated, time-variant, nonvolatile collection of data in support of management's decision-making process."
- "The three main types of data sources for BI":

| Type | Slide wording |
|---|---|
| Data Marts (DM) | "a subset of a DW, typically consisting of a single subject area" |
| Operational Data Stores (ODS) | "provides a form of customer information file whose contents are updated throughout the course of business operations." |
| Enterprise Data Warehouses (EDW) | "a large-scale data warehouse used across the enterprise for decision support." |

**In plain words (extra, not on the slides — the slide gives the four words but does not explain them):**

| Word | Meaning |
|---|---|
| subject-oriented | Organised by topic (customer, product, sales), not by computer system. |
| integrated | Data from many sources is put into one common format. |
| time-variant | It keeps history. Every record belongs to a point in time. |
| nonvolatile | After loading, data is not changed or deleted. It is only read. |

**Slide 26 — "Data Warehouse (DW) as a Foundation for BI (cont.)".**
- "Data from many different sources can be extracted, transformed, and loaded into a DW for further access and analytics for decision support."
- "Data is structured to be available in a form ready for analytical processing activities": "OLAP, data mining, querying, reporting, decision support applications".

Figure 1.8 "Data Warehouse Framework and Views" reads left to right:
1. "Data Sources": "ERP", "Legacy", "POS", "Other OLTP/Web", "External Data"
2. "ETL Process": "Select", "Extract", "Transform", "Integrate", "Load"
3. "Enterprise Data Warehouse", with "Metadata" and "Replication"
4. "Data Marts": "Data mart (Marketing)", "Data mart (Operations)", "Data mart (Finance)", "Data mart (...)"; or the "No data mart options" path
5. "API/Middleware"
6. "Applications (Visualization)": "Routine Business Reporting"; "Data/Text Mining"; "OLAP, Dashboard, Web"; "Custom-Built Applications"

**Slide 27 — "Transaction Processing versus Analytic Processing".**
- "Transaction processing systems are constantly involved in handling updates to what may be known as operational databases."
- "OLTP (OnLine Transaction Processing) systems handle a company's routine ongoing business, where the computer responds immediately to user requests."
- "The OLTP system is efficient for transaction processing, but inefficient for end-user ad hoc reports, queries, and analysis."
- "In contrast, a DW is typically a distinct system that provides storage for data that will be used for analysis by OLAP (OnLine Analytical Processing) systems."

| | OLTP | OLAP |
|---|---|---|
| Full name | "OnLine Transaction Processing" | "OnLine Analytical Processing" |
| Job | "handle a company's routine ongoing business" | "analysis" of the data stored in the DW |
| Speed | "the computer responds immediately to user requests" | Picture: "Slow queries" |
| Good at | "efficient for transaction processing" | Ad hoc reports, queries, analysis (the things OLTP is "inefficient" for) |
| Data (picture) | "Transactional", "Fast processing", "Normalized", "Current data" | "Analytical", "Slow queries", "denormalized", "Historical data" |
| Sits on (picture) | "BUSINESS PROCESS" ("Operations") | "BUSINESS DATA WAREHOUSE" ("Information") |

**Example (extra, not on the slides):** tapping an Octopus card at an MTR gate is OLTP: one small record, answered at once. Asking "which station had the most exits each Sunday last year?" is OLAP: many old records, read from a warehouse.

**Slide 28 — "Business Intelligence".**
- "The fundamental reasons for investing in BI must be aligned with the company's business strategy."
- "BI improve company business processes and transforming it to be more data driven."
- "BI tools adopts new technologies and sometimes integrated among themselves, resulting in six key trends":
  1. "Big Data"
  2. "Focus on customer experience as opposed to just operational efficiency."
  3. "Mobile and even newer user interfaces—visual, voice, mobile."
  4. "Predictive and prescriptive analytics, machine learning, artificial intelligence."
  5. "Migration to cloud."
  6. "Much greater focus on security and privacy protection."

## Part 8 — Data analytics: definition, users, focus, life cycle, pipeline (slides 29–34)

★ The 6-step life cycle and the 5-step pipeline are ordered lists. Order questions are easy to set.

**Slide 29 — "What is Data Analytics?" (Source: KPMG).**
- "Data analytics is the process of examining data to uncover useful information and support decision-making"
- "The goal is to discover patterns, trends, and insights that would otherwise be hidden in the mass of data"

The picture shows a funnel. Inputs: "Economic data", "Internal sales data", "Social media data", "Cost data", "Operational data". Outputs: "Insights", "Trends", "Risks".

**Slide 30 — "Who uses Data Analytics".** "Data analytics has been adopted by nearly all sectors and industries":
- "Banking And Securities"
- "Media & Entertainment"
- "Healthcare (example in later slides)"
- "Hotel & Hospitality"
- "Manufacturing"
- "Retail (example in later slides)"

Two more bullets on the slide: "Large amounts of data" and "Turnarounds are quick".

**Slide 31 — "Primary Focus for Analytics" (four).**

| Focus | Slide wording |
|---|---|
| "Understand Customer Behavior" | "To make a favor to customer in order to maximize profit" |
| "Understand Products Usage" | "Improve new products by observing how it is used" |
| "Increase Operational Efficiency" | "Reduce time and cost" |
| "Business Model Innovation" | "Use data to create/support a new market" |

**Slide 32 — "Data Analytics Life Cycle" (six steps, drawn as a circle).**

| Step | Name | Slide wording |
|---|---|---|
| 1 | "Discovery" | "Know what problem you are solving" |
| 2 | "Data Preparation" | "Identify useful data, and ETL (extract, transform, load)" |
| 3 | "Model Planning" | "Decide which models (/solution/tools) to use" |
| 4 | "Build & Execute Model" | "Implement your decided model on the selected data" |
| 5 | "Communicate results" | "Present your findings clearly" |
| 6 | "Operationalizing" | "Deploy the model for the coming operational data" |

The slide adds: "We focus more on 3 and 4 in this course".

**Slide 33 — "Data Analytics Pipeline" (five boxes).** "It involves collecting raw data from different sources, cleaning and organizing (ETL) it, and using tools and techniques to analyze and present it."

"Collect" → "Transform (ELT)" → "Store" → "Analyze" → "Presentation"

Note: the sentence on the slide says "(ETL)" but the box says "Transform (ELT)". Both spellings are on the slide. **(extra, not on the slides)** ETL means transform before loading; ELT means load first and transform later.

**Slide 34 — video placeholder.** "Data Transformation Revisit" (YouTube). Topic: how data is transformed (the ETL step).

## Part 9 — The four types of data analytics (slides 35–42)

★★ Four parallel items with a question, tools, popularity and value each. This is the best table in the lecture for multiple choice, true/false (swap two types) and a short question. Learn the whole table.

**Slide 35.** "Analytics [is] not a tool/technology, rather it is the way of thinking and acting on data."

**Complete comparison (slides 35–42).**

| | Descriptive | Diagnostic | Predictive | Prescriptive |
|---|---|---|---|---|
| Question (slide 35) | "What has happened?" | "Where & Why did it happen?" | "What might happen?" | "What should we do?" |
| Question (slide 36, KPMG) | "What happened?" | "Why did it happen?" | "What will happen?" | "What should we do?" |
| Slide title (37–40) | "What happened?" | "Where & Why did it happen?" | "What will happen?" | "Make it happen" |
| "Answer to question…" (slide 41) | "What happened?" | "Where and/or Why exactly?" | "What are trends?" | "What to do?" |
| First line (37–40) | "insight into the past" | "to understand where and why" | "to understand the future" | "to advice on possible outcomes" |
| What it does (37–40) | "aims to provide insight into what has happened" | "focuses on analysis of data to find out the causes of the event and relates to Root-cause analysis" | "helps model and forecast what might happen"; "probabilistic in nature" | "seeks to determine the best solution or outcome among various choices, given the known parameters" |
| Methods and technologies (37–40) | "frequency distribution, dashboards, business activity monitoring, content analytics, geospatial analytics" | "A/B testing, data mining and interactive visualization, pattern/anomaly detection and clustering/classification" | "data mining, forecasting, clustering, machine learning and simulations" | "fuzzy logic, optimization, expert system, and generative AI" |
| "Example Tools/Techniques" (slide 41) | "Sampling, mean, mode, median, standard deviation, range, variance, histogram, quartiles, and frequency distributions" | "A/B Testing, Cluster and factor analysis, multiple regression, data mining" | "Cluster analysis, association analysis, multiple regression, decision tree, neural networks, simulation, and forecasting tools" | "Fuzzy logic, Expert system, optimization, generative AI" |
| "Level of popularity" (slide 41) | "Used by almost all organizations" | "Used by many organizations" | "Used by a small but growing group of organizations" | "Not yet widespread" |
| KPMG description (slide 36) | "Produce reports to understand current situation" | "Retrospective analysis to understand the outcome that occurred" | "Use of historical data and driver-based analysis with advanced analytical modeling to understand potential range of outcomes" | "Development of models incorporating predictive analytics to optimise decisions" |
| KPMG example (slide 36) | "Revenue by dimension (geography, product, service, customer)" | "Drill down into historical revenue numbers to understand the drivers" | "Future estimates of revenue and profitability based on demand drivers" | "Strategic scenario analysis of opportunities to improve profitable growth (new markets, customers, services, channels)" |
| Value and difficulty (slide 42) | Lowest value, lowest difficulty: "the most common and easiest" | Higher | Higher again | Highest value, highest difficulty |
| Arrow label (slide 42) | "Hindsight" end | between "Hindsight" and "Insight" | between "Insight" and "Foresight" | "Foresight" end |
| KPMG scale (slide 36) | "Foundational" end | | | "Leading-edge" end |

**In plain words:** the first two types look back (what, then why). The last two look forward (what will happen, then what to do). Each step is harder, less common, and worth more.

**Extra details from the slides.**
- Slide 39 (predictive): "It tells 'What is likelihood / probability of something happening in future?'. In general predictive analytics is probabilistic in nature." It gives a chance, not a certain answer.
- Slide 42: the chart has "Value" on the vertical axis and "Difficulty" on the horizontal axis. The four boxes climb from Descriptive (bottom left) to Prescriptive (top right) along an arrow labelled "Hindsight", "Insight", "Foresight".
- Slide 42: "Descriptive analysis is the most common and easiest" – "Understand distribution, variance".
- Slide 42: "When to use which type depends on": (1) "The problem you want to solve" (2) "What data do you have" (3) "Any assumption you can put to your model".

**Watch out:** some tools are listed under two types. "data mining" is under both diagnostic and predictive. "multiple regression" and cluster analysis are also under both (slide 41). Generative AI, fuzzy logic, expert system and optimization are only under prescriptive. Mean, median, histogram are only under descriptive. A/B testing is only under diagnostic.

**Example (extra, not on the slides):** a Wellcome store. Descriptive: "we sold 500 boxes of mooncakes last week". Diagnostic: "sales fell in Sha Tin because a rival opened next door". Predictive: "we will probably sell 2,000 boxes in Mid-Autumn week". Prescriptive: "order 2,200 boxes and put them at the entrance".

## Part 10 — Case studies (slides 43–58)

★ Cases can be asked as "which type of analytics?" or "what data was used?". Learn the company, the data, the method and the number.

**Slides 43–44 — "Healthcare Analytics (Preventing Falls in Seniors)" (Humana).**
- Problem and company: "Accidental falls are a major health risk for adults age 65+ years", with costs "estimated to be $34 billion in 2013 alone". "Humana is a major health insurance company, with 3.2 million members, most of whom are seniors."
- Data used: "Administrative medical and pharmacy claims, clinical data, temporal clinical patterns, and other data".
- Method and result: "the Falls PM (Predictive Models)", so this is predictive analytics. Humana could "identify 20,000 consumers at a high risk of falling". They "wear a device that detects falls and alerts a service for immediate assistance."

**Slide 45 — "Retail Analytics".**
- "Goal of the analytics industry is to use information about business suppliers, customers, employees, and stakeholders to make better decisions."
- "Amazon's enormous investments in analytics to power their value chain."
- "Walmart & Target have invested millions of dollars in analytics for their supply chains."

**Slides 46–47 — Table 1.1 "Examples of Analytics Applications in the Retail Value Chain" (picture, nine applications).**

| No. | "Analytic Application" | "Business Question" | "Business Value" (short) |
|---|---|---|---|
| 1 | "Inventory Optimization" | "Which products have high demand?"; "Which products are slow moving or becoming obsolete?" | "Forecast the consumption of fast-moving products" to "avoid a stock out scenario"; faster turnover of slow products "by combining them with one in high demand" |
| 2 | "Price Elasticity" | "How much net margin do I have on the product?"; "How much discount can I give on this product?" | "Markdown prices for each product can be optimized to reduce the margin dollar loss"; optimized bundle price |
| 3 | "Market-Basket Analysis" | "What products should I combine to create a bundle offer?"; "Should I combine products based on slow-moving and fast-moving characteristics?"; "Should I create a bundle from the same category or a different category line?" | "The affinity analysis identifies the hidden correlations between the products"; better bundles; more "cross-selling or up-selling" |
| 4 | "Shopper Insight" | "Which customer is buying what product at what location?" | "By customer segmentation, the business owner can create personalized offers resulting in better customer experience and retention of the customer." |
| 5 | "Customer Churn Analysis" | "Who are the customers who will not return?"; "How much business will I lose?"; "How can I retain the customers?"; "What demography of customer is my loyal customer?" | Find relationships that "show high churn"; "Based on the customer lifetime value (LTV), the business can do targeted marketing resulting in retention of the customer." |
| 6 | "Channel Analysis" | "Which channel has lower customer acquisition cost?"; "Which channel has better customer retention?"; "Which channel is more profitable?" | "Marketing budget can be optimized based on insight for better return on investment." |
| 7 | "New Store Analysis" | "What location should I open?"; "What and how much opening inventory should I keep?" | "Best practices of other locations and channels can be used to get a jump-start"; "Comparison with competitor data" to attract new customers |
| 8 | "Store Layout" | "How should I do store layout for better topline?"; "How can I increase my in-store customer experience?" | "Understand the association of products to decide store layout"; plan "Workforce deployment" |
| 9 | "Video Analytics" | "What demography is entering the store during the peak period of sales?"; "How can I identify a customer with high LTV at the store entrance so that a better personalized experience can be provided to this customer?" | "In-store promotions and events can be planned based on the demography of incoming traffic"; "Targeted customer engagement and instant discount" gives "higher retention" |

**Slide 48 — "More Cases Studies" (overview of the four companies).**

| Company | Uses of data named on slide 48 |
|---|---|
| Facebook | "Personalised recommendations"; "Ad targeting"; "Content optimisation" |
| Uber | "Ride Matching"; "Dynamic Pricing"; "Route Optimization"; "Predictive Maintenance" |
| AXA | "Matching with Financial Consultant"; "Discovery of correlation between claims risk & energy consumption" |
| HKTVmall | "Inventory forecasting"; "CRM"; "Product Recommendation and Review Dashboard" |

**Slides 49–50 — Facebook.** "Well known social media platform".
- "Personalised recommendations": recommends content "based on their interests, past interactions, and demographic information". The picture compares "COLLABORATIVE FILTERING" ("Similar users") with "CONTENT-BASED FILTERING" ("Similar articles").
- "Ad targeting": "targeted Advertisement to users based on their preferences, behaviors, and online activity."
- "Content optimisation": "By analysing user posts and interactions", Facebook can "enhance user engagement, improve content visibility, and foster community interactions."

**Slides 51–53 — Uber.**
- Data: "Uber's system collect Big Data for predictive modeling including vehicles locations, traffic patterns, user demand, driver availability, and weather or events".
- "Ride Matching and Allocation": uses "current bookings, driver locations, optimal route paths, traffic updates, and rider preferences to match riders with the best available drivers".
- "Dynamic Pricing (Surge Pricing)": "machine-learning algorithms" set the price from "historical data, current supply and demand, time of day, weather conditions, and local events".
- "Route Optimization": "predictive analytics to anticipate changes in traffic patterns and adjust routes proactively rather than reactively"; data: "historical traffic patterns, real-time speed data, and predictive models".
- "Predictive Maintenance": "analyzing data from vehicle sensors and using machine learning models to predict when a vehicle component is likely to fail and proactively schedule maintenance."

**Slides 54–55 — AXA Hong Kong.**
- General: "Use of AI to transform all areas of the business: marketing, operations, finance, etc."; "engaging different teams to use data and analytics effectively on a daily basis". Source on the slide: the "Big Data - Insurance category at HKB Technology Excellence Awards 2022".
- "Matching between customers and financial consultants": "leveraging big data to analyzing their pattern of similarities (e.g. age, family profile and residential address)". Result: "enhanced customer experience and generated better business results."
- "GO GREEN home insurance campaign": "discovery of a correlation between claims risk and energy consumption". Data: "text mining" of "the home claim data", plus "external energy consumption and weather data from the government's open database". Hypothesis: "the longer stay-at-home due to COVID lead to higher home energy consumption, hence higher claim frequency". Finding: "a positive correlation between home claims, energy consumption, and a few weather factors is mathematically proven". Output: a "Green Score for each individual household", using "a tree-based machine learning algorithm".

**Slides 56–58 — HKTVmall.**
- "inventory forecasting": needed "during promotional periods where the sales increment could be well over 100 %!!"; "The pain point comes when retailers don't have enough stock".
- "Customer Relationship Management (CRM)": data = "a customer's browsing history and purchase behaviors"; companies can "easily target promotions at prospective buyers. This leads to higher conversion rates."
- "Product Recommendation" "for add-on offering": after a purchase, customers "are prompted to buy further products that might interest them." Result: "increase conversion rates by up to 15 per cent, or HKD100 per basket."
- Slide 58 — video placeholder: "HKTVMall – Product Review Dashboard" (YouTube). Topic: a dashboard that shows product reviews.

**Which type of analytics? (extra, not on the slides — my reading, using the tool lists on slides 37–41. The slides themselves only use the word "predictive" for Humana and Uber.)**

| Case | Likely type | Why |
|---|---|---|
| Humana falls | Predictive | "Predictive Models" find who is at high risk. |
| Retail: churn, inventory | Predictive | "Who are the customers who will not return?", "Forecast the consumption". |
| Retail: price elasticity | Prescriptive | Prices "can be optimized"; optimization is a prescriptive tool. |
| Facebook recommendations | Predictive | Predicts what content a user will like. |
| Uber | Predictive, then prescriptive | "predictive modeling"; pricing and routing also decide what to do. |
| AXA GO GREEN | Diagnostic, then predictive | Tests why claims rise (correlation); then a tree-based model scores households. |
| HKTVmall inventory | Predictive | "inventory forecasting". |
| HKTVmall review dashboard | Descriptive | "dashboards" are a descriptive tool (slide 37). |

## Part 11 — AI and BI: intelligence, intelligent agents, AI in decisions (slides 59–66)

★ The intelligent agent definition and the four AI support steps are likely multiple-choice material.

**Slide 59.** Section title: "AI and BI".

**Slide 60 — "What Is Intelligence?"** "Intelligence is a broad term measured by an IQ test." Six "signs of human intelligence":
1. "Learning or understanding from experience"
2. "Making sense out of ambiguous, incomplete, or even contradictory messages and information"
3. "Responding quickly and successfully to a new situation"
4. "Understanding/inferring in a rational way, and solving problems"
5. "Applying knowledge to manipulate environments and situations"
6. "Recognizing & judging the relative importance of elements in a situation"

**Slide 61 — "How Intelligent Is AI?"**
- "AI machines have demonstrated superiority over humans in playing complex games such as chess, Jeopardy!, and Go by defeating the world's best players."
- "Despite this many AI applications still show less intelligence than humans."

Table 2.1 "Artificial Intelligence versus Human Intelligence" (picture; "Consistency" appears twice on the slide):

| "Area" | "AI" | "Human" |
|---|---|---|
| Execution | "Very fast" | "Can be slow" |
| Emotions | "Not yet" | "Can be positive or negative" |
| Computation speed | "Very fast" | "Slow, may have trouble" |
| Imagination | "Only what is programmed for" | "Can expand existing knowledge" |
| Answers to questions | "What is in the program" | "Can be innovative" |
| Flexibility | "Rigid" | "Large, flexible" |
| Foundation | "A binary code" | "Five senses" |
| Consistency | "High" | "Variable, can be poor" |
| Process | "As modeled" | "Cognitive" |
| Form | "Numbers" | "Signals" |
| Memory | "Built in, or accessed in the cloud" | "Use of content and scheme memory" |
| Brain | "Independent" | "Connected to a body" |
| Creativity | "Uninspired" | "Truly creative" |
| Durability | "Permanent, but can get obsolete if not updated" | "Perishable, but can be updated" |
| Duplication, documentation, and dissemination | "Easy" | "Difficult" |
| Cost | "Usually low and declining" | "Maybe high and increasing" |
| Consistency | "Stable" | "Erratic at times" |
| Reasoning process | "Clear, visible" | "Difficult to trace at times" |
| Perception | "By rules and data" | "By patterns" |
| Figure missing data | "Usually cannot" | "Frequently can" |

**In plain words:** AI wins on speed, consistency, cost and copying. Humans win on creativity, flexibility, emotion and filling in missing data.

**Slide 62 — "Intelligent Agents".**
- "An intelligent agent (IA) is a small computer software program that observes and acts upon changes in its environment by running specific tasks autonomously."
- "An IA directs an agent's activities to achieve specific goals related to the changes in the surrounding environment."
- "IAs have the ability to learn by using their knowledge"

Figure 2.4 "The Major AI Technologies" has "Artificial Intelligence" in the centre. The boxes around it: "Intelligent Agents", "Machine Learning", "Neural Network", "Deep Learning", "Cognitive Computing", "Machine Computer Visions", "Image Generations", "Video Analysis", "Robotics", "Autonomous Vehicle", "Knowledge Systems", "Chatbots", "Natural Language Process", "Speech and Voice Understanding and Generation", "Machine Translation of Languages", and one box printed as "Degenerated Reality".

**Slide 63 — "Intelligent Agents (cont.)".** "IAs are tools for overcoming Internet information overload and making computers viable decision support tools."
- "Example 1": "a virus detection program. It resides in a computer, scans incoming data, and removes viruses automatically while learning to detect new virus types and detection methods."
- "Example 2": "Allstate Business Insurance uses an intelligent agent to reduce call center traffic and provide human insurance agents during the rate-quoting process with business customers."

**Slide 64 — "Issues and Factors in Using AI in Decision Making".** "These factors determine the justification of AI usage and its chance of success":
1. "The nature of the decision (E.g., routine decisions = likely automated)"
2. "The method of support, what technologies are used"
3. "Cost-benefit & Risk Analyses: necessary for large-scale decisions, but hard to compute with AI models due to difficulties in measuring costs, risks, & benefits."
4. "Using Business Rule: AI systems can be based on business rules, whose quality determines that of the automated."
5. "AI Algorithms: are the basis for automated decisions & decision support."
6. "Speed: Decision automation is dependent on the speed decisions needs to be made. Some decisions takes too much time to get all the relevant input data."

**Slide 65 — "AI Support of the Decision-Making Process" (four steps).**

| Step | Slide wording |
|---|---|
| 1. "Problem Identification" | "collecting data through technology that can be used by AI algorithms. Performance levels of machines are compared to standards, and trend analysis can point to opportunities." |
| 2. "Generating/Finding Alternative Solutions" | "matching problem characteristics with best practice, or proven solutions stored in databases. Tools such as case-based reasoning and neural computing are for this purpose." |
| 3. "Selecting a Solution" | "evaluate proposed solutions, predict future impacts, asses[s] chance of success, or predict a reply to actions taken by a competitor." |
| 4. "Implementing the Solutions" | "demonstrates the superiority of proposals and to assess resistance to changes." |

**In plain words:** these four steps match Simon's four phases (Intelligence, Design, Choice, Implementation), with different names.

**Slide 66 — "Automated Decision Making".**
- "The process of automated decision making starts with knowledge acquisition and creation of a knowledge repository."
- "The system generates and submits responses to user's questions. Solutions are evaluated to improve the knowledge repository, and complex situations are forwarded to humans."
- "Companies use automated decision making for both their external operations (e.g., sales) and internal operations (e.g., resource allocation)"
- "Example: Supporting Nurses' Diagnosis Decisions": "Researchers used AI tools to conduct data mining to predict the probable success of automated nursing diagnoses based on patient characteristics."

## Part 12 — Analytics versus AI, and why they converge (slides 67–72)

★ "Analytics vs AI" and "why combine" are two short lists. They suit a short question or true/false.

**Slide 67 — "Major Differences between Analytics and AI".**

| | Analytics | AI |
|---|---|---|
| What it does | "processes historical data using statistical, management science and other computational tools to describe situations, predict results, and propose recommendations for solutions to problems" | "AI's major objective is to mimic the manner in which people think, learn, reason, make decisions, and solve problems." |
| Main tool | "computation" | "knowledge and intelligence" |

"The emphasis in AI is on knowledge and intelligence as major tools for solving problems rather than relying on computation, which we do in analysis."

**Slide 68 — "Why Combine AI and Analytics, and other Intelligent Systems technology?"** "Analytics, AI and their different technologies have limitations, resulting in only a small chance that they can be used to reach organizational excellence." Five reasons:
1. "Predictive models have unintended effects (e.g. bias)"
2. "The results of analytics may be good for some applications but not for others"
3. "Models are as good as their input data and assumptions"
4. "Data could be incomplete/inaccurate."
5. "Data collected from different sources can vary in format and quality."

**Slide 69 — "Why Combine AI and Analytics (cont')".**
- "A major reason for the high failure rate of AI is that some of its technologies need a large amount of data (Big Data)."
- "Without this continuous flow of data, there would not be good learning in AI."

**Slide 70 — "How Convergence Can Help?"**
- "The next generation of business intelligence platforms will use AI to automatically locate, visualize, and narrate important things. This can also be used to create automatic alerts and notifications."
- "Machine learning and deep learning can support analytics by conducting pattern recognition and more accurate predictions. AI will help to compare actual performance with the predicted one."

**Slide 71 — "Big Data Is Empowering AI Technologies".**
- "Technologies and methods that enable capturing, cleaning, and analyzing Big Data, can also enable companies to make real-time decisions."
- "The availability of new Big Data analytics enables new capabilities in AI technologies that were not possible until recently."
- "Big Data can empower AI due to":
  1. "The new capabilities of processing Big Data at a much reduced cost."
  2. "The availability of large data sets online."
  3. "The scale up of algorithms, including deep learning, is enabling powerful AI capabilities."

**Slide 72 — "The Convergence of AI and the IoT".**
- "The IoT collects a large amount of data from sensors and other 'things.' These data need to be processed for decision support."
- "Combining AI and IoT can":
  - "lead to the 'next-level solutions and experiences.' The emphasis in such combination is on learning more about customers and their needs."
  - "facilitate competitive analysis and business operation."
- "Three examples of combining AI and IoT": (1) "The smart thermostat of Nest Labs" (2) "Automated vacuum cleaners" (3) "Self-driving vehicles"

**In plain words:** analytics needs AI to find patterns and predict better. AI needs Big Data to learn. IoT sensors supply the data. So the three grow together.

## Part 13 — AI in marketing, advertising and CRM (slides 73–79)

★ This is the bridge to the CRM half of the course. The 14 examples and Salesforce Einstein are likely multiple-choice items.

**Slide 73 — "AI in Marketing, Advertising, and CRM". "Examples of AI in marketing" (14):**
1. "Product & personal recommendations"
2. "Smart search engines"
3. "Fraud and data breaches detection"
4. "Social semantics"
5. "Website design"
6. "Producer pricing"
7. "Predictive customer service"
8. "Ad targeting"
9. "Speech/Image recognition"
10. "Language translation"
11. "Customer Segmentation"
12. "Sales forecasting"
13. "Content generation"
14. "Using bots, robo advisors, etc."

**Slide 74 — "Customer Experiences and CRM".** "A major impact of AI technologies is changing customer experiences through":
1. "Use NLP for creating user documentation. This improves customer–machine dialogue."
2. "Use visual categorization to organize images (E.g., IBM's Visual Recognition & Clarifai)"
3. "Provide personalized and segmented services by analyzing customer data. This includes improving shopping experience and CRM."

**Slide 75 — "Example: Salesforce's AI Einstein".**
- "Salesforce Einstein is an AI set of technologies used for enhancing customer interactions and supporting sales."
- "The system delivers dynamic sales dashboards to sales reps, tracks performance and manages teamwork by using sales analytics. The AI product also can provide predictions and recommendations."
- "Einstein's automatically prioritized sales leads make sales reps more productive when dealing with sales leads and potential opportunities. The sales reps also get insights about customers' sentiments, competitors' involvement, and other information."

**In plain words:** Einstein tells a salesperson which lead to call first, shows a sales dashboard, and gives predictions and recommendations.

**Slide 76 — video placeholder.** A YouTube link with no slide title. The picture shows a Salesforce video named "Einstein Copilot Analytics". Topic: a demo of Salesforce Einstein.

**Slide 77 — "Other Uses of AI in Marketing".** "The following show the diversity of AI technologies used in marketing":
- "Bots can mimic the expertise of in-store sales people, and make shopping easier." (The picture is a Hang Seng Bank chatbot screen.)
- "It provides lead generation. AI can help generate sales leads by analyzing customers' data. The program can generate predictions. Insights can be generated by intelligent analytics."
- "It can increase customer loyalty using personalization."

**Slide 78 — "Other Uses of AI in Marketing (cont.)".** "It can improve the sales pipeline. Robots can convert unknown visitors into customers using the following three stages":
1. "Prepare a list of target customers in the database"
2. "Send information, ads, videos, and so on to prospects on the list created earlier"
3. "Provide the company sales department with a list of leads that successfully convert potential customers to buyers."

**Slide 79 — "Summary".** The lecture's own summary: "Business Intelligence and Decision Support System"; "Components of a Decision Support System"; "Data Analytics" ("Types of Data Analytics", "Application in various domains"); "AI and BI".

## How this lecture is examined

**Past questions on this lecture**

- Mid-term past paper, multiple choice: "Which of the following is NOT typically considered a component of a DSS? A) Data management subsystem B) Model management subsystem C) User interface subsystem D) Network management subsystem". Answer: D. Source: slide 14 (the fourth real component is the knowledge-based management subsystem).
- Mid-term past paper, multiple choice on OLTP vs OLAP. Correct option: "OLTP systems provide immediate responses for routine transactions, while OLAP systems are designed for analytical queries and reporting." Source: slide 27.
- Mid-term past paper, multiple choice: "Which BI technique allows organizations to identify customer base segments and attach value?" Answer: data mining. Nearest slide content: slide 8 names data mining as a BI tool; slide 23 says business analytics tools are for "manipulating, mining, and analyzing the data in the DW"; slides 38–41 list data mining and cluster analysis; slide 46 says "By customer segmentation, the business owner can create personalized offers". The exact sentence of the question is not on the BI1 slides.
- 2023-24 final, matching item: "OLAP" matched with "Online analysis of warehoused data". Source: slide 27.
- 2024-25 and 2025-26 finals: 20 multiple-choice questions over all lectures (text not released). This year's paper adds a true/false part. Expect the fixed lists of this lecture: Simon's 4 phases, the 2-dimension DSS framework, the 4 DSS components and their sub-elements, MIS → DSS → EIS, the 4 BI components, the DW definition, DM / ODS / EDW, OLTP vs OLAP, the 6 BI trends, the 6-step life cycle, the 5-step pipeline, the 4 types of analytics, analytics vs AI, intelligent agents, why combine AI and analytics, AI in marketing / CRM, and Salesforce Einstein.

**Model answers**

**Q (4 marks). Describe the four phases of Simon's decision-making process.**
1. Intelligence: "The decision maker examines reality, identifies and defines the problem". (1 mark)
2. Design: a model of the system is built by "making assumptions to simplify reality" and "identifying relationships between variables", and then validated. (1 mark)
3. Choice: "Selection of a proposed solution to the model"; the solution "is tested to determine its viability". (1 mark)
4. Implementation: success means "solving the real problem"; "Failure leads to a return to an earlier phase of the process." (1 mark)

**Q (4 marks). Name the four components of a DSS and state one fact about each.**
1. Data management subsystem: made of the DSS database, database management system, data directory and query facility; it can connect to the corporate data warehouse. (1 mark)
2. Model management subsystem: holds "quantitative models that provide the system's analytical capabilities"; includes the model base and the MBMS. (1 mark)
3. User interface subsystem: "The user communicates with and commands the DSS" through it; the Web browser is an effective DSS GUI. (1 mark)
4. Knowledge-based management subsystem: "provides intelligence to augment the decision maker's own intelligence". (1 mark)

**Q (4 marks). What is a data warehouse? Name the three main types of data sources for BI.**
1. A DW is "a subject-oriented, integrated, time-variant, nonvolatile collection of data in support of management's decision-making process". (1 mark)
2. Data mart (DM): "a subset of a DW, typically consisting of a single subject area". (1 mark)
3. Operational data store (ODS): "a form of customer information file whose contents are updated throughout the course of business operations". (1 mark)
4. Enterprise data warehouse (EDW): "a large-scale data warehouse used across the enterprise for decision support". (1 mark)

**Q (4 marks). Distinguish OLTP from OLAP.**
1. OLTP (OnLine Transaction Processing) handles "a company's routine ongoing business". (1 mark)
2. In OLTP "the computer responds immediately to user requests"; it constantly updates operational databases. (1 mark)
3. OLTP is "efficient for transaction processing, but inefficient for end-user ad hoc reports, queries, and analysis". (1 mark)
4. OLAP (OnLine Analytical Processing) analyses data stored in a DW, which is "a distinct system" from the transaction system. (1 mark)

**Q (8 marks). Describe the four types of data analytics. For each, give the question it answers and one tool.**
1. Descriptive: "What happened?" — insight into the past. (1 mark)
2. Tool: mean, median, histogram, frequency distribution or dashboards. (1 mark)
3. Diagnostic: "Where & Why did it happen?" — finds the causes; root-cause analysis. (1 mark)
4. Tool: A/B testing, factor analysis or data mining. (1 mark)
5. Predictive: "What might happen?" / "What will happen?" — forecasts; it is probabilistic. (1 mark)
6. Tool: decision tree, neural networks, simulation or forecasting. (1 mark)
7. Prescriptive: "What should we do?" — finds "the best solution or outcome among various choices". (1 mark)
8. Tool: optimization, fuzzy logic, expert system or generative AI. (1 mark)

If the question also asks to compare them: descriptive is "the most common and easiest" and is "Used by almost all organizations"; prescriptive is "Not yet widespread"; value and difficulty rise from descriptive to prescriptive.

**Q (3 marks). State the major differences between analytics and AI.**
1. Analytics "processes historical data using statistical, management science and other computational tools". (1 mark)
2. AI's major objective is "to mimic the manner in which people think, learn, reason, make decisions, and solve problems". (1 mark)
3. AI's emphasis is on "knowledge and intelligence as major tools for solving problems rather than relying on computation", which analytics does. (1 mark)

## Easy to mix up

| A | B | How to tell them apart |
|---|---|---|
| OLTP | OLAP | T = Transactions: daily business, immediate response, operational database. A = Analytical: analysis of data in the DW. |
| Descriptive | Diagnostic | Both look back. Descriptive = what happened (mean, histogram). Diagnostic = where and why (A/B testing, root cause). |
| Predictive | Prescriptive | Both look forward. Predictive = what might happen (a probability). Prescriptive = what to do (the best choice). |
| Popularity of predictive | Popularity of prescriptive | Predictive: "a small but growing group". Prescriptive: "Not yet widespread". |
| Design phase | Choice phase | Design builds the model and finds alternatives. Choice selects one solution and tests it. |
| Intelligence phase (Simon) | Business Intelligence / artificial intelligence | In Simon's process, Intelligence only means finding and defining the problem. |
| Data management subsystem | Model management subsystem | Data: DSS database, DBMS, data directory, query facility. Model: model base, MBMS, modeling language, model directory, execution. |
| 4 DSS components | 4 BI components | DSS: data, model, user interface, knowledge-based. BI: DW, business analytics, BPM, user interface. Only the user interface is in both. |
| Data mart (DM) | Enterprise data warehouse (EDW) | DM = "a subset", "a single subject area". EDW = "large-scale", "across the enterprise". |
| ODS | DW | ODS contents are "updated throughout the course of business operations". A DW is "nonvolatile". |
| MIS | EIS | MIS = "a variety of reports". EIS = for executives, "graphical dashboards" tracking KPIs. |
| Strategic planning | Management control | Strategic = "long-range goals/policies". Management = "efficient use of resources". Operational = "execution of specific tasks". |
| Structured | Unstructured | Structured = "Routine/repetitive", standard methods exist. Unstructured = "no clear, standard solution methods". A DSS supports semistructured or unstructured problems. |
| Life cycle (6 steps) | Pipeline (5 boxes) | Life cycle starts with the problem ("Discovery") and ends with "Operationalizing". Pipeline starts with data ("Collect") and ends with "Presentation". |
| Analytics | AI | Analytics = computation on historical data. AI = knowledge and intelligence, mimics people. |
| Simon's 4 phases | AI support 4 steps (slide 65) | Same idea, different names: Problem Identification, Generating/Finding Alternative Solutions, Selecting a Solution, Implementing the Solutions. |

## Memory hooks

- **Simon's phases — "I Do Choose It":** Intelligence, Design, Choice, Implementation.
- **DSS components — "Data Models Use Knowledge":** Data management, Model management, User interface, Knowledge-based management.
- **Data management elements — "three D's and a Q":** DSS Database, DBMS, Data directory, Query facility.
- **Model management elements — "five M's":** Model base, MBMS, Modeling language, Model directory, Model execution (integration, command processor).
- **Evolution — "Reports, then Decisions, then Dashboards":** MIS, DSS, EIS.
- **DSS framework — "3 by 3":** Structured / Semi structured / Unstructured by Operational / Management / Strategic.
- **BI chain — "D-I-D-A":** Data → Information → Decisions → Actions.
- **BI components — "Store, Analyse, Monitor, Show":** DW, Business analytics, BPM, User interface.
- **DW definition — "SIT-N":** Subject-oriented, Integrated, Time-variant, Nonvolatile.
- **OLTP / OLAP:** T for Today's Transactions; A for Analysis of the Archive.
- **Six BI trends — "Big Customers Move Predictably to Cloud Securely":** Big Data, Customer experience, Mobile and newer interfaces, Predictive and prescriptive analytics / ML / AI, Cloud, Security and privacy.
- **Life cycle — "Do Data, Plan, Build, Communicate, Operate":** Discovery, Data Preparation, Model Planning, Build & Execute Model, Communicate results, Operationalizing.
- **Pipeline — "C-T-S-A-P":** Collect, Transform, Store, Analyze, Presentation.
- **Four types of analytics — think of a doctor:** describe the symptoms, diagnose the cause, predict what will happen, prescribe the medicine.
- **Popularity ladder:** almost all → many → small but growing → not yet widespread.
- **Value ladder:** Hindsight → Insight → Foresight.
- **Intelligent agent — "small, watches, acts alone, learns".**
- **Humana numbers:** 65+, $34 billion (2013), 3.2 million members, 20,000 identified.
- **HKTVmall numbers:** sales increment "well over 100 %" in promotions; conversion up "15 per cent, or HKD100 per basket".

## Test yourself

**Multiple choice**

1. Which of the following is NOT one of the four subsystems of a DSS on the slides?
   A) Model management subsystem
   B) Knowledge-based management subsystem
   C) Business process management subsystem
   D) User interface subsystem

2. In Simon's process, in which phase does the decision maker examine reality and identify and define the problem?
   A) Design
   B) Intelligence
   C) Choice
   D) Implementation

3. Which system was "designed as graphical dashboards that allow decision makers to keep track of the key performance indicators"?
   A) MIS
   B) OLTP
   C) EIS
   D) ODS

4. A DW is "a subject-oriented, integrated, ______, nonvolatile collection of data". The missing word is:
   A) real-time
   B) time-variant
   C) transaction-oriented
   D) normalized

5. Which statement about OLTP and OLAP is correct?
   A) OLTP is inefficient for transaction processing but efficient for ad hoc analysis.
   B) OLAP handles a company's routine ongoing business with immediate responses.
   C) OLTP handles routine ongoing business with immediate responses; OLAP analyses data stored in the DW.
   D) OLTP and OLAP are two names for the same operational database system.

6. Which data source "provides a form of customer information file whose contents are updated throughout the course of business operations"?
   A) Data mart
   B) Enterprise data warehouse
   C) Operational data store
   D) Model base

7. Which type of analytics is "Used by a small but growing group of organizations"?
   A) Descriptive
   B) Diagnostic
   C) Predictive
   D) Prescriptive

8. Which set of tools is listed for prescriptive analytics?
   A) Mean, median, histogram
   B) A/B testing, factor analysis
   C) Decision tree, neural networks, forecasting tools
   D) Fuzzy logic, expert system, optimization, generative AI

9. In the data analytics life cycle, "Identify useful data, and ETL (extract, transform, load)" describes:
   A) Discovery
   B) Data Preparation
   C) Model Planning
   D) Operationalizing

10. Which is NOT one of the six key BI trends on the slides?
    A) Big Data
    B) Migration to cloud
    C) Focus on operational efficiency as opposed to customer experience
    D) Much greater focus on security and privacy protection

**True or false**

1. In Simon's process, the model is constructed and validated in the Choice phase, and a solution is selected and tested in the Design phase.
2. OLAP systems handle a company's routine ongoing business and respond immediately to user requests, while OLTP systems analyse the data stored in the data warehouse.
3. Diagnostic analytics answers "What happened?" and is used by almost all organizations.
4. According to the slides, predictive analytics is "Not yet widespread", while prescriptive analytics is "Used by a small but growing group of organizations".
5. The model management subsystem of a DSS is composed of the DSS database, the database management system, the data directory and the query facility.
6. A data mart is a subset of a DW and typically consists of a single subject area.
7. The emphasis in AI is on knowledge and intelligence as major tools for solving problems, rather than on computation, which analytics relies on.
8. In the data analytics life cycle, Data Preparation comes before Model Planning, and the course focuses more on Model Planning and Build & Execute Model.

**Short questions**

1. (4 marks) Name the four major components of BI and state what each one is for.
2. (3 marks) In the Humana case, state (a) the business problem, (b) the data used, and (c) the type of analytics and its result.
3. (4 marks) What is an intelligent agent? Give its definition, one ability, and one example from the slides.

### Answers

**Multiple choice**

1. **C.** BPM is one of the four BI components (slide 23), not a DSS subsystem (slide 14). B looks strange but it is the real fourth DSS subsystem.
2. **B.** Intelligence = examine reality, identify and define the problem. A is tempting, but Design starts after the problem statement and builds the model.
3. **C.** EIS = dashboards for executives tracking KPIs. A is tempting, but MIS is only "a variety of reports".
4. **B.** The four words are subject-oriented, integrated, time-variant, nonvolatile. D is tempting because "Normalized" appears in the OLTP picture, but it is not in the DW definition.
5. **C.** This is slide 27. A and B swap the two systems; D is wrong because the DW is "a distinct system".
6. **C.** That is the ODS wording. A is tempting, but a data mart is "a subset of a DW" for "a single subject area".
7. **C.** Predictive. D is tempting, but prescriptive is "Not yet widespread".
8. **D.** Slide 41. C is the predictive list, B the diagnostic list, A the descriptive list.
9. **B.** Step 2, Data Preparation. A is tempting, but Discovery is "Know what problem you are solving".
10. **C.** The real trend is the reverse: "Focus on customer experience as opposed to just operational efficiency."

**True or false**

1. **False.** The two phases are swapped. Design builds and validates the model; Choice selects and tests the solution.
2. **False.** The two names are swapped. OLTP handles routine business with immediate response; OLAP analyses DW data.
3. **False.** That describes descriptive analytics. Diagnostic answers "Where and/or Why exactly?" and is "Used by many organizations".
4. **False.** Swapped. Predictive = "a small but growing group of organizations"; prescriptive = "Not yet widespread".
5. **False.** Those four are the elements of the data management subsystem. Model management has the model base, MBMS, modeling language, model directory, and model execution, integration and command processor.
6. **True.** This is the slide 25 wording. Do not confuse it with the EDW, which is "large-scale" and "across the enterprise".
7. **True.** Slide 67. Analytics relies on computation on historical data; AI relies on knowledge and intelligence.
8. **True.** Order: Discovery, Data Preparation, Model Planning, Build & Execute Model, Communicate results, Operationalizing. The slide says "We focus more on 3 and 4 in this course".

**Short questions**

1. Four BI components (slide 23):
   1. DW "with its source data" — stores the data. (1 mark)
   2. Business analytics — "a collection of tools for manipulating, mining, and analyzing the data in the DW". (1 mark)
   3. Business Process Management (BPM) — "for monitoring & analyzing performance". (1 mark)
   4. User interface — for example a dashboard (also browser or portal). (1 mark)
   Do not write the four DSS subsystems here; that is the tempting wrong answer.

2. Humana (slides 43–44):
   1. Problem: accidental falls are a major health risk for adults aged 65+; cost about $34 billion in 2013; Humana has 3.2 million members, mostly seniors. (1 mark)
   2. Data: "Administrative medical and pharmacy claims, clinical data, temporal clinical patterns, and other data". (1 mark)
   3. Type and result: predictive analytics (the "Falls PM (Predictive Models)"); it identified 20,000 high-risk consumers, who wear a device that detects falls and alerts a service. (1 mark)
   Do not call it descriptive: the model looks forward to who is likely to fall.

3. Intelligent agent (slides 62–63):
   1. It is "a small computer software program". (1 mark)
   2. It "observes and acts upon changes in its environment by running specific tasks autonomously". (1 mark)
   3. Ability: "IAs have the ability to learn by using their knowledge". (1 mark)
   4. Example: a virus detection program that scans incoming data and removes viruses automatically while learning new virus types; or Allstate Business Insurance's agent that reduces call centre traffic. (1 mark)
   Do not describe a human insurance agent: an IA is software.
