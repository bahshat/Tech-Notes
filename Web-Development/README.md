
---

## 🔌 API Design & Communication Notes

---

### 1. **REST (Representational State Transfer)**

#### ✅ Core Principles

* **Stateless**: Server doesn't store client session
* **Uniform Interface**: Standard HTTP methods (GET, POST, PUT, DELETE)
* **Resource-based**: Expose resources via URIs
* **Client-server separation**
* **Cacheable** responses

#### ✅ HTTP Methods

| Method | Purpose         |
| ------ | --------------- |
| GET    | Fetch resource  |
| POST   | Create new item |
| PUT    | Full update     |
| PATCH  | Partial update  |
| DELETE | Remove item     |

#### ✅ Status Codes

| Code | Meaning                           |
| ---- | --------------------------------- |
| 200  | OK                                |
| 201  | Created                           |
| 204  | No Content (success, no response) |
| 400  | Bad Request                       |
| 401  | Unauthorized                      |
| 403  | Forbidden                         |
| 404  | Not Found                         |
| 409  | Conflict                          |
| 500  | Internal Server Error             |

#### ✅ RESTful Best Practices

* Use nouns for resource paths (`/users`, not `/getUser`)
* Use plural (`/orders`, `/products`)
* Versioning: `/api/v1/...`
* Return proper HTTP status codes
* Use pagination and filtering:

  ```
  GET /products?page=2&limit=20
  ```

---

### 2. **WebSockets**

#### ✅ What is WebSocket?

* Full-duplex, bidirectional communication channel over a single TCP connection.
* Persistent connection → real-time updates (e.g., chat, logs, dashboard).

#### ✅ Use Cases:

* Chat applications
* Live logs/notifications
* Real-time dashboards
* Multiplayer games

#### ✅ Basic Concept

* Starts as HTTP → upgrades to WebSocket
* Maintains open socket for sending/receiving data without re-requesting

#### ✅ Python WebSocket Server Example (with `websockets`)

```python
import asyncio
import websockets

async def echo(ws, path):
    async for msg in ws:
        await ws.send(f"You said: {msg}")

start_server = websockets.serve(echo, "localhost", 8765)
```

#### ✅ Flask WebSocket: `flask-socketio`

```python
from flask_socketio import SocketIO, emit

socketio = SocketIO(app)

@socketio.on('message')
def handle_message(data):
    emit('reply', f"Got: {data}")
```

---

### 3. **GraphQL (vs REST)**

| Feature       | REST               | GraphQL                  |
| ------------- | ------------------ | ------------------------ |
| Data Fetching | Multiple endpoints | Single endpoint          |
| Overfetching  | Common             | Avoided (client-defined) |
| Versioning    | Needed             | Usually not needed       |
| Type System   | No                 | Strongly typed schema    |

#### ✅ Example Query

```graphql
query {
  user(id: "1") {
    name
    posts {
      title
    }
  }
}
```

#### ✅ Tools:

* `graphene` for Python
* `Apollo Client` for frontend

---

### 4. **WSGI vs ASGI**

| Feature     | WSGI                        | ASGI                     |
| ----------- | --------------------------- | ------------------------ |
| Protocol    | Synchronous HTTP            | Async (HTTP + WebSocket) |
| Performance | Blocking                    | Non-blocking             |
| Used By     | Django (traditional), Flask | FastAPI, Django (3.0+)   |

#### ✅ WSGI (Web Server Gateway Interface)

* Standard for Python web servers
* Used by Flask, Django with Gunicorn/UWSGI

#### ✅ ASGI (Asynchronous Server Gateway Interface)

* Supports async I/O and WebSockets
* Required for FastAPI, Django Channels

#### ✅ Uvicorn (ASGI server) vs Gunicorn (WSGI server)

---

### 5. **API Security Essentials**

* Use HTTPS
* Token-based auth (JWT, OAuth2)
* Rate limiting (e.g., `X-RateLimit-Remaining`)
* CORS headers (`Access-Control-Allow-Origin`)
* Input validation and sanitization

---

### 6. **Interview Questions**

* What are the REST principles?
* How does WebSocket differ from HTTP?
* When would you prefer GraphQL over REST?
* What are WSGI and ASGI?
* How would you handle authentication in a REST API?
* What’s the role of status codes in API responses?

---
