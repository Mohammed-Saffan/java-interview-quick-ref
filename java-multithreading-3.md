#### 1. **What is Multithreading?**

* Process of executing **multiple threads** simultaneously.
* Improves performance by utilizing **CPU cores** effectively.
* Each thread runs independently but shares the process memory.
* Each thread has its own stack.

---

#### 2. **Thread vs Process**

| Thread                         | Process                         |
| ------------------------------ | ------------------------------- |
| Lightweight, part of a process | Independent, heavy              |
| Share memory                   | Separate memory space           |
| Low overhead                   | High context switching overhead |

---

#### 3. **Creating Threads in Java**

**Two main ways:**

1. **Extend `Thread` class**

```java
class MyThread extends Thread {
    public void run() {
        // task
    }
}
```

2. **Implement `Runnable` interface** (preferred)

```java
class MyRunnable implements Runnable {
    public void run() {
        // task
    }
}
```

Start the thread:

```java
Thread t = new Thread(new MyRunnable());
t.start();
```

---

#### 4. **Thread Lifecycle (States)**

1. **New** → created but not started
2. **Runnable** → ready to run
3. **Running** → currently executing
4. **Blocked/Waiting** → waiting for a resource or signal
5. **Terminated** → finished execution

**Use `start()` to run a thread** — don't call `run()` directly.

---

#### 5. **Thread Priorities**

* Use `setPriority(int)` — values from `Thread.MIN_PRIORITY (1)` to `Thread.MAX_PRIORITY (10)`
* **Doesn’t guarantee order** — it’s just a hint to the scheduler.

---

#### 6. **Synchronization**

* Prevents **race conditions** when multiple threads access shared data.
* Achieved via:

  * `synchronized` keyword (on methods or blocks)
  * Locks (`ReentrantLock` in `java.util.concurrent.locks`)

**Example:**

```java
synchronized void increment() {
    count++;
}
```

---

#### 7. **Volatile Keyword**

* Ensures **visibility** of changes to variables across threads.
* Doesn't guarantee atomicity.

```java
volatile boolean flag = true;
```

---

#### 8. **Deadlock**

* Two or more threads waiting **forever** for each other to release resources.
* Write resource accessing (for two or more threads) in same order to prevent deadloak
* Avoid by:

  * Lock ordering 
  * Try-lock mechanisms
  * Timeouts

---

#### 9. **Thread-safe Collections**

* Legacy: `Vector`, `Hashtable` (synchronized methods)
* Modern: `Collections.synchronizedList()`, `ConcurrentHashMap`, `CopyOnWriteArrayList`

---

#### 10. **Executor Framework (Java 5+)**

* Better than manually managing threads.
* Use `ExecutorService` to manage thread pools.

```java
ExecutorService executor = Executors.newFixedThreadPool(3);
executor.execute(new MyRunnable());
executor.shutdown();
```
