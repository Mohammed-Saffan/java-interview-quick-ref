### 🎯 INTERVIEW-STYLE BREAKDOWN: OOP CONCEPTS (Java-focused)

#### 1. **Encapsulation**

* Wrapping data + methods into a single unit (class).
* Access to fields controlled via getters/setters.
* **Access modifiers** (private, public, protected) are key here.
* **Why it's useful:** protects internal state, maintains control over data.

**Example:**
You make `balance` private in a `BankAccount` class and expose `deposit()` and `withdraw()` methods — users can’t mess with `balance` directly.

---

#### 2. **Abstraction**

* Hides **implementation details**, shows **essential features**.
* Achieved via **abstract classes** or **interfaces** in Java.
* **Focus:** What an object *does*, not *how* it does it.

**Example:**
You interact with `List` without caring whether it’s an `ArrayList` or `LinkedList`.

---

#### 3. **Inheritance**

* A class (child) inherits fields and methods from another (parent).
* Promotes **code reuse**.
* Java supports **single inheritance** only (one parent class).
* Use `super` to access parent properties/methods.

**Caution:**
Overusing inheritance = tight coupling. Prefer **composition** over inheritance when possible.

---

#### 4. **Polymorphism**

* **Compile-time (method overloading):** Same method name, different parameters.
* **Run-time (method overriding):** Subclass provides its own version of a method.
* Enables dynamic method dispatch via **method overriding + upcasting**.

**Example:**
`Animal a = new Dog(); a.speak();` — Java calls `Dog`'s version of `speak()` at runtime.

---

#### 5. **Composition vs Inheritance** (Tricky, often asked)

* **Composition:** HAS-A relationship. A class uses another class.
* **Inheritance:** IS-A relationship. A class extends another.
* **Interview Tip:** Favor composition for flexibility and loose coupling.

---

#### 6. **Interface vs Abstract Class** (Hot question!)

| Feature              | Interface                                          | Abstract Class              |
| -------------------- | -------------------------------------------------- | --------------------------- |
| Multiple inheritance | Yes                                                | No                          |
| Method types         | Only abstract (Java 7), + default/static (Java 8+) | Abstract + concrete         |
| Fields               | `public static final` only                         | Can have instance variables |
| Constructor          | No                                                 | Yes                         |

**When to use what?**

* Interface: unrelated classes with common behavior
* Abstract class: classes with shared code or base structure
---
#### 7. **Constructor Overloading**

* Multiple constructors with different parameter lists.
* Used to create flexible object instantiation.

#### 8. **Final Keyword in OOP**

* `final class` → cannot be extended
* `final method` → cannot be overridden
* `final variable` → acts as a constant

#### 9. **Downcasting and Upcasting**

* **Upcasting**: Child → Parent (safe)

  ```java
  Animal a = new Dog();
  ```
* **Downcasting**: Parent → Child (requires explicit cast, risky)

  ```java
  Dog d = (Dog) a;
  ```

#### 10. **this vs super**

* `this` → refers to current class instance
* `super` → refers to parent class

#### 11. **Object Class Methods** (Everyone forgets these!)

* `toString()`, `equals()`, `hashCode()`, `clone()`, `finalize()`
* Customizing `equals()` and `hashCode()` is vital for collections (e.g., HashMap keys)

#### 12. **SOLID Principles** *(More often in senior roles)*

* Even if not explicitly asked, sneak these in to show design thinking

  * **S**: Single Responsibility
  * **O**: Open/Closed
  * **L**: Liskov Substitution
  * **I**: Interface Segregation
  * **D**: Dependency Inversion
---
