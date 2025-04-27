# AI-For-Python-Beginners

## Week 3 - Working with Files in Python

---

## Table of Contents

1. Lesson 1: Using Files in Python
   - Opening a Text File and Saving it as a String
   - Using LLMs to Extract Bullet Points from the Email
     
2. Lesson 2: Loading and Using Your Own Data
   - Reading Files in the Working Directory
   - Uploading and Reading Your Own Text Files
   - Using AI to Summarize File Contents
     
3. Lesson 3: Reading Journals from Food Critics
   - Working with Text Data
   - Determining if Text Files are Relevant Using LLMs
   - Checking All Files Using a For Loop
   - Investigating an Irrelevant File
     
4. Lesson 4: Extracting Restaurant Information from Journal Entries
   - Using AI to Highlight Important Information
   - Extracting Restaurants and Best Dishes
   - Looping Through Multiple Journals
   - Writing Files

5. Lesson 5: Vacation Planning Using CSV Files
   - Loading Data from a CSV File
   - Structured Data Visualization
   - Using AI to Suggest Trip Activities

6. Lesson 6: Turning Code Blocks into Reusable Functions
   - Functions Used Previously
     
---

## Lesson 5: Vacation Planning Using CSV Files

### Overview
In this lesson, we build a vacation planner by reading destinations from a CSV file, using AI to generate trip suggestions, and saving the results into a text file.

#### 1. Loading data from a CSV file

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

#### 2. Structured Data Visualization

```python
display_table(itinerary)
```
Filter by country:
```python
filtered_data = []

for trip_stop in itinerary:
    if trip_stop["Country"] == "Japan":
        filtered_data.append(trip_stop)

display_table(filtered_data)
```

#### 3. Using AI to Suggest Trip Activities

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

## Lesson 6: Turning Code Blocks into Reusable Functions

### Overview
In this lesson, we learn how to fetch real-time flight prices using an API, send alerts for price drops, and automate flight monitoring.

Import helper function:
```python
from helper_functions import print_llm_response
from IPython.display import Markdown, display
```

#### Functions Used Previously:

print function:
```python
print("Hello World!")
```
len function:
```python
friends_list = ["Tommy", "Isabel", "Daniel", "Otto"]
len(friends_list)
```
Helper function:
```python
print_llm_response
```





