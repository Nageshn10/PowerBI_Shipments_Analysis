# DAX Measures – Power BI Shipments Dashboard

This file contains all **DAX formulas** used in the Power BI Shipments Analysis project.  
These measures were developed as part of the dashboard development and are fully functional with the sample dataset.

---

## 1. Total Amount
Calculates the total shipment amount.
```DAX
Total Amount = SUM(shipments[Amount])
```

2. Total Amount (Last Year)
Calculates the total amount for the same period last year
```DAX
Total Amount (last year) = CALCULATE(
    [Total Amount],
    SAMEPERIODLASTYEAR('calendar'[cal_date])
)
```

3. Total Amount (12 Month Variance)
Calculates the variance of Total Amount compared to last year.
```DAX
Total Amount (12 month variance) = 
VAR Ta_ly = [Total Amount (last year)]
RETURN
IF(ISBLANK(Ta_ly), BLANK(), [Total Amount] - Ta_ly)
```

4. Total Boxes
Calculates the total number of boxes shipped.
```DAX
Total Boxes = SUM(shipments[Boxes])
```

5. Total Boxes (Last Year)
Calculates total boxes for the same period last year.
```DAX
Total Boxes (last year) = CALCULATE(
    [Total Boxes],
    SAMEPERIODLASTYEAR('calendar'[cal_date])
)
```

6. Total Boxes (12 Month Variance)
Calculates the variance in boxes compared to last year.
```DAX
Total Boxes (12 month variance) = 
VAR Ta_ly = [Total Boxes (last year)]
RETURN
IF(ISBLANK(Ta_ly), BLANK(), [Total Boxes] - Ta_ly)
```

7. Total Costs
Calculates the total cost for all shipments.
```DAX
Total Costs = SUM(shipments[cost])
```

8. Total Profit
Calculates total profit as the difference between Total Amount and Total Costs.
```DAX
Total Profit = [Total Amount] - [Total Costs]
```

9. Profit %
Calculates profit as a percentage of Total Amount.
```DAX
Profit % = [Total Profit] / [Total Amount]
```

10. Shipment Count
Counts the number of shipments.
```DAX
Shipment Count = COUNTROWS(shipments)
```

## Notes / Usage

- Works with the sample dataset in the `datasets` folder.  
- Table names (`shipments`, `calendar`, etc.) must match exactly.  
- Use these measures in visuals, tables, and cards for the dashboard.  
- Dashboard screenshots are in `images` (e.g., `dashboard.png`, `profit_analysis.png`).  
- Tip: Use `VAR` for intermediate calculations; ensure the calendar table is continuous and marked as Date table.
