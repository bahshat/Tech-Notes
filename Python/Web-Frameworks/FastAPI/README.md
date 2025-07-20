
---

## ⚡ FastAPI Interview Notes

---

### 1. **What is FastAPI?**

* Modern, high-performance web framework for building APIs with Python 3.6+.
* Based on **ASGI** (Asynchronous Server Gateway Interface).
* Automatic docs with **Swagger (OpenAPI)** and **ReDoc**.
* Built-in validation with **Pydantic**.

---

### 2. **Key Features**

| Feature              | Description                                           |
| -------------------- | ----------------------------------------------------- |
| ASGI                 | Enables async handling (better concurrency than WSGI) |
| Pydantic Models      | Data validation and type parsing                      |
| Auto Docs            | Swagger UI and ReDoc via `/docs` and `/redoc`         |
| Dependency Injection | Built-in for clean service-oriented design            |
| Async Support        | Full support for `async def` routes                   |

---

### 3. **Basic Example**

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello World"}
```

---

### 4. **Path & Query Parameters**

```python
@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    return {"item_id": item_id, "q": q}
```

---

### 5. **Request Body with Pydantic**

```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    age: int

@app.post("/users/")
def create_user(user: User):
    return user
```

---

### 6. **Validation with Pydantic**

```python
class Product(BaseModel):
    name: str
    price: float
    tags: list[str] = []
```

* Automatically rejects invalid types
* Optional fields, defaults, enums, nested models

---

### 7. **Dependency Injection**

```python
from fastapi import Depends

def get_db():
    return "db_connection"

@app.get("/items/")
def read_items(db=Depends(get_db)):
    return {"db": db}
```

---

### 8. **Status Codes, Responses**

```python
from fastapi import status, HTTPException

@app.get("/items/{id}", status_code=200)
def get_item(id: int):
    if id != 1:
        raise HTTPException(status_code=404, detail="Item not found")
    return {"id": id}
```

---

### 9. **Authentication (JWT Example)**

* Use `fastapi.security` for OAuth2, API key, JWT handling

```python
from fastapi.security import OAuth2PasswordBearer
oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

@app.get("/users/me")
def get_user(token: str = Depends(oauth2_scheme)):
    return {"token": token}
```

---

### 10. **Middleware**

```python
from fastapi import Request

@app.middleware("http")
async def add_process_time_header(request: Request, call_next):
    response = await call_next(request)
    response.headers["X-Time"] = "123ms"
    return response
```

---

### 11. **Async Support**

```python
@app.get("/async")
async def async_task():
    await some_async_function()
    return {"status": "done"}
```

---

### 12. **Documentation**

* Auto-generated at:

  * Swagger UI: `/docs`
  * ReDoc: `/redoc`

* Custom tags and summaries:

```python
@app.get("/users", tags=["Users"], summary="Get all users")
```

---

### 13. **Testing**

```python
from fastapi.testclient import TestClient

client = TestClient(app)

def test_home():
    res = client.get("/")
    assert res.status_code == 200
```

---

### 14. **Deployment**

* Run with **uvicorn** (ASGI server)

```bash
uvicorn app:app --reload
```

* Production setup:

  * Use with Nginx + Gunicorn + Uvicorn workers
  * Or Dockerized deployment

---

### 15. **Interview Questions**

* Why FastAPI over Flask?
* What is ASGI and how is it different from WSGI?
* How does FastAPI validate incoming data?
* What are Pydantic models?
* How is dependency injection implemented in FastAPI?
* Explain how async improves performance in FastAPI.

---
