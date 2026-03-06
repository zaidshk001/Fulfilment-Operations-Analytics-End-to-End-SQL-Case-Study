# Fulfilment Operations Analytics – End-to-End SQL Case Study

This project analyzes a simulated **e-commerce fulfilment pipeline** using SQL to uncover operational bottlenecks, SLA risks, hub capacity issues, and logistics cost drivers.

The analysis replicates the workflow of a **Business Analyst supporting fulfilment and logistics operations**, turning raw operational event data into actionable insights.

The project answers **45 real-world business questions** covering fulfilment performance, SLA adherence, hub utilization, shipping efficiency, and return behavior.

---

# Project Objectives

The goal of this project is to analyze fulfilment operations and answer key business questions such as:

- Where do operational delays occur in the fulfilment pipeline?
- Which stages contribute most to SLA breaches?
- Which hubs are approaching capacity limits?
- How do logistics costs impact operational performance?
- What factors drive returns and customer dissatisfaction?

This project demonstrates how SQL can be used to support **data-driven operational decision-making**.

---

# Tech Stack

- **SQL (PostgreSQL)**
- **Python (Data generation & simulation)**
- Window Functions
- Common Table Expressions (CTEs)
- Materialized Views
- Operational KPI modeling

---

# Data Generation

The dataset used in this project was **synthetically generated using Python** to simulate a realistic fulfilment pipeline.

The Python script generated:

- Order data
- Fulfilment stage events
- Shipping details
- Returns data
- SLA definitions
- Hub capacity information

This approach allowed the project to replicate **real operational data scenarios**, including:

- Missing timestamps
- Operational delays
- Rework stages
- SLA violations
- Capacity stress

---

# Data Model

The project uses the following core tables:

---

## Orders

Stores order-level information.

| Column | Description |
|------|------|
| order_id | Unique order identifier |
| order_date | Order placement date |
| hub_id | Fulfilment hub |
| order_value | Order revenue |
| priority_flag | Express vs standard |
| promised_delivery_date | Delivery SLA |

---

## Fulfilment Events

Tracks order progression across operational stages.

| Column | Description |
|------|------|
| order_id | Order identifier |
| stage_name | Fulfilment stage |
| stage_start_time | Stage start time |
| stage_end_time | Stage completion time |
| status | Stage status |
| hub_id | Processing hub |

Pipeline stages:
