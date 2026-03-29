# 📊 Project Description – Football API ETL Pipeline

## 📌 Overview

This project implements a **data pipeline (ETL)** using Python to extract football league standings from an external API, transform the data into a structured format, and load it into a SQL Server database for further analysis and visualization.

The notebook focuses on a **single season of league standings (Premier League 2024)** and demonstrates how to convert raw JSON data into a clean analytical dataset.

---

## ⚙️ What the Notebook Does

### 🔹 1. Extract (API Data Collection)

* Connects to the **API-Football service**
* Uses an API key stored in environment variables (`.env`)
* Sends a request to the endpoint:

  * `/standings`
* Filters data using parameters:

  * `league = 39` (Premier League)
  * `season = 2024`
* Retrieves data in **JSON format**

👉 Output: Raw nested JSON response with league standings

---

### 🔹 2. Transform (Data Processing & Cleaning)

The notebook processes the raw JSON and converts it into a structured dataset:

* Navigates nested JSON:

  * `response → league → standings`

* Extracts relevant fields for each team:

  * Position (rank)
  * Team ID and name
  * Matches played, won, drawn, lost
  * Goals for / against
  * Goal difference
  * Points
  * Form (recent performance)

* Builds a clean tabular structure:

  * Creates a list of rows
  * Converts it into a **Pandas DataFrame**

👉 Output: Structured DataFrame with one row per team

---

### 🔹 3. Load (Database Integration)

* Connects to **SQL Server** using:

  * `SQLAlchemy`
  * `pyodbc` driver

* Uses environment variables for:

  * Server name
  * Database name

* Loads the DataFrame into a table:

  * Table name: `standings`
  * Behavior: `replace` (overwrites existing data)

👉 Output: Clean dataset stored in SQL Server

---

## 🛠️ Technologies Used

* **Python**

  * `requests` → API calls
  * `pandas` → data transformation
  * `json` → formatting responses
  * `dotenv` → environment variables
* **SQL Server**

  * Data storage
* **SQLAlchemy + pyodbc**

  * Database connection

---

## 📊 Final Dataset Structure

Each row represents a team in the league with fields such as:

* `season`
* `position`
* `team_id`
* `team`
* `played`
* `won`
* `draw`
* `lost`
* `goals_for`
* `goals_against`
* `goal_diff`
* `points`
* `form`

---

## 🎯 Purpose of the Project

* Demonstrate an **end-to-end ETL pipeline**
* Practice working with:

  * Real-world APIs
  * Nested JSON data
  * Database integration
* Prepare data for:

  * Analysis
  * Dashboards (e.g., Power BI)

---

## 🚀 Key Takeaways

* How to extract real-time sports data from an API
* How to transform complex JSON into a clean dataset
* How to automate data loading into SQL Server
* How to build a reusable data pipeline for analytics projects

---

## 🔮 Possible Extensions

* Automate daily data updates
* Store historical seasons
* Build a Power BI dashboard on top of the database
* Add data validation and logging
* Deploy pipeline to the cloud (Azure)

---

## 👤 Author

**Ariel Chocobar**
