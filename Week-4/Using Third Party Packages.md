## 📊 Lesson 3: Unlocking Data Magic with Third-Party Packages

Python’s third-party libraries make it extremely powerful for data handling and visualization.

🔹 Working with pandas:
  - Install pandas if needed:

```python
pip install panda
```

Import and use it:
```python
import pandas as pd

# Load CSV data
data = pd.read_csv('car_data.csv')

# Display first 5 rows
print(data.head())

# Filter data where Price >= 10000
print(data[data["Price"] >= 10000])

# Median price of cars from 2015
print(data[data["Year"] == 2015]["Price"].median())
```

  - read_csv() loads data from a CSV file.
  - head() shows a quick view of your data.
  - Filtering and aggregating data becomes super easy.

🔹 Working with matplotlib:

Install matplotlib:
```python
pip install matplotlib
```

Example usage:
```python
import matplotlib.pyplot as plt

years = [2010, 2011, 2012, 2013, 2014]
prices = [5000, 7000, 8000, 8500, 9000]

plt.plot(years, prices)
plt.title('Car Prices Over Years')
plt.xlabel('Year')
plt.ylabel('Price')
plt.show()
```

  - plot() creates a line chart.
  - title(), xlabel(), ylabel() make the chart readable.
  - show() displays the plot window.

✅ Summary:
  - pandas → Load, filter, and analyze data easily.
  - matplotlib → Create beautiful charts and graphs.
  - Essential tools for Data Science, Analytics, and Machine Learning.
