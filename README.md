 ✈️ Flight Operational Difficulty Prediction System

📘 Overview

This project aims to help **United Airlines** proactively identify **operationally difficult flights** using data science.  
By combining flight, passenger, baggage, and airport-level data, the system calculates a **Flight Difficulty Score**, ranks daily flights, and classifies them as **Easy**, **Medium**, or **Difficult**.

The goal is to optimize **resource allocation**, **crew planning**, and **on-time performance** by predicting which flights are most complex to operate.

---

🧠 Problem Statement

Operational teams often face challenges such as:
- Tight ground time between flights  
- High passenger load  
- Complex baggage transfers  
- Many special service requests (wheelchair, infants, etc.)

These factors increase operational workload and delay risk.

This project builds a **data-driven model** to assign each flight a **difficulty score** based on historical and operational data.

---

🚀 Project Workflow

 🧩 1. Data Loading
Imported 5 key datasets:
| Dataset | Description | Rows | Columns |
|----------|--------------|-------|----------|
| Flights | Flight schedules, timings, seats, aircraft | 8099 | 15 |
| Bags | Baggage details, transfer info | 687K | 8 |
| PNR Flight | Passenger service requests | 51K | 4 |
| PNR Remarks | Passenger details, children, stroller, etc. | 687K | 12 |
| Airports | Airport IATA codes, country info | 5612 | 2 |

🧹 2. Data Cleaning
- Converted all date/time columns to `datetime`  
- Removed duplicates  
- Filled missing country codes  
- Standardized text columns (lowercase, stripped spaces)  
- Ensured all datasets are consistent and joinable on `(company_id, flight_number, scheduled_departure_date_local)`

 🏗️ 3. Feature Engineering
Created advanced metrics to capture operational complexity:

**Flight-Level Features**
- `ground_time_ratio = scheduled_ground_time / minimum_turn_time`
- `departure_delay` & `arrival_delay`
- `load_ratio = total_pax / total_seats`
- Time-based features → hour, day_of_week, month, weekend flag

**Passenger Features (from PNR Remarks)**
- `total_pax`, `child_count`, `stroller_count`, `lap_child_count`
- Ratios: `child_ratio`, `stroller_ratio`, `basic_econ_ratio`
- `ssr_count` = number of special service requests per flight

**Bag Features**
- `total_bags`, `transfer_bags`
- `transfer_bag_ratio = transfer_bags / total_bags`
- `baggage_per_pax = total_bags / total_pax`

**Complexity Score**
python
complexity_score = 0.25*child_ratio + 0.25*transfer_bag_ratio + 0.25*basic_econ_ratio + 0.25*(ssr_count / total_pax)

🚀 4. How to run
  🔗 Kaggle Notebook:
 [**Kaggle Profile - ashishSoni1234**](https://www.kaggle.com/ashishSoni1234)
 🔗 GitHub Repository:
[Click here to view the full project on GitHub](https://github.com/ashishSoni1234/Flight_Difficulty_score_system)

- Go to given link of public kaggle link or paste it on  any browser.
- Go to Copy & Edit Button on  top-right corner
- Click on Run all button 
- View all real  time prediction and analysis
