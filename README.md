# Loan Risk & Credit Portfolio Analysis - LendingClub Dataset

## Project Overview

This project analyses the historical LendingClub loan portfolio to understand three connected areas of credit risk:

* **Borrower risk** — which borrower and loan characteristics are associated with higher default rates?
* **Portfolio exposure** — how much loan value is associated with those higher-risk segments?
* **Loan pricing** — how does interest rate vary across borrower risk segments and other characteristics?

The analysis focuses on historical loan outcomes and uses **Charged Off** as the default outcome.

The objective is not to build a predictive model, but to demonstrate how credit-risk data can be investigated, segmented, and translated into portfolio-level business insights.

---

## Business Questions

The analysis addresses the following questions:

1. Which borrower characteristics show the strongest relationship with historical default?
2. How does default behaviour vary across credit grades?
3. Does borrower debt burden, measured by DTI, relate to default rates?
4. Does loan amount consistently relate to default risk?
5. Which loan-purpose segments show higher historical default rates?
6. How is charged-off loan exposure distributed across credit grades?
7. How do interest rates vary across borrower risk grades?
8. Do DTI, income, verification status, home ownership, or loan purpose provide additional pricing context?
9. How do risk and financial exposure differ when evaluating the portfolio?

---

## Dataset

The project uses the **LendingClub loan dataset**.

### Dataset progression

| Stage                           |  Loans | Columns |
| ------------------------------- | -----: | ------: |
| Original dataset                | 39,717 |     111 |
| Validated dataset               | 39,715 |      49 |
| Loans with known final outcomes | 38,575 |      49 |

The validated dataset contains fully populated values across the 49 retained analytical columns.

For default analysis, loans with a **Current** status were excluded because their final repayment outcome was not yet known.

### Outcome definition

* **Fully Paid** → successful final repayment outcome
* **Charged Off** → default outcome used for historical charge-off analysis
* **Current** → excluded from final-outcome default calculations

---

## Analytical Approach

The analysis follows a business-focused workflow:

1. **Business understanding**
2. **Data exploration**
3. **Data cleaning and validation**
4. **Outcome definition**
5. **Borrower and loan segmentation**
6. **Default-rate analysis**
7. **Portfolio exposure analysis**
8. **Interest-rate analysis**
9. **Combined segment analysis**
10. **Business interpretation**

The analysis primarily uses descriptive statistics, segmentation, grouped comparisons, and portfolio-level measures.

---

# Key Findings

## 1. Credit Grade Provides the Strongest Risk Segmentation

Credit grade showed the clearest and most consistent relationship with historical default rates.

| Grade | Default Rate | Avg. Interest Rate |
| ----- | -----------: | -----------------: |
| A     |        5.99% |              7.33% |
| B     |       12.20% |             11.01% |
| C     |       17.19% |             13.53% |
| D     |       21.99% |             15.66% |
| E     |       26.85% |             17.63% |
| F     |       32.68% |             19.64% |
| G     |       33.78% |             21.31% |

The historical charge-off rate increases substantially from Grade A to Grade G.

At the same time, average interest rates also increase across the grades.

This means that **lower credit grades were associated with both higher historical default rates and higher average interest rates**.

> Grade is therefore the strongest risk-segmentation variable observed in this descriptive analysis. This does not establish that grade itself causes default or determines pricing.

---

## 2. Overall Historical Default Rate

Among the 38,575 loans with known final outcomes:

* **5,626 loans were Charged Off**
* **32,949 loans were Fully Paid**
* Historical charge-off rate: **14.58%**

This means approximately **1 in 7 loans** in the analysed population were charged off.

This is a historical portfolio measure rather than a prediction of future default probability.

---

## 3. DTI Shows a Secondary Relationship with Default

Debt-to-Income (DTI) was divided into four approximately equal-sized groups.

| DTI Group   | Default Rate |
| ----------- | -----------: |
| Low         |       12.34% |
| Low to Mid  |       13.83% |
| Mid to High |       15.39% |
| Above High  |       16.79% |

The default rate increased from **12.34% to 16.79%** across the DTI groups.

This suggests that higher borrower debt burden was associated with higher historical default rates.

However, the difference was much smaller than the separation observed across credit grades.

**Conclusion:** DTI provides useful supporting risk information, but it was a weaker separator than credit grade in this analysis.

---

## 4. Loan Amount Is More Directly Relevant to Exposure Than Default Risk

The average loan amount was:

* **Charged Off:** $12,105.65
* **Fully Paid:** $10,866.76

Charged-off loans therefore had a higher average loan amount.

However, loan size did **not** show a consistently increasing default rate across all loan-amount groups.

| Loan Amount Group | Default Rate |
| ----------------- | -----------: |
| Low               |       13.88% |
| Low to Mid        |       12.69% |
| Mid to High       |       13.57% |
| High              |       18.75% |

The highest loan-amount group had the highest default rate, but the relationship was not monotonic.

Therefore:

> A larger loan should not automatically be interpreted as higher credit risk.

Loan amount is particularly important when assessing **financial exposure** because a default on a larger loan represents a larger amount of principal associated with that default.

---

## 5. Portfolio Exposure and Default Risk Are Different Dimensions

The total loan amount associated with charged-off loans was:

**$68.11 million**

Across the full analysed portfolio, charged-off loans represented:

* **14.58% of loans by count**
* **15.98% of total loan amount**

The difference shows why both **risk probability** and **exposure magnitude** need to be considered.

A segment can have a high default rate but relatively small portfolio volume, while another segment can have a lower default rate but much greater total exposure.

> The $68.11 million figure represents the original loan amount associated with charged-off loans. It should not be interpreted as the lender's actual financial loss because borrowers may have made repayments before charge-off.

---

## 6. Grade B Contains the Largest Total Charged-Off Exposure

Charged-off exposure by grade:

| Grade | Charged-Off Loans | Charged-Off Loan Amount |
| ----- | ----------------: | ----------------------: |
| A     |               602 |                  $4.70M |
| B     |             1,424 |                 $15.54M |
| C     |             1,347 |                 $14.88M |
| D     |             1,118 |                 $13.64M |
| E     |               715 |                 $11.33M |
| F     |               319 |                  $6.15M |
| G     |               101 |                  $1.87M |

Grade G has the highest default rate, but it does **not** have the largest charged-off exposure.

Grade B produced the largest charged-off exposure because it combined:

* a large number of loans,
* a substantial number of charged-off loans, and
* meaningful average loan amounts.

This demonstrates an important portfolio-risk principle:

> **Highest default rate does not necessarily mean highest financial exposure.**

Portfolio volume must be considered alongside risk rate.

---

## 7. Loan Purpose Provides Additional Risk Segmentation

Historical default rates varied by loan purpose.

The highest observed rate was for **small-business loans**:

* Total loans: **1,753**
* Charged Off: **474**
* Default rate: **27.04%**

Small-business loans also had the highest average interest rate among the analysed purposes at **12.90%**.

Loan purpose therefore provides additional context for both historical risk and pricing.

However, unlike credit grade, loan purpose does not form a systematic ordered risk scale.

---

## 8. Income Shows an Association with Repayment Outcomes

Reported annual income differed between repayment outcomes.

| Outcome     | Mean Annual Income | Median Annual Income |
| ----------- | -----------------: | -------------------: |
| Charged Off |            $62,421 |              $53,000 |
| Fully Paid  |            $69,861 |              $60,000 |

Borrowers whose loans were charged off had lower reported average and median income.

This provides evidence of an association between reported income and repayment outcomes, but income alone does not explain default behaviour.

---

## 9. Verification Status Shows Differences, but the Relationship Varies by Grade

Overall historical default rates were:

| Verification Status | Default Rate |
| ------------------- | -----------: |
| Not Verified        |       12.83% |
| Source Verified     |       14.82% |
| Verified            |       16.80% |

At the overall portfolio level, the rates differ.

However, when verification status was analysed within individual credit grades, the pattern was not consistent across every grade.

Credit grade continued to show a much stronger and more consistent relationship with historical default.

Therefore, verification status should be treated as **additional context rather than the primary risk-segmentation variable** in this analysis.

---

# Interest Rate & Loan Pricing

## Grade and Interest Rate

Average interest rate increased substantially across credit grades:

**Grade A → 7.33%**

**Grade G → 21.31%**

This is a **13.98 percentage-point difference**.

The same grade progression also showed substantially higher historical charge-off rates.

This provides a clear descriptive relationship between **credit grade, historical risk, and observed loan pricing**.

---

## DTI and Interest Rate

Average interest rates across DTI groups were:

| DTI Group   | Avg. Interest Rate |
| ----------- | -----------------: |
| Low         |             11.24% |
| Low to Mid  |             11.83% |
| Mid to High |             12.29% |
| Above High  |             12.37% |

The difference between the lowest and highest groups was only **1.13 percentage points**.

Compared with the much larger difference across credit grades, DTI showed a relatively weak pricing relationship.

---

## Grade + DTI

When Grade and DTI were analysed together, Grade remained the dominant segmentation variable.

For example:

* Grade A + Above High DTI → **7.65%** default rate
* Grade G + Above High DTI → **36.26%** default rate

DTI showed additional variation within several grades, but the pattern was not consistently monotonic across every grade.

This suggests that:

> Credit grade provided the strongest segmentation, while DTI supplied additional borrower-level risk context.

---

## Grade + Loan Amount

Combining Grade and loan amount produced a similar result.

Credit grade continued to separate historical default rates strongly, while loan amount showed a less consistent relationship within individual grades.

This reinforces the distinction between:

**Risk → How likely is the loan to default?**

