# Java-inheritance-
# ☕ Java Inheritance — **Advanced Detailed Notes (Complete Study Material)**

These notes are designed for **lecture teaching, lab preparation, exams, and interviews**. They expand on concepts with rules, examples, edge cases, and best practices.

---

# 1️⃣ What is Inheritance?

Inheritance is an **OOP mechanism** where a class (child/subclass) **acquires properties and behaviors** of another class (parent/superclass).

It supports **code reuse and hierarchical classification**.

### Real-world idea

A child inherits features from parents.

Example:

```
Animal → Dog
Vehicle → Car
Employee → Manager
```

---

# 2️⃣ Basic Syntax

```java
class Parent {
    // properties
    // methods
}

class Child extends Parent {
    // extra properties
    // extra methods
}
```

Keyword used: `extends`

---

# 3️⃣ Key Terminology

| Term        | Meaning                 |
| ----------- | ----------------------- |
| Superclass  | Parent class            |
| Subclass    | Child class             |
| extends     | Keyword for inheritance |
| IS-A        | Relationship type       |
| Reusability | Code reuse              |

Example:
Dog **IS-A** Animal.

---

# 4️⃣ Memory Representation

When a child object is created:

```
Child Object
   ↓
Parent Properties
   +
Child Properties
```

The child object contains:

* Parent members
* Child members

---

# 5️⃣ Types of Inheritance in Java

## 1. Single Inheritance

One parent, one child.

```
A → B
```

---

## 2. Multilevel Inheritance

Inheritance chain.

```
A → B → C
```

---

## 3. Hierarchical Inheritance

One parent, multiple children.

```
      A
     / \
    B   C
```

---

## 4. Multiple Inheritance (Not via classes)

Not allowed in Java classes.

```
A   B
 \ /
  C
```

Reason: **Diamond Problem** (ambiguity).

---

## 5. Hybrid Inheritance

Combination via interfaces.

---

# 6️⃣ Constructor Behavior in Inheritance

Important rule:

**Parent constructor runs first.**

Execution flow:

```
Parent Constructor
        ↓
Child Constructor
```

Example:

```java
class A {
    A() {
        System.out.println("A Constructor");
    }
}

class B extends A {
    B() {
        System.out.println("B Constructor");
    }
}
```

Output:

```
A Constructor
B Constructor
```

---

# 7️⃣ super Keyword

`super` refers to the parent class.

## Uses

1. Access parent variable
2. Call parent method
3. Call parent constructor

Example:

```java
class A {
    int x = 10;
}

class B extends A {
    int x = 20;

    void show() {
        System.out.println(super.x);
    }
}
```

Output:

```
10
```

---

# 8️⃣ Method Overriding

Child class changes parent method behavior.

### Rules

* Same method name
* Same parameters
* Same return type
* Cannot reduce access level
* Parent method must not be private

Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
```

---

# 9️⃣ Overriding Rules (Important)

| Rule                           | Explanation          |
| ------------------------------ | -------------------- |
| Method signature same          | Name + parameters    |
| Return type same               | Or covariant         |
| Access not reduced             | public → protected ❌ |
| private methods not overridden | They are hidden      |
| static methods not overridden  | They are hidden      |

---

# 🔟 Covariant Return Type

Child method may return **subclass type**.

Example:

```java
class A {}
class B extends A {}

class Test {
    A show() { return new A(); }
}

class Demo extends Test {
    B show() { return new B(); }
}
```

---

# 1️⃣1️⃣ Access Modifiers and Inheritance

| Modifier  | Accessible in Child |
| --------- | ------------------- |
| public    | Yes                 |
| protected | Yes                 |
| default   | Same package only   |
| private   | No                  |

---

# 1️⃣2️⃣ final Keyword Effects

| Usage          | Result               |
| -------------- | -------------------- |
| final class    | Cannot be inherited  |
| final method   | Cannot be overridden |
| final variable | Constant             |

Example:

```java
final class A {}
class B extends A {} // ERROR
```

---

# 1️⃣3️⃣ Polymorphism with Inheritance

Parent reference, child object.

```java
Animal a = new Dog();
a.sound();
```

Output:

```
Dog barks
```

Called:
**Runtime Polymorphism**

---

# 1️⃣4️⃣ instanceof Operator

Checks object type.

```java
Dog d = new Dog();

