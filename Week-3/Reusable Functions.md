## Lesson 6: Turning Code Blocks into Reusable Functions 🔄💡

### ✨ Overview
In this lesson, you'll learn how to transform code blocks into reusable functions to streamline tasks such as fetching real-time flight prices using an API, sending alerts for price drops, and automating flight monitoring. By the end of the lesson, you’ll be able to:
  - Create reusable functions for common tasks.
  - Integrate API requests to fetch flight prices.
  - Automate price monitoring and send alerts.

📝 1. Importing Helper Functions
First, you'll need to import some helper functions and necessary libraries:
```python
from helper_functions import print_llm_response
from IPython.display import Markdown, display
```

#### 📝 2. Reusing Code with Functions
Next, let’s explore some code blocks you’ve already used and turn them into reusable functions.

Example: Basic Print Function

print function:
```python
def print_message(message):
    print(message)
```
Now you can reuse the function whenever you need to print a message:
```python
print_message("Hello, World!")
```
Example: Length Function for Lists
Instead of calling len() directly, you can define a function to get the length of a list:
len function:
```python
def get_list_length(my_list):
    return len(my_list)
```
And use it like this:
```python
friends_list = ["Tommy", "Isabel", "Daniel", "Otto"]
print(get_list_length(friends_list))
```
Example: Helper Function (LLM Response)
You’ve already used the print_llm_response function in your project. Let’s formalize it into a reusable helper function:
```python
def display_llm_response(prompt):
    response = print_llm_response(prompt)
    display(Markdown(response))
```
You can now call display_llm_response() with any prompt to display the response:
```python
prompt = "What's the weather like today?"
display_llm_response(prompt)
```

🌟 Summary
  - Transform code into functions: Learn how to convert common code blocks into reusable functions for efficiency.
