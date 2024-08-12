Cross-Origin Resource Sharing (CORS) is a security feature implemented by web browsers to prevent web pages from making requests to a different domain than the one that served the web page. This is a crucial part of web security, known as the "same-origin policy," which restricts how resources on a web page can interact with resources from another domain.

Here’s a breakdown of what CORS is and how it works:

### Key Concepts

1. **Same-Origin Policy**: This is a fundamental security measure implemented by browsers that restricts how a web page can interact with resources from a different origin (domain, protocol, or port). For example, a web page loaded from `https://example.com` cannot make requests to `https://anotherdomain.com` unless explicitly allowed.

2. **CORS**: CORS is a mechanism that allows servers to specify who can access their resources and how. It uses HTTP headers to tell the browser whether the resource can be shared with the requesting origin.

### How CORS Works

1. **Preflight Request**: For certain types of requests (like those using methods other than GET or POST, or with custom headers), the browser sends an initial `OPTIONS` request to the server. This is known as a "preflight" request. The server must respond with appropriate CORS headers to indicate whether the actual request is allowed.

2. **CORS Headers**: The server responds with specific headers that control access:
   - `Access-Control-Allow-Origin`: Specifies which origins are allowed to access the resource. It can be a specific origin or `*` to allow all origins.
   - `Access-Control-Allow-Methods`: Specifies the HTTP methods (GET, POST, etc.) allowed when accessing the resource.
   - `Access-Control-Allow-Headers`: Lists the headers that can be used in the actual request.
   - `Access-Control-Allow-Credentials`: Indicates whether credentials (such as cookies) can be included with the request.
   - `Access-Control-Max-Age`: Defines the time for which the results of a preflight request can be cached.

### Example

If your web application on `https://example.com` needs to make a request to `https://api.example.com`, the server at `https://api.example.com` must include the appropriate CORS headers to allow the request from `https://example.com`.

**Server Response Example:**
```http
HTTP/1.1 200 OK
Access-Control-Allow-Origin: https://example.com
Access-Control-Allow-Methods: GET, POST
Access-Control-Allow-Headers: Content-Type
```

### Why CORS is Important

CORS helps to secure web applications by preventing malicious websites from making unauthorized requests to your server. It allows you to control which domains can access your resources, thereby mitigating risks associated with cross-origin attacks.

In summary, CORS is essential for web security, enabling servers to manage access control while allowing legitimate cross-origin requests.