if(d instanceof Animal)
    System.out.println("Yes");
```

---

# 1️⃣5️⃣ Upcasting and Downcasting

## Upcasting (Safe)

```java
Animal a = new Dog();
```

## Downcasting (Risky)

```java
Dog d = (Dog) a;
```

Needs explicit cast.

---

# 1️⃣6️⃣ Object Class in Java

Every class inherits:

```java
java.lang.Object
```

Common methods:

* toString()
* equals()
* hashCode()
* getClass()

---

# 1️⃣7️⃣ Inheritance vs Composition

Inheritance:

```
Car IS-A Vehicle
```

Composition:

```
Car HAS-A Engine
```

Prefer composition if relationship is HAS-A.

---

# 1️⃣8️⃣ Advantages of Inheritance

* Code reuse
* Easy maintenance
* Logical structure
* Supports polymorphism

---

# 1️⃣9️⃣ Disadvantages

* Tight coupling
* Complex hierarchy
* Hard debugging
* Fragile base class problem

---

# 2️⃣0️⃣ Best Practices

✔ Use inheritance only for IS-A
✔ Avoid deep hierarchy
✔ Keep classes independent
✔ Prefer composition sometimes

---

# 2️⃣1️⃣ Common Mistakes by Students

❌ Forgetting super() call
❌ Wrong overriding signature
❌ Using private methods
❌ Confusing overloading and overriding

---

# 2️⃣2️⃣ Viva & Interview Questions

1. What is inheritance?
2. Why no multiple inheritance in Java?
3. Difference between overriding & overloading?
4. What is super?
5. Constructor execution order?
6. What is upcasting?
7. What is instanceof?

---

# 2️⃣3️⃣ Exam Quick Revision

✔ extends keyword
✔ IS-A relationship
✔ super keyword
✔ overriding
✔ constructor order
✔ polymorphism

---

---

## ✅ Next Lecture Recommended Topics

Next topics usually taught after inheritance:

1. Method Overriding
2. Runtime Polymorphism
3. Abstract Classes
4. Interfaces
5. super Keyword
6. Object Class Methods

---
# ☕ Java Inheritance — Detailed Notes

## 📌 1. Introduction to Inheritance

Inheritance is one of the **core concepts of Object-Oriented Programming (OOP)** in Java.

It allows one class to **acquire properties and behaviors** (fields and methods) of another class.

### ✔ Purpose of Inheritance

* Code reusability
* Method extension
* Method overriding
* Hierarchical classification
* Easier maintenance

---

## 📌 2. Definition

**Inheritance** is a mechanism where one class inherits the properties and methods of another class.

### Syntax

```java
class Parent {
    // fields and methods
}

class Child extends Parent {
    // additional fields and methods
}
```

Here:

* `Parent` = Superclass / Base class
* `Child` = Subclass / Derived class
* `extends` keyword is used.

---

## 📌 3. Terminology

| Term              | Meaning                             |
| ----------------- | ----------------------------------- |
| Superclass        | Parent class                        |
| Subclass          | Child class                         |
| extends           | Keyword used to inherit             |
| IS-A relationship | Relationship created by inheritance |

Example:
Dog IS-A Animal

---

## 📌 4. Simple Example

```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();   // inherited
        d.bark();
    }
}
```

Output:

```
Animal eats
Dog barks
```

---

## 📌 5. Types of Inheritance in Java

### 1. Single Inheritance

One child inherits one parent.

```
A → B
```

Example:

```java
class A {}
class B extends A {}
```

---

### 2. Multilevel Inheritance

Inheritance chain.

```
A → B → C
```

Example:

```java
class A {}
class B extends A {}
class C extends B {}
```

---

### 3. Hierarchical Inheritance

One parent, multiple children.

```
      A
     / \
    B   C
```

Example:

```java
class A {}
class B extends A {}
class C extends A {}
```

---

### 4. Multiple Inheritance (Not Supported via Classes)

Java does **not support multiple inheritance using classes** due to ambiguity.

```
A   B
 \ /
  C
