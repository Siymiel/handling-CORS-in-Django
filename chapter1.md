# Django CORS Handling Documentation

To handle Cross-Origin Resource Sharing (CORS) in your Django application, you can use the `django-cors-headers` package. This package provides easy-to-use middleware for adding CORS headers to your Django views.

### Steps to Handle CORS in Django:

1. **Install the `django-cors-headers` package:**

   You can install it using pip:
   ```bash
   pip install django-cors-headers
   ```

2. **Add `corsheaders` to your `INSTALLED_APPS` in `settings.py`:**

   ```python
   INSTALLED_APPS = [
       ...
       'corsheaders',
       ...
   ]
   ```

3. **Add the CORS middleware to your `MIDDLEWARE` in `settings.py`:**

   The `corsheaders.middleware.CorsMiddleware` should be placed as high as possible, especially before any middleware that can generate responses, like `CommonMiddleware`.

   ```python
   MIDDLEWARE = [
       'corsheaders.middleware.CorsMiddleware',
       ...
   ]
   ```

4. **Configure CORS settings:**

   You can configure CORS settings in `settings.py` based on your requirements.

   - To allow requests from all origins:
     ```python
     CORS_ALLOW_ALL_ORIGINS = True
     ```

   - To allow requests from specific origins:
     ```python
     CORS_ALLOWED_ORIGINS = [
         "https://example.com",
         "https://another-example.com",
     ]
     ```

   - To allow CORS for specific HTTP methods:
     ```python
     CORS_ALLOW_METHODS = [
         "GET",
         "POST",
         "PUT",
         "DELETE",
         "OPTIONS",
     ]
     ```

   - To allow CORS for specific headers:
     ```python
     CORS_ALLOW_HEADERS = [
         "content-type",
         "authorization",
         ...
     ]
     ```

5. **Additional Configuration:**

   Depending on your use case, you might want to configure additional settings like:

   - `CORS_ALLOW_CREDENTIALS`: To allow cookies to be included in cross-origin requests.
   - `CORS_EXPOSE_HEADERS`: To expose specific headers to the browser.

   Example:
   ```python
   CORS_ALLOW_CREDENTIALS = True
   CORS_EXPOSE_HEADERS = ["Content-Disposition"]
   ```

### Example `settings.py` Configuration:
```python
INSTALLED_APPS = [
    ...
    'corsheaders',
    ...
]

MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware',
    ...
]

CORS_ALLOWED_ORIGINS = [
    "https://example.com",
    "https://another-example.com",
]

CORS_ALLOW_CREDENTIALS = True
CORS_ALLOW_METHODS = ["GET", "POST", "PUT", "DELETE", "OPTIONS"]
CORS_ALLOW_HEADERS = ["content-type", "authorization"]
```

This setup will enable CORS for your Django views, allowing requests from the specified origins, methods, and headers.