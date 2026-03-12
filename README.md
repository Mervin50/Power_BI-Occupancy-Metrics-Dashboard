# Power_BI-Occupancy-Metrics-Dashboard

<img width="1176" height="662" alt="Image" src="https://github.com/user-attachments/assets/0349a677-9e7a-43b2-a6c4-1630054d2357" />

<img width="1202" height="702" alt="Image" src="https://github.com/user-attachments/assets/b2cba325-6411-45c1-ad70-5deb94e2c669" />

### Overview
This repository holds the semantic model and documentation for a fictional U.S. shipping company. The goal of the model is to bring together web session data, booking records, and vessel occupancy information into a unified analytical framework. Data is sourced from:

• Google Analytics (sessions, users, site searches)

• SAP BusinessObjects (BO) (booking and production details)

• Excel files (daily production logs)

Using Power BI, we created a semantic layer that organizes these disparate sources into a coherent data structure, enabling interactive reporting of key performance indicators (KPIs).

### Business Context
The shipping company seeks to understand how online engagement (web sessions and site searches) translates into actual bookings and vessel occupancy. By analyzing:

• Web traffic (sessions, new users, bounce rate)

• Search behavior (keywords and site searches)

• Booking activity (number of bookings, passenger counts)

• Production/occupancy (actual sailings and capacity usage)

• Stakeholders can make data‑driven decisions on marketing effectiveness, pricing strategies, and operational planning.

### Data Sources and Tables
The semantic model includes the following tables:

### Table Name	Description

• Calendar	Date dimension (year, month, week, custom periods)

• Hours	Hour-of-day dimension for time-based analysis

• GA_Sessions	Website sessions, bounces, average session duration

• GA_Users	Unique and new users by date and hour

• GA_Bookings	Transactions recorded in Google Analytics

• GA_Site_Search	Search terms and refined keywords used on the site

• WIZ_Daily_Production	Daily visit counts from Excel production logs

• BO_Production	SAP BO booking data: booking ID, dates, passenger count

• Page	Page-level data imported from site logs

• Page_Category	Categorized page views and traffic metrics

• Price Catalogue	Price descriptions and catalog details

• Each table has been documented in the Data Dictionary.xlsx file included in this repo.

### Semantic Relationships

To create a unified model, we defined one‑to‑many relationships from our dimensions (Calendar, Hours) into each fact table. For example:

• Calendar[Date] → BO_Production[Booking Date]

• Calendar[Date] → GA_Sessions[Date]

• Hours[Hour] → GA_Users[Hour]

This structure allows any time‑based filter (e.g., selecting a specific week or hour) to propagate to all measures across the report.

### Key Measures and Calculations

The following DAX measures were created to surface critical insights:

### Measure Name	Purpose

• Total Bookings	Counts total booking records (COUNT(BO_Production[Booking ID]))

• Bookings Last Week	Bookings in the previous 7‑day period

• Bookings Previous Week	Bookings in the 7 days prior to last week

• Bookings Difference	Week‑over‑week change (Bookings Last Week – Prev Week)

• Bookings by Pax	Counts bookings by passenger count (1 Pax, 2 Pax, etc.)

• Total Sessions	Sum of web sessions plus daily visits

• Occupancy Rate	Ratio of actual sailings versus capacity

• Weighted Bookings	Applies a weight factor by passenger category

• All DAX expressions are detailed in the Data Dictionary under the “Expression” column for each measure.

# Analytical Scenario & Solution

• Situation: Marketing teams noticed fluctuations in web traffic but lacked a clear view of how sessions translated into bookings. Operations managers needed accurate occupancy forecasts to optimize vessel utilization.

# Solution Approach:

• Integrate web analytics and booking systems into a single semantic model.

• Define time intelligence measures to compare week‑over‑week and month‑over‑month trends.

• Calculate occupancy rates and segment bookings by passenger count.

• Visualize KPIs in Power BI, enabling interactive exploration of date ranges, search behavior, and booking performance.

### Stakeholders can now:

• Track conversion rates from sessions to bookings in real time.

• Identify peak search terms that drive bookings.

• Monitor occupancy to adjust pricing and marketing spend.
