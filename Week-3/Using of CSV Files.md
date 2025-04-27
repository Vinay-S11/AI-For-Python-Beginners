## Lesson 5: Vacation Planning Using CSV Files 🌍✈️

### ✨ Overview
In this lesson, you’ll create a vacation planner that reads destinations from a CSV file, uses AI to generate trip suggestions, and saves the results to a text file. By the end, you will know how to:
  - Load data from a CSV file.
  - Visualize structured data.
  - Generate AI-based trip activities.

📝 1. Loading Data from a CSV File
  - Import necessary modules:

```python
from helper_functions import get_llm_response, print_llm_response, display_table
from IPython.display import Markdown
import csv

f = open("itinerary.csv", 'r')
csv_reader = csv.DictReader(f)
itinerary = []
for row in csv_reader:
    print(row)
    itinerary.append(row)
f.close()
```
Check content:
```python
print(itinerary)
type(itinerary)
```
Access first item:
```python
print(itinerary[0])
print(itinerary[0]["Country"])
```

#### 📝 2. Structured Data Visualization
  - Display the entire itinerary as a table:

```python
display_table(itinerary)
```
Filter data by country (e.g., Japan):
```python
filtered_data = []

for trip_stop in itinerary:
    if trip_stop["Country"] == "Japan":
        filtered_data.append(trip_stop)

display_table(filtered_data)
```

#### 📝 3. Using AI to Suggest Trip Activities
  - Select a trip stop:

```python
trip_stop = itinerary[0]
print(trip_stop)

city = trip_stop["City"]
country = trip_stop["Country"]
arrival = trip_stop["Arrival"]
departure = trip_stop["Departure"]

prompt = f"""I will visit {city}, {country}, from {arrival} to {departure}. 
Please create a detailed daily itinerary."""

print(prompt)

response = get_llm_response(prompt)
display(Markdown(response))
```

### 🌟 Summary
  - Load and read data from CSV: Use Python’s csv module to load travel destinations and details from a CSV file.
  - Visualize structured data: Display the itinerary data in a clean and readable format using display_table.
  - Generate AI-based activities: Use AI to create a detailed daily itinerary based on the provided city, country, and travel dates.
  - Filter data: Filter and display data based on specific criteria, such as country.
