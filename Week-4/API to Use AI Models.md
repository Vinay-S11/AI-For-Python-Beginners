## ✨ Lesson 6: APIs to Use AI Models

### Overview:
In this lesson, you will interact with the OpenAI API to query a language model and learn how to fine-tune the behavior of the model through system messages and response settings.

Content:
#### 1. Importing Necessary Libraries
Import libraries to interact with OpenAI and manage environment variables:
```python
import os
from dotenv import load_dotenv
from openai import OpenAI
```

#### 2. Setting Up the OpenAI API Key
Access the OpenAI API key using dotenv:
```python
load_dotenv('.env', override=True)
openai_api_key = os.getenv('OPENAI_API_KEY')
client = OpenAI(api_key=openai_api_key)
```

#### 3 Defining the get_llm_response Function
This function queries the model with a user’s prompt and retrieves the response:
```python
def get_llm_response(prompt):
    completion = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[
            {"role": "system", "content": "You are a helpful AI assistant."},
            {"role": "user", "content": prompt},
        ],
        temperature=0.0,
    )
    response = completion.choices[0].message.content
    return response
```

#### 4. Querying the Model
Pass a simple prompt to the model and print the response:
```python
prompt = "What is the capital of France?"
response = get_llm_response(prompt)
print(response)
```

#### 5. Customizing System Behavior
You can change the assistant’s tone by adjusting the system message, such as making it sarcastic:
```python
def get_llm_response(prompt):
    completion = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[
            {"role": "system", "content": "You are a sarcastic AI assistant."},
            {"role": "user", "content": prompt},
        ],
        temperature=0.0,
    )
    response = completion.choices[0].message.content
    return response
```

#### 6. Adjusting Temperature for Creative Responses
Modify the temperature setting to generate more creative or random responses:
```python
def get_llm_response(prompt):
    completion = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[
            {"role": "system", "content": "You are a helpful AI assistant."},
            {"role": "user", "content": prompt},
        ],
        temperature=1.0,
    )
    response = completion.choices[0].message.content
    return response
```

Summary:
  - In this lesson, you learned how to:
  - Query the OpenAI API for model responses
  - Customize the model’s behavior using system messages
  - Vary the creativity of the responses by adjusting the temperature setting

