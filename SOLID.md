
## What is SOLID?
SOLID is a group of design principles that when combined together provide a good roadmap for effective, maintainable object-oriented code. SOLID stands for:
- **S**: single responsibility principle
- **O**: open-closed principle
- **L**: Liskov substitution principle
- **I**: interface segragation principle
- **D**: dependency injection principle

## Open-Closed Principle
**definition:** software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification. In other words, when you need to modify your software, you should not need to dig through internals to change it. You should be able to add new functions or classes to extend upon the already existing classes and functions. i.e. you don't need to perform chest surgery to put on a coat.  
-You can do this by using abstractions through interfaces and abstract base classes. In procedural code, we can add parameters to functions. Introducing "seams" where parts of the application can be easily divided and replaced.

### Three Ways of Acheiving the Open-Closed Principle
1. Parameters (procedural programming) - allow the client to control behavior through parameters in methods. Combined with delegats/lambdas can be powerful. This is sometimes means attributing state to a function. 
2. Inheritance/Template Method - child types that override base classes or interfaces
3. Composition/Strategy Pattern -find the abstraction, creating an interface, extracting out the logic into separate classes in which each represents a particular node in the decision tree.

### Negatives of OCP
-Adds complexity to the design so not suitable for simple things
-It's best to not try OCP at first, but if you see yourself changing the class more than once, then refactor to achieve OCP
-No design can be closed against all changes in code.

### Related Fundamentals
-Single Responsibility Pattern
-Strategy Pattern
-Template Method Pattern
-Recommended Reading: Agile Practices by Robert C. Martin

## The Liskov Substitution Princple




