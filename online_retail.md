# Portfolio Project: Online Retail Exploratory Data Analysis with Python

## Overview

In this project, you will step into the shoes of an entry-level data analyst at an online retail company, helping interpret real-world data to help make a key business decision.

## Case Study
In this project, you will be working with transactional data from an online retail store. The dataset contains information about customer purchases, including product details, quantities, prices, and timestamps. Your task is to explore and analyze this dataset to gain insights into the store's sales trends, customer behavior, and popular products. 

By conducting exploratory data analysis, you will identify patterns, outliers, and correlations in the data, allowing you to make data-driven decisions and recommendations to optimize the store's operations and improve customer satisfaction. Through visualizations and statistical analysis, you will uncover key trends, such as the busiest sales months, best-selling products, and the store's most valuable customers. Ultimately, this project aims to provide actionable insights that can drive strategic business decisions and enhance the store's overall performance in the competitive online retail market.

## Prerequisites

Before starting this project, you should have some basic knowledge of Python programming and Pandas. In addition, you may want to use the following packages in your Python environment:

- pandas
- numpy
- seaborn
- matplotlib

These packages should already be installed in Coursera's Jupyter Notebook environment, however if you'd like to install additional packages that are not included in this environment or are working off platform you can install additional packages using `!pip install packagename` within a notebook cell such as:

- `!pip install pandas`
- `!pip install matplotlib`

## Project Objectives
1. Describe data to answer key questions to uncover insights
2. Gain valuable insights that will help improve online retail performance
3. Provide analytic insights and data-driven recommendations

## Dataset

