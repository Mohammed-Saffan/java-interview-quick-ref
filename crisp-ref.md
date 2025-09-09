### 📝 QUICK REVISION NOTES — OOP in Java

**1. Encapsulation**

* Hide data via `private`
* Use getters/setters
* Protect internal state

**2. Abstraction**

* Hide implementation, expose interface
* Achieved via `abstract class` or `interface`

**3. Inheritance**

* Reuse code via `extends`
* IS-A relationship
* Java supports only single inheritance

**4. Polymorphism**

* **Compile-time:** Method overloading
* **Run-time:** Method overriding
* Enables flexible code

**5. Composition vs Inheritance**

* Composition (HAS-A) = better for flexibility
* Inheritance (IS-A) = reuse but tightly coupled

**6. Interface vs Abstract Class**

* Interface: multiple inheritance, behavior only
* Abstract class: shared structure + behavior

**7. Constructor Overloading**

* Multiple constructors for flexible object creation

**8. final Keyword**

* `final class/method/var` limits inheritance, overrides, reassignment

**9. Upcasting / Downcasting**

* Upcast = safe; Downcast = explicit, risky

**10. this vs super**

* `this`: current class; `super`: parent class

**11. Object Class Methods**

* Override `toString()`, `equals()`, `hashCode()` in real projects

**12. SOLID Principles** (Advanced)

* Clean, maintainable, scalable OOP design
Perfect. Here's your **📝 Quick Revision Notes — Java Exception Handling**:

---

### JAVA EXCEPTION HANDLING — CHEAT SHEET

**1. What is Exception Handling?**

* Mechanism to manage runtime errors
* Prevents crashes, aids debugging
* Core keywords: `try`, `catch`, `finally`, `throw`, `throws`

---

**2. Exception Types**

| Type      | Description             | Examples                                      |
| --------- | ----------------------- | --------------------------------------------- |
| Checked   | Checked at compile time | `IOException`, `SQLException`                 |
| Unchecked | Runtime exceptions      | `NullPointerException`, `ArithmeticException` |

* **Errors** (e.g., `OutOfMemoryError`) are not exceptions — JVM-level issues.

---

**3. Key Keywords**

* `try`: Wrap risky code
* `catch`: Handle exceptions
* `finally`: Always runs (cleanup, close streams, etc.)
* `throw`: Used to **throw** an exception
* `throws`: Used to **declare** exception in method signature

---

**4. throw vs throws**

| `throw`                       | `throws`                         |
| ----------------------------- | -------------------------------- |
| Inside method                 | In method signature              |
| Throws actual object          | Declares potential exceptions    |
| `throw new Exception("msg");` | `void method() throws Exception` |

---

**5. Custom Exception**

* Extend `Exception` or `RuntimeException`
* Use for **domain-specific error handling**

```java
class MyException extends Exception {
    public MyException(String msg) { super(msg); }
}
```

---

**6. Multi-catch (Java 7+)**

```java
catch (IOException | SQLException e) {
    // Handle both
}
```

---

**7. Best Practices**

* Catch **specific** exceptions first
* Don’t catch `Exception` unless absolutely necessary
* Use `finally` for cleanup
* Use **logging** in catch blocks
* Write custom exceptions for business logic clarity

---
Perfect — here's your **📝 Quick Revision Notes — Java Multithreading**:

---

### JAVA MULTITHREADING — CHEAT SHEET

**1. What is Multithreading?**

* Multiple threads run concurrently.
* Used for parallelism, responsiveness, and better CPU utilization.
* Threads share memory space; processes do not.

---

**2. Creating Threads**

| Approach              | How                           | Notes                     |
| --------------------- | ----------------------------- | ------------------------- |
| Extending Thread      | `class A extends Thread`      | Override `run()`          |
| Implementing Runnable | `class A implements Runnable` | Preferred (more flexible) |

* Start using: `new Thread(new A()).start();`
* **Don’t call `run()` directly.**

---

**3. Thread Lifecycle**

1. New
2. Runnable
3. Running
4. Blocked/Waiting
5. Terminated

---

**4. Thread Priorities**

* Range: 1 to 10 (`MIN_PRIORITY` to `MAX_PRIORITY`)
* Use `setPriority(int)`
* Not guaranteed by JVM (OS dependent)

---

**5. Synchronization**

* Prevents race conditions
* Use `synchronized` on methods/blocks
* Or use `ReentrantLock` from `java.util.concurrent.locks`

```java
synchronized void method() { ... }
```

---

**6. volatile Keyword**

* Ensures **visibility**, not atomicity
* Use when one thread modifies a shared flag or variable

```java
volatile boolean isRunning = true;
```

---

**7. Deadlock**

* Occurs when threads block each other forever
* Avoid by:

  * Lock ordering
  * Try-locks (`tryLock()`)
  * Timeouts

---

**8. Thread-safe Collections**

| Legacy               | Modern Alternatives    |
| -------------------- | ---------------------- |
| `Vector`             | `CopyOnWriteArrayList` |
| `Hashtable`          | `ConcurrentHashMap`    |
| `synchronizedList()` | Wrapper over ArrayList |

---

**9. Executor Framework (Java 5+)**

* Preferred for thread management
* Use `ExecutorService`, `Executors`

```java
ExecutorService pool = Executors.newFixedThreadPool(3);
pool.execute(new Task());
pool.shutdown();
```

---

**10. Best Practices**

* Use `Runnable` or `Callable`, not `Thread` directly
* Prefer **Executors** over manual threads
* Avoid shared mutable state
* Handle exceptions inside threads
---
###  JAVA COLLECTIONS FRAMEWORK — CHEAT SHEET

