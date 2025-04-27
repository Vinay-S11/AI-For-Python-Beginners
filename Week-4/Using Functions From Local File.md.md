## 🚀 Lesson 1: Importing and Using Functions from Local Files

### ✨ Overview
In real-world projects, writing all code in a single file becomes messy.
Instead, Python allows you to split your functions into separate .py files and import them wherever needed.

🔹 Creating and Importing Local Functions:

Suppose you have a file called helper_functions.py:
```python
def celsius_to_fahrenheit(celsius_temp):
    return (celsius_temp * 9/5) + 32

def print_llm_response(response):
    print(f"LLM Response: {response}")
```

You can import and use these functions in your main program:
```python
from helper_functions import celsius_to_fahrenheit, print_llm_response

temp_in_f = celsius_to_fahrenheit(25)
print(temp_in_f)  # Output: 77.0

print_llm_response("What is AI?") 
# Output: LLM Response: What is AI?
```

You can also import the whole file:
```python
import helper_functions

temp_in_f = helper_functions.celsius_to_fahrenheit(30)
helper_functions.print_llm_response("Define Robotics")
```

🔹 Different Import Styles:
  - import helper_functions (access functions with file name prefix)
  - from helper_functions import function_name (use function directly)
  - from helper_functions import * (import all functions — not recommended for large projects)

✅ Summary:
  - Split code into multiple files for better organization.
  - Use import to bring functions into your main script.
  - Prefer specific imports over import * for clarity.
  - Example: Import celsius_to_fahrenheit and use it to convert temperatures.
