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
