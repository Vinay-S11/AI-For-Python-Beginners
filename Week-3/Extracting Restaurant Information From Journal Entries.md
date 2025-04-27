## Lesson 4: Extracting Restaurant Information from Journal Entries 🍽️📖

### ✨ Overview
In this lesson, you'll use Large Language Models (LLMs) to extract specific restaurant information from journal entries. Specifically, you’ll identify restaurant names and signature dishes, then highlight or list them for easy access.

📝 1. Using AI to Highlight Important Information

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

#### 📝 2. Extracting Restaurants and Best Dishes

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

#### 📝 3. Looping Through Multiple Journals

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

#### 📝 4. Writing Files

```python
display(HTML(html_response))

f = open("highlighted_text.html", 'w')
f.write(html_response)
f.close()
```

🌟 Summary
  - Highlight and extract restaurant data: Use LLMs to identify restaurants and their signature dishes in journal entries.
  - Display highlighted content: Output results as HTML for easy viewing in Jupyter Notebooks.
  - Extract and list data: Convert restaurant names and dishes into a CSV format for further use.
  - Loop through multiple files: Automate the extraction from multiple journals for scalability.
  - Save your results: Write the processed data into an HTML file for archiving or further processing.
