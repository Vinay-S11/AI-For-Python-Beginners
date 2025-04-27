# Lesson 2: Loading and Using Your Own Data 📂✍️

---

## ✨ Overview

In this lesson, you will learn how to **upload your own `.txt` files** into a Jupyter Notebook, **read** them using Python, and **summarize** their content using **LLMs** (Large Language Models).

By the end of this lesson, you will be able to:
- List files in your working directory.
- Upload and open your custom text files.
- Generate a short summary using AI tools.

---

## 🚀 Prerequisites

First, import the following helper functions:

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
🔥 Challenge for You
  - Upload two different .txt files.
  - Summarize each file in one sentence instead of two.
  - Modify the prompt: try asking for key points instead of a summary!

📚 Summary
  - You can list and upload files directly in your Jupyter environment.
  - Reading files is simple using open(), read(), and close().
  - Using LLMs, you can summarize, extract information, or even transform text data easily.