```

But can be achieved using **interfaces**.

---

### 5. Hybrid Inheritance

Combination of types using interfaces.

---

## 📌 6. super Keyword

`super` refers to the parent class object.

### Uses of super

1. Access parent variable
2. Call parent method
3. Call parent constructor

Example:

```java
class Animal {
    Animal() {
        System.out.println("Animal constructor");
    }
}

class Dog extends Animal {
    Dog() {
        super();
        System.out.println("Dog constructor");
    }
}
```

---

## 📌 7. Method Overriding

Subclass provides new implementation of parent method.

### Rules

* Same method name
* Same parameters
* Same return type
* Parent method must not be private

Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
```

---

## 📌 8. Constructor in Inheritance

* Constructor is **not inherited**
* Parent constructor executes first
* `super()` is automatically called

Execution order:

```
Parent Constructor → Child Constructor
```

---

## 📌 9. Access Modifiers & Inheritance

| Modifier  | Accessible in Child? |
| --------- | -------------------- |
| public    | Yes                  |
| protected | Yes                  |
| default   | Same package only    |
| private   | No                   |

---

## 📌 10. Benefits of Inheritance

* Code reuse
* Reduces duplication
* Improves readability
* Easy modification
* Extensibility

---

## 📌 11. Limitations of Inheritance

* Tight coupling
* Hard maintenance if hierarchy grows
* Can lead to complexity

---

## 📌 12. Real-World Examples

* Vehicle → Car, Bike
* Employee → Manager, Developer
* Animal → Dog, Cat

---

## 📌 13. Best Practices

✔ Use inheritance for IS-A relationship
✔ Avoid deep inheritance chains
✔ Prefer composition when needed
✔ Override methods carefully

---

## 📌 14. Interview Questions

1. What is inheritance?
2. Why Java doesn't support multiple inheritance?
3. Difference between overriding and overloading?
4. What is super keyword?
5. Constructor execution order?

---

## 📌 15. Quick Summary

* Inheritance uses `extends`
* Promotes code reuse
* Supports method overriding
* Parent constructor runs first
* Multiple inheritance via interfaces only

---
# 🔷 Detailed Notes on `super` Keyword in Java

## 📌 1. Introduction to `super`

The `super` keyword in Java is a **reference variable** used to refer to the **immediate parent class object**.

It is mainly used when **inheritance** is involved.

👉 `super` helps resolve ambiguity when:

* Parent and child class have same variable names
* Parent and child class have same method names
* Parent constructor needs to be called

---

# 📌 2. Why Do We Need `super`?

When a subclass inherits from a superclass, it may:

* Define variables with the same name
* Override methods
* Have its own constructor

In such cases, `super` allows access to the **parent class version**.

---

# 📌 3. Uses of `super` Keyword

There are **three main uses** of `super`:

1. To access parent class variables
2. To call parent class methods
3. To call parent class constructors

---

# 🔹 1️⃣ Using `super` to Access Parent Class Variables

When both parent and child class have a variable with the same name, the child class variable hides the parent class variable.

### Example:

```java
class Person {
    String name = "Parent Name";
}

class Student extends Person {
    String name = "Child Name";

    void display() {
        System.out.println(name);         // Child variable
        System.out.println(super.name);   // Parent variable
    }
}
```

### 🔎 Explanation:

* `name` → Refers to child class variable
* `super.name` → Refers to parent class variable

This is called **variable hiding**.

---

# 🔹 2️⃣ Using `super` to Call Parent Class Method

When a child class overrides a method of parent class, we can use `super` to call the parent version.

### Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }

    void display() {
        sound();         // Calls Dog's sound()
        super.sound();   // Calls Animal's sound()
    }
}
```

### 🔎 Explanation:

* `sound()` → Calls overridden method in child
* `super.sound()` → Calls parent class method

This is useful when:

* You want to extend parent functionality instead of completely replacing it.

---

# 🔹 3️⃣ Using `super()` to Call Parent Constructor

`super()` is used inside child class constructor to call parent class constructor.

### Example:

```java
class Animal {
    Animal() {
        System.out.println("Animal constructor called");
    }
}

