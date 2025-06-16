
# Performance Dashboard - Sales Analysis 📊📈

## 📋 Overview
This repository contains a Power BI performance dashboard designed to analyze Total Sales vs Target over time. It provides interactive visualizations to help organizations assess their performance across multiple dimensions like time, region, and sales personnel.


![Dashboard Screenshot](Screenshot%202025-06-16%20123909.png)



## 🎯 AIMS Grid
| **Aspect**   | **Details**                                                                 |
|--------------|------------------------------------------------------------------------------|
| **A**im      | Track and analyze sales performance vs targets using Power BI               |
| **I**nputs   | Sales Data, Targets, Calendar, Sales Team Data                              |
| **M**ethods  | Power BI, DAX measures, Data Modeling, Visualizations                        |
| **S**uccess  | Improved visibility, faster decision-making, identification of key trends   |

---


## ✨ Key Features
- **Total Sales vs Target Trend** (Monthly View)
- **KPI Cards**: Total Sales, Total Target, Variance, Variance %, YTD data
- **Dynamic Visuals**: Period-wise, Salesperson-wise, and Team-wise breakdowns
- **Visual Trend Indicators**: Color-coded performance status with sparklines
- **Textual Insights**: Auto-generated dynamic text summaries

---

## 🛠️ Challenges Faced
### 1. Data Cleaning
- **Inconsistent Formats**: Sales and target data from different regions used varying date and currency formats.
- **Missing Values**: Several months had null or missing values which were handled using interpolation or imputation techniques.
- **Duplicate Records**: Duplicate entries for sales data were identified and removed based on unique identifiers (Salesperson, Month).

### 2. Data Modeling
- **Relationship Setup**: Creating correct relationships between the Actuals, Calendar, Sales Team, and Target tables was key to ensure accurate calculations.
- **Normalization**: Redundant columns were normalized to separate dimension tables (Calendar, Salesperson, Region).
- **Time Intelligence**: Built a custom Calendar table to enable period-wise slicing and time-based analysis.

---

## 📐 Measures and Calculations
### KPI Measures
- `Total_Sales` = SUM(Actual[Sales])
- `Total_Target` = SUM(Targets[Target])
- `Variance` = [Total_Sales] - [Total_Target]
- `Variance%` = DIVIDE([Variance], [Total_Target], 0)
- `YTD Sales/Target/Variance` using `DATESYTD` for each measure

### Dynamic Measures and Headings
- Created dynamic header text measures like Column_chart_Header:
  - Example:
  ```DAX
    Header_Column_Chart = 
        var month_count=COUNTROWS('Calendar')
    RETURN "Target achieved in" & " " & [Months Target Reached]&" Out of "& month_count& " Months"

- Created dynamic Divergence between actual and target values and assigned emojis to it:-
  - Example:
  ```DAX
  Variance_PCT_Label = 
        var up="🟢"
        var down="🔴"
        var formatted_Var_Pct=format(abs([Variance%]),"0.0%")
    return
     formatted_Var_Pct & " " & if([Variance%]>0,up,down)

### 📊 Business Use Case
This dashboard provides business stakeholders and analysts with:

- **Time-wise Performance Analysis**:
  - Analyze achievement vs targets over months, quarters, or fiscal years

- **Sales Team Performance**:
  - Identify high and low performers
  - Track team-wise contributions to total sales

- **Region/Branch-wise Analysis** (if dimensions exist):
  - Compare performance across regions
  - Uncover underperforming branches

- **Strategic Planning**:
  - Enable managers to set realistic targets
  - Improve sales strategies by analyzing past trends

---

### ▶️ How to Use
1. Load the dataset using Power BI Desktop.
2. Navigate to the main dashboard view.
3. Use filters to drill down by month, salesperson, or team.
4. Observe KPIs, variance trends, and insights.

---

### 🔮 Future Improvements
- Add drill-through to regional and customer-wise performance
- Embed alerts for target shortfall
- Integrate predictive analytics for forecasting future targets

---

### 🪪 License
This project is provided for educational and analytical purposes.


