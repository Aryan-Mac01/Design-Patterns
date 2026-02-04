# OOP Principles & Design Patterns Guide

## Table of Contents
- [Core OOP Concepts](#core-oop-concepts)
  - [Coupling](#coupling)
  - [Composition](#composition)
- [SOLID Principles](#solid-principles)
- [Design Patterns](#design-patterns)
  - [I. Behavioral Patterns](#i-behavioral-patterns)
  - [II. Structural Patterns](#ii-structural-patterns)
  - [III. Creational Patterns](#iii-creational-patterns)

---

## Core OOP Concepts

### Coupling

**Definition:** Coupling is the degree of dependency between different classes.

**High Coupling**
- Classes are highly interconnected
- Makes it difficult to modify or maintain them independently

**Low Coupling**
- Classes are loosely interconnected
- Makes independent modifications easier

**Example:**
```csharp
var order = new Order(new EmailSender());
order.PlaceOrder();
```

---

### Composition

**Definition:** Composition involves creating complex objects by combining simpler objects or components.

**Key Characteristics:**
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

## I. Behavioral Patterns

Behavioral patterns focus on how objects interact and communicate with each other.

### 1. Memento Pattern

**Definition:** Used to restore an object to a previous state.

**Example:**
```csharp
var editor = new Editor();
var history = new History(editor);
history.Backup();
editor.Title = "Test";
history.Backup();
editor.Content = "Hello there, my name is Aryan";
history.Backup();
editor.Title = "The life of a dev: my momentos";

history.Undo();
```

---

### 2. State Pattern

**Definition:** An object changes how it behaves when its state changes.

**Simple Analogy:** Imagine a traffic light 🚦
- 🔴 **Red** → cars must stop
- 🟡 **Yellow** → cars get ready
- 🟢 **Green** → cars can go

**Key Insight:**
- The traffic light itself does not decide what to do every time
- Its behavior changes based on its current state
- When it is Red, it behaves like Red; when it is Green, it behaves like Green

**Example:**
```csharp
var doc = new Document();
doc.State = DocumentState.Moderation;
doc.CurrentUserRole = UserRoles.Admin;
doc.Publish();
```

---

### 3. Iterator Pattern

**Definition:** Iterator lets you see things one by one without opening the box.

**Simple Analogy:** Imagine you have a box of toys 🧸🧸🧸
- You want to look at toys one by one
- Not dump the whole box on the floor 😄
- You say: "Give me the next toy"

**You don't care:**
- How toys are stored
- How many toys are inside
- What kind of box it is

**You only know:**
- Is there another toy?
- Give me the next toy

**Key Benefit:** Provides a way of iterating over an object without having to expose the object's internal structure.

**Real-World Example:** 📺 TV Remote
- `HasNextChannel()`
- `NextChannel()`
- You don't know how channels are stored, you just press Next

---

### 4. Command Pattern

**Definition:** Encapsulates a request as an object, allowing you to parameterize clients with queues, requests, or operations.

**Simple Analogy:** Imagine you have a TV 📺
- You don't touch the TV directly
- You use a remote control 🎮
- When you press "ON", "OFF", "VOLUME UP"
- The remote does not know how the TV works, it just sends a command

**Key Concept:** A command is a note that tells someone what to do, without knowing how they do it.

**Benefits:**
- Decouples sender from receiver
- Flexibility in execution of commands
- Supports undoable operations

**Real-World Example:** 🍔 Restaurant
- You (customer) write an order slip
- Waiter takes it
- Kitchen executes it
- You don't go into the kitchen yourself 😄

---

### 5. Observer Pattern

**Definition:** A subject maintains a list of its dependent objects (observers) and notifies them automatically of any state changes.

**Simple Analogy:** Imagine a school bell 🔔
- Many kids are playing
- When the bell rings… 🔔 ALL kids hear it at the same time

**Important:**
- The bell does not know who the kids are
- Kids decide what to do when they hear the bell

**Key Concept:** Observer is when many people listen to one thing, and when that thing speaks, everyone hears.

**Real-World Example:** 📺 YouTube Subscribe Button
- You subscribe to a channel
- When a new video is uploaded, you get a notification
- The channel doesn't message you personally
- Subscribers = Observers, Channel = Subject

---

### 6. Chain of Responsibility

**Definition:** Allows building a chain of objects to handle a request. A request is passed through a chain of handlers.

**Simple Analogy:** You want permission to go out and play 🏃‍♂️⚽
1. Ask Mom → If Mom says "I don't know" →
2. Ask Dad → If Dad says "I'm busy" →
3. Ask Grandpa

**Important:**
- You don't ask everyone at once
- You ask one by one
- The first person who can help handles it
- Others are not bothered

**Key Concept:** Passing a request along until someone can handle it.

**Real-World Example:** 🏢 Office Approval System
- Employee requests leave
- Team Lead checks → can approve?
- Manager checks → can approve?
- HR checks → can approve?
- Request flows step by step, not all together

---

### 7. Mediator Pattern

**Definition:** Defines an object (the Mediator) that describes how a set of objects interact with each other, reducing chaotic dependencies.

**Simple Analogy:** Imagine a classroom 🏫
- Kids want to talk to each other
- If everyone talks directly to everyone → chaos 😵‍💫
- So there is a teacher 👩‍🏫

**Rules:**
- Kids do not talk directly to other kids
- They talk to the teacher
- Teacher tells the other kid what to do

**Key Concept:** A mediator is a helper that makes people talk nicely without talking to each other directly.

**Real-World Example:** ✈️ Air Traffic Control
- Planes do not talk to other planes
- All planes talk to Control Tower
- Tower coordinates everything
- Control Tower = Mediator

---

## II. Structural Patterns

Structural patterns focus on the composition of classes and objects to form larger structures while keeping these structures flexible and efficient.

**Benefits:**
1. Promote code reusability and modularity
2. Make the codebase more maintainable and scalable
3. Enhance flexibility and extensibility
4. Allow system structure to evolve without major changes

**When to Use:** When you already have classes, don't want to rewrite them, and want to connect, wrap, or simplify them safely.

---

### 1. Facade Pattern

**Definition:** Provides a simplified interface to a complex system.

**Simple Analogy:** Imagine a remote control 📺
- Instead of pressing buttons inside the TV, you press one simple button
- You don't care how the TV works or what happens inside
- You just want: "TV ON"

**Why Facade is Used:**
- Hides complexity
- Gives one entry point
- Protects internal structure

**Facade vs Command:**
- **Command** = one action
- **Facade** = many actions behind one interface

> "Facade is used to provide a simplified interface to complex subsystems."

---

### 2. Adapter Pattern

**Definition:** Allows incompatible interfaces between classes to work together by providing a wrapper that translates one interface into another.

**Simple Analogy:** Your phone charger 🔌 and socket ⚡
- They don't match 😢
- So you use an adapter
- Phone stays the same, socket stays the same
- Adapter connects them

**Real Applications:**
- Payment gateways
- Logging libraries
- Notification services
- Third-party APIs

**Adapter vs Facade:**
- **Facade** simplifies your own system
- **Adapter** connects to someone else's system

> "Adapter allows incompatible interfaces to work together without modifying existing code."

---

### 3. Decorator Pattern

**Definition:** Allows behavior to be added to individual objects dynamically, enhancing functionality without altering the object's structure.

**Simple Analogy:** You have an ice cream 🍦
- You add chocolate 🍫
- You add nuts 🥜
- Ice cream is still ice cream
- You didn't change it, you wrapped it

**Real Problem Decorator Solves:**
- Add new behavior WITHOUT changing existing class
- WITHOUT creating many subclasses

**Real Applications:**
- UI components
- Logging
- Streams (Java / .NET)
- Feature toggles

> "Decorator adds responsibilities to an object dynamically without modifying its class."

---

### 4. Bridge Pattern

**Definition:** Separates a large class, or a set of related classes, into two separate hierarchies so they can be developed independently.

**Simple Analogy:** Remote-controlled toys 🚗🚁

Without Bridge (bad ❌):
- CarWithSimpleRemote
- CarWithAdvancedRemote
- HelicopterWithSimpleRemote
- HelicopterWithAdvancedRemote
- Too many toys 😵‍💫

With Bridge (good ✅):
- Toys don't care which remote
- Remotes don't care which toy
- A bridge connects them 🌉

**Real Example:** Phone + Operating System
- Phone types: Samsung, Pixel, iPhone
- OS types: Android, iOS
- Instead of: SamsungAndroidPhone, SamsungIOSPhone, etc.
- Phone is one thing, OS is another, bridge connects them

**When to Use Bridge:**
- ✔ You have two things that change independently
- ✔ You want to avoid class explosion
- ✔ You want to combine them dynamically

**Common Uses:**
- UI + Rendering engine
- Device + Driver
- Shape + Drawing API

---

### 5. Composite Pattern

**Definition:** Enables the creation of tree-like structures to represent collections of objects, where both individual objects and groups are treated uniformly.

**Simple Analogy:** Imagine a tree 🌳
- A tree has branches
- Branches can have more branches
- Branches finally have leaves

**The Magic ✨:**
- Whether it's a tree, a branch, or a leaf
- You can say "grow" to all of them
- You don't need to ask "Are you a leaf?" or "Are you a branch?"

**Key Concept:** Composite lets us treat one thing and many things the same way.

**Real Example:** File System
- Folder can contain files and other folders
- You can open a file or open a folder
- You don't care what's inside
- File & Folder use the same interface

**When to Use:**
- ✔ Objects form a tree structure
- ✔ Single objects and groups behave the same
- ✔ Client should not care if it's one or many

**Common Uses:**
- UI components
- Organization hierarchy
- Menu systems
- File systems

---

### 6. Flyweight Pattern

**Definition:** Minimizes memory usage by sharing common state between multiple objects.

**Simple Analogy:** Classroom 👶👶👶 with 100 kids
- All kids wear the same uniform
- Sit on different chairs
- Have different names
- Would you make 100 uniforms? ❌
- No! You make ONE uniform and share it

**Key Concept:** Sharing common things = Flyweight Pattern

**Real Example:** ✏️ Text Editor
- When you type: `aaaaaabbbbbbbcccc`
- Computer does NOT store 15 separate letter objects
- It stores: One 'a', One 'b', One 'c'
- And reuses them → Saves memory 🧠

**When to Use:**
- ✔ You have many objects
- ✔ Most data is same/shared
- ✔ Memory usage matters

**Common Uses:**
- Text rendering
- Game characters (trees, bullets)
- UI icons
- Cache systems

---

### 7. Proxy Pattern

**Definition:** Provides a proxy object to control access to another object, allowing for additional functionality such as caching, logging, lazy loading, or access control.

**Simple Analogy:** You want to talk to a king 👑
- You cannot just walk in
- There is a guard 🛡️ at the door
- You talk to the guard
- Guard checks: Are you allowed? Is the king busy?
- If yes → guard lets you talk to the king
- If no → guard stops you

**Key Concept:** Proxy is a helper that controls access to the real thing.

**Real Example:** 🏦 Bank ATM
- You don't go inside the bank vault
- ATM checks PIN
- ATM talks to the bank system
- ATM = Proxy

**When to Use:**
- ✔ You want to control access
- ✔ Object creation is expensive
- ✔ You want security, logging, caching, or lazy loading

**Proxy Types:**
1. **Protection Proxy** → access control
2. **Virtual Proxy** → lazy loading
3. **Remote Proxy** → remote objects
4. **Caching Proxy** → performance

**Common Uses:**
- Security checks
- Lazy loading
- API gateways
- Database access
- File systems

---

## III. Creational Patterns

Creational design patterns focus on object creation, dealing with the best way to create objects while hiding the creation logic.

**Benefits:**
- Encapsulation of object creation
- Enhanced flexibility and extensibility
- Improved code reusability
- Promotion of separation of concerns
- Support for dependency injection

**The Big Idea:** Instead of making toys directly everywhere (which breaks when design changes), use special toy-making rules so toys can change later without breaking things.

---

### 1. Singleton Pattern

**Definition:** Ensures a class has only one instance and provides a global point of access to that instance.

**Simple Analogy:**
- There must be ONLY ONE principal in school 🏫
- If there are many principals → chaos 😵

**What Problem It Solves:**
- Ensures only one instance
- Provides a single shared access point

**Where Used:**
- Configuration manager
- Logging system
- Cache
- Database connection pool

---

### 2. Factory Pattern

**Definition:** Defines an interface for creating objects, but allows subclasses to alter the type of objects that will be created.

**Simple Analogy:**
- You don't make toys yourself
- You go to a toy factory 🏭 and say: "Give me a car"
- You don't care how it's made

**What Problem It Solves:**
- Removes `new` from client code
- Centralizes object creation
- Makes code easy to extend

**Where Used:**
- User creation
- Payment method selection
- Document creation
- Service instantiation

---

### 3. Abstract Factory Pattern

**Definition:** Provides an interface for creating families of related objects without specifying their concrete classes.

**Simple Analogy:** You go to a LEGO factory 🧱
- It gives you: LEGO car, LEGO wheels, LEGO driver
- All parts match each other

**What Problem It Solves:**
- Creates families of related objects
- Ensures compatibility
- Hides concrete classes

**Where Used:**
- UI themes (Dark / Light)
- Cross-platform UI toolkits
- Database providers

---

### 4. Builder Pattern

**Definition:** Used to construct complex objects step by step, providing clarity and flexibility in the creation process.

**Simple Analogy:** Building a burger 🍔
- Bun
- Patty
- Cheese
- Sauce
- You don't want 10 constructors 😵
- You build step-by-step

**What Problem It Solves:**
- Too many constructor parameters
- Complex object creation
- Improves readability

**Where Used:**
- Request objects
- Configuration objects
- Report generation
- Complex domain objects

---

### 5. Prototype Pattern

**Definition:** Allows objects to be copied or cloned, providing a mechanism to create new instances by copying existing objects.

**Simple Analogy:**
- You draw one picture 🎨
- Then make photocopies 📄📄📄
- Instead of drawing again

**What Problem It Solves:**
- Object creation is expensive
- You want copies of existing objects

**Where Used:**
- Game objects
- Templates
- Configuration cloning

---

## Contributing

Feel free to contribute by adding more patterns or improving existing explanations!

