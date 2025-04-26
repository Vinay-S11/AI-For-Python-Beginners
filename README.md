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

## Lesson 1: Using Files in Python

### Overview
In this lesson, you will learn how to read files using Python. You will begin by working with data that has already been stored in files. This includes opening and reading text files using Python, which will be the main focus of the lesson.

To start, load the necessary functions used in the notebook:

```python
from helper_functions import get_llm_response
from IPython.display import display, Markdown
```

### Code Walkthrough

#### 1. Opening a Text File and Saving it as a String

```python
f = open("email.txt", "r")
email = f.read()
f.close()
print(email)
```
#### 2. Using LLMs to Extract Bullet Points from the Email

```python
prompt = f"""Extract bullet points from the following email. 
Include the sender information. 

Email:
{email}"""
bullet_points = get_llm_response(prompt)
print(bullet_points)

display(Markdown(bullet_points))
```


## Lesson 2: Loading and Using Your Own Data

### Overview
In this lesson, you will work with your own .txt files. You will learn how to upload text files to the notebook, load them, and use LLMs to summarize the content.

To start, load the necessary functions used in the notebook:

```python
from helper_functions import upload_txt_file, list_files_in_directory, print_llm_response
```

#### 1. Reading Files in the Working Directory
To access data you have stored in files and folders on your computer, you need to tell Python where to find them.
Python can access files in the directory where your Jupyter notebook is located. Use the following code to list the files in the working directory:

```python
list_files_in_directory()
```

#### Example:

```python
f = open("email.txt", "r")
email = f.read()
f.close()
print(email)
```

```python
f = open("recipe.txt", "r")
recipe = f.read()
f.close()
print(recipe)
```

#### 2. Uploading and Reading Your Own Text Files

Upload your text file
```python
upload_txt_file()
```
List the files in current working directory
```python
list_files_in_directory()
```
Then add your file in the code
```python
f = open("your_file.txt", "r")
your_file_content = f.read()
f.close()
print(your_file_content)
```

#### 3. Using AI to Summarize File Contents
Now, you will summarize the contents of your file using an LLM. The prompt is created to ask the LLM to summarize the file in at most two sentences:

```python
prompt = f"""Summarize the content from the following text
in at most two sentences. 

Text:
{your_file_content}"""
print(prompt)
print_llm_response(prompt)
```

## Lesson 3: Reading Journals from Food Critics

### Overview
In this lesson, you will learn how to use AI to determine whether a text file is relevant to food and restaurants. You'll work with journal entries from food critics and use LLMs to classify them based on their content.

#### 1. Working with Text Data
You will open and read journal entries about food and restaurants. First, load the journal from Cape Town:

```python
f = open("cape_town.txt", "r")
journal_cape_town = f.read()
f.close()
print(journal_cape_town)
```
Next, open the Tokyo journal and print its contents:

```python
f = open("tokyo.txt", "r")
journal_tokyo = f.read()
f.close()
print(journal_tokyo)
```

#### 2. Determining if Text Files are Relevant Using LLMs
You will now ask an LLM to determine if a journal entry is relevant to food and restaurants. For example, to check the Tokyo journal, you will define the following prompt:

```python
prompt = f"""Respond with "Relevant" or "Not relevant": 
the journal describes restaurants and their specialties. 

Journal:
{journal_tokyo}"""
print_llm_response(prompt)
```

#### 3. Checking All Files Using a For Loop
You can iterate over multiple journal files using a for loop. The code below checks if each journal is relevant:

```python
files = ["cape_town.txt", "madrid.txt", "rio_de_janeiro.txt", "sydney.txt", "tokyo.txt"]

for file in files:
    f = open(file, "r")
    journal = f.read()
    f.close()

    prompt = f"""Respond with "Relevant" or "Not relevant": 
    the journal describes restaurants and their specialties. 

    Journal:
    {journal}"""

    print(f"{file} -> {get_llm_response(prompt)}")
```

#### 4. Investigating an Irrelevant File
If any journal is flagged as "Not relevant," you can print its contents to investigate why:

```python
f = open("madrid.txt", "r")
print(f.read())
f.close()
```

## Lesson 4: Extracting restaurant information from journal entries

### Overview
In this lesson, you'll use an LLM to extract specific information from a text file - in this case restaurant names and signature dishes.

#### 1. Using AI to highlight important information

Import helper functions:

```python
from helper_functions import *
from IPython.display import display, HTML
```

Load the journal entry:

```python
journal_rio_de_janeiro = read_journal("rio_de_janeiro.txt")
```

Write and print the prompt:

```python
prompt = f"""
Given the following journal entry from a food critic, identify the restaurants and their best dishes.
Highlight and bold each restaurant (in orange) and best dish (in blue) within the original text. 
Provide the output as HTML suitable for display in a Jupyter notebook. 
Journal entry:
{journal_rio_de_janeiro}
"""
print(prompt)
```

Pass the prompt to an LLM:

```python
html_response = get_llm_response(prompt)
print(html_response)
display(HTML(html_response))
```

Try the same for Tokyo:

```python
journal_tokyo = read_journal("tokyo.txt")

prompt = f"""
Given the following journal entry from a food critic, identify the restaurants and their best dishes.
Highlight and bold each restaurant (in orange) and best dish (in blue) within the original text. 
Provide the output as HTML suitable for display in a Jupyter notebook. 
Journal entry:
{journal_tokyo}
"""

html_response = get_llm_response(prompt)
display(HTML(html_response))
```

#### 2. Extracting Restaurants and Best Dishes

Modify the prompt to list out data instead of highlighting:

```python
prompt = f"""Please extract a comprehensive list of the restaurants 
and their respective best dishes mentioned in the following journal entry. 
Ensure that each restaurant name is accurately identified and listed. 
Provide your answer in CSV format, ready to save. 
Exclude the "csv" declaration, don't add spaces after the comma, include column headers.

Format:
Restaurant,Dish
Res_1,Dsh_1
...

Journal entry:
{journal_rio_de_janeiro}
"""
restaurants_csv_ready_string = get_llm_response(prompt)
print(restaurants_csv_ready_string)
```

#### 3. Looping through multiple journals

```python
files = ["cape_town.txt", "istanbul.txt", "new_york.txt", "paris.txt", 
         "rio_de_janeiro.txt", "sydney.txt", "tokyo.txt"]

for file in files:
    journal_entry = read_journal(file)

    prompt = f"""Please extract a comprehensive list of the restaurants 
    and their respective best dishes mentioned in the following journal entry. 
    Ensure that each restaurant name is accurately identified and listed. 
    Provide your answer in CSV format, ready to save.
    Exclude the "csv" declaration, don't add spaces after the comma, include column headers.

    Format:
    Restaurant,Dish
    Res_1,Dsh_1
    ...

    Journal entry:
    {journal_entry}
    """
    
    print(file)
    print_llm_response(prompt)
    print("")
```

#### 4. Writing Files

```python
display(HTML(html_response))

f = open("highlighted_text.html", 'w')
f.write(html_response)
f.close()
```

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