The dataset you will be working with is the "Online Retail" dataset. It contains transactional data of an online retail store from 2010 to 2011. The dataset is available as a .xlsx file named `Online Retail.xlsx`. This data file is already included in the Coursera Jupyter Notebook environment, however if you are working off-platform it can also be downloaded [here](https://archive.ics.uci.edu/ml/machine-learning-databases/00352/Online%20Retail.xlsx).

The dataset contains the following columns:

- InvoiceNo: Invoice number of the transaction
- StockCode: Unique code of the product
- Description: Description of the product
- Quantity: Quantity of the product in the transaction
- InvoiceDate: Date and time of the transaction
- UnitPrice: Unit price of the product
- CustomerID: Unique identifier of the customer
- Country: Country where the transaction occurred

## Tasks

You may explore this dataset in any way you would like - however if you'd like some help getting started, here are a few ideas:

1. Load the dataset into a Pandas DataFrame and display the first few rows to get an overview of the data.
2. Perform data cleaning by handling missing values, if any, and removing any redundant or unnecessary columns.
3. Explore the basic statistics of the dataset, including measures of central tendency and dispersion.
4. Perform data visualization to gain insights into the dataset. Generate appropriate plots, such as histograms, scatter plots, or bar plots, to visualize different aspects of the data.
5. Analyze the sales trends over time. Identify the busiest months and days of the week in terms of sales.
6. Explore the top-selling products and countries based on the quantity sold.
7. Identify any outliers or anomalies in the dataset and discuss their potential impact on the analysis.
8. Draw conclusions and summarize your findings from the exploratory data analysis.

## Task 1: Load the Data


```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Optional: Improve visualization style
sns.set(style="whitegrid")
plt.rcParams['figure.figsize'] = (10,6)
```


```python
df = pd.read_excel("Online Retail.xlsx")
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>InvoiceNo</th>
      <th>StockCode</th>
      <th>Description</th>
      <th>Quantity</th>
      <th>InvoiceDate</th>
      <th>UnitPrice</th>
      <th>CustomerID</th>
      <th>Country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>536365</td>
      <td>85123A</td>
      <td>WHITE HANGING HEART T-LIGHT HOLDER</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>2.55</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>1</th>
      <td>536365</td>
      <td>71053</td>
      <td>WHITE METAL LANTERN</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>2</th>
      <td>536365</td>
      <td>84406B</td>
      <td>CREAM CUPID HEARTS COAT HANGER</td>
      <td>8</td>
      <td>2010-12-01 08:26:00</td>
      <td>2.75</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>3</th>
      <td>536365</td>
      <td>84029G</td>
      <td>KNITTED UNION FLAG HOT WATER BOTTLE</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
    <tr>
      <th>4</th>
      <td>536365</td>
      <td>84029E</td>
      <td>RED WOOLLY HOTTIE WHITE HEART.</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.shape
```




    (541909, 8)




```python
df.isnull().sum()
```




    InvoiceNo           0
    StockCode           0
    Description      1454
    Quantity            0
    InvoiceDate         0
    UnitPrice           0
    CustomerID     135080
    Country             0
    dtype: int64




```python
df = df.dropna(subset=['CustomerID'])
```


```python
df.isnull().sum()
```




    InvoiceNo      0
    StockCode      0
    Description    0
    Quantity       0
    InvoiceDate    0
    UnitPrice      0
    CustomerID     0
    Country        0
    dtype: int64




```python
df = df.dropna(subset=['CustomerID'])
```


```python
df.isnull().sum()
```




    InvoiceNo      0
    StockCode      0
    Description    0
    Quantity       0
    InvoiceDate    0
    UnitPrice      0
    CustomerID     0
    Country        0
    dtype: int64




```python
df = df.dropna(subset=['Description'])
```


```python
df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])
```


```python
df['CustomerID'] = df['CustomerID'].astype(int)
```


```python
df = df[df['Quantity'] > 0]
```


```python
df = df[df['UnitPrice'] > 0]
```


```python
df = df.drop_duplicates()
```


```python
df['TotalPrice'] = df['Quantity'] * df['UnitPrice']
```


```python
df.shape
df.describe()
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 392692 entries, 0 to 541908
    Data columns (total 9 columns):
     #   Column       Non-Null Count   Dtype         
    ---  ------       --------------   -----         
     0   InvoiceNo    392692 non-null  object        
     1   StockCode    392692 non-null  object        
     2   Description  392692 non-null  object        
     3   Quantity     392692 non-null  int64         
     4   InvoiceDate  392692 non-null  datetime64[ns]
     5   UnitPrice    392692 non-null  float64       
     6   CustomerID   392692 non-null  int64         
     7   Country      392692 non-null  object        
     8   TotalPrice   392692 non-null  float64       
    dtypes: datetime64[ns](1), float64(2), int64(2), object(4)
    memory usage: 30.0+ MB



```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Quantity</th>
      <th>UnitPrice</th>
      <th>CustomerID</th>
      <th>TotalPrice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>392692.000000</td>
      <td>392692.000000</td>
      <td>392692.000000</td>
      <td>392692.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>13.119702</td>
      <td>3.125914</td>
      <td>15287.843865</td>
      <td>22.631500</td>
    </tr>
    <tr>
      <th>std</th>
      <td>180.492832</td>
      <td>22.241836</td>
      <td>1713.539549</td>
      <td>311.099224</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>0.001000</td>
      <td>12346.000000</td>
      <td>0.001000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.000000</td>
      <td>1.250000</td>
      <td>13955.000000</td>
      <td>4.950000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>6.000000</td>
      <td>1.950000</td>
      <td>15150.000000</td>
      <td>12.450000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>12.000000</td>
      <td>3.750000</td>
      <td>16791.000000</td>
      <td>19.800000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>80995.000000</td>
      <td>8142.750000</td>
      <td>18287.000000</td>
      <td>168469.600000</td>
    </tr>
  </tbody>
</table>
</div>




```python
total_revenue = df['TotalPrice'].sum()
average_order_value = df['TotalPrice'].mean()

print("Total Revenue:", total_revenue)
print("Average Transaction Value:", average_order_value)
```

    Total Revenue: 8887208.894
    Average Transaction Value: 22.631499735169474



```python
df['YearMonth'] = df['InvoiceDate'].dt.to_period('M')
df['Month'] = df['InvoiceDate'].dt.month
df['DayOfWeek'] = df['InvoiceDate'].dt.day_name()
```


```python
monthly_sales = df.groupby('YearMonth')['TotalPrice'].sum()

monthly_sales.plot()
plt.title("Monthly Sales Trend")
plt.xlabel("Month")
plt.ylabel("Revenue")
plt.xticks(rotation=45)
plt.show()
```


![png](output_27_0.png)



```python
daily_sales = df.groupby('DayOfWeek')['TotalPrice'].sum()

daily_sales = daily_sales.reindex([
    'Monday','Tuesday','Wednesday','Thursday',
    'Friday','Saturday','Sunday'
])

daily_sales.plot(kind='bar')
plt.title("Sales by Day of Week")
plt.show()
```


![png](output_28_0.png)



```python
top_products = df.groupby('Description')['Quantity'].sum().sort_values(ascending=False).head(10)

top_products.plot(kind='bar')
plt.title("Top 10 Products by Quantity Sold")
plt.show()
```


![png](output_29_0.png)



```python
top_revenue_products = df.groupby('Description')['TotalPrice'].sum().sort_values(ascending=False).head(10)

top_revenue_products.plot(kind='bar')
plt.title("Top 10 Products by Revenue")
plt.show()
```


![png](output_30_0.png)



```python
country_sales = df.groupby('Country')['TotalPrice'].sum().sort_values(ascending=False)

country_sales.head(10).plot(kind='bar')
plt.title("Top 10 Countries by Revenue")
plt.show()
```


![png](output_31_0.png)



```python
top_customers = df.groupby('CustomerID')['TotalPrice'].sum().sort_values(ascending=False).head(10)

top_customers.plot(kind='bar')
plt.title("Top 10 Customers by Revenue")
plt.show()
```


![png](output_32_0.png)



```python
sns.boxplot(x=df['TotalPrice'])
plt.title("Revenue Distribution")
plt.show()
```


![png](output_33_0.png)

