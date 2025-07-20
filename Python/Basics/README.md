
---

## 🐍 Python Programming Interview Notes

---

### 1. **Python Language Essentials**

* **Interpreted, dynamically typed, high-level language**
* **Strong standard library**
* Used in: web dev, data science, scripting, automation, ML

---

### 2. **Key Language Features**

* **Indentation-based syntax**
* **Mutable vs Immutable**:

  * Immutable: `int`, `str`, `tuple`
  * Mutable: `list`, `dict`, `set`
* **Comprehensions**:

  ```python
  squares = [x**2 for x in range(10)]
  ```
* **Lambda Functions**:

  ```python
  add = lambda a, b: a + b
  ```
* **`zip`, `enumerate`**:

  ```python
  for i, val in enumerate(['a', 'b']): ...
  ```

---

### 3. **OOP Concepts in Python**

#### ✅ Classes and Objects

```python
class Dog:
    def __init__(self, name):
        self.name = name

    def speak(self):
        return f"{self.name} barks"
```

#### ✅ Inheritance

```python
class Puppy(Dog):
    def speak(self):
        return f"{self.name} yaps"
```

#### ✅ Important OOP Terms

| Term          | Description                       |
| ------------- | --------------------------------- |
| Inheritance   | Child class gets parent features  |
| Polymorphism  | Same method, different behavior   |
| Encapsulation | Hiding internal state via methods |
| Abstraction   | Hiding implementation details     |

#### ✅ MRO (Method Resolution Order)

* Determines method lookup order in multiple inheritance.

```python
print(Class.__mro__)
```

---

### 4. **Error Handling**

```python
try:
    # risky code
except ValueError as e:
    print(e)
else:
    print("No error")
finally:
    print("Always runs")
```

#### ✅ Custom Exceptions

```python
class CustomError(Exception):
    pass
```

---

### 5. **Decorators**

* Wrap a function to extend its behavior

```python
def my_decorator(fn):
    def wrapper():
        print("Before")
        fn()
        print("After")
    return wrapper

@my_decorator
def say_hi():
    print("Hi")
```

---

### 6. **Generators & Iterators**

* **Generators**: Use `yield`, memory efficient

```python
def counter():
    yield 1
    yield 2
```

* **Iterators**: Implement `__iter__` and `__next__`

---

### 7. **Typing and Type Hinting**

```python
def add(a: int, b: int) -> int:
    return a + b
```

* `Optional`, `List[str]`, `Dict[str, Any]` from `typing` module

---

### 8. **Common Built-in Functions**

* `map`, `filter`, `sorted`, `any`, `all`, `max`, `min`, `sum`, `reversed`

---

### 9. **Data Structures & Algorithms (DSA)**

| DS   | Operations                              |                  |
| ---- | --------------------------------------- | ---------------- |
| List | `append`, `pop`, slicing, comprehension |                  |
| Set  | Unique values, \`                       | & -\` operations |
| Dict | `get`, `items()`, `keys()`, `values()`  |                  |

#### ✅ Algorithms

* Searching: linear, binary
* Sorting: bubble, quicksort, mergesort
* Recursion, dynamic programming (basic idea)
* Big O Notation: Time & Space complexity

---

### 10. **Best Practices**

* Follow PEP8 (style guide)
* Use `venv` for environments
* Use `requirements.txt` or `pyproject.toml`
* Lint with `flake8`, format with `black`

---

### 11. **Interview Questions**

* Difference between `is` vs `==`
* How does Python manage memory?
* What are Python's scopes (LEGB rule)?
* What is a closure? What is a decorator?
* Explain shallow vs deep copy.
* Mutable default argument problem:

  ```python
  def f(a=[]): pass  # ❌
  ```

---
