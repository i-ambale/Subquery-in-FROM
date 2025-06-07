# 📘 README.md
## 🇺🇳 United Nations Database SQL Exploration
This Jupyter notebook is designed for local use and will not run on Google Colab due to its dependency on a local MySQL server. The notebook explores SQL querying techniques, specifically the use of subqueries in the `FROM` clause, using data from the `Access_to_Basic_Services` table in the `united_nations` database.

## 🧠 Learning Objectives
In this notebook, you'll learn:

- How to connect to a local MySQL database using Python.
  
- How to use a subquery as a temporary table with the FROM clause in SQL.
  
- How to filter, aggregate, and analyze real-world data using SQL.

## 📂 Project Structure
```
united-nations-sql/
│
├── notebook.ipynb         # Main Jupyter Notebook with SQL queries and analysis
├── README.md              # This file
├── requirements.txt       # Python dependencies
└── db_setup/              # Optional folder to include SQL schema or sample data
```

## 🧰 Requirements
Make sure the following tools are installed on your local machine:

- MySQL Server

- MySQL Workbench

- Python 3.8+

- `pip` for installing Python packages

You also need the following Python libraries:
```
pip install pymysql sqlalchemy pandas
```
Or use the `requirements.txt` file:
```
pip install -r requirements.txt
```
## 🛠️ Setup Instructions
1. Ensure your MySQL server is running locally.

2. Open MySQL Workbench and verify that the `united_nations` database exists and contains the `Access_to_Basic_Services` table.

3. Update the database connection string in the notebook:

```
DATABASE_URL = "mysql+pymysql://root:<your-password>@localhost:3306/united_nations"
```
4. Launch the Jupyter Notebook:
```
jupyter notebook
```
Open the notebook and run each cell in sequence.

## 🧪 Example Query with Subquery in FROM Clause
```
SELECT 
    sub.Country_name,
    AVG(sub.Est_gdp_in_billions) AS Avg_GDP,
    AVG(sub.Est_population_in_millions) AS Avg_Population
FROM (
    SELECT 
        Country_name,
        Est_gdp_in_billions,
        Est_population_in_millions
    FROM 
        Access_to_Basic_Services
    WHERE 
        Pct_unemployment > 5
        AND Time_period = 2020
) AS sub
GROUP BY 
    sub.Country_name;
```
This query calculates average GDP and population per country for countries with unemployment > 5% in 2020.

## ❗ Important Notes
- This notebook will not work in cloud environments like Google Colab, because it needs access to localhost, where your MySQL server runs.

- If you want to make it cloud-compatible, consider using a hosted MySQL database or services like PlanetScale, ClearDB, or Amazon RDS.

## 📝 License
MIT License — feel free to use and adapt this for learning or teaching purposes.
