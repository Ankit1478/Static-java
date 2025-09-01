# Static in Java – Interview Notes

## 1. Definition
- The `static` keyword in Java means the member belongs to the **class itself**, not to instances of the class.
- Memory for static members is allocated once when the class is loaded, and all objects share it.

---

## 2. Usage of `static`

### a) Static Variables (Class Variables)
- Shared across all instances of a class.
- Useful for counters, configuration values, and constants.

```java
class Student {
    static int count = 0;
    String name;

    Student(String name) {
        this.name = name;
        count++;
    }
}
```

### b) Static Methods
- Can be called without creating an object.
- Can directly access only static variables and static methods.
- Commonly used for utility/helper methods.
- Example: `Math.sqrt()`

### c) Static Blocks
- Executed once when the class is loaded.
- Typically used for initializing static variables.

```java
class Config {
    static int setting;
    static {
        setting = 42;
    }
}
```

### d) Static Nested Classes
- A nested class declared with `static`.
- Does not require an instance of the outer class.
- Can only access static members of the outer class directly.

```java
class Outer {
    static class Inner {
        void show() {
            System.out.println("Static nested class");
        }
    }
}
```

---

## 3. Key Differences: Static vs Non-Static

| Aspect               | Static Members                   | Non-Static Members                  |
|----------------------|----------------------------------|--------------------------------------|
| Belongs to           | Class                           | Individual object                    |
| Memory Allocation    | Once, when class is loaded       | Each time a new object is created    |
| Access               | Via class name or object         | Via object only                      |
| Example              | `Math.sqrt()`                    | `s1.name`                            |

---

## 4. Important Points
- `main()` is static so the JVM can execute it without creating an object.
- Static methods cannot be overridden, but they can be hidden (method hiding).
- Static variables are often combined with `final` to define constants, e.g., `public static final double PI`.
- Overuse of static reduces flexibility and testability of code.

---

## 5. Common Interview Questions
1. **Why is the `main` method static?**  
   JVM calls it without creating an object of the class.

2. **Can static methods be overridden?**  
   No. They are resolved at compile time (method hiding).

3. **Difference between static and instance variables?**  
   Static: one copy shared by all objects. Instance: separate copy per object.

4. **When do you use a static block?**  
   For initializing static variables or running setup code once when the class loads.

5. **Use case of static nested class?**  
   Groups related classes together and avoids requiring an outer object. Often used in builder patterns.

