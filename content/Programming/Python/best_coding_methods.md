# Common Python Design Patterns

Design patterns are reusable solutions to common software engineering problems. They help developers write code that is more maintainable, scalable, and easier to understand.

---

# 1. Factory Pattern

## Purpose
The Factory Pattern is used to create objects without exposing the object creation logic to the client.

Instead of directly calling a class constructor, a factory decides which object should be created.

## Best For
- Creating different object types
- Hiding complex initialization
- Reducing object creation logic

## Real-world Example
A notification system that can send Email, SMS, or Push notifications.

## Example

```python
from abc import ABC, abstractmethod

class Notification(ABC):
    @abstractmethod
    def send(self, message):
        pass

class Email(Notification):
    def send(self, message):
        print(f"Email: {message}")

class SMS(Notification):
    def send(self, message):
        print(f"SMS: {message}")

class NotificationFactory:
    @staticmethod
    def create(notification_type):
        if notification_type == "email":
            return Email()
        elif notification_type == "sms":
            return SMS()
        else:
            raise ValueError("Unknown notification type")

notification = NotificationFactory.create("email")
notification.send("Hello World")
```

### Advantages

- Encapsulates object creation
- Easy to add new object types
- Reduces duplicated code

---

# 2. Strategy Pattern

## Purpose

The Strategy Pattern allows you to switch between multiple algorithms at runtime.

Instead of using many if-else statements, each algorithm is placed inside its own class.

## Best For

- Multiple algorithms
- Swappable business logic
- Machine Learning pipelines

## Real-world Example

Payment methods in an e-commerce application.

## Example

```python
from abc import ABC, abstractmethod

class PaymentStrategy(ABC):

    @abstractmethod
    def pay(self, amount):
        pass

class CreditCard(PaymentStrategy):

    def pay(self, amount):
        print(f"Paid ${amount} using Credit Card")

class PayPal(PaymentStrategy):

    def pay(self, amount):
        print(f"Paid ${amount} using PayPal")

class ShoppingCart:

    def __init__(self, strategy):
        self.strategy = strategy

    def checkout(self, amount):
        self.strategy.pay(amount)

cart = ShoppingCart(PayPal())
cart.checkout(100)
```

### Advantages

- Removes long if-else blocks
- Easy to extend
- Open for extension, closed for modification

---

# 3. Dependency Injection (DI)

## Purpose

Dependency Injection supplies required objects from outside instead of creating them inside a class.

This makes classes loosely coupled.

## Best For

- Enterprise applications
- FastAPI
- Django
- Large AI systems

## Real-world Example

Injecting a database connection into a service.

## Example

```python
class Database:

    def save(self):
        print("Saving data")

class UserService:

    def __init__(self, database):
        self.database = database

    def register(self):
        self.database.save()

db = Database()

service = UserService(db)
service.register()
```

### Advantages

- Easier testing
- Loose coupling
- Easy to replace dependencies

---

# 4. Observer Pattern

## Purpose

The Observer Pattern notifies multiple objects whenever one object changes.

## Best For

- Event systems
- GUI applications
- Notifications

## Real-world Example

YouTube subscribers receiving notifications.

## Example

```python
class Subscriber:

    def update(self, message):
        print(message)

class Channel:

    def __init__(self):
        self.subscribers = []

    def subscribe(self, subscriber):
        self.subscribers.append(subscriber)

    def notify(self, message):
        for sub in self.subscribers:
            sub.update(message)

channel = Channel()

user = Subscriber()

channel.subscribe(user)

channel.notify("New Video Uploaded!")
```

### Advantages

- Loose coupling
- Automatic notifications
- Event-driven programming

---

# 5. Decorator Pattern

## Purpose

Decorator adds extra functionality to an existing function without modifying it.

## Best For

- Logging
- Authentication
- Timing
- Validation

## Real-world Example

Logging every API request.

## Example

```python
def logger(func):

    def wrapper():
        print("Before execution")
        func()
        print("After execution")

    return wrapper

@logger
def greet():
    print("Hello")

greet()
```

