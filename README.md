# Fit.ly Subscriber Churn & Support Resolution Analysis


---

## Executive Summary

Fit.ly, a subscription-based fitness platform, currently faces an overall **28.50% account churn rate** across its 400 total subscriber accounts. This analysis investigates customer support latency and subscription tier friction to identify the core drivers of attrition and establish an operational framework to protect recurring revenue.

### Key Findings
1. **Support Latency Drives Attrition:** Active subscribers experience a median support resolution time of **6.50 hours**, whereas churned subscribers face a median wait time of **18.50 hours** (with a severe bottleneck tail extending past 30 hours).
2. **Free Tier Vulnerability:** Subscribers on the Free plan churn at an alarming **40.95%** (12.45 percentage points above the 28.50% baseline), compared to **22.35%** for Pro tier users.
3. **High Volume Base:** Basic and Free tiers account for **55.75%** of all subscriber accounts, making onboarding and support efficiency in these plans critical to platform retention.

---

## Datasets Evaluated

The analysis merges three key datasets covering 400 user accounts and 918 support tickets:

| Dataset | Records | Description | Key Fields |
| :--- | :--- | :--- | :--- |
| `account_info` | 400 rows | Subscriber demographics & plan details | `account_id`, `plan_tier`, `churn` |
| `customer_support` | 918 rows | Support ticket history & response times | `ticket_id`, `resolution_time_hours`, `category` |
| `user_activity` | 445 rows | Platform engagement metrics | `account_id`, `workout_sessions`, `logins` |

---

## Visual Analysis & Baseline Metrics

### Baseline Metrics Overview
* **Overall Account Churn Rate:** `28.50%` (114 / 400 Accounts)
* **Overall Support Resolution Time (Median):** `9.04 Hours` (Mean: `10.42 Hours`)

### Tier Performance vs. Baseline (28.50%)

| Subscription Plan | Total Accounts | Churned Accounts | Churn Rate (%) | Variance vs. Baseline | Risk Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Free** | 105 | 43 | **40.95%** | **+12.45%** | High Risk |
| **Enterprise** | 92 | 24 | **26.09%** | **-2.41%** | Stable |
| **Basic** | 118 | 28 | **23.73%** | **-4.77%** | Stable |
| **Pro** | 85 | 19 | **22.35%** | **-6.15%** | Lowest Risk |

---

## Proposed Business KPI & SLA Framework

To align Support, Customer Success, and Product teams on retention, I define the primary operational KPI as:

> **Primary KPI:** Average Support Ticket Resolution Time (Hours)

### Target Benchmarks
* **Target SLA Goal:** Resolve 90%+ of support tickets in **< 6.00 Hours** (aligning with active user baseline of 6.50 hours).
* **Automated Risk Threshold:** Auto-flag open tickets exceeding **> 12.00 Hours** in the CRM for proactive Customer Success intervention.

---

## Strategic Recommendations

1. **Priority SLA Support Queue Routing:** Re-engineer support ticket queue triage to route critical billing and technical inquiries immediately, targeting resolutions under 6 hours.
2. **Proactive CRM Retention Workflows:** Trigger automated CRM alerts for Customer Success teams whenever open tickets cross 12 hours, enabling proactive check-ins or trial extensions before cancellation occurs.
3. **Self-Service Onboarding for Free Tier:** Deploy interactive in-app tutorials, guided setup flows, and expanded FAQs tailored for Free plan users to decrease support ticket volume and curb initial trial drop-off.

---

## Repository Deliverables

* `notebooks/fitly_churn_analysis.ipynb` — Full data cleaning, EDA and visualization.
* `presentation/fitly_churn_presentation.pdf` — PDF export of the presentation slides.
