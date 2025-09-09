### 🏦 ONE EXAMPLE: `BankAccount` — Explaining All 4 OOP Concepts

---

### 1. **Encapsulation — “Hiding the data”**

Think of a `BankAccount` class that **hides** account balance and allows controlled access through **methods**.

```java
public class BankAccount {
    private double balance;  // Private: hidden from outside

    public void deposit(double amount) {
        if (amount > 0) balance += amount;
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) balance -= amount;
    }

    public double getBalance() {
        return balance;
    }
}
```

**Key idea**: Fields are private, methods are public → **Encapsulation**
🔒 "Data is protected, access is controlled"

---

### 2. **Abstraction — “Expose only what’s needed”**

From the user’s point of view, they **don’t care how deposit/withdraw logic works**, they just call the method.

```java
BankAccount account = new BankAccount();
account.deposit(1000);
account.withdraw(500);
```

* Internally, validation, logging, or complex checks might happen.
* But the user only sees **simple methods** — not the inner workings.

🎭 **Abstraction = Showing only the essential features, hiding complexity**

---

### 3. **Inheritance — “Reusing behavior”**

Now, suppose we have different types of accounts.

```java
public class SavingsAccount extends BankAccount {
    private double interestRate;

    public void applyInterest() {
        double interest = getBalance() * interestRate;
        deposit(interest);  // Inherited method
    }
}
```

* `SavingsAccount` inherits all features of `BankAccount` (deposit, withdraw, etc.)
* Adds its own behavior (`applyInterest()`)

📚 **Inheritance = Reuse common code by extending a base class**

---

### 4. **Polymorphism — “Same method, different behavior”**

Let’s say we have both `SavingsAccount` and `CurrentAccount`.
They both override a method called `monthlyMaintenance()`:

```java
public class BankAccount {
    public void monthlyMaintenance() {
        System.out.println("General maintenance applied.");
    }
}

public class SavingsAccount extends BankAccount {
    @Override
    public void monthlyMaintenance() {
        System.out.println("Interest added for savings.");
    }
}

public class CurrentAccount extends BankAccount {
    @Override
    public void monthlyMaintenance() {
        System.out.println("Service fee charged for current account.");
    }
}
```

Now, you can do this:

```java
BankAccount account1 = new SavingsAccount();
BankAccount account2 = new CurrentAccount();

account1.monthlyMaintenance();  // Output: Interest added for savings.
account2.monthlyMaintenance();  // Output: Service fee charged...
```

🌀 **Polymorphism = One interface, many implementations**

---

### ✅ Summary: All 4 OOP Concepts in `BankAccount`

| Concept       | How it's shown in the example                                    |
| ------------- | ---------------------------------------------------------------- |
| Encapsulation | Fields like `balance` are private; accessed via methods          |
| Abstraction   | Users interact with simple methods like `deposit()`              |
| Inheritance   | `SavingsAccount` and `CurrentAccount` extend `BankAccount`       |
| Polymorphism  | `monthlyMaintenance()` is overridden, called via base class type |
