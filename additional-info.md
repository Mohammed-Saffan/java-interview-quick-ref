## Difference between **Comparable** and **Comparator**.

---

### 🔍 First, what's the problem we're solving?

Java can’t sort custom objects (like `Student`, `Book`, etc.) by itself — you have to **tell it how to compare** those objects.

There are two main ways to do that:

* `Comparable` (built-in or “natural” order)
* `Comparator` (custom order)

---

## 🥇 Comparable

**Use when:** You want the class to define its *own* default sort order.

### ✅ Key points:

| Comparable             | Details                  |
| ---------------------- | ------------------------ |
| Purpose                | Natural/default ordering |
| Method                 | `compareTo(T o)`         |
| Where it's implemented | Inside the class itself  |
| Interface name         | `Comparable<T>`          |

---

### 🧱 Example:

```java
class Student implements Comparable<Student> {
    int id;
    String name;

    public Student(int id, String name) {
        this.id = id;
        this.name = name;
    }

    // Default sorting by ID
    public int compareTo(Student other) {
        return this.id - other.id;
    }
}
```

Now you can sort a `List<Student>` like this:

```java
Collections.sort(studentList);
```

✅ No need to pass any extra Comparator — Java knows how to compare by `id`.

---

## 🥈 Comparator

**Use when:** You want to define **multiple** or **custom** sorting rules — *without modifying the class*.

### ✅ Key points:

| Comparator      | Details               |
| --------------- | --------------------- |
| Purpose         | Custom ordering       |
| Method          | `compare(T o1, T o2)` |
| Where it's used | Passed as an argument |
| Interface name  | `Comparator<T>`       |

---

### 🧱 Example:

```java
class Student {
    int id;
    String name;

    public Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
}

// Custom Comparator to sort by name
class NameComparator implements Comparator<Student> {
    public int compare(Student a, Student b) {
        return a.name.compareTo(b.name);
    }
}
```

Usage:

```java
Collections.sort(studentList, new NameComparator());
```

✅ Now students are sorted by name instead of id.

---

## 🧠 Recap Table:

| Feature           | `Comparable`             | `Comparator`                                      |
| ----------------- | ------------------------ | ------------------------------------------------- |
| Sorting Type      | Natural ordering         | Custom ordering                                   |
| Method Name       | `compareTo()`            | `compare()`                                       |
| Method Parameters | `this.compareTo(other)`  | `compare(obj1, obj2)`                             |
| Where Used        | Implemented in the class | Passed as an argument to sort                     |
| Flexibility       | One way to sort          | Many ways to sort (you can make many comparators) |

---
## **fail-fast** vs **fail-safe** .

---

## 🔍 What's the problem we're solving?

You're looping over a collection (like `ArrayList`, `HashMap`, etc.), and **another thread (or even your own code)** tries to modify it at the same time.

This can cause weird bugs — so Java has **two types** of behaviors to handle this:

---

## 🟥 Fail-Fast

### 🔸 What it does:

* **Immediately throws `ConcurrentModificationException`** if the collection is modified *while you're iterating*

### 🔸 Why?

* To **alert you early** that the structure has been modified unsafely

### 🔸 Where it's used:

* **Non-thread-safe** collections:

  * `ArrayList`, `HashMap`, `HashSet`, etc.

### 🔸 Example:

```java
List<String> list = new ArrayList<>();
list.add("A");
list.add("B");

for (String s : list) {
    list.add("C"); // ❌ Modifying while iterating
}
```

🔺 This will throw:

```text
ConcurrentModificationException
```

### 🧠 Remember:

> **Fail-fast** = “I see a problem. I’ll FAIL NOW.”

---

## 🟩 Fail-Safe

### 🔸 What it does:

* **Avoids exceptions** during concurrent modifications
* Works on a **separate copy** of the collection

### 🔸 Why?

* To **allow safe iteration** even when other threads modify the structure

### 🔸 Where it's used:

* **Thread-safe / concurrent** collections:

  * `ConcurrentHashMap`, `CopyOnWriteArrayList`, etc.

### 🔸 Example:

```java
List<String> list = new CopyOnWriteArrayList<>();
list.add("A");
list.add("B");

for (String s : list) {
    list.add("C"); // ✅ Safe: creates a copy
}
```

🔹 No exception is thrown — but `"C"` might not be part of the loop.

---

## 🧠 Recap Table:

| Feature                     | Fail-Fast                                | Fail-Safe                                   |
| --------------------------- | ---------------------------------------- | ------------------------------------------- |
| Behavior on modification    | Throws `ConcurrentModificationException` | No exception thrown                         |
| Works in multithreaded env? | ❌ No                                     | ✅ Yes                                       |
| Underlying mechanism        | Monitors structural changes              | Works on a cloned copy                      |
| Examples                    | `ArrayList`, `HashMap`                   | `CopyOnWriteArrayList`, `ConcurrentHashMap` |

---
