# Fulfilment Operations Analytics – End-to-End SQL Case Study

This project analyzes a simulated e-commerce fulfilment pipeline using SQL to uncover operational bottlenecks, SLA risks, hub capacity issues, and logistics cost drivers.

The analysis replicates the workflow of a Business Analyst supporting fulfilment and logistics operations, turning raw operational event data into actionable insights.

The project answers 45 real-world business questions covering fulfilment performance, SLA adherence, hub utilization, shipping efficiency, and return behavior.

# Project Objectives

-- The goal of this project is to analyze fulfilment operations and answer key business questions such as:
-- Where do operational delays occur in the fulfilment pipeline?
-- Which stages contribute most to SLA breaches?
-- Which hubs are approaching capacity limits?
-- How do logistics costs impact operational performance?
-- What factors drive returns and customer dissatisfaction?

-- This project demonstrates how SQL can be used to support data-driven operational decision-making.

# Tech Stack

SQL (PostgreSQL)
Python (Data generation & simulation)
Window Functions
CTEs
Materialized Views
Operational KPI modeling

# Data Generation
The dataset used in this project was synthetically generated using Python to simulate a realistic fulfilment pipeline.
The Python script generated:
Order data

Fulfilment stage events

Shipping details

Returns data

SLA definitions

Hub capacity information

This approach allowed the project to replicate real operational data scenarios, including:

Missing timestamps

Operational delays

Rework stages

SLA violations

Capacity stress

Data Model

The project uses the following core tables:

Orders

Stores order-level information.

Column	Description
order_id	Unique order identifier
order_date	Order placement date
hub_id	Fulfilment hub
order_value	Order revenue
priority_flag	Express vs standard
promised_delivery_date	Delivery SLA
Fulfilment Events

Tracks order progression across operational stages.

Column	Description
order_id	Order identifier
stage_name	Fulfilment stage
stage_start_time	Stage start time
stage_end_time	Stage completion time
status	Stage status
hub_id	Processing hub

Pipeline stages:

Intake → QC → Packing → Shipping → Delivery
Hubs

Stores fulfilment hub capacity data.

Column	Description
hub_id	Hub identifier
hub_name	Hub name
capacity_per_day	Maximum orders per day
Shipping

Contains logistics partner and shipping cost information.

Column	Description
shipping_partner	Delivery provider
shipping_cost	Shipment cost
weight_bucket	Shipment weight category
Returns

Tracks returned orders and refund details.

Column	Description
return_reason	Reason for return
refund_amount	Refunded value
SLA

Defines stage-level SLA thresholds.

stage_name	sla_hours
QC	Stage SLA
Packing	Stage SLA
Shipping	Stage SLA
Delivery	Final delivery SLA
Data Validation & Cleaning

Before analysis, extensive data quality checks were performed.

Key validations included:

Null value detection

Missing stage timestamps

Negative stage durations

Duplicate stage events

Orphan records

Orders missing delivery stage

Capacity violations

Overlapping stage events

Missing stage_end_time values were handled using window functions by imputing the start time of the next stage.

A materialized view (fulfilment_events_clean) was created for optimized analysis.

Key Business Questions Answered

The project solves 45 operational KPI questions, including:

Fulfilment Performance

Stage-wise average processing time

Overall order turnaround time

Queue time between stages

Processing variability by stage

SLA Monitoring

Delivery SLA breach rate

SLA breach contribution by stage

Monthly SLA breach trends

QC contribution to delivery failures

Hub Performance

Hub-level SLA performance

Throughput per hub

Capacity utilization

Hub stability and variability

Operational Optimization

Bottleneck stage detection

QC delay impact on backlog

Impact of reducing QC time

Demand stress simulation

Logistics & Cost Analysis

Shipping partner performance

Cost per on-time delivery

Shipping cost vs SLA performance

Fulfilment pipeline cost drivers

Returns Analysis

Overall return rate

Return probability vs delivery delays

Return rate by hub

Margin impact of returns

Key Insights

Some insights derived from the analysis include:

QC delays are a leading indicator of downstream SLA breaches.

Certain hubs operate near capacity limits and show higher SLA variance.

High utilization correlates with increased backlog formation.

Shipping costs significantly impact fulfilment margin efficiency.

Late deliveries increase the probability of customer returns.
