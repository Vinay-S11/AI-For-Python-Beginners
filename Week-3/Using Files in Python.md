# Lesson 1: Using Files in Python 📂🐍

---

## ✨ Overview

In this lesson, you will learn **how to open and read files** using Python.  
You'll work with **existing text files**, explore **basic file operations**, and utilize **LLMs (Large Language Models)** to process file contents.

By the end of this lesson, you will be able to:
- Open and read a text file.
- Save file contents into a string variable.
- Use an LLM to extract structured information from the file data.

---

## 🚀 Prerequisites

Make sure the following functions are available before starting:
```python
from helper_functions import get_llm_response
from IPython.display import display, Markdown
```

🛠️ Code Walkthrough
1. Opening a Text File and Saving it as a String

```python
f = open("email.txt", "r")
email = f.read()
f.close()
print(email)
```
🔵 Notes:
Always close the file after reading to free up system resources.
Alternatively, you can use a with open(...) block for automatic handling (shown later).

2. Using LLMs to Extract Bullet Points from the Email

```python
prompt = f"""Extract bullet points from the following email. 
Include the sender information. 

Email:
{email}"""
bullet_points = get_llm_response(prompt)
print(bullet_points)

display(Markdown(bullet_points))
```

🔥 Challenge for You:
  - Try creating your own email2.txt file.
  - Repeat the same process to read and extract bullet points.
  - Modify the prompt to extract summary instead of bullet points!

📚 Summary
  - Open files using open() or with open().
  - Always read the file before processing.
  - Use LLMs creatively to structure unorganized text into readable formats.
