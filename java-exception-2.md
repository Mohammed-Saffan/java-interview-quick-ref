#### 1. **What is Exception Handling?**

* A mechanism to handle **runtime errors** in a controlled way.
* Prevents app crashes and helps with debugging and graceful failure.
* Java uses **try-catch-finally** blocks for this.

---

#### 2. **Types of Exceptions**

Java divides exceptions into two main categories:

| Type           | Checked Exceptions            | Unchecked Exceptions                                     |
| -------------- | ----------------------------- | -------------------------------------------------------- |
| Defined in     | `java.lang.Exception`         | `java.lang.RuntimeException`                             |
| Compiler check | ✅ Must handle/declare         | ❌ Optional to handle                                     |
| Examples       | `IOException`, `SQLException` | `NullPointerException`, `ArrayIndexOutOfBoundsException` |

**Interview Tip:**
Be ready to name a few of each and explain why one is checked and the other isn't.

---

#### 3. **Error vs Exception**

* **Exception** = can be handled
* **Error** = serious issue (JVM-related, like `OutOfMemoryError`), usually not handled by code

---

#### 4. **Try-Catch-Finally Syntax**

```java
try {
    // risky code
} catch (ExceptionType name) {
    // handling
} finally {
    // always runs (even if exception is thrown)
}
```

**finally block always executes**, even if an exception is not thrown or caught.

---

#### 5. **throw vs throws**

| Keyword  | Purpose                                | Used In          |
| -------- | -------------------------------------- | ---------------- |
| `throw`  | To **manually throw** an exception     | Inside method    |
| `throws` | To **declare** that method might throw | Method signature |

**Example:**

```java
void readFile() throws IOException {
    throw new IOException("File not found");
}
```

---

#### 6. **Custom Exceptions**

* Extend `Exception` or `RuntimeException`
* Use when app needs specific error logic

```java
class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}
```

---

#### 7. **Multi-catch block (Java 7+)**

You can catch multiple exceptions in one catch block:

```java
catch (IOException | SQLException e) {
    // handle both
}
```

---

#### 8. **Best Practices**

* Catch specific exceptions first
* Don’t swallow exceptions silently (don’t just `catch (Exception e) {}`)
* Use logging in catch blocks
* Prefer custom exceptions for domain logic

---
## `throw` vs `throws` in Java

| Keyword  | What it does                           | Where it's used             | Used for               |
| -------- | -------------------------------------- | --------------------------- | ---------------------- |
| `throw`  | Actually **throws** an exception       | **Inside** a method         | To trigger an error    |
| `throws` | **Declares** that a method might throw | **In** the method signature | For checked exceptions |

---

### 🎯 How to remember:

> 🔹 **`throw`** = "Do it"

> 🔹 **`throws`** = "Warn about it"

---

### 📌 Example to Remember

```java
// DECLARES the method might throw an exception
public void readFile() throws IOException {
    // Actually THROWS the exception
    throw new IOException("File not found");
}

// HANDLES the exception
public void processFile() {
    try {
        readFile();
    } catch (IOException e) {
        System.out.println("Handled: " + e.getMessage());
    }
}
```

---

### 🧠 Extra Tips:

* `throw` is followed by **one exception instance**
  e.g., `throw new IllegalArgumentException("Invalid input");`

* `throws` is followed by **one or more exception classes**
  e.g., `public void myMethod() throws IOException, SQLException`

* For **unchecked exceptions** (like `NullPointerException`, `ArithmeticException`):
  No need to use `throws` or `try-catch` (but you can if you want)

* For **checked exceptions** (like `IOException`, `FileNotFoundException`):
  You **must** use `throws` or `try-catch`
