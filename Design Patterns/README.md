
---

## 🧠 Design Patterns Interview Notes

---

### 1. **What are Design Patterns?**

* Reusable solutions to common software design problems.
* Improve code structure, maintainability, and scalability.
* Categories:

  * **Creational** (object creation)
  * **Structural** (object composition)
  * **Behavioral** (object interaction)

---

### 2. **Common Design Patterns in Python**

#### ✅ Singleton

Ensures a class has only one instance.

```python
class Singleton:
    _instance = None
    def __new__(cls):
        if not cls._instance:
            cls._instance = super().__new__(cls)
        return cls._instance
```

---

#### ✅ Factory Pattern

Creates objects without specifying the exact class.

```python
class Dog:
    def speak(self): return "Woof"

class Cat:
    def speak(self): return "Meow"

def animal_factory(animal="dog"):
    return Dog() if animal == "dog" else Cat()
```

---

#### ✅ Strategy Pattern

Encapsulates algorithms and makes them interchangeable.

```python
class Strategy:
    def execute(self, data): pass

class PrintUpper(Strategy):
    def execute(self, data): print(data.upper())

class PrintLower(Strategy):
    def execute(self, data): print(data.lower())

def run(strategy: Strategy, data: str):
    strategy.execute(data)
```

---

#### ✅ Decorator Pattern

Adds new behavior dynamically.

```python
def decorator(fn):
    def wrapper():
        print("Before")
        fn()
        print("After")
    return wrapper

@decorator
def greet():
    print("Hello")
```

---

#### ✅ Observer Pattern

Notify dependent objects of state changes.

```python
class Observer:
    def update(self, msg): print("Got:", msg)

class Subject:
    def __init__(self): self.subs = []
    def register(self, obs): self.subs.append(obs)
    def notify(self, msg):
        for obs in self.subs: obs.update(msg)
```

---

#### ✅ Adapter Pattern

Makes incompatible interfaces work together.

```python
class EuropeanPlug:
    def charge(self): return "220V"

class USAdapter:
    def __init__(self, euro): self.euro = euro
    def charge(self): return f"Adapted: {self.euro.charge()}"
```

---

### 3. **Architectural Patterns**

#### ✅ MVC (Model-View-Controller)

* **Model**: Manages data and logic
* **View**: UI representation
* **Controller**: User input logic

✅ Example: Django

* Model → Models
* View → Templates
* Controller → Views.py

---

#### ✅ MVVM (Model-View-ViewModel)

* Mostly used in frontend (e.g., Angular)
* ViewModel binds logic to the View using observers

---

#### ✅ Layered Architecture

* Typical backend structure:

  * **Controller** (routes)
  * **Service** (business logic)
  * **DAO/Repository** (DB interaction)
  * **Model** (data definition)

---

#### ✅ Microservices Patterns (brief overview)

| Pattern           | Purpose                        |
| ----------------- | ------------------------------ |
| API Gateway       | Entry point to services        |
| Circuit Breaker   | Prevent cascading failures     |
| Service Discovery | Dynamic service lookup         |
| Event Sourcing    | Track state changes via events |
| CQRS              | Separate read/write models     |

---

### 4. **Best Practices**

* Favor composition over inheritance
* Use design patterns only when needed
* Keep code testable and loosely coupled
* Follow SOLID principles

---

### 5. **Interview Questions**

* Explain Singleton. How do you ensure thread safety?
* How is Factory pattern useful in real-world apps?
* Difference between Decorator and Inheritance?
* Where have you used MVC in your projects?
* What is Dependency Injection?
* How do you design scalable architecture for a microservice?

---
