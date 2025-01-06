# Finance Insights Dashboard

## 📌 **Project Overview**

This Finance Insights Dashboard provides an interactive and analytical view of personal expenses. It helps users understand their spending habits, track daily expenditures, and identify areas where they can save money. With built-in AI-driven insights, this dashboard empowers users to make informed financial decisions.

## 🎯 **Key Features**

- **Executive Dashboard**: A high-level summary of income vs. expenses, savings trends, and key financial KPIs.

- **Geographical Analysis (Map)**: Displays spending trends by location.

- **Product Detail**: Breakdown of expenses by product category.

- **Customer Detail**: Categorizes expenses based on user behavior.

- **Category Tooltip**: Customizes Tooltip's style.

- **AI: Decomposition Tree**: Identifies key factors influencing expenses.

- **AI: Key Influencers**: Uses Power BI's AI capabilities to highlight trends and anomalies.

- **Interactive Features**: Slicers, drill-throughs, and AI visuals for an enhanced analytical experience.

## 📊 **Data Sources**

The dashboard is built using:

- Excel / CSV datasets (for tracking expenses)

- Manual Data Entry (for user-specific inputs)


## 🔧 **Installation & Setup**

To use this Power BI dashboard:

- Install Power BI Desktop

- Clone this repository:

``` 
git clone https://github.com/your-username/your-repo.git
```

- Open `Adventure_Works_Project.pbix` in Power BI Desktop.

- Connect to your own dataset (if required) and refresh the dashboard.

## 🚀 **Dashboard Walkthrough**

**1. Executive Dashboard**

- Visualizes total income vs. total expenses
- Displays monthly savings trends
- Highlights key financial KPIs

![Screenshot 2025-01-06 064836](https://github.com/user-attachments/assets/4a378036-39a0-4fae-9fff-39cdf614f57a)

**2. Map (Geographical Analysis)**

- Shows spending distribution across different locations.
- Useful for analyzing expenses related to travel or city-based spending patterns.

![Screenshot 2025-01-06 065651](https://github.com/user-attachments/assets/f5b0d243-e020-47c8-a8b3-c09fc146908f)

**3. Product Detail**

- Breaks down spending by category (e.g., groceries, dining, shopping, utilities).
- Helps identify which categories contribute the most to total expenses.

![Screenshot 2025-01-06 064946](https://github.com/user-attachments/assets/40643659-e8f2-4f99-98f9-eee0a8869341)

**4. Customer Detail**

- Analyzes spending habits based on different user profiles (if applicable).
- Useful for understanding spending behavior by demographic.

![Screenshot 2025-01-06 065015](https://github.com/user-attachments/assets/da38139e-624f-4f3a-9b0d-672ae41b55be)

**5. AI-Powered Insights**

- _Decomposition Tree_: Explores key factors influencing expenses.

  ![Screenshot 2025-01-06 065104](https://github.com/user-attachments/assets/5884d2fc-bd53-4938-b975-86e1304acd82)

- _Key Influencers_: Uses AI to detect anomalies and predict financial trends.

  ![Screenshot 2025-01-06 065130](https://github.com/user-attachments/assets/ba526ba9-bf9e-4731-9068-855638fb92cc)

## 📊 **DAX Measures Used**

Here are some key DAX (Data Analysis Expressions) formulas used in the dashboard:

- **_Total Expenses_**
```
Total Expenses = SUM(Expenses[Amount])
```
- **_Total Income_**
```
Total Income = SUM(Income[Amount])
```
- **_Savings Calculation_**
```
Total Savings = [Total Income] - [Total Expenses]
```
- **_Monthly Expense Growth Rate_**
```
Monthly Growth Rate = 
VAR PreviousMonth = CALCULATE([Total Expenses], PREVIOUSMONTH(Expenses[Date]))
RETURN 
IF(NOT ISBLANK(PreviousMonth), ([Total Expenses] - PreviousMonth) / PreviousMonth, BLANK())
```
- **_Cumulative Total Expenses_**
```
Cumulative Expenses = 
CALCULATE(
    [Total Expenses],
    FILTER(
        ALLSELECTED(Expenses[Date]),
        Expenses[Date] <= MAX(Expenses[Date])
    )
)
```
- **_Year-over-Year Expense Growth_**
```
YoY Growth = 
VAR PreviousYear = CALCULATE([Total Expenses], SAMEPERIODLASTYEAR(Expenses[Date]))
RETURN 
IF(NOT ISBLANK(PreviousYear), ([Total Expenses] - PreviousYear) / PreviousYear, BLANK())
```
- **_Expense Category Percentage Contribution_**
```
Category Contribution = 
DIVIDE([Total Expenses], CALCULATE([Total Expenses], ALL(Expenses[Category])), 0)
```
- **_Average Daily Expense_**
```
Avg Daily Expense = 
DIVIDE([Total Expenses], DISTINCTCOUNT(Expenses[Date]))
```
and there's many more... 

## 🛠 **Usage Instructions**

- Use slicers to filter expenses by date, category, or location.

- Hover over charts for tooltips with deeper insights.

- Use drill-through features for detailed analysis.

- Refresh the dataset regularly to ensure up-to-date financial tracking.

## 🚀 **Future Improvements**

- Integration with live bank transaction data

- Automated expense categorization using machine learning

- Mobile-friendly Power BI version

## 🤝 **Contributing**

If you’d like to improve this project, feel free to fork the repository and submit pull requests!

## 📜 **License**

This project is open-source under the MIT License.

---
⭐ Star this repository if you found this project useful!
