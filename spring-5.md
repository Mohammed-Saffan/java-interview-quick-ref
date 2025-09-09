#### 1. **What is Spring Framework?**

* A **lightweight**, **open-source** Java framework.
* Simplifies enterprise application development.
* Supports **Dependency Injection (DI)**, **Aspect-Oriented Programming (AOP)**, **transaction management**, and more.
* Promotes **loose coupling** and easier testing.

---

#### 2. **Core Modules**

* **Spring Core:** Dependency Injection container
* **Spring MVC:** Web framework for building RESTful apps
* **Spring Data:** Simplifies database access
* **Spring Security:** Authentication & Authorization
* **Spring Boot:** Opinionated framework for quick app setup

---

#### 3. **Dependency Injection (DI) / Inversion of Control (IoC)**

* Objects get their dependencies **injected** by the container rather than creating them directly.
* Benefits: Loose coupling, easier testing, better modularity.

Types of DI:

* **Constructor Injection**
* **Setter Injection**
* **Field Injection** (less preferred)

---

#### 4. **Bean Lifecycle**

* Beans are managed by Spring container.
* Lifecycle phases: Instantiate → Populate properties → Initialize → Destroy.
* Can use annotations like `@PostConstruct` and `@PreDestroy`.

---

#### 5. **Annotations to Know**

* `@Component`: Marks a class as a Spring-managed bean
* `@Service`: For service layer beans (specialized Component)
* `@Repository`: For DAO layer (adds exception translation)
* `@Controller` / `@RestController`: For MVC controllers
* `@Autowired`: For automatic dependency injection
* `@Qualifier`: To specify which bean to inject if multiple candidates
* `@Configuration`: Marks a class as a source of bean definitions
* `@Bean`: Declares a bean within a `@Configuration` class

---

#### 6. **Spring Boot**

* Simplifies Spring app setup with auto-configuration, starter dependencies.
* Embedded server (Tomcat, Jetty).
* Reduces boilerplate configs.

---

#### 7. **Spring MVC Basics**

* **DispatcherServlet** is the front controller.
* Handles HTTP requests and maps them to controller methods.
* Uses `@RequestMapping` / `@GetMapping`, `@PostMapping` annotations.
* Supports RESTful web services (`@RestController` returns JSON by default).

---

#### 8. **Aspect-Oriented Programming (AOP)**

* Separates cross-cutting concerns (e.g., logging, transactions).
* Core concepts: Aspect, Advice, Join Point, Pointcut, Weaving.
* Implemented with `@Aspect` and `@Around`, `@Before`, `@After` annotations.

---

#### 9. **Transaction Management**

* Declarative transactions with `@Transactional` annotation.
* Manages commit/rollback automatically.

---

#### 10. **Spring Security (Brief)**

* Authentication and authorization framework.
* Uses filters and configurable providers.
* Supports OAuth, JWT, LDAP, etc.

---

### 1. **What is a Bean in Spring?**

* A **Bean** is an object that is **instantiated, assembled, and managed by the Spring IoC container**.
* Simply put, any object that Spring creates and manages during runtime is called a bean.
* Beans are the backbone of a Spring application — everything runs inside this container.

**Key points:**

* Defined in XML or annotated classes (`@Component`, `@Service`, etc.)
* Scope defaults to **singleton** (one instance per container) unless configured otherwise
* Lifecycle managed by Spring (creation, initialization, destruction)

---

### 2. **What is Inversion of Control (IoC)?**

* IoC means the **control of object creation and dependency management is inverted** — instead of the object creating dependencies itself, the container does it.
* This promotes **loose coupling** and easier testing.

**Simple Example Concept:**

Without IoC (manual):

```java
class Service {
    Repository repo = new Repository(); // tightly coupled
}
```

With IoC:

```java
class Service {
    private Repository repo;
    
    // Repo is injected by container
    public Service(Repository repo) {
        this.repo = repo;
    }
}
```

Here, the Spring container **injects the Repository** object into Service, so Service doesn’t create it itself.

---

### 3. **Most Asked Spring Annotations**

| Annotation        | Purpose                                                | Where Used                    |
| ----------------- | ------------------------------------------------------ | ----------------------------- |
| `@Component`      | Marks a class as a Spring bean                         | General-purpose beans         |
| `@Service`        | Marks service layer class                              | Business logic classes        |
| `@Repository`     | Marks DAO layer class + exception translation          | Data access layer             |
| `@Controller`     | Marks MVC controller                                   | Web controllers               |
| `@RestController` | Controller + `@ResponseBody` combo (for REST APIs)     | REST controllers              |
| `@Autowired`      | Injects dependency automatically                       | Fields, constructors, setters |
| `@Qualifier`      | Resolves bean ambiguity when multiple candidates exist | Along with `@Autowired`       |
| `@Configuration`  | Marks class as a source of bean definitions            | Configuration classes         |
| `@Bean`           | Defines a bean in a `@Configuration` class             | Methods creating beans        |
| `@PostConstruct`  | Runs method after bean initialization                  | Initialization steps          |
| `@PreDestroy`     | Runs method before bean destruction                    | Cleanup steps                 |
| `@Transactional`  | Manages transactions declaratively                     | Service or DAO methods        |
