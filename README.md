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

