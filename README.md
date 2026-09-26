# Analysis of Student Willingness-to-Pay for Premium Ed-Tech Tools: A Predictive Modelling Approach

## Individual Business Analytics Case Study

**Student:** Mithresh M  
**Register Number:** CB.SC.U4CSE23039  
**Programme:** B.Tech Computer Science and Engineering  
**Section:** CSE-A  
**University:** Amrita Vishwa Vidyapeetham, Coimbatore Campus  
**Academic Year:** 2026–2027  

---

## 1. Project Overview

Ed-Tech platforms commonly use freemium business models in which basic functionality is available without payment while advanced features are offered through premium subscriptions.

This case study analyses publicly available Google Play app reviews to identify observable signals associated with premium engagement, including references to subscriptions, purchasing, pricing, free access, cancellation, and feature limitations.

The study uses review-derived premium engagement as a proxy. It does not directly observe actual willingness-to-pay, subscription transactions, or confirmed purchases.

---

## 2. Problem Statement

Ed-tech platforms attract millions of users through freemium models, but only a small percentage convert to premium subscriptions, resulting in inefficient marketing efforts and lost revenue opportunities. Businesses need a data-driven approach to identify users with genuine purchase intent rather than relying solely on basic engagement metrics.

This study uses publicly available app-review text and platform-level review metadata to identify observable signals associated with premium engagement, while recognising that verified behavioural, attitudinal, demographic, and transaction-level information is unavailable.

---

## 3. Objectives

1. To collect and analyse a large publicly available dataset of Ed-Tech application reviews.

2. To identify review-based signals associated with premium features, pricing, subscriptions, free access, cancellation, and feature limitations.

3. To develop and evaluate predictive models for the review-derived premium engagement score and derive practical business insights for premium-feature and subscription strategy.

---

## 4. Dataset

### Applications

The dataset contains public Google Play reviews from:

- Duolingo
- Photomath
- Brainly

### Dataset Size

| Stage | Records |
|---|---:|
| Reviews collected | 10,800 |
| Duplicate records removed | 0 duplicate review IDs |
| Final analytical dataset | **10,800** |

Each application contributes **3,600 reviews**.

### Application Distribution

| Application | Reviews |
|---|---:|
| Duolingo | 3,600 |
| Photomath | 3,600 |
| Brainly | 3,600 |
| **Total** | **10,800** |

### Main Attributes

The dataset contains fields including:

- `app_id`
- `app_name`
- `score`
- `text`
- `review_id`
- `country`
- `app_version`
- `thumbs_up`
- `reviewed_at`
- `language`

Reviewer-identifying fields were not retained for the analytical dataset.

---

## 5. Data Source and Collection

The review records were collected from publicly available Google Play app-review pages using the **Apify Google Play Store Reviews Scraper**.

The collection process involved:

1. Selecting three Ed-Tech applications: Duolingo, Photomath, and Brainly.
2. Collecting public Google Play reviews for each application.
3. Collecting 3,600 reviews per application.
4. Using English-language reviews from the US storefront.
5. Requesting reviews in newest-first order.
6. Combining the collected records.
7. Checking review identifiers for duplicates.
8. Preparing the final dataset for analysis.

The final analytical dataset contains **10,800 public app reviews**.

### Data Source

**Source:** Google Play public app-review pages  
**Collection tool:** Apify Google Play Store Reviews Scraper  
**Collection date:** September 2026

---

## 6. Data Privacy and Limitations

The dataset represents public app-review activity. It does not provide:

- Verified student identities
- Demographic characteristics
- Subscription transaction records
- Actual payment information
- Confirmed willingness-to-pay values
- Individual app usage history
- Verified conversion outcomes

Therefore, the review-derived premium engagement score is treated as a **proxy** rather than actual willingness-to-pay or confirmed subscription conversion.

---

## 7. Data Preparation

The following preprocessing steps were performed:

- Duplicate review identifiers were checked.
- Missing values were inspected.
- Review text was standardised for keyword-based feature extraction.
- Review character length was calculated.
- Word count was calculated.
- Exclamation and question mark counts were calculated.
- Premium-related keyword indicators were generated.
- A premium engagement score was constructed.
- Engagement categories were created from the resulting score.

### Premium-Related Signals

Six categories were used:

1. Premium and subscription references
2. Purchase and payment references
3. Price and affordability references
4. Free access and advertisements
5. Cancellation and refund references
6. Limitations and locked-feature references

---

## 8. Premium Engagement Score

The premium engagement score is calculated as the sum of six binary indicators:

```text
Premium Engagement Score =
has_premium
+ has_purchase
+ has_price
+ has_free
+ has_cancel
+ has_limitation