class Dog extends Animal {
    Dog() {
        super();   // Calls Animal constructor
        System.out.println("Dog constructor called");
    }
}
```

### Output:

```
Animal constructor called
Dog constructor called
```

---

# 📌 4. Important Rules About `super()`

### ✅ Rule 1:

`super()` must be the **first statement** in constructor.

❌ Incorrect:

```java
Dog() {
    System.out.println("Hello");
    super();   // ERROR
}
```

---

### ✅ Rule 2:

If you don’t write `super()`, Java automatically inserts it.

```java
Dog() {
    System.out.println("Dog constructor");
}
```

Internally Java adds:

```java
Dog() {
    super();
    System.out.println("Dog constructor");
}
```

---

### ✅ Rule 3:

If parent has parameterized constructor, you must call it explicitly.

```java
class Animal {
    Animal(String type) {
        System.out.println("Type: " + type);
    }
}

class Dog extends Animal {
    Dog() {
        super("Domestic Animal");
    }
}
```

---

# 📌 5. Constructor Chaining Using `super`

When inheritance hierarchy exists, constructors execute in order:

👉 Parent → Child

Example:

```java
class A {
    A() {
        System.out.println("A constructor");
    }
}

class B extends A {
    B() {
        super();
        System.out.println("B constructor");
    }
}

class C extends B {
    C() {
        super();
        System.out.println("C constructor");
    }
}
```

### Output:

```
A constructor
B constructor
C constructor
```

This process is called **constructor chaining**.

---

# 📌 6. Difference Between `this` and `super`

| `this`                          | `super`                        |
| ------------------------------- | ------------------------------ |
| Refers to current class object  | Refers to parent class object  |
| Access current class variables  | Access parent class variables  |
| Calls current class constructor | Calls parent class constructor |
| Used within same class          | Used in subclass               |

---

# 📌 7. When `super` Cannot Be Used

❌ In static methods
Reason: Static methods belong to class, not object.

❌ To access private members of parent
Reason: Private members are not inherited.

❌ Outside child class

---

# 📌 8. Memory Concept of `super`

When child object is created:

```java
Dog d = new Dog();
```

Memory contains:

* Parent part
* Child part

`super` refers to the **parent portion of the same object**.

---

# 📌 9. Real-Time Example

```java
class Employee {
    double salary = 30000;
}

class Manager extends Employee {
    double salary = 50000;

    void showSalary() {
        System.out.println("Manager Salary: " + salary);
        System.out.println("Employee Salary: " + super.salary);
    }
}
```

Here:

* `salary` → Manager salary
* `super.salary` → Employee salary

---

# 📌 10. Exam / Viva Important Points

✔ `super` is a keyword
✔ Used only in subclass
✔ Refers to immediate parent class
✔ Used for variable, method, constructor
✔ `super()` must be first statement
✔ Cannot be used in static context

---

# 📌 11. Summary

* `super` refers to parent class object.
* Resolves ambiguity between parent and child members.
* Calls parent constructor using `super()`.
* Enables constructor chaining.
* Must be used carefully as per Java rules.

---

If you want, I can also provide:

* 🔹 10 Viva Questions on `super`
* 🔹 MCQs with answers
* 🔹 Programs with output-based questions
* 🔹 Memory diagram explanation
* 🔹 Difference between `super` and method overriding

Just tell me 😊

# 📘 Java Notes: Static Method, Static Field, and Final Keyword

---

# 🔷 1. Static Keyword in Java

The **static keyword** in Java is used for **memory management**.
It belongs to the **class rather than the object**.

When a member is declared as `static`, it is **shared among all objects of the class**.

Static can be used with:

* Variables (Fields)
* Methods
* Blocks
* Nested Classes

Here we will focus on:

* **Static Fields**
* **Static Methods**

---

# 📌 2. Static Field (Static Variable)

## 🔹 Definition

A **static field** is a variable declared using the `static` keyword.
It belongs to the **class**, not to individual objects.

Only **one copy of the variable exists** and it is shared by all objects.

---

## 🔹 Syntax

```java
static datatype variableName;
```

---

## 🔹 Example

```java
class Student {
    int rollNo;
    String name;
    static String college = "DY Patil";

    Student(int r, String n) {
        rollNo = r;
        name = n;
    }

