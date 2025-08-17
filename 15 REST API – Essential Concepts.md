## REST API – Essential Concepts 🚀

1️⃣ **Fundamentals of REST API**

REST (Representational State Transfer) – Architectural style for web services.
Statelessness – Each request is independent, no session stored on the server.
Client-Server Architecture – Separation of frontend and backend.
Cacheability – Responses can be cached for performance optimization.


2️⃣ **HTTP Methods (CRUD Operations)**

GET – Retrieve data (Read).
POST – Create new data (Create).
PUT – Update existing data (Update).
PATCH – Partially update data (Modify).
DELETE – Remove data (Delete).


3️⃣ **API Endpoints & URL Structure**

Resource Naming – Use plural nouns (/users, /orders).
Hierarchical Structure – Use nested URLs (/users/{id}/orders).
Query Parameters – Filter results (/products?category=electronics).
Path Parameters – Identify resources (/users/{id}).


4️⃣ **Request & Response Format**

JSON (JavaScript Object Notation) – Standard format for data exchange.
Headers – Define content type, authentication tokens.
Status Codes –
    - 200 OK – Success.
    - 201 Created – New resource created.
    - 400 Bad Request – Invalid request.
    - 401 Unauthorized – Authentication required.
    - 403 Forbidden – Access denied.
    - 404 Not Found – Resource doesn’t exist.
    - 500 Internal Server Error – Server-side issue.


5️⃣ **Authentication & Security**

API Keys – Unique keys to access API.
OAuth 2.0 – Secure authorization framework.
JWT (JSON Web Tokens) – Token-based authentication.
Rate Limiting – Prevent API abuse.
CORS (Cross-Origin Resource Sharing) – Control resource access.


6️⃣ **REST API Best Practices**

Use Proper HTTP Methods – Follow standard conventions.
Handle Errors Gracefully – Return meaningful error messages.
Pagination – Limit data returned (/users?page=1&limit=10).
Versioning – Manage API versions (/api/v1/users).
Idempotency – Ensure repeated requests yield the same results.


7️⃣ **Tools & Testing**

Postman – API testing and debugging.
Swagger (OpenAPI) – API documentation and visualization.
cURL – Command-line API testing.
