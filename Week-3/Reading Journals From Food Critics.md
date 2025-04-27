## 🍽️ Lesson 3: Reading Journals from Food Critics

## ✨ Overview
In this lesson, you'll explore how AI can classify journal entries from food critics, determining whether a text file is relevant to food and restaurant topics. You’ll work with journal entries, leverage Large Language Models (LLMs) to analyze their content, and classify them accordingly.

## 📝 1. Working with Text Data
First, we’ll load and read journal entries from different cities. Let's start by opening and printing the Cape Town journal:


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

#### 🤖 2. Determining Relevance Using LLMs
You will now ask an LLM to determine if a journal entry is relevant to food and restaurants. For example, to check the Tokyo journal, you will define the following prompt:

```python
prompt = f"""Respond with "Relevant" or "Not relevant": 
the journal describes restaurants and their specialties. 

Journal:
{journal_tokyo}"""
print_llm_response(prompt)
```

#### 🔄 3. Checking All Files Using a For Loop
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

#### 🔍 4. Investigating an Irrelevant File
If any journal is flagged as "Not relevant," you can print its contents to investigate why:

```python
f = open("madrid.txt", "r")
print(f.read())
f.close()
```

Summary
In this lesson, you learned how to analyze food-related journal entries using AI. By leveraging LLMs, you can automatically classify journal entries as relevant or not based on their content. We also explored how to automate the classification process for multiple files and investigate any flagged entries.
