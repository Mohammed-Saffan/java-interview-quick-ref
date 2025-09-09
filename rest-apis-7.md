#### 1. **What is a REST API?**

* **REST (Representational State Transfer)** is an architectural style for designing networked applications.
* Uses standard HTTP methods (`GET`, `POST`, `PUT`, `DELETE`, etc.).
* Resources are identified by **URIs**.
* Stateless communication between client and server.

---

#### 2. **Key REST Principles**

* **Statelessness:** Each request from client contains all info needed.
* **Client-Server separation:** Client and server evolve independently.
* **Uniform Interface:** Standard HTTP methods and status codes.
* **Cacheable:** Responses can be cached to improve performance.
* **Layered System:** Architecture can have multiple layers (proxy, firewall).
* **Code on Demand (optional):** Server can send executable code.

---

#### 3. **HTTP Methods and their usage**

| Method | Use Case                             |
| ------ | ------------------------------------ |
| GET    | Retrieve resource(s)                 |
| POST   | Create new resource                  |
| PUT    | Update existing resource (or create) |
| PATCH  | Partial update of resource           |
| DELETE | Remove resource                      |

---

#### 4. **Status Codes You Must Know**

| Code | Meaning               |
| ---- | --------------------- |
| 200  | OK                    |
| 201  | Created               |
| 204  | No Content            |
| 400  | Bad Request           |
| 401  | Unauthorized          |
| 403  | Forbidden             |
| 404  | Not Found             |
| 500  | Internal Server Error |

---

#### 5. **REST in Spring Boot**

* Use `@RestController` for controllers that return JSON/XML.
* Map HTTP methods with `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`.
* Use `@RequestBody` to map request payload to Java objects.
* Use `@PathVariable` to extract data from the URL path.
* Use `@RequestParam` for query parameters.

---

#### 6. **Idempotency in REST**

* Methods like `GET`, `PUT`, `DELETE` should be **idempotent** (same effect no matter how many times called).
* `POST` is not idempotent (creates a new resource each time).

---

#### 7. **HATEOAS (Hypermedia as the Engine of Application State)**

* Advanced REST concept: Responses include links to related actions/resources.
* Helps clients navigate API dynamically.

---

#### 8. **REST vs SOAP**

* REST is lightweight, uses HTTP, and flexible.
* SOAP is protocol-heavy, uses XML, and has strict contracts.

---
