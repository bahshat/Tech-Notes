
---

## 🕸️ Django Interview Notes

---

### 1. **What is Django?**

* High-level Python web framework.
* Batteries-included: ORM, admin panel, auth, forms, middleware.
* Follows **MTV** architecture (Model-Template-View).

---

### 2. **MTV vs MVC**

| Term in MVC | Django Equivalent  |
| ----------- | ------------------ |
| Model       | Model              |
| View        | Template           |
| Controller  | View (logic layer) |

---

### 3. **Project Structure**

```text
myproject/
├── manage.py
├── myproject/          ← settings, URLs
├── app1/               ← models, views, urls
```

---

### 4. **Creating Project & App**

```bash
django-admin startproject myproject
cd myproject
python manage.py startapp blog
```

---

### 5. **Model Example**

```python
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField()
    published = models.BooleanField(default=False)
    created = models.DateTimeField(auto_now_add=True)
```

---

### 6. **Migrations**

```bash
python manage.py makemigrations
python manage.py migrate
```

---

### 7. **Views**

```python
from django.http import HttpResponse

def hello(request):
    return HttpResponse("Hello Django")
```

#### Class-based View (CBV)

```python
from django.views import View

class HelloView(View):
    def get(self, request):
        return HttpResponse("Hi")
```

---

### 8. **Templates**

```python
# views.py
return render(request, "hello.html", {"name": "Rais"})

# hello.html
<h1>Hello {{ name }}</h1>
```

---

### 9. **URLs**

```python
# app/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('hello/', views.hello),
]

# project/urls.py
path('', include('app.urls'))
```

---

### 10. **Admin Panel**

```python
# admin.py
from .models import Post
admin.site.register(Post)
```

```bash
python manage.py createsuperuser
```

---

### 11. **Forms & ModelForms**

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField()
    message = forms.CharField(widget=forms.Textarea)
```

---

### 12. **Django ORM Queries**

```python
Post.objects.all()
Post.objects.filter(published=True)
Post.objects.get(id=1)
Post.objects.create(title="New Post")
```

---

### 13. **Middlewares**

* Process request/response at global level

```python
# settings.py
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    ...
]
```

---

### 14. **REST API with Django**

Use **Django REST Framework (DRF)**

```bash
pip install djangorestframework
```

#### Serializer

```python
from rest_framework import serializers

class PostSerializer(serializers.ModelSerializer):
    class Meta:
        model = Post
        fields = '__all__'
```

#### ViewSet

```python
from rest_framework import viewsets

class PostViewSet(viewsets.ModelViewSet):
    queryset = Post.objects.all()
    serializer_class = PostSerializer
```

#### URLs

```python
from rest_framework.routers import DefaultRouter

router = DefaultRouter()
router.register(r'posts', PostViewSet)

urlpatterns += router.urls
```

---

### 15. **Deployment**

* Use `gunicorn` + `nginx`
* Collect static files:

```bash
python manage.py collectstatic
```

* Set `ALLOWED_HOSTS`, `DEBUG=False`, and configure `.env`

---

### 16. **Interview Questions**

* What is Django ORM and how does it work?
* Compare Django with Flask/FastAPI.
* How does Django handle security (e.g., CSRF, XSS)?
* What are signals in Django?
* Difference between `get()` and `filter()`?
* Explain middleware and context processors.
* What is a QuerySet and when is it evaluated?

---
