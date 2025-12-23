# Eye-health Product Market & Consumer Awareness Analysis

**Market Structure, Advertising Claims, and Evidence Gap**

## Project Overview

This project investigates the **market structure, demand characteristics, and consumer awareness** of eye-health nutrition products in China.
Motivated by the widespread use of exaggerated and weakly supported advertising claims in the eye-health supplement market, the project aims to provide **data-driven evidence** for why an automated advertising claim verification agent is necessary.

Before building such an agent, this project conducts **systematic market analysis, social media advertising analysis, and consumer awareness analysis** to establish the problem context from both the **supply side** and the **demand side**.

------

## Data Sources

### Dataset A: E-commerce Market Data (Taobao)

- **Platform:** Taobao
- **Data collection:** Web scraping
- **Sample size:** 300 products
- **Keywords used (Top 50 per keyword):**
  - Lutein
  - Lutein + Zeaxanthin
  - Blueberry (eye-health related)
  - Astaxanthin
  - DHA
  - General eye-health supplements

**Fields include:**

- Product title
- Category (keyword-based)
- Sales volume
- Number of reviews
- Add-to-cart count
- Repeat customers

**Purpose:**
To characterize the **overall supply structure**, **product concentration**, and **market demand intensity** of eye-health nutrition products.

------

### Dataset B: Social Media Advertising Data (Xiaohongshu)

**Purpose**
To demonstrate that exaggerated or misleading eye-health claims are **widespread and systematic** in real consumer-facing marketing language, rather than isolated cases.

**Data Format**

- Structured CSV files
- Each record corresponds to one advertising claim extracted from social media posts

**Methodological Choice**
Advertising language on social media is highly unstructured and context-dependent. Fully automated crawling tends to produce large volumes of noisy text with limited analytical value.
Therefore, this dataset adopts a **manual sampling + rule-based annotation** strategy, prioritizing **representativeness, interpretability, and linguistic validity** over scale.

**Key Insight**
Unlike e-commerce platforms, Xiaohongshu is **scenario-oriented rather than product-oriented**.
Content creators and consumers rarely use ingredient-based terminology; instead, they frame products around:

- **Symptoms** (e.g., eye fatigue, blurred vision)
- **Life situations** (e.g., prolonged screen use, late-night studying)
- **Identity groups** (e.g., children, students, office workers)

To realistically capture the marketing language consumers are exposed to, **scenario-based keywords** are required instead of reusing ingredient-based e-commerce keywords.

**Scenario-based Keyword Categories**

- **Core anxiety-driven scenarios**
  - Child myopia prevention
  - Vision stabilization
  - Eye fatigue from prolonged screen use
  - Late-night eye strain
- **High-risk efficacy claims**
  - Restore vision
  - Improve eyesight
  - Prevent vision decline
  - Relieve dry eyes
- **Ingredient + scenario combinations**
  - Lutein + blurred vision
  - Anthocyanins + eye fatigue
  - Astaxanthin + eye protection

Using this strategy, **42 representative exaggerated advertising claims** were collected and annotated for both qualitative and quantitative analysis.

**Purpose in the project:**
This dataset provides **direct linguistic evidence** that misleading or overconfident claims are embedded in everyday marketing narratives encountered by consumers.

------

### Dataset C: Consumer Awareness Survey

- **Format:** Questionnaire (CSV)
- **Focus areas:**
  - Information sources used when evaluating eye-health products
  - Skepticism toward advertising claims
  - Willingness to consult scientific evidence
  - Demand for automated claim verification tools
  - Demographic information (age, gender)

**Purpose:**
To analyze **consumer cognition, information-seeking behavior, and reliance on external verification mechanisms**.

------

## Analysis Structure

### 1. Market Coverage & Target Population Analysis (Dataset A)

- Extraction of target population cues from product titles
- Normalization into age groups and audience types

**Visualization:**

- Word cloud of audience-related terms
- Lifecycle coverage across age groups
- Single-age vs. multi-age targeting patterns

**Key insight:**
Eye-health demand is a **full-lifecycle, multi-population rigid demand**, with a noticeable emphasis on adults but no exclusive age restriction.

------

### 2. Supply Structure Analysis by Ingredient Category (Dataset A)

- Keyword-based categorization of products
- Horizontal bar chart showing product concentration across ingredient categories

**Key insight:**
The market is **not driven by a single “core ingredient”**, but instead exhibits **parallel saturation across multiple ingredient tracks**, indicating a mature and highly competitive market.

------

### 3. Market Demand Analysis Based on Sales Distribution (Dataset A)

- Log-scale boxplot of sales volumes
- Log–log scatter plot of sales volume vs. review count

**Key insight:**
Sales volumes are extremely uneven, with top products showing very high cumulative sales.
The strong positive relationship between sales and reviews indicates **long-term, repeated consumption behavior**, rather than one-off impulse purchases.

------

### 4. Exaggerated Advertising Claims Analysis (Dataset B)

- Classification of advertising claims by claim type (symptom relief, vision improvement, prevention, etc.)
- Frequency analysis of high-risk claim categories
- Representative examples of exaggerated claims

**Key insight:**
Misleading or weakly supported claims are **not exceptional**, but follow recurring linguistic patterns across different scenarios and target groups.
This demonstrates that exaggerated advertising is a **structural characteristic of the market**, rather than the result of individual sellers.

------

### 5. Consumer Information Sources Analysis (Dataset C)

- Binary encoding of information sources from multi-choice survey responses
- Lollipop chart showing the percentage of respondents using each source

**Key insight:**
Consumers rely predominantly on **social media platforms and e-commerce reviews**, while **direct consultation of scientific evidence remains marginal**, revealing a substantial information asymmetry.

------

### 6. Advertising Skepticism and Demand for Verification Tools (Dataset C)

- Mapping of advertising skepticism levels (Low / Medium / High)
- Cross-tabulation with demand for verification tools
- Stacked bar visualization

**Key insight:**
Higher skepticism toward advertising does **not** lead to independent evidence-seeking behavior.
Instead, it significantly **increases reliance on external verification tools**, reinforcing the necessity of an automated claim verification agent.

------

## File Structure

```
├── dataset/
│   ├── taobao_eye_supplement_products.csv
│   ├── xiaohongshu_claims_labeled.csv
│   └── eye_health_awareness_survey.csv
│
├── code/
│   ├── survey_analysis_eye_products_code/survey_analysis_eye_products_code.ipynb
│   └── taobao_scraper_code/taobao_scraper.ipynb
│
├── figures/
├── requirements.txt
└── README.md
```

### Prepare the Environment
```bash
conda create -n eye_health python=3.10
conda activate eye_health
pip install -r requirements.txt
```

### Data Collection Scripts (Optional)

Scripts for automated data collection (taobao_scraper.ipynb`) are provided
for transparency only and are **not required** to run the analysis notebook.

------

## Key Contribution

This project provides **empirical and multi-source justification** for building an eye-health advertising claim verification agent by demonstrating that:

1. The eye-health supplement market is **large-scale, saturated, and competitive**
2. Exaggerated advertising claims are **systemic in real consumer-facing language**
3. Consumers rely heavily on **non-evidence-based information channels**
4. Skepticism increases **demand for external verification**, not independent fact-checking

------

