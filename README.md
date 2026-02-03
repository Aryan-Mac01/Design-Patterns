# OOP Principles & Design Patterns Guide

## Table of Contents
- [Coupling](#coupling)
- [Composition](#composition)
- [SOLID Principles](#solid-principles)
- [Design Patterns](#design-patterns)
  - [Behavioral Patterns](#behavioral-patterns)

---

## Coupling

**Definition:** Coupling is the degree of dependency between different classes.

### Types of Coupling

**High Coupling**
- Classes are highly interconnected
- Makes it difficult to modify or maintain them independently

**Low Coupling**
- Classes are loosely interconnected
- Makes independent modifications easier

### Example Usage
```csharp
// using ConsoleApp1.src.OopsPrinciples.Coupling;
// var order = new Order(new EmailSender());
// order.PlaceOrder();
```

---

## Composition

**Definition:** Composition involves creating complex objects by combining simpler objects or components.

### Key Characteristics
- Objects are assembled together to form larger structures
- Each component object maintains its own state and behavior
- Described in terms of **"has-a" relationship**

---

## SOLID Principles

### 1. Single Responsibility Principle (SRP)
> "A class should have only one reason to change, meaning it should have only one responsibility or purpose."

### 2. Open-Closed Principle (OCP)
> "Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification."

### 3. Liskov Substitution Principle (LSP)
> "Objects of a superclass should be replaceable by objects of its subclass without affecting the correctness of the program."

### 4. Interface Segregation Principle (ISP)
> "Clients should not be forced to depend on interfaces they don't use."

### 5. Dependency Inversion Principle (DIP)
> "High-level modules should not depend on low-level modules. Both should depend on abstractions."

---

## Design Patterns

### Behavioral Patterns

#### 1. Memento Pattern

**Purpose:** Used to restore an object to a previous state.

**Example Usage:**
```csharp
// using ConsoleApp1.src.DesignPattern.Behavioral.Momento;

// var editor = new Editor();
// var history = new History(editor);
// history.Backup();
// editor.Title = "Test";
// history.Backup();
// editor.Content = "Hello there, my name is Aryan";
// history.Backup();
// editor.Title = "The life of a dev: my momentos";

// Console.WriteLine("Title: " + editor.Title);
// Console.WriteLine("Content: " + editor.Content);

// history.Undo();

// Console.WriteLine("Title: " + editor.Title);
// Console.WriteLine("Content: " + editor.Content);
```

---

#### 2. State Pattern

**Purpose:** An object changes how it behaves when its state changes.

**Analogy:** Imagine a traffic light 🚦

- 🔴 **Red** → cars must stop
- 🟡 **Yellow** → cars get ready
- 🟢 **Green** → cars can go

**Key Points:**
- The traffic light itself does not decide what to do every time
- Its behavior changes based on its current state
- When it is Red, it behaves like Red
- When it is Green, it behaves like Green

**Example Usage:**
```csharp
// using ConsoleApp1.src.DesignPattern.Behavioral.State;

// var doc = new Document();
// doc.State = DocumentState.Moderation;
// doc.CurrentUserRole = UserRoles.Admin;

// Console.WriteLine(doc.State);

// doc.Publish();

// Console.WriteLine(doc.State);
```

---

#### 3. Iterator Pattern

**Purpose:** Iterator lets you see things one by one without opening the box.

**Analogy:** Imagine you have a box of toys 🧸🧸🧸

You want to:
- Look at toys one by one
- Not dump the whole box on the floor 😄

You don't care about:
- How toys are stored
- How many toys are inside
- What kind of box it is

You only know:
- Is there another toy?
- Give me the next toy

**Key Benefit:** The Iterator Pattern provides a way of iterating over an object without having to expose the object's internal structure, which may change in the future. Changing the internals of an object should not affect its consumers.

---

#### 4. Command Pattern

**Purpose:** A behavioral pattern that encapsulates a request as an object, allowing you to parameterize clients with queues, requests, or operations.

**Benefits:**
- Decouples the sender from the receiver
- Provides flexibility in the execution of commands
- Supports undoable operations

**Analogy:** Imagine you have a TV 📺

- You don't touch the TV directly
- You use a remote control 🎮

When you press:
- "ON"
- "OFF"
- "VOLUME UP"

The remote does not know how the TV works. It just sends a command.

**Key Concept:** A command is a note that tells someone what to do, without knowing how they do it.

---

## Contributing

Feel free to contribute by adding more patterns or improving existing explanations!

## License

[Add your license information here]