### Advantages

- Reusable
- Cleaner code
- Follows Open-Closed Principle

---

# 6. Context Manager

## Purpose

Automatically manages resources like files, sockets, and database connections.

## Best For

- File handling
- Database connections
- Network resources

## Real-world Example

Opening and closing files.

## Example

```python
with open("sample.txt", "w") as file:
    file.write("Hello World")
```

Python automatically closes the file.

### Advantages

- Prevents resource leaks
- Cleaner code
- Automatic cleanup

---

# 7. Builder Pattern

## Purpose

Builds complex objects step-by-step.

## Best For

- Objects with many optional parameters
- Complex configurations

## Real-world Example

Building a computer configuration.

## Example

```python
class Computer:

    def __init__(self):
        self.cpu = None
        self.ram = None

class ComputerBuilder:

    def __init__(self):
        self.computer = Computer()

    def add_cpu(self, cpu):
        self.computer.cpu = cpu
        return self

    def add_ram(self, ram):
        self.computer.ram = ram
        return self

    def build(self):
        return self.computer

pc = (
    ComputerBuilder()
    .add_cpu("Intel i9")
    .add_ram("32GB")
    .build()
)

print(pc.cpu)
```

### Advantages

- Easy object construction
- Readable code
- Flexible configuration

---

# 8. Adapter Pattern

## Purpose

Makes incompatible interfaces work together.

## Best For

- Third-party libraries
- Legacy systems

## Real-world Example

Using different payment gateways with a common interface.

## Example

```python
class OldPrinter:

    def old_print(self):
        print("Printing...")

class Adapter:

    def __init__(self, printer):
        self.printer = printer

    def print(self):
        self.printer.old_print()

printer = Adapter(OldPrinter())
printer.print()
```

### Advantages

- Reuse old code
- Integrate third-party libraries
- Improve compatibility

---

# 9. Repository Pattern

## Purpose

Separates business logic from database operations.

## Best For

- Database applications
- Clean Architecture
- Enterprise systems

## Real-world Example

User Repository in a web application.

## Example

```python
class UserRepository:

    def get_user(self, user_id):
        print(f"Fetching user {user_id}")

class UserService:

    def __init__(self, repository):
        self.repository = repository

    def profile(self, user_id):
        self.repository.get_user(user_id)

repo = UserRepository()

service = UserService(repo)

service.profile(1)
```

### Advantages

- Separates concerns
- Easier testing
- Easy database replacement

---

# 10. Singleton Pattern

## Purpose

Ensures only one instance of a class exists throughout the application.

## Best For

- Logger
- Configuration
- Cache
- Settings
- Database connection pool

## Example

```python
class Logger:

    _instance = None

    def __new__(cls):

        if cls._instance is None:
            cls._instance = super().__new__(cls)

        return cls._instance

logger1 = Logger()
logger2 = Logger()

print(logger1 is logger2)
```

Output

```
True
```

### Advantages

- One shared instance
- Saves memory
- Centralized management

### Disadvantages

- Global state
- Hard to test
- Tight coupling
- Often overused

In modern Python, module-level objects or Dependency Injection are usually preferred over Singleton unless a true single shared instance is required.

---

# Summary Table

| Pattern | Primary Purpose | Common Use Cases |
|----------|-----------------|------------------|
| Factory | Create objects | APIs, Notifications, ML Models |
| Strategy | Swap algorithms | Payment Systems, ML Algorithms |
| Dependency Injection | Loose coupling | FastAPI, Django, Enterprise Apps |
| Observer | Event notifications | GUI, Messaging, YouTube |
| Decorator | Add behavior | Logging, Authentication |
| Context Manager | Resource management | Files, Databases |
| Builder | Construct complex objects | Configuration Objects |
| Adapter | Interface compatibility | Legacy Systems |
| Repository | Database abstraction | CRUD Applications |
| Singleton | One shared object | Logger, Configuration |

https://docs.python-guide.org/#shipping-great-python-code