and

**Exposure → How much money is associated with that risk?**

---

# Credit Risk Framework

The project uses several standard credit-risk concepts as an analytical framework.

### Probability of Default — PD

Historical **Charged Off rates** are used as a descriptive proxy for comparing default behaviour across portfolio segments.

### Exposure at Default — EAD

Loan amount is used to understand the amount of lending associated with different risk segments.

The project does **not** calculate contractual outstanding balances at the point of default, so this should not be interpreted as a formal EAD model.

### Loss Given Default — LGD

Charge-off status provides information about default outcomes, but the project does not contain sufficient recovery information to calculate a formal LGD measure.

Therefore, the analysis focuses primarily on:

**Historical default behaviour + loan exposure + pricing**

rather than a complete PD/LGD/EAD modelling framework.

---

# Portfolio Risk Perspective

The analysis demonstrates why credit-risk analysis should not rely on a single metric.

A useful portfolio assessment combines:

### 1. Risk

How frequently does a segment default?

Example:

**Grade G → 33.78% historical default rate**

### 2. Exposure

How much lending is associated with the segment?

Example:

**Grade B → $127.66M total loan amount**

### 3. Pricing

How does observed interest rate vary with risk segmentation?

Example:

**Grade A → 7.33% average interest**

**Grade G → 21.31% average interest**

### 4. Concentration

Where is the portfolio's charged-off exposure concentrated?

Example:

**Grade B → $15.54M charged-off loan amount**

These dimensions provide a more complete view than analysing default rates alone.

---

# Key Business Takeaways

1. **Credit grade provided the strongest and most consistent historical risk segmentation.**
2. **Lower credit grades had substantially higher historical charge-off rates.**
3. **Lower credit grades also had substantially higher average interest rates.**
4. **DTI showed a secondary relationship with default, but its separation was weaker than Grade.**
5. **Loan amount did not show a consistent relationship with default risk, but it was important for measuring exposure.**
6. **Grade B had the largest total charged-off exposure despite Grade G having the highest default rate.**
7. **Small-business loans showed the highest historical default rate among loan purposes.**
8. **Reported income was lower on average among charged-off borrowers.**
9. **Verification status showed differences in default rates, but those differences varied across credit grades.**
10. **Risk rate and financial exposure are separate dimensions and should be analysed together.**

---

# Limitations

This project is a **descriptive historical analysis**, not a production credit-risk model.

Therefore:

* Associations should not be interpreted as causation.
* No machine-learning default prediction model was built.
* No formal PD model was developed.
* Formal EAD was not calculated from outstanding balances at default.
* Formal LGD was not calculated because recovery data was not available.
* Current loans were excluded from final-outcome analysis because their eventual outcomes were unknown.
* Small portfolio segments can produce volatile rates because of limited observations.
* Observed interest-rate differences show associations in the dataset and do not establish the exact underwriting or pricing decision process used by LendingClub.

---

# Tools & Technologies

* **Python**
* **Pandas**
* **Jupyter Notebook**
* **SQL concepts**
* **Power BI**
* **GitHub**
* **Microsoft Excel**

---

# Project Structure

```text
Loan-Risk-Credit-Portfolio-Analysis---LendingClub-Dataset/
│
├── Lending_Club.ipynb
├── lending_club_validated.csv
├── Loan Analysis.pbix
├── README.md
└── ...
```

---

# Dashboard

The project also includes a Power BI dashboard designed to communicate portfolio risk, default behaviour, exposure, and pricing patterns.

### Dashboard Preview

<img width="1169" height="657" alt="LendingClub dashboard — portfolio overview" src="https://github.com/user-attachments/assets/20dde0c6-1f0a-47d0-af5c-66971b6ec431" />

<img width="1164" height="657" alt="LendingClub dashboard — risk analysis" src="https://github.com/user-attachments/assets/3fb23a92-6a60-47a8-887a-c5f0b044c3a5" />

<img width="1164" height="656" alt="LendingClub dashboard — exposure and pricing analysis" src="https://github.com/user-attachments/assets/7290a03b-724d-44bb-8084-4f7801faaf90" />

---

# What This Project Demonstrates

This project demonstrates practical ability in:

* Exploratory data analysis
* Data cleaning and validation
* Credit-risk segmentation
* Default-rate analysis
* Portfolio exposure analysis
* Risk-versus-exposure reasoning
* Interest-rate and pricing analysis
* Business-focused interpretation
* Data-driven communication
* Power BI dashboard development

The central analytical approach is:

**Borrower & loan characteristics → risk segmentation → default behaviour → financial exposure**

while also examining:

**Borrower & loan characteristics → observed loan pricing**

---

## Author

**Asif Farook Khaja Moideen**

MSc Data Science | B.Tech Information Technology

Interested in **Data Analytics, Credit Risk, Financial Data, Business Intelligence, and Data Science**.
