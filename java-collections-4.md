#### 1. **What is the Collections Framework?**

* Set of **interfaces + classes** to handle **groups of objects** (collections).
* Located in `java.util` package.
* Supports **List, Set, Queue, Map**, etc.
* Offers **algorithms**, **utilities**, and **thread-safe** variants.

---

#### 2. **Hierarchy Overview (Core Interfaces)**

```
Collection (root)
├── List      (ordered, duplicates allowed)
├── Set       (no duplicates)
│   └── SortedSet / NavigableSet
└── Queue     (FIFO)
Map (Not a Collection, but part of the framework)
```

---

#### 3. **List Interface**

| Implementation | Ordered? | Duplicates? | Random Access  | Thread-safe?       |
| -------------- | -------- | ----------- | -------------- | ------------------ |
| `ArrayList`    | ✅        | ✅           | ✅              | ❌ (but fast)       |
| `LinkedList`   | ✅        | ✅           | ❌ (uses nodes) | ❌                  |
| `Vector`       | ✅        | ✅           | ✅              | ✅ (legacy)         |
| `Stack`        | ✅ (LIFO) | ✅           | ✅              | ✅ (extends Vector) |

**Tip:** Prefer `ArrayList` unless you need frequent insertions/removals from the middle → then use `LinkedList`.

---

#### 4. **Set Interface**

| Implementation  | Ordered?            | Allows Null? | Thread-safe? | Unique elements? |
| --------------- | ------------------- | ------------ | ------------ | ---------------- |
| `HashSet`       | ❌ (unordered)       | ✅ (1 null)   | ❌            | ✅                |
| `LinkedHashSet` | ✅ (insertion order) | ✅ (1 null)   | ❌            | ✅                |
| `TreeSet`       | ✅ (sorted)          | ❌            | ❌            | ✅                |

---

#### 5. **Map Interface** *(NOT extending Collection)*

| Implementation      | Ordered?            | Null Keys/Values?          | Thread-safe? |
| ------------------- | ------------------- | -------------------------- | ------------ |
| `HashMap`           | ❌ (unordered)       | 1 null key, many null vals | ❌            |
| `LinkedHashMap`     | ✅ (insertion order) | 1 null key                 | ❌            |
| `TreeMap`           | ✅ (sorted keys)     | ❌                          | ❌            |
| `Hashtable`         | ❌ (legacy)          | ❌                          | ✅            |
| `ConcurrentHashMap` | ❌                   | ❌                          | ✅ (modern)   |

---

#### 6. **Queue Interface**

* FIFO behavior
* Use cases: task scheduling, messaging systems

| Implementation  | Description                 |
| --------------- | --------------------------- |
| `PriorityQueue` | Elements sorted by priority |
| `ArrayDeque`    | Double-ended queue (Deque)  |
| `LinkedList`    | Can also act as a queue     |

---

#### 7. **Comparable vs Comparator**

| Comparable           | Comparator         |
| -------------------- | ------------------ |
| Natural ordering     | Custom ordering    |
| `compareTo()` method | `compare()` method |
| Implemented in class | Passed as argument |

---

#### 8. **Fail-fast vs Fail-safe**

| Fail-fast                                | Fail-safe                                             |
| ---------------------------------------- | ----------------------------------------------------- |
| Throws `ConcurrentModificationException` | No exception thrown                                   |
| Examples: `ArrayList`, `HashMap`         | Examples: `CopyOnWriteArrayList`, `ConcurrentHashMap` |

---

#### 9. **Synchronized Collections**

* Legacy: `Vector`, `Hashtable`
* Wrappers: `Collections.synchronizedList()`
* Modern: `java.util.concurrent` package
