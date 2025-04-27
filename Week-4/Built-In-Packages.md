## 🌟 Lesson 2: Exploring Python’s Built-in Power with Packages

Python provides many built-in modules so you don't have to write basic functionality from scratch.

🔹 Using the math Module:
```python
from math import sin, cos, pi, floor

print(sin(pi/2))  # 1.0
print(cos(pi))    # -1.0
print(floor(3.9)) # 3
```

sin(pi/2) → 1: Sine of 90 degrees.
cos(pi) → -1: Cosine of 180 degrees.
floor(3.9) → 3: Rounds down to nearest whole number.

🔹 Using the statistics Module:
```python
from statistics import mean, stdev

data = [10, 20, 30, 40, 50]
print(mean(data))   # 30
print(stdev(data))  # 15.811...
```

mean() calculates the average.
stdev() shows the spread of the data.

🔹 Using the random Module:
```python
from random import sample

spices = ["cumin", "turmeric", "oregano", "paprika"]
vegetables = ["lettuce", "tomato", "carrot", "broccoli"]
proteins = ["chicken", "tofu", "beef", "fish", "tempeh"]

random_spices = sample(spices, 2)
random_vegetables = sample(vegetables, 2)
random_protein = sample(proteins, 1)

print(random_protein)
```

🔹 Use an LLM to suggest a recipe for you using those 'randomly selected' ingredients.

Create a prompt that asks an LLM to create a recipe using your randomly selected ingredients:
```python
prompt = f"""Please suggest a recipe that includes the following ingredients.

Spices: {random_spices}
Vegetables: {random_vegetables}
Proteins: {random_protein}
"""
print(prompt)
```

Next, import the get_llm_response function from helper_functions.py to use to generate the recipe:
```python
from helper_functions import get_llm_response

recipe = get_llm_response(prompt)
print(recipe)
```


✅ Summary:
  - math → Advanced math operations (sin, cos, floor).
  - statistics → Easily calculate mean, stdev for data.
  - random → Add randomness to your program (like random selection).
