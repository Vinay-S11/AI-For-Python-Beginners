## 🌟 Lesson 4: Installing Packages

### ✨ Overview:
In this lesson, you will install third-party Python packages using pip, import functions from the installed packages, and learn how to extract useful data from a webpage using BeautifulSoup.

Content:
#### 1. Installing Packages with pip

First, use pip to install external packages. For example:
For Jupyter Notebook
```python
!pip install bs4
```

For CLI
```python
pip install bs4
```

#### 2. Importing and Using Packages

After installation, import the package and start using its functions:
```python
from bs4 import BeautifulSoup
import requests
from helper_functions import * 
from IPython.display import HTML, display
```

#### 3. Fetching Data from the Web

Retrieve content from a website using requests:
```python
url = 'https://www.deeplearning.ai/the-batch/the-world-needs-more-intelligence/'
response = requests.get(url)
print(response)
```
Display the content using an HTML iframe:
```python
HTML(f'<iframe src={url} width="60%" height="400"></iframe>')
```

#### 4. Extracting and Combining Text with BeautifulSoup

Parse HTML and extract paragraphs:
```python
soup = BeautifulSoup(response.text, 'html.parser')
all_text = soup.find_all('p')
combined_text = ""
for text in all_text:
    combined_text = combined_text + "\n" + text.get_text()
print(combined_text)
```

#### 5. Using LLMs for Data Extraction

Pass the extracted text to an LLM (Large Language Model) for key bullet points:
```python
prompt = f"""Extract the key bullet points from the following text.

Text:
{combined_text}
"""
print_llm_response(prompt)
```

Summary:
  - In this lesson, you learned how to:
  - Install packages using pip
  - Import and use functions from third-party libraries
  - Extract and process data from a webpage using BeautifulSoup
  - Leverage LLMs to summarize extracted text
