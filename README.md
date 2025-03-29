# SOLID Principles

## Introduction
When joining a new project, managing a complex codebase can be challenging. Without proper design patterns, the code can become unmanageable, making it hard to modify or extend. To address this, our team lead has asked us to study the SOLID principles and refactor the codebase accordingly. SOLID is a set of five object-oriented design principles that help developers create scalable, maintainable, and flexible software.

## SOLID Principles

### 1. Single Responsibility Principle (SRP)
* A class should have only one reason to change, meaning it should have only one job.
* This principle helps in making the code more modular and easier to understand and maintain.
* Example:
  ```java
  class Report {
      void generateReport() {
          // Code to generate report
      }
  }
  
  class ReportPrinter {
      void printReport(Report report) {
          // Code to print report
      }
  }
  ```
  Here, `Report` is responsible only for generating the report, while `ReportPrinter` handles printing it, following SRP.

### 2. Open/Closed Principle (OCP)
* A class should be open for extension but closed for modification.
* This means we should be able to add new functionality without changing existing code, reducing the risk of introducing bugs.
* Example:
  ```java
  interface Payment {
      void pay();
  }
  
  class CreditCardPayment implements Payment {
      public void pay() {
          // Payment logic for credit card
      }
  }
  
  class PayPalPayment implements Payment {
      public void pay() {
          // Payment logic for PayPal
      }
  }
  ```
  Here, new payment methods can be added by creating new classes implementing `Payment` without modifying existing code.

### 3. Liskov Substitution Principle (LSP)
* Subtypes must be replaceable by their base types without altering program behavior.
* This ensures that derived classes extend base classes without breaking functionality.
* Example:
  ```java
  class Bird {
      void fly() {
          System.out.println("This bird can fly");
      }
  }
  
  class Sparrow extends Bird {}
  
  class Penguin extends Bird {
      @Override
      void fly() {
          throw new UnsupportedOperationException("Penguins can't fly");
      }
  }
  ```
  Here, `Penguin` violates LSP because it cannot fly, unlike other `Bird` types. A better approach would be to create separate interfaces for flying and non-flying birds.

### 4. Interface Segregation Principle (ISP)
* Clients should not be forced to implement interfaces they do not use.
* Instead of having one large interface, break it into smaller ones, so classes only implement what they need.
* Example:
  ```java
  interface Printer {
      void print();
  }
  
  interface Scanner {
      void scan();
  }
  
  class AllInOnePrinter implements Printer, Scanner {
      public void print() {
          // Print logic
      }
      
      public void scan() {
          // Scan logic
      }
  }
  
  class SimplePrinter implements Printer {
      public void print() {
          // Print logic
      }
  }
  ```
  Here, `SimplePrinter` only implements the `Printer` interface without unnecessary scan functionality, following ISP.

### 5. Dependency Inversion Principle (DIP)
* High-level modules should not depend on low-level modules. Both should depend on abstractions.
* Abstractions should not depend on details. Details should depend on abstractions.
* Example:
  ```java
  interface Database {
      void connect();
  }
  
  class MySQLDatabase implements Database {
      public void connect() {
          // MySQL connection logic
      }
  }
  
  class Application {
      private Database database;
      
      public Application(Database database) {
          this.database = database;
      }
      
      void start() {
          database.connect();
      }
  }
  ```
  Here, `Application` depends on `Database` abstraction rather than a specific database implementation, making it more flexible.

## Conclusion
Applying SOLID principles enhances the maintainability, scalability, and readability of a project. It helps in writing cleaner, more reusable, and testable code. By refactoring our codebase using these principles, we can ensure that our software is robust and easier to extend in the future.

## References
* [DigitalOcean - SOLID Principles](https://www.digitalocean.com/community/conceptual_articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design)
* [SOLID Principles YouTube Playlist](https://www.youtube.com/playlist?list=PL6n9fhu94yhXjG1w2blMXUzyDrZ_eyOme)
