# Excel_Project#2 -Telecom Customer Churn Analysis

An Excel-based customer churn analysis project focused on **data cleaning, transformation, visualization, Power Query, Power Pivot, and DAX**.

Unlike my first Excel project, which focused primarily on building an interactive dashboard, this project focuses on the **data analysis workflow behind the visualizations** — transforming raw data into usable analytical structures and building a simple relational data model.

---

## 📌 Project Overview

The project uses a telecom customer dataset containing **7,043 customer records and 38 columns**.

The analysis was carried out using:

- Microsoft Excel
- Power Query
- Power Pivot
- DAX
- PivotTables & PivotCharts
- Slicers

The project follows the workflow:

**Raw Data → Power Query → Data Transformation → Visualization → Power Pivot → DAX → Analysis**

---

## 🗂️ Project Structure

The project consists of three main analyses:

1. **Internet Type Analysis**
2. **Add-on Analysis**
3. **City Churn Analysis using Power Pivot & DAX**

---

## 1. Data Cleaning & Transformation

The original dataset contained **7,043 customer records and 38 columns**.

Using **Power Query**, I:

- Imported and standardized the dataset.
- Corrected the relevant data types.
- Removed unnecessary columns.
- Filtered out records with missing `Online Security` values.
- Reorganized the remaining fields into a cleaner analytical structure.

This produced the cleaned `Telecom_Churn_Analysis` query, which was used as the source for the subsequent analyses.

<img width="1661" height="822" alt="Screenshot 2026-10-03 123140" src="https://github.com/user-attachments/assets/8d61f1b7-2553-4c35-b4c4-c5bd45cbb485" />

---

## 2. Internet Type Analysis

The cleaned dataset was used to analyse customer status across different internet types.

Using **Power Query**, I:

- Selected the relevant `Internet Type` and `Customer Status` fields.
- Transformed customer status into separate columns: **Stayed, Churned and Joined**.
- Grouped the data by `Internet Type`.
- Aggregated each status using **Sum** to obtain customer counts.

This resulted in a compact analytical table containing:

- Fiber Optic
- DSL
- Cable

<img width="1663" height="822" alt="Screenshot 2026-10-03 124031" src="https://github.com/user-attachments/assets/8af822b6-e594-4548-868a-d4134c0f141b" />


A clustered bar chart was then created to visualize **Customer Status by Internet Type**.

<img width="1445" height="657" alt="Screenshot 2026-10-03 124726" src="https://github.com/user-attachments/assets/71ddfda8-a5e9-49a9-bf8d-24c6ae657c32" />


---

## 3. Add-on Analysis

The original dataset contained multiple Yes/No columns representing services such as:

- Device Protection
- Online Security
- Online Backup
- Streaming TV
- Streaming Movies
- Streaming Music
- Unlimited Data
- Premium Tech Support

Using **Power Query**, I:

- Converted `Yes` values into their corresponding add-on names.
- Replaced `No` values with blanks.
- Unpivoted the add-on columns.
- Removed blank records and unnecessary columns.

<img width="1661" height="822" alt="Screenshot 2026-10-03 123732" src="https://github.com/user-attachments/assets/8866e2df-ceec-485c-8403-d216b2e9e9be" />


This transformed the data from multiple binary columns into a **customer–add-on structure**, where each row represents a customer and an associated add-on.

A PivotTable was then used to analyse add-on usage by customer status, with a **Customer Status slicer** added for interactive exploration.

<img width="1598" height="681" alt="Screenshot 2026-10-03 124858" src="https://github.com/user-attachments/assets/150c4bf6-7c24-43d0-8f9d-1b95afc18eaf" />


---

## 4. City Churn — Power Pivot & DAX

For the final analysis, I created separate tables from the cleaned data with different levels of detail and loaded them into the **Power Pivot Data Model**.

### Data Modeling

- Created a relationship between the tables using **Customer ID**.
- Used the relationship to connect customer-level information with the transformed data.
- Created an explicit **DAX measure** using `DISTINCTCOUNT` and `CALCULATE`.
- The measure counts only unique customers whose status is **Churned**.
- Used `City` as the row field and the DAX measure as the value.
```
Churned Customers:=CALCULATE(
    DISTINCTCOUNT(Customer_City_Table[Customer ID]),
    Customer_Status_Table[Customer Status] = "Churned"
)
```

This produced a **Churned Customers by City** analysis without manually filtering out other customer statuses.

### Power Pivot Data Model

<img width="866" height="640" alt="Screenshot 2026-10-03 125010" src="https://github.com/user-attachments/assets/f37aa437-f6b5-4ac5-b15d-156820982be2" />

### City Churn Visualization

<img width="1360" height="623" alt="Screenshot 2026-10-03 130043" src="https://github.com/user-attachments/assets/70e70bc2-6d85-44d7-8175-900e47e4b0b8" />

---

## 🛠️ Tools & Concepts Demonstrated

### Excel
- PivotTables
- PivotCharts
- Slicers
- Data visualization

### Power Query
- Data cleaning
- Data type transformation
- Column selection
- Filtering
- Grouping & aggregation
- Pivoting
- Unpivoting
- Data restructuring

### Power Pivot
- Data modeling
- Table relationships
- Different data grains
- Relational analysis

### DAX
- `CALCULATE`
- `DISTINCTCOUNT`

---

## 📊 Key Learning

The main objective of this project was not to create a highly designed dashboard, but to understand how raw business data can be **cleaned, transformed, modeled and analysed** using Excel's data analytics tools.

The project helped me explore the progression from:

**Power Query → Data Transformation → Data Modeling → DAX → Analysis**
