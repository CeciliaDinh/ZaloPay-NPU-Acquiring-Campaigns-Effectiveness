# ZaloPay-NPU-Acquiring-Campaigns-Effectiveness
# ZaloPay New Paying User (NPU) Campaign Effectiveness
**Analytical Case Study & Business Insights**

## 1. Project Overview & Executive Summary

### Business Context
In the highly competitive digital payments and fintech ecosystem, acquiring high-quality New Paying Users (NPUs) is a primary driver of market share and long-term profitability. This project analyzes the effectiveness of marketing campaigns in driving NPU acquisition for ZaloPay over a 7-month observation period (June - December 2022).

### Project Objectives
*   **Understand NPU acquisition performance** and quantify individual campaign contributions.
*   **Identify high-performing campaigns** and uncover overarching acquisition bottlenecks.
*   **Evaluate campaign efficiency and acquired-user quality** (within data constraints).
*   **Translate analytical findings into recommendations** for campaign optimization and marketing budget allocation.

### Executive Summary
Despite explosive overall platform growth (GTV grew by over 163% in H2 2022), **NPU acquisition steadily declined by 56%** from June to December. User acquisition is highly concentrated and vulnerable, with just 3 out of 453 campaigns driving 21% of all NPUs. Furthermore, nearly 63% of newly acquired users leverage their first promotional incentive on low-margin, high-utility services (Balance Increases and Utility Payments). To sustain platform growth, ZaloPay must urgently diversify its acquisition channels, combat top-of-funnel campaign fatigue, and build immediate cross-sell journeys to shift users from utility to lifestyle services.

---

## 2. Dataset Overview

The analysis relies on three relational datasets containing transactional and categorical data. 

*   **Business Domain:** Fintech / Digital Payments
*   **Observation Window:** June 2022 – December 2022

| Dataset | Records | Description & Analytical Purpose |
| :--- | :--- | :--- |
| `transaction_info` | 301,107 | Core fact table. Used to calculate GTV, track applied discounts, and determine the chronological first transaction for accurate NPU identification. |
| `user_info` | 33,686 | Dimension table providing demographic context and account creation dates to measure activation latency. |
| `merchant_info` | 748 | Dimension table mapping `appID` to macro and micro service categories to understand where users spend their first promotional incentive. |

### Data Quality & Preprocessing
*   **Status Resolution:** 28,366 negative status codes were identified as failed transactions. Only `transStatus == 1` was considered valid for financial metrics and NPU activation.
*   **Strict NPU Identification:** To avoid falsely flagging existing organic users as NPUs, the logic evaluated a user's *absolute first successful transaction on the platform chronologically*. Only if that first transaction utilized a campaign (`campaignID != 0`) was the user classified as a campaign-acquired NPU.

### Data Schema
