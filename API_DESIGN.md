#  API Design Best Practices Checklist 

---
<img width="816" height="1024" alt="image" src="https://github.com/user-attachments/assets/c255ba91-358b-40fd-b680-777a9fcd84de" />


---
A well-designed API feels invisible—it just works. Behind that simplicity lies a set of consistent design principles that make APIs predictable, secure, and scalable.

| Principle | Status |
| :--- | :--- |
| Use appropriate HTTP methods for CRUD | ✅ |
| Implement idempotency keys for POST/PATCH | ✅ |
| Name resources as **nouns** (plural) | ✅ |
| **Version** your API from day one | ✅ |
| Secure all endpoints with **JWT** / **HTTPS** | ✅ |
| Implement **pagination** for list endpoints | ✅ |
| Return consistent response formats | ✅ |
| Provide clear error messages | ✅ |
| Document your API thoroughly | ✅ |

-----

## 1\. Idempotency

An operation is **idempotent** if making the same request multiple times produces the same result without unintended side effects. This is critical for safe retries in unreliable network conditions.

### HTTP Method Idempotence

| Method | Idempotent | Operation |
| :--- | :---: | :--- |
| `GET` | **✅ Yes** | Safe, read-only |
| `HEAD` | **✅ Yes** | Safe, headers only |
| `PUT` | **✅ Yes** | Complete resource replacement |
| `DELETE` | **✅ Yes** | Resource removal |
| `POST` | **❌ No** | Resource creation (each call is new) |
| `PATCH` | **❌ No** | Partial resource update (state changes) |

### Implementing Idempotency Keys

For non-idempotent methods (`POST`, `PATCH`), clients should send a unique `Idempotency-Key` in the header.

> **Example Request (Payment Creation):**
>
> ```http
> POST /api/payments
> Idempotency-Key: 550e8400-e29b-41d4-a716-446655440000
> Content-Type: application/json
> ```

> {
> "amount": 100.00,
> "currency": "USD"
> }
>
> ```
> ```

  * **Server Logic:** The server checks the key. If it exists, it returns the stored response. If new, it processes the request and stores the key/response pair.

-----

## 2\. RESTful Resource Naming

Endpoints must focus on **nouns** (resources) and use HTTP methods to define the action.

| Operation | HTTP Method | Endpoint (Noun) | Description |
| :--- | :--- | :--- | :--- |
| Create | `POST` | `/api/products` | Create a new product |
| Read (Collection) | `GET` | `/api/products` | List all products |
| Read (Specific) | `GET` | `/api/products/{id}` | Get specific product |
| Replace | `PUT` | `/api/products/{id}` | Replace entire resource |
| Update (Partial) | `PATCH` | `/api/products/{id}` | Modify specific fields |
| Delete | `DELETE` | `/api/products/{id}` | Remove resource |

> **❌ Avoid Verb-based Endpoints:** `GET /api/getUsers`, `POST /api/createOrder`

-----

## 3\. Versioning

Versioning prevents breaking changes for existing clients when the API evolves.

  * **URL-based Versioning (Recommended):** The version number is explicit in the path.
      * `GET https://api.example.com/v1/users`
      * `GET https://api.example.com/v2/users`
  * **Query Parameter Versioning:** The version is passed as a query string.
      * `GET https://api.example.com/users?version=1`

-----

## 4\. Security

Security must be implemented for every endpoint.

  * **Protocol:** Always use **HTTPS** (TLS/SSL).
  * **Authentication:** Use **JSON Web Tokens (JWTs)** as **Bearer Tokens** in the `Authorization` header.

> **Authenticated Request Example:**
>
> ```http
> GET /api/orders?limit=3&offset=0
> Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
> ```

### JWT Structure

JWTs are composed of three parts, separated by dots:

1.  **Header:** Specifies the token type and signing algorithm.
2.  **Payload (Claims):** Contains the user data (claims), like ID, name, and permissions.
3.  **Signature:** Used by the server to verify the token's authenticity.

-----

## 5\. Pagination

Mandatory for endpoints returning large lists of data to ensure efficient and consistent responses.

### Offset-based Pagination (Common)

Uses `limit` (number of items) and `offset` (starting position).

  * **Example:** `GET /api/orders?limit=3&offset=0`

### Consistent Response Format

The response should include the data and descriptive pagination metadata.

```json
{
  "data": [
    {"id": 1, "name": "Order 1"},
    // ...
  ],
  "pagination": {
    "limit": 3,
    "offset": 0,
    "total": 150,
    "has_more": true
  }
}
```

-----