**1. What is it?**

* Framework of **interfaces + classes** to manage groups of objects
* Key interfaces: `List`, `Set`, `Queue`, `Map`
* Utility class: `Collections` (for sorting, synchronizing, etc.)

---

**2. Core Interfaces Hierarchy**

```
Collection
├── List        → ordered, duplicates allowed
├── Set         → unique elements, unordered
├── Queue       → FIFO structure
Map (separate)  → key-value pairs, no duplicates in keys
```

---

**3. List Implementations**

| Class      | Ordered  | Duplicates | Thread-safe | Notes                         |
| ---------- | -------- | ---------- | ----------- | ----------------------------- |
| ArrayList  | ✅        | ✅          | ❌           | Fast access, slow insertions  |
| LinkedList | ✅        | ✅          | ❌           | Good for insert/delete        |
| Vector     | ✅        | ✅          | ✅ (legacy)  | Synchronized, rarely used now |
| Stack      | ✅ (LIFO) | ✅          | ✅ (legacy)  | Based on Vector               |

---

**4. Set Implementations**

| Class         | Ordered       | Nulls      | Unique Only | Notes                        |
| ------------- | ------------- | ---------- | ----------- | ---------------------------- |
| HashSet       | ❌             | ✅ (1 null) | ✅           | Backed by HashMap            |
| LinkedHashSet | ✅ (insertion) | ✅ (1 null) | ✅           | Maintains order              |
| TreeSet       | ✅ (sorted)    | ❌          | ✅           | Uses natural or custom order |

---

**5. Map Implementations**

| Class             | Ordered?        | Nulls                        | Thread-safe? |
| ----------------- | --------------- | ---------------------------- | ------------ |
| HashMap           | ❌               | ✅ 1 null key, many null vals | ❌            |
| LinkedHashMap     | ✅ (insertion)   | 1 null key                    | ❌            |
| TreeMap           | ✅ (sorted keys) | ❌                            | ❌            |
| Hashtable         | ❌ (legacy)      | ❌                            | ✅            |
| ConcurrentHashMap | ❌               | ❌                            | ✅ (modern)   |

---

**6. Queue Implementations**

* `PriorityQueue`: Orders elements by natural/comparator priority
* `ArrayDeque`: Fast double-ended queue
* `LinkedList`: Implements Queue and Deque

---

**7. Comparable vs Comparator**

| Trait      | Comparable                         | Comparator                  |
| ---------- | ---------------------------------- | --------------------------- |
| Method     | `compareTo()`                      | `compare()`                 |
| Defined in | Class itself                       | Separate class              |
| Usage      | Natural order (e.g., sort by name) | Custom order (e.g., by age) |

---

**8. Fail-fast vs Fail-safe**

| Fail-fast                                | Fail-safe                                       |
| ---------------------------------------- | ----------------------------------------------- |
| Throws `ConcurrentModificationException` | Works safely in multi-threaded env              |
| Ex: `ArrayList`, `HashMap`               | Ex: `ConcurrentHashMap`, `CopyOnWriteArrayList` |

---

**9. Thread-safe Collections**

* Legacy: `Vector`, `Hashtable`
* Wrapper: `Collections.synchronizedList()`
* Modern: `ConcurrentHashMap`, `CopyOnWriteArrayList`

---

**10. Utility Methods**

* `Collections.sort(list)`
* `Collections.reverse(list)`
* `Collections.synchronizedList(list)`
* `Collections.unmodifiableList(list)`
---

###  SPRING FRAMEWORK — CHEAT SHEET

**1. What is a Bean?**

* Object managed by Spring IoC container
* Created, initialized, and destroyed by Spring
* Defined via annotations (`@Component`, `@Service`, etc.) or XML
* Default scope: Singleton

---

**2. Inversion of Control (IoC)**

* Container controls creation & wiring of dependencies
* Promotes loose coupling
* Dependencies injected via constructor, setter, or field
* Example: Service class gets Repository injected by Spring instead of creating it

---

**3. Key Annotations**

| Annotation        | Purpose                                      |
| ----------------- | -------------------------------------------- |
| `@Component`      | Marks any Spring-managed bean                |
| `@Service`        | Marks service/business layer bean            |
| `@Repository`     | Marks DAO layer + translates exceptions      |
| `@Controller`     | Marks MVC web controller                     |
| `@RestController` | Controller + JSON response (`@ResponseBody`) |
| `@Autowired`      | Injects dependencies automatically           |
| `@Qualifier`      | Chooses among multiple beans                 |
| `@Configuration`  | Class with bean definitions                  |
| `@Bean`           | Defines a bean inside configuration class    |
| `@PostConstruct`  | Runs method after bean initialization        |
| `@PreDestroy`     | Runs method before bean destruction          |
| `@Transactional`  | Manages database transactions declaratively  |

---

**4. Spring Boot**

* Auto-configures apps, embedded server, starter dependencies
* Minimal boilerplate, fast setup

---

**5. Spring MVC**

* DispatcherServlet routes requests
* Use `@RequestMapping` and variants to map HTTP methods
* `@RestController` returns JSON by default

---

**6. Aspect-Oriented Programming (AOP)**

* Separates cross-cutting concerns (logging, transactions)
* Use `@Aspect`, `@Before`, `@After`, `@Around` annotations

---

**7. Transaction Management**

* Use `@Transactional` on service/DAO methods
* Manages commit/rollback automatically
