
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

```Javascript

//Non OCP Method: Will only work for anyone named Sonda. To modify, to use different names, you will need to modify the internal of the function.
function PrintMyName(){
 var name = "Sonda";
 console.log("My name is" + name);
}

//More OCP: Now you can pass whatever name you wish as a parameter of the function, and the function works without any internal modification.
function PrintMyName(name){
 console.log("My name is" + name);
}

```

2. Inheritance/Template Method - child types that override base classes or interfaces
3. Composition/Strategy Pattern -find the abstraction, creating an interface, extracting out the logic into separate classes in which each represents a particular node in the decision tree. More info: http://stackoverflow.com/questions/91932/how-does-the-strategy-pattern-work

### Negatives of OCP
-Adds complexity to the design so not suitable for simple things
-It's best to not try OCP at first, but if you see yourself changing the class more than once, then refactor to achieve OCP
-No design can be closed against all changes in code.

### Related Fundamentals
-Single Responsibility Pattern
-Strategy Pattern
-Template Method Pattern
-Recommended Reading: Agile Practices by Robert C. Martin

## The Liskov Substitution Principle
**definition:** child classes should be able to be subsituted for their base classes. Child classes must not remove base class behavior or violate base class invariants.
-A lot of people use the is-a to describe the relationship between child and base classes. With LSP, consider using "is-substitutable-for" as a relationship. For example, a hound is-a base class dog, but a hound is-subsitutable-for dog, meaning it can work for any places that require a dog? Derived classes must not violate any constraints defined (or assumed by clients) on their base classes.

clients - other classes that make use of your class
invariants - 