    void display() {
        System.out.println(rollNo + " " + name + " " + college);
    }
}

public class Test {
    public static void main(String[] args) {

        Student s1 = new Student(1, "Rahul");
        Student s2 = new Student(2, "Amit");

        s1.display();
        s2.display();
    }
}
```

### Output

```
1 Rahul DY Patil
2 Amit DY Patil
```

---

## 🔹 Explanation

Here:

```
static String college = "DY Patil";
```

* `college` is **common for all students**.
* Only **one memory location** is created.
* All objects share it.

---

## 🔹 Memory Concept

```
Class Area (Method Area)
-------------------------
college = "DY Patil"

Heap Memory
-------------------------
s1 -> rollNo, name
s2 -> rollNo, name
```

Static variables are stored in **class memory**, not in object memory.

---

# 📌 3. Static Method in Java

## 🔹 Definition

A **static method** belongs to the **class rather than the object**.
It can be called **without creating an object**.

---

## 🔹 Syntax

```java
static returnType methodName()
```

---

## 🔹 Example

```java
class MathUtil {

    static int square(int x) {
        return x * x;
    }

}

public class Test {
    public static void main(String[] args) {

        int result = MathUtil.square(5);
        System.out.println(result);

    }
}
```

### Output

```
25
```

---

## 🔹 Explanation

The method is called using:

```
ClassName.methodName()
```

Example:

```
MathUtil.square(5)
```

No object required.

---

# 📌 4. Rules of Static Methods

### 1️⃣ Static method can access static variables directly

```java
static int a = 10;

static void show() {
    System.out.println(a);
}
```

---

### 2️⃣ Static method cannot access non-static variables directly

❌ Example:

```java
int x = 10;

static void show() {
    System.out.println(x);  // ERROR
}
```

Reason:
Static methods belong to class, but non-static variables belong to objects.

---

### 3️⃣ Static method cannot use `this` or `super`

Because `this` and `super` refer to objects.

---

### 4️⃣ Main method is static

```
public static void main(String[] args)
```

Reason:
JVM calls it **without creating object**.

---

# 🔷 5. Final Keyword in Java

The **final keyword** is used to **restrict modification**.

It can be used with:

* Variables
* Methods
* Classes

---

# 📌 6. Final Variable

## 🔹 Definition

A **final variable** is a constant whose value cannot be changed.

---

## 🔹 Example

```java
class Test {
    final int x = 10;

    void display() {
        // x = 20;  ERROR
        System.out.println(x);
    }
}
```

Once assigned, the value cannot change.

---

## 🔹 Convention

Final variables are usually written in **UPPERCASE**.

Example:

```
final double PI = 3.14;
```

---

# 📌 7. Final Method

## 🔹 Definition

A **final method cannot be overridden** by a subclass.

---

## 🔹 Example

```java
class Parent {

    final void show() {
        System.out.println("Parent method");
    }

}

class Child extends Parent {

    // void show() {}  ERROR

}
```

Child class cannot override the `show()` method.

---

# 📌 8. Final Class

## 🔹 Definition

A **final class cannot be inherited**.

---

## 🔹 Example

```java
final class Vehicle {
    void run() {
        System.out.println("Vehicle running");
    }
}

class Car extends Vehicle {  // ERROR
}
```

---

## 🔹 Example from Java Library

The **String class** is final.

```
public final class String
```

Reason:

* Security
* Immutability

---

# 📌 9. Difference Between Static and Final

| Static                         | Final                                |
| ------------------------------ | ------------------------------------ |
| Belongs to class               | Cannot be modified                   |
| Shared by all objects          | Value fixed                          |
| Used for methods and variables | Used for variables, methods, classes |

---

# 📌 10. Summary

### Static Field

* Shared by all objects
* Belongs to class

### Static Method

* Called using class name
* No object required
* Cannot access non-static data directly

### Final Variable

* Constant value

### Final Method

* Cannot be overridden

### Final Class

* Cannot be inherited

---

If you want, I can also give:

* **MCQs on static and final**
* **Tricky output-based questions**
* **Interview questions**
* **Memory diagrams**
* **Short exam notes (5 marks / 10 marks)**.
