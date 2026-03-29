# 🧱 Object-Oriented Programming (OOP) with TypeScript

> A comprehensive, practical guide to understanding OOP concepts — from building blocks to the four core pillars — with real-world TypeScript examples.

---

## 📚 Table of Contents

1. [What is Object-Oriented Programming?](#1-what-is-object-oriented-programming)
   - [Programming Paradigms](#programming-paradigms)
   - [Where Does OOP Fall?](#where-does-oop-fall)
2. [Building Blocks of OOP](#2-building-blocks-of-oop)
   - [Classes](#classes)
   - [Objects](#objects)
   - [Class & Object Example](#class--object-example)
   - [Advantages of OOP](#advantages-of-oop)
3. [Pillars of OOP](#3-pillars-of-oop)
   - [Abstraction](#i-abstraction)
   - [Encapsulation](#ii-encapsulation)
   - [Inheritance (In Depth)](#iii-inheritance-in-depth)
     - [Types of Inheritance](#types-of-inheritance)
       - [Single Inheritance](#1-single-inheritance)
       - [Multi-level Inheritance](#2-multi-level-inheritance)
       - [Hierarchical Inheritance](#3-hierarchical-inheritance)
       - [Multiple Inheritance (via Interfaces)](#4-multiple-inheritance-via-interfaces)
   - [Polymorphism](#iv-polymorphism)
3. [What's Next?](#-whats-next)

---

## 1. What is Object-Oriented Programming?

**Object-Oriented Programming (OOP)** is a programming paradigm built around the concept of **objects** i.e., objects are self-contained units that combine **data** (attributes/properties/characteristics) and **behavior** (methods/functions/actions) together.

Instead of writing a program as a long list of sequential instructions, OOP allows you to model your software around real-world entities. A `Car` object, for example, would have properties like `color` and `speed`, and behaviors like `accelerate()` and `brake()`.

### Programming Paradigms

A **programming paradigm** is a fundamental style or approach to programming — a way of thinking about and structuring code. Different paradigms offer different mental models for solving problems.

The most widely used paradigms are:

| Paradigm | Core Idea | Example Languages |
|---|---|---|
| **Procedural** | Code is a sequence of step-by-step instructions (procedures/functions) executed top-to-bottom | C, Pascal, early PHP |
| **Functional** | Computation is treated as evaluating mathematical functions — data is immutable, no side effects | Haskell, Elixir, F# |
| **Object-Oriented** | Code is organized around objects that bundle data and behavior together | Java, C++, Python, TypeScript |
| **Declarative** | You describe *what* you want, not *how* to get it | SQL, HTML, CSS |

These paradigms are not mutually exclusive — many modern languages (like TypeScript, Python, Kotlin) support **multiple paradigms** simultaneously.

### Where Does OOP Fall?

OOP is an **imperative, object-based paradigm** — meaning you still tell the computer _how_ to do things, but you structure those instructions inside objects instead of loose procedures.

**Why OOP became dominant for large-scale software:**

- **Real-world modeling** — Software often represents real things (Users, Orders, Products). OOP maps naturally to that.
- **Procedural code doesn't scale** — As programs grow, a flat list of functions and global variables becomes impossible to manage. OOP provides structure through encapsulation and modularity.
- **Code reuse** — Inheritance and interfaces let you write logic once and reuse it across many types.
- **Team collaboration** — Different developers can own different classes/modules without stepping on each other.

---

## 2. Building Blocks of OOP

The fundamental building blocks of OOP are **Classes** and **Objects**. Everything in OOP revolves around these concepts — classes define structure, objects bring it to life, and inheritance lets you extend and reuse it.

### Classes

A **class** is a **user-defined data type** that acts as a **blueprint, template, or prototype** for creating objects. It defines the structure and behavior that all its instances (objects) will share — but it holds no actual data itself.

Think of a class like an **architectural blueprint** for a house. The blueprint describes the number of rooms, windows, and doors — but it's not a house itself. You build actual houses (objects) from that blueprint.

**Key characteristics of a class:**
- Defines **properties** (data/state) an object will hold
- Defines **methods** (functions/behavior) an object can perform
- Serves as a reusable factory for creating multiple objects
- Allocates **no memory** on its own — memory is only allocated when an object is created

### Objects

An **object** is a concrete **instance of a class** — a real entity in memory created from the class blueprint. When a class is instantiated, memory is allocated and an actual object comes to life.

Every object has three defining characteristics:

| Characteristic | Description | Example (`Car` object) |
|---|---|---|
| **Identity** | A unique identifier (memory address) distinguishing it from all other objects | `car1` vs `car2` |
| **State** | The data currently stored in the object's fields/properties | `color: "red"`, `speed: 120` |
| **Behavior** | The actions the object can perform via its methods | `accelerate()`, `brake()` |

---

### Class & Object Example

```typescript
// Blueprint (Class)
class Car {
  brand: string;
  model: string;
  speed: number;

  constructor(brand: string, model: string) {
    this.brand = brand;
    this.model = model;
    this.speed = 0;
  }

  accelerate(amount: number): void {
    this.speed += amount;
    console.log(`${this.brand} ${this.model} is now going ${this.speed} km/h`);
  }

  brake(amount: number): void {
    this.speed = Math.max(0, this.speed - amount);
    console.log(`${this.brand} ${this.model} slowed down to ${this.speed} km/h`);
  }

  getInfo(): string {
    return `${this.brand} ${this.model} | Speed: ${this.speed} km/h`;
  }
}

// Creating Objects (Instances)
const car1 = new Car("Toyota", "Corolla"); // Object 1
const car2 = new Car("BMW", "M3");         // Object 2

// Each object has its own independent state
car1.accelerate(60); // Toyota Corolla is now going 60 km/h
car2.accelerate(120); // BMW M3 is now going 120 km/h

car1.brake(20); // Toyota Corolla slowed down to 40 km/h

console.log(car1.getInfo()); // Toyota Corolla | Speed: 40 km/h
console.log(car2.getInfo()); // BMW M3 | Speed: 120 km/h
```

**🔍 Explanation:**
- `Car` is the **class** (blueprint) — it defines what every car will look like and what it can do.
- `car1` and `car2` are **objects** (instances) — each is an independent entity with its own state.
- Both objects share the same **behavior** (`accelerate`, `brake`) but maintain their own **state** (`speed`).
- Calling `car1.accelerate()` does not affect `car2`'s speed — each object is isolated.

---

### Advantages of OOP

These are the practical benefits you gain by structuring your code around objects:

| Advantage | Description |
|---|---|
| **Clear structure** | Code is organized around real-world entities — easier to navigate and reason about |
| **Maintainability** | Changes in one class don't ripple unexpectedly across unrelated parts of the codebase |
| **Code reuse** | Inheritance and composition let you build on existing code rather than rewriting it |
| **DRY principle** | _"Don't Repeat Yourself"_ — shared logic lives in one place (base classes, interfaces) |
| **Scalability** | Adding new features is as simple as adding a new class — existing code stays untouched |
| **Testability** | Objects with clear interfaces and encapsulated state are far easier to unit test in isolation |
| **Collaboration** | Teams can work on different classes/modules independently, then compose them together |

---

## 3. Pillars of OOP

The four pillars are the core principles that make OOP powerful. They work together to manage software complexity, promote code reuse, and improve long-term maintainability.

```
┌──────────────────────────────────────────────┐
│                  OOP Pillars                  │
│                                              │
│   Abstraction    |    Encapsulation          │
│   ─────────────────────────────────          │
│   Inheritance    |    Polymorphism           │
└──────────────────────────────────────────────┘
```

---

## I. Abstraction

### What is Abstraction?

**Abstraction** is the process of **hiding complex implementation details** and **exposing only the essential features** that the user needs to interact with. It focuses on **what an object does**, not **how it does it**.

Think of a **TV remote** — you press the "Volume Up" button and the volume increases. You don't need to know the circuit logic, signals, or internal processing happening behind the scenes. The complexity is hidden; only the essential interface is exposed.

### Abstraction in TypeScript

TypeScript achieves abstraction through two constructs:

| Construct | Keyword | Purpose |
|---|---|---|
| **Interface** | `implements` | Pure contract — defines the shape/signature only, zero implementation |
| **Abstract Class** | `extends` | Partial contract — can define both abstract methods (no body) and concrete methods (with body) |

### Access Modifiers in Abstraction

| Modifier | Accessible From |
|---|---|
| `private` | Only within the class itself — not by subclasses or external code |
| `protected` | Within the class itself **and** any subclass that extends it — not from outside |
| `public` | Accessible from anywhere |

> **Rule of Thumb:** In abstract classes, use `protected` for abstract methods (subclasses need them) and `private` for concrete helper methods (implementation details no one else should touch).

---

### 🔷 Scenario 1 — Payment Gateway

```typescript
// Abstract class defines the contract for all payment providers
abstract class PaymentGateway {
  protected abstract processPayment(amount: number): boolean;
  protected abstract refundPayment(transactionId: string): boolean;

  // Concrete shared logic available to all subclasses
  public pay(amount: number): void {
    console.log(`Initiating payment of $${amount}...`);
    const success = this.processPayment(amount);
    if (success) {
      console.log("✅ Payment successful!");
    } else {
      console.log("❌ Payment failed. Please try again.");
    }
  }

  public refund(transactionId: string): void {
    console.log(`Processing refund for transaction: ${transactionId}`);
    const success = this.refundPayment(transactionId);
    console.log(success ? "✅ Refund processed." : "❌ Refund failed.");
  }
}

// Concrete implementation — Stripe
class StripeGateway extends PaymentGateway {
  protected processPayment(amount: number): boolean {
    console.log(`[Stripe] Charging $${amount} via Stripe API...`);
    // Complex Stripe API logic hidden here
    return true;
  }

  protected refundPayment(transactionId: string): boolean {
    console.log(`[Stripe] Issuing refund for ${transactionId}...`);
    return true;
  }
}

// Concrete implementation — PayPal
class PayPalGateway extends PaymentGateway {
  protected processPayment(amount: number): boolean {
    console.log(`[PayPal] Processing $${amount} via PayPal...`);
    // Complex PayPal API logic hidden here
    return true;
  }

  protected refundPayment(transactionId: string): boolean {
    console.log(`[PayPal] Reversing transaction ${transactionId}...`);
    return false; // Simulating a failed refund
  }
}

// Usage — the caller doesn't know or care HOW payment is processed
const stripe = new StripeGateway();
stripe.pay(99.99);
stripe.refund("TXN-001");

const paypal = new PayPalGateway();
paypal.pay(49.99);
paypal.refund("TXN-002");
```

**🔍 Explanation:**
- The `PaymentGateway` abstract class defines the **contract**: every payment provider _must_ implement `processPayment` and `refundPayment`.
- The `pay()` and `refund()` methods in the base class provide **shared orchestration logic** — the user calls these without knowing the underlying provider.
- `StripeGateway` and `PayPalGateway` hide all their internal API complexity behind the abstract contract.

---

### 🔷 Scenario 2 — Notification Service (Interface-based)

```typescript
// Pure contract — interface defines WHAT must be done, not HOW
interface NotificationService {
  send(recipient: string, message: string): void;
  getServiceName(): string;
}

// Email implementation
class EmailNotification implements NotificationService {
  send(recipient: string, message: string): void {
    // Internal SMTP logic hidden from the caller
    console.log(`📧 Sending email to ${recipient}: "${message}"`);
  }

  getServiceName(): string {
    return "Email Service";
  }
}

// SMS implementation
class SMSNotification implements NotificationService {
  send(recipient: string, message: string): void {
    // Internal Twilio/SMS gateway logic hidden
    console.log(`📱 Sending SMS to ${recipient}: "${message}"`);
  }

  getServiceName(): string {
    return "SMS Service";
  }
}

// Push Notification implementation
class PushNotification implements NotificationService {
  send(recipient: string, message: string): void {
    // Internal Firebase/APNs logic hidden
    console.log(`🔔 Sending push notification to ${recipient}: "${message}"`);
  }

  getServiceName(): string {
    return "Push Notification Service";
  }
}

// Dispatcher works with the abstraction — not the concrete classes
class NotificationDispatcher {
  constructor(private service: NotificationService) {}

  notify(recipient: string, message: string): void {
    console.log(`[${this.service.getServiceName()}]`);
    this.service.send(recipient, message);
  }
}

// Usage
const emailDispatcher = new NotificationDispatcher(new EmailNotification());
emailDispatcher.notify("user@example.com", "Your order has shipped!");

const smsDispatcher = new NotificationDispatcher(new SMSNotification());
smsDispatcher.notify("+923001234567", "OTP: 482910");

const pushDispatcher = new NotificationDispatcher(new PushNotification());
pushDispatcher.notify("device-token-xyz", "You have a new message!");
```

**🔍 Explanation:**
- The `NotificationService` **interface** is a pure contract — no logic, just method signatures.
- Each class (`EmailNotification`, `SMSNotification`, `PushNotification`) provides its own implementation, hiding the internal delivery mechanism.
- `NotificationDispatcher` works entirely against the interface — it can use any notification service without modification.

---

### 🔷 Scenario 3 — Database Repository

```typescript
// Interface for any data store — SQL, NoSQL, file-based, etc.
interface UserRepository {
  findById(id: number): object | null;
  save(user: object): void;
  delete(id: number): void;
}

// MySQL implementation
class MySQLUserRepository implements UserRepository {
  findById(id: number): object | null {
    console.log(`[MySQL] SELECT * FROM users WHERE id = ${id}`);
    return { id, name: "Alice", email: "alice@example.com" };
  }

  save(user: object): void {
    console.log(`[MySQL] INSERT INTO users VALUES...`, user);
  }

  delete(id: number): void {
    console.log(`[MySQL] DELETE FROM users WHERE id = ${id}`);
  }
}

// MongoDB implementation
class MongoUserRepository implements UserRepository {
  findById(id: number): object | null {
    console.log(`[MongoDB] db.users.findOne({ _id: ${id} })`);
    return { id, name: "Bob", email: "bob@example.com" };
  }

  save(user: object): void {
    console.log(`[MongoDB] db.users.insertOne(...)`, user);
  }

  delete(id: number): void {
    console.log(`[MongoDB] db.users.deleteOne({ _id: ${id} })`);
  }
}

// Service layer depends only on the abstraction
class UserService {
  constructor(private repo: UserRepository) {}

  getUser(id: number): object | null {
    return this.repo.findById(id);
  }

  createUser(user: object): void {
    this.repo.save(user);
    console.log("User created successfully.");
  }
}

// Swap databases without touching UserService
const mysqlService = new UserService(new MySQLUserRepository());
mysqlService.getUser(1);

const mongoService = new UserService(new MongoUserRepository());
mongoService.getUser(42);
```

**🔍 Explanation:**
- `UserRepository` abstracts away the database layer entirely.
- `UserService` doesn't care whether data lives in MySQL or MongoDB — it only depends on the contract.
- Swapping the database requires zero changes to `UserService`.

---

## II. Encapsulation

### What is Encapsulation?

**Encapsulation** is the practice of **bundling data (properties) and the methods that operate on that data into a single unit (class)**, while **restricting direct access** to the object's internal state from the outside world.

Think of it as a **medicine capsule** — the active ingredients (data) are sealed inside. You can't directly touch or modify them. You interact with the capsule through its defined interface (swallowing it).

> 💡 **Core Idea:** Expose only what's necessary, hide everything else. Control _how_ your internal data is accessed and modified.

### Access Modifiers for Encapsulation

| Modifier | Description |
|---|---|
| `private` | Accessible **only** within the class — no external or subclass access |
| `readonly` | Can only be assigned **once** (at declaration or in the constructor) — equivalent to `final` in Java |
| `public` | Accessible from anywhere (default if not specified) |

Use **getter/setter methods** to provide controlled access to `private` fields.

---

### 🔷 Scenario 1 — Bank Account

```typescript
class BankAccount {
  private balance: number;
  private readonly accountNumber: string;
  private transactionHistory: string[] = [];

  constructor(accountNumber: string, initialDeposit: number) {
    this.accountNumber = accountNumber;
    this.balance = initialDeposit;
    this.transactionHistory.push(`Account opened with $${initialDeposit}`);
  }

  // Controlled deposit — with validation
  deposit(amount: number): void {
    if (amount <= 0) {
      throw new Error("Deposit amount must be positive.");
    }
    this.balance += amount;
    this.transactionHistory.push(`Deposited: $${amount}`);
    console.log(`✅ Deposited $${amount}. New balance: $${this.balance}`);
  }

  // Controlled withdrawal — with validation
  withdraw(amount: number): void {
    if (amount <= 0) {
      throw new Error("Withdrawal amount must be positive.");
    }
    if (amount > this.balance) {
      throw new Error("Insufficient funds.");
    }
    this.balance -= amount;
    this.transactionHistory.push(`Withdrawn: $${amount}`);
    console.log(`✅ Withdrew $${amount}. Remaining balance: $${this.balance}`);
  }

  // Read-only access to balance — no direct mutation allowed
  getBalance(): number {
    return this.balance;
  }

  getAccountNumber(): string {
    return `****${this.accountNumber.slice(-4)}`; // Masked for security
  }

  getTransactionHistory(): string[] {
    return [...this.transactionHistory]; // Return a copy, not the original array
  }
}

const account = new BankAccount("ACC-987654321", 1000);
account.deposit(500);
account.withdraw(200);

console.log(`Balance: $${account.getBalance()}`);            // $1300
console.log(`Account: ${account.getAccountNumber()}`);       // ****4321
console.log("History:", account.getTransactionHistory());

// ❌ These would cause TypeScript errors — direct mutation is blocked:
// account.balance = 99999;       // Error: Property 'balance' is private
// account.accountNumber = "XYZ"; // Error: Cannot assign to 'accountNumber' (readonly)
```

**🔍 Explanation:**
- `balance` and `accountNumber` are `private` — no external code can directly read or modify them.
- `accountNumber` is also `readonly` — it's set once in the constructor and can never change.
- `deposit()` and `withdraw()` are the **controlled interfaces** — they validate input before modifying the internal state.
- `getBalance()` exposes the balance **read-only**, and `getTransactionHistory()` returns a copy to prevent external mutation.

---

### 🔷 Scenario 2 — User Profile with Validation

```typescript
class UserProfile {
  private _username: string;
  private _email: string;
  private _age: number;
  private readonly createdAt: Date;

  constructor(username: string, email: string, age: number) {
    this._username = username;
    this._email = email;
    this._age = age;
    this.createdAt = new Date();
  }

  // Getter — read access
  get username(): string {
    return this._username;
  }

  // Setter with validation
  set username(value: string) {
    if (value.length < 3) {
      throw new Error("Username must be at least 3 characters.");
    }
    this._username = value;
  }

  get email(): string {
    return this._email;
  }

  set email(value: string) {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(value)) {
      throw new Error("Invalid email format.");
    }
    this._email = value;
  }

  get age(): number {
    return this._age;
  }

  set age(value: number) {
    if (value < 13 || value > 120) {
      throw new Error("Age must be between 13 and 120.");
    }
    this._age = value;
  }

  getProfile(): object {
    return {
      username: this._username,
      email: this._email,
      age: this._age,
      memberSince: this.createdAt.toDateString(),
    };
  }
}

const user = new UserProfile("alice_dev", "alice@example.com", 28);
console.log(user.getProfile());

user.username = "alice_2024"; // ✅ Valid
user.email = "newemail@example.com"; // ✅ Valid

try {
  user.age = 5; // ❌ Will throw: Age must be between 13 and 120
} catch (e: any) {
  console.error(e.message);
}

try {
  user.email = "not-an-email"; // ❌ Will throw: Invalid email format
} catch (e: any) {
  console.error(e.message);
}
```

**🔍 Explanation:**
- TypeScript **getters and setters** (`get`/`set`) provide clean, property-like syntax while enforcing validation logic internally.
- `createdAt` is `readonly` — a user's registration date should never change.
- Invalid data is rejected at the point of entry, keeping the object's internal state always valid.

---

### 🔷 Scenario 3 — Inventory Item

```typescript
class InventoryItem {
  private readonly itemId: string;
  private _name: string;
  private _price: number;
  private _stock: number;

  constructor(itemId: string, name: string, price: number, stock: number) {
    this.itemId = itemId;
    this._name = name;
    this._price = price;
    this._stock = stock;
  }

  get itemId_(): string { return this.itemId; }
  get name(): string { return this._name; }
  get price(): number { return this._price; }
  get stock(): number { return this._stock; }

  set price(value: number) {
    if (value < 0) throw new Error("Price cannot be negative.");
    this._price = value;
  }

  addStock(quantity: number): void {
    if (quantity <= 0) throw new Error("Quantity must be positive.");
    this._stock += quantity;
    console.log(`📦 Added ${quantity} units. Total stock: ${this._stock}`);
  }

  sellItem(quantity: number): void {
    if (quantity > this._stock) {
      throw new Error(`Insufficient stock. Available: ${this._stock}`);
    }
    this._stock -= quantity;
    console.log(`🛒 Sold ${quantity} unit(s). Remaining: ${this._stock}`);
  }

  isAvailable(): boolean {
    return this._stock > 0;
  }
}

const laptop = new InventoryItem("ITEM-001", "Gaming Laptop", 1299.99, 50);
laptop.addStock(20);
laptop.sellItem(5);
laptop.price = 1199.99; // Apply discount
console.log(`Available: ${laptop.isAvailable()}, Stock: ${laptop.stock}, Price: $${laptop.price}`);
```

**🔍 Explanation:**
- `itemId` is `private readonly` — once an item is created, its ID never changes.
- Stock can only be modified through `addStock()` and `sellItem()`, which enforce business rules.
- Price updates go through a setter that prevents negative values.

---

## III. Inheritance (In Depth)

### What is Inheritance?

**Inheritance** is a mechanism where a **child class (subclass/derived class)** acquires the properties and behaviors of a **parent class (superclass/base class)**. This promotes code reuse by allowing new classes to build upon existing ones without rewriting shared logic.

> 💡 **Core Idea:** Inheritance models an **"is-a" relationship** — a `Dog` _is-a_ `Animal`, a `SavingsAccount` _is-a_ `BankAccount`.

In TypeScript, the `extends` keyword is used for inheritance. The child class can:
- **Inherit** all public and protected members from the parent
- **Override** parent methods to provide specialized behavior
- **Extend** the parent by adding new properties and methods
- Call the parent's constructor using `super()`

---

### Types of Inheritance

#### 1. Single Inheritance

A child class inherits from exactly **one** parent class.

```
   Animal
     │
     ▼
    Dog
```

```typescript
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  eat(): void {
    console.log(`${this.name} is eating.`);
  }

  sleep(): void {
    console.log(`${this.name} is sleeping.`);
  }
}

class Dog extends Animal {
  breed: string;

  constructor(name: string, breed: string) {
    super(name); // Call the parent constructor
    this.breed = breed;
  }

  // Extending parent with new behavior
  bark(): void {
    console.log(`${this.name} says: Woof! 🐕`);
  }

  // Overriding parent behavior
  eat(): void {
    console.log(`${this.name} (${this.breed}) eats dog food enthusiastically.`);
  }
}

const dog = new Dog("Buddy", "Golden Retriever");
dog.eat();   // Overridden: Buddy (Golden Retriever) eats dog food enthusiastically.
dog.sleep(); // Inherited: Buddy is sleeping.
dog.bark();  // Own method: Buddy says: Woof!
```

---

#### 2. Multi-level Inheritance

A chain of inheritance — `C` extends `B`, which extends `A`. Each level inherits from the level above it.

```
   Animal
     │
     ▼
  Mammal
     │
     ▼
    Dog
```

```typescript
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  breathe(): void {
    console.log(`${this.name} is breathing.`);
  }
}

class Mammal extends Animal {
  furColor: string;

  constructor(name: string, furColor: string) {
    super(name);
    this.furColor = furColor;
  }

  nurseYoung(): void {
    console.log(`${this.name} nurses its young.`);
  }
}

class Dog extends Mammal {
  breed: string;

  constructor(name: string, furColor: string, breed: string) {
    super(name, furColor);
    this.breed = breed;
  }

  fetch(): void {
    console.log(`${this.name} the ${this.breed} fetches the ball! 🎾`);
  }
}

const dog = new Dog("Rex", "Golden", "Labrador");
dog.breathe();    // Inherited from Animal
dog.nurseYoung(); // Inherited from Mammal
dog.fetch();      // Own method
console.log(`Fur color: ${dog.furColor}`); // Property from Mammal
```

---

#### 3. Hierarchical Inheritance

Multiple child classes inherit from the **same** parent class. Each child specializes independently.

```
       Animal
      /      \
   Dog        Cat
```

```typescript
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  move(): void {
    console.log(`${this.name} is moving.`);
  }

  makeSound(): void {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log(`${this.name} says: Woof! 🐕`);
  }

  fetch(): void {
    console.log(`${this.name} fetches the stick.`);
  }
}

class Cat extends Animal {
  makeSound(): void {
    console.log(`${this.name} says: Meow! 🐱`);
  }

  purr(): void {
    console.log(`${this.name} is purring...`);
  }
}

class Bird extends Animal {
  makeSound(): void {
    console.log(`${this.name} says: Tweet! 🐦`);
  }

  fly(): void {
    console.log(`${this.name} is flying!`);
  }
}

const dog = new Dog("Rex");
const cat = new Cat("Whiskers");
const bird = new Bird("Tweety");

// All share the base behavior
dog.move(); cat.move(); bird.move();

// Each specializes makeSound independently
dog.makeSound();  // Rex says: Woof!
cat.makeSound();  // Whiskers says: Meow!
bird.makeSound(); // Tweety says: Tweet!

// Each also has unique behaviors
dog.fetch();
cat.purr();
bird.fly();
```

---

#### 4. Multiple Inheritance (via Interfaces)

TypeScript classes **cannot** extend multiple classes directly (to avoid the "diamond problem"). However, a class can **implement multiple interfaces**, achieving the effect of multiple inheritance cleanly.

```
  Flyable    Swimmable
      \        /
       \      /
        Duck
```

```typescript
interface Flyable {
  fly(): void;
  altitude: number;
}

interface Swimmable {
  swim(): void;
  depth: number;
}

interface Walkable {
  walk(): void;
  speed: number;
}

// Duck can fly, swim, AND walk — implementing multiple interfaces
class Duck implements Flyable, Swimmable, Walkable {
  name: string;
  altitude: number = 50;
  depth: number = 2;
  speed: number = 3;

  constructor(name: string) {
    this.name = name;
  }

  fly(): void {
    console.log(`🦆 ${this.name} is flying at ${this.altitude}m altitude.`);
  }

  swim(): void {
    console.log(`🦆 ${this.name} is swimming ${this.depth}m deep.`);
  }

  walk(): void {
    console.log(`🦆 ${this.name} is waddling at ${this.speed} km/h.`);
  }

  quack(): void {
    console.log(`🦆 ${this.name} says: Quack!`);
  }
}

const donald = new Duck("Donald");
donald.fly();
donald.swim();
donald.walk();
donald.quack();
```

**🔍 Explanation of Inheritance Types:**

| Type | Structure | Keyword | Use When |
|---|---|---|---|
| **Single** | One parent → one child | `extends` | Simple specialization |
| **Multi-level** | A → B → C chain | `extends` (chained) | Increasing specialization levels |
| **Hierarchical** | One parent → many children | `extends` (multiple classes) | Shared base, different specializations |
| **Multiple** | Many parents → one child | `implements` (multiple interfaces) | A class needs capabilities from multiple sources |

---

### 🔷 Inheritance Scenario — Employee Management System

```typescript
// Base class
class Employee {
  protected name: string;
  protected employeeId: string;
  protected baseSalary: number;

  constructor(name: string, employeeId: string, baseSalary: number) {
    this.name = name;
    this.employeeId = employeeId;
    this.baseSalary = baseSalary;
  }

  calculateSalary(): number {
    return this.baseSalary;
  }

  getDetails(): string {
    return `[${this.employeeId}] ${this.name} — Salary: $${this.calculateSalary().toFixed(2)}`;
  }
}

// Full-time employee with bonus
class FullTimeEmployee extends Employee {
  private bonus: number;

  constructor(name: string, id: string, baseSalary: number, bonus: number) {
    super(name, id, baseSalary);
    this.bonus = bonus;
  }

  calculateSalary(): number {
    return this.baseSalary + this.bonus;
  }
}

// Part-time employee paid by hours
class PartTimeEmployee extends Employee {
  private hoursWorked: number;
  private hourlyRate: number;

  constructor(name: string, id: string, hourlyRate: number, hoursWorked: number) {
    super(name, id, 0);
    this.hourlyRate = hourlyRate;
    this.hoursWorked = hoursWorked;
  }

  calculateSalary(): number {
    return this.hourlyRate * this.hoursWorked;
  }
}

// Contractor — flat fee per project
class Contractor extends Employee {
  private projectFee: number;

  constructor(name: string, id: string, projectFee: number) {
    super(name, id, 0);
    this.projectFee = projectFee;
  }

  calculateSalary(): number {
    return this.projectFee;
  }
}

// Hierarchical inheritance — all extend Employee
const fullTime = new FullTimeEmployee("Alice", "EMP-001", 5000, 1000);
const partTime = new PartTimeEmployee("Bob", "EMP-002", 25, 80);
const contractor = new Contractor("Charlie", "EMP-003", 3500);

console.log(fullTime.getDetails());   // Alice: $6000
console.log(partTime.getDetails());   // Bob: $2000
console.log(contractor.getDetails()); // Charlie: $3500
```

---

## IV. Polymorphism

### What is Polymorphism?

**Polymorphism** (Greek for _"many shapes"_) is the ability of different objects to be **treated through a common interface** while each responding to the same method call in its **own unique way**.

Think of a **"Shape"** — you can tell any shape to `draw()` itself. A circle draws a circle, a rectangle draws a rectangle, and a triangle draws a triangle. The command is the same (`draw()`), but the behavior differs per object.

> 💡 **Core Idea:** Write code that works with the **parent type**, but at runtime it automatically uses the **child's implementation**. One interface, many behaviors.

### Types of Polymorphism

| Type | Description | TypeScript Mechanism |
|---|---|---|
| **Compile-time (Static)** | Resolved at compile time | Method overloading (via union types) |
| **Runtime (Dynamic)** | Resolved at runtime based on actual object type | Method overriding via inheritance |

---

### 🔷 Scenario 1 — Shape Drawing Engine

```typescript
// Base class defines the contract
abstract class Shape {
  color: string;

  constructor(color: string) {
    this.color = color;
  }

  abstract draw(): void;
  abstract getArea(): number;
  abstract getPerimeter(): number;

  describe(): void {
    console.log(`Shape: ${this.constructor.name} | Color: ${this.color}`);
    console.log(`  Area: ${this.getArea().toFixed(2)} | Perimeter: ${this.getPerimeter().toFixed(2)}`);
  }
}

class Circle extends Shape {
  constructor(private radius: number, color: string) {
    super(color);
  }

  draw(): void {
    console.log(`⭕ Drawing a ${this.color} circle with radius ${this.radius}`);
  }

  getArea(): number {
    return Math.PI * this.radius ** 2;
  }

  getPerimeter(): number {
    return 2 * Math.PI * this.radius;
  }
}

class Rectangle extends Shape {
  constructor(private width: number, private height: number, color: string) {
    super(color);
  }

  draw(): void {
    console.log(`▭ Drawing a ${this.color} rectangle (${this.width} x ${this.height})`);
  }

  getArea(): number {
    return this.width * this.height;
  }

  getPerimeter(): number {
    return 2 * (this.width + this.height);
  }
}

class Triangle extends Shape {
  constructor(private a: number, private b: number, private c: number, color: string) {
    super(color);
  }

  draw(): void {
    console.log(`🔺 Drawing a ${this.color} triangle with sides ${this.a}, ${this.b}, ${this.c}`);
  }

  getArea(): number {
    const s = (this.a + this.b + this.c) / 2;
    return Math.sqrt(s * (s - this.a) * (s - this.b) * (s - this.c));
  }

  getPerimeter(): number {
    return this.a + this.b + this.c;
  }
}

// Polymorphism in action — one loop, many behaviors
const shapes: Shape[] = [
  new Circle(5, "red"),
  new Rectangle(4, 6, "blue"),
  new Triangle(3, 4, 5, "green"),
];

// Each shape responds to the SAME method calls differently
shapes.forEach(shape => {
  shape.draw();
  shape.describe();
  console.log("---");
});
```

**🔍 Explanation:**
- `Shape` is the common base type. The array holds different shapes but they're all treated as `Shape`.
- Calling `draw()` on each shape triggers the **correct implementation** at runtime — circle draws a circle, rectangle draws a rectangle.
- You can add a new shape (`Pentagon`, `Hexagon`) without changing the loop — the existing code just works.

---

### 🔷 Scenario 2 — Animal Sound Simulator

```typescript
abstract class Animal {
  constructor(protected name: string) {}

  abstract makeSound(): string;
  abstract move(): string;

  // Concrete method using polymorphic calls
  performActions(): void {
    console.log(`\n🐾 ${this.name}:`);
    console.log(`  Sound: ${this.makeSound()}`);
    console.log(`  Movement: ${this.move()}`);
  }
}

class Dog extends Animal {
  makeSound(): string { return "Woof! Woof! 🐕"; }
  move(): string { return "Runs on four legs"; }
}

class Cat extends Animal {
  makeSound(): string { return "Meow~ 🐱"; }
  move(): string { return "Prowls silently"; }
}

class Bird extends Animal {
  makeSound(): string { return "Tweet tweet! 🐦"; }
  move(): string { return "Flaps wings and soars"; }
}

class Snake extends Animal {
  makeSound(): string { return "Hisssss 🐍"; }
  move(): string { return "Slithers on the ground"; }
}

// Polymorphic processing — same interface, different results
const zoo: Animal[] = [
  new Dog("Buddy"),
  new Cat("Whiskers"),
  new Bird("Rio"),
  new Snake("Kaa"),
];

zoo.forEach(animal => animal.performActions());
```

---

### 🔷 Scenario 3 — Logger System (Method Overloading Style)

```typescript
// Runtime polymorphism — different log targets, same interface
abstract class Logger {
  abstract log(message: string, level: "info" | "warn" | "error"): void;

  protected formatMessage(message: string, level: string): string {
    const timestamp = new Date().toISOString();
    return `[${timestamp}] [${level.toUpperCase()}] ${message}`;
  }
}

class ConsoleLogger extends Logger {
  log(message: string, level: "info" | "warn" | "error"): void {
    const formatted = this.formatMessage(message, level);
    if (level === "error") console.error(`❌ ${formatted}`);
    else if (level === "warn") console.warn(`⚠️ ${formatted}`);
    else console.log(`ℹ️ ${formatted}`);
  }
}

class FileLogger extends Logger {
  constructor(private filePath: string) { super(); }

  log(message: string, level: "info" | "warn" | "error"): void {
    const formatted = this.formatMessage(message, level);
    // Simulating file write
    console.log(`[FileLogger → ${this.filePath}] ${formatted}`);
  }
}

class RemoteLogger extends Logger {
  constructor(private endpoint: string) { super(); }

  log(message: string, level: "info" | "warn" | "error"): void {
    const formatted = this.formatMessage(message, level);
    // Simulating HTTP POST to remote logging service
    console.log(`[RemoteLogger → POST ${this.endpoint}] ${formatted}`);
  }
}

// Application code works with any Logger — polymorphically
class Application {
  constructor(private logger: Logger) {}

  start(): void {
    this.logger.log("Application starting...", "info");
  }

  processData(data: any): void {
    if (!data) {
      this.logger.log("No data received.", "warn");
      return;
    }
    this.logger.log(`Processing ${JSON.stringify(data)}`, "info");
  }

  crash(error: string): void {
    this.logger.log(`Critical error: ${error}`, "error");
  }
}

// Swap logger without changing Application logic
const app1 = new Application(new ConsoleLogger());
app1.start();
app1.processData(null);
app1.crash("Segmentation fault");

const app2 = new Application(new FileLogger("/var/log/app.log"));
app2.start();

const app3 = new Application(new RemoteLogger("https://logs.example.com/api"));
app3.start();
```

**🔍 Explanation:**
- `Application` accepts any `Logger` — it only calls `log()` without knowing the concrete type.
- Swapping between `ConsoleLogger`, `FileLogger`, and `RemoteLogger` requires zero changes to `Application`.
- This pattern (combined with polymorphism) is the foundation of the **Strategy Pattern** in software design.

---

## Summary

```
OOP in a Nutshell
─────────────────────────────────────────────────────
  Abstraction   → Hide complexity, expose interface
  Encapsulation → Bundle data + behavior, restrict access
  Inheritance   → Reuse and extend parent class functionality
  Polymorphism  → Same interface, different behavior per object
─────────────────────────────────────────────────────
```

These four pillars work together. Abstraction defines **what** to expose. Encapsulation protects **how** data is stored. Inheritance lets you **reuse and extend**. Polymorphism allows one piece of code to **work with many types**. Master them together and you'll write software that is clean, flexible, and built to last.

---

## 🚀 What's Next?

Now that you have a solid understanding of OOP fundamentals and its four pillars, the natural next step is to learn **how to write better OOP code** — not just correct code, but clean, scalable, and maintainable code.

This leads us to two essential topics:

**Design Principles** — Guidelines like _KISS_ (Keep It Simple, Stupid), _DRY_ (Don't Repeat Yourself), and _YAGNI_ (You Aren't Gonna Need It) that shape good software design habits.

**SOLID Principles** — Five foundational rules specifically designed for OOP that help you write code that is easy to extend, maintain, and test:

| Principle | Stands For |
|---|---|
| **S** | Single Responsibility Principle |
| **O** | Open/Closed Principle |
| **L** | Liskov Substitution Principle |
| **I** | Interface Segregation Principle |
| **D** | Dependency Inversion Principle |

> These principles are what separate a **good OOP developer** from a **great one**. They are the bridge between knowing OOP and applying it professionally.

👉 **Continue your learning here:**
**[Design Principles & SOLID Principles with TypeScript](https://github.com/jafari-dev/oop-expert-with-typescript)**

---

> 📌 **TypeScript Version:** Examples in this guide use TypeScript with strict typing. Run with `ts-node` or compile with `tsc`.
