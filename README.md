## Project Title
**Car Sales Dynamics**

## Project Description
The Car Sales Dynamics Dashboard is a comprehensive Power BI project designed to provide detailed insights into car sales metrics. This dashboard tracks various sales parameters including total sales, average prices, and the number of cars sold on both yearly and monthly bases. It offers a detailed breakdown of sales trends by body style, company, color, and dealer region.

## Installation / Prerequisites
   - **Power BI Desktop**: Ensure you have the latest version of Power BI Desktop installed on your machine.
   - **Data Sources**: The project requires car sales data, which should be formatted in a compatible structure (e.g., CSV or Excel).

## Project Structure
### DAX Calculations
   ```DAX
    Total Sales = SUM(Sheet1[Price ($)])
    
    YTD Total Sales = TOTALYTD(SUM(Sheet1[Price ($)]), 'Calendar Table'[Date])
    
    YTD Cars Sold = TOTALYTD(COUNT(Sheet1[Car_id]), 'Calendar Table'[Date])
    
    YTD Avg Price = TOTALYTD([Avg Price], 'Calendar Table'[Date])
    
    YOY Sales Growth = [Sales Diff]/[PYTD Sales]
    
    YOY Cars Sold Growth = [Cars Sold Diff]/[PYTD Cars Sold]
    
    YOY Avg Growth = [Avg Diff]/[PYTD Avg price]
    
    PYTD Sales = CALCULATE(SUM(Sheet1[Price ($)]), SAMEPERIODLASTYEAR('Calendar Table'[Date]))
    
    PYTD Cars Sold = CALCULATE(COUNT(Sheet1[Car_id]), SAMEPERIODLASTYEAR('Calendar Table'[Date]))
    
    PYTD Avg price = CALCULATE([Avg Price], SAMEPERIODLASTYEAR('Calendar Table'[Date]))
    
    Sales Diff = [YTD Total Sales] - [PYTD Sales]
    
    Sales Icon = IF([Sales Diff]>0, "+", "-")
    
    Sales Diff and Icon = CONCATENATE([Sales Icon] , FORMAT([Sales Diff]/1000000, "$0.0M"))
    
    MTD Total Price = TOTALMTD(SUM(Sheet1[Price ($)]), 'Calendar Table'[Date])
    
    MTD Conc = CONCATENATE("MTD Total Sales : ", FORMAT([MTD Total Price]/1000000, "$0.00M"))
    
    MTD Cars Sold Conc = CONCATENATE("MTD Cars Sold : ", FORMAT([MTD Cars Sold]/1000, "0.00K"))
    
    MTD Cars Sold = TOTALMTD(COUNT(Sheet1[Car_id]), 'Calendar Table'[Date])
    
    MTD Avg Sales = TOTALMTD([Avg Price], 'Calendar Table'[Date])
    
    MTD Avg Conc = CONCATENATE("MTD Avg Price : ", FORMAT([MTD Avg Sales]/1000, "$0.00K"))
    
    Data Range = CONCATENATE(MIN('Calendar Table'[Date]), " to ")
    
    Max Point on Trend Line = IF(MAXX(ALLSELECTED('Calendar Table'[Week]), [Total Sales]) = [Total Sales] , MAXX(ALLSELECTED('Calendar Table'[Week]), [Total Sales]) , BLANK())
    
    Cars Sold Diff = [YTD Cars Sold] - [PYTD Cars Sold]
    
    Cars Sold Icon = IF([Cars Sold Diff]>0, "+", "-")
    
    Cars Diff and Icon = CONCATENATE([Cars Sold Icon] , FORMAT([Cars Sold Diff]/1000, "$0.0K"))
    
    Avg Price = SUM(Sheet1[Price ($)])/ COUNT(Sheet1[Car_id])
    
    Avg Diff = [YTD Avg Price] - [PYTD Avg price]
    
    Avg Icon = IF([Avg Diff]>0, "+", "")
    
    Avg Diff and Icon = CONCATENATE([Avg Icon] , FORMAT([Avg Diff]/1000, "$0.00K"))
    
    Avg Color = IF([Avg Diff]>0, "Green", "Red")
   ```

## Project Background
  The visualization and design of the dashboard were crafted using **Figma** and **Adobe Photoshop** to ensure an intuitive and user-friendly interface.
