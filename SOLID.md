
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
-Polymorphism also states that a derived class may be treated as objects of a base class in places such as method parameters, collections, or arrays. 

clients - other classes that make use of your class

### LSP Violation Code Smells
-If you are calling on base properties to perform an action. It's better to have the base class just call a method that uses it's own properties.
-if you doing a lot of if then checks that use passed in properties.
-"Tell Don't Ask" = don't interogate an object for their internal, rather you should just tell the object to perform an action.
-If you have a child type that inherits from the base class or interface, but does not actually fully implement that interface.

``` C#

public abstract class Shape
{
  public abstract int Area();
}

public class Rectangle : Shape 
{
 public int Height {get; set;}
 public int Width {get; set;}
 
 public override int Area()
 {
  return Height * Width;
 }
 
}

public class Square : Shape
{
 public int Length { get; set: }

 public override int Area()
 {
  return Length * Length;
 }
}

public void Main()
{
  var shapes = new List<Shape>
  {
   new Rectangle{ Height = 5, Width = 10},
   new Square {Length = 5}
  }
  var areas = new List<int>()
  foreach(Shape shape in shapes)
  {
   areas.Add(shape.Area()); //See how you just tell it do calculate area and the child classes will calculate area for itself.
  }
}

```
## The Interface Segregation Principle

When you use an interface you must use all of its required methods, but you should not create a massive interface that forces a class to use all those methods, even ones that it has no need to use. 

Violations of the interface segregation result into a lot of coupling, which reduces flexibility and maintainability. This also violates the Liskov substitution principle if you have a base class that has an interface and a child class that has the same interface but with not implemented exceptions.

**Ways to combat this:**
- Make small, many interfaces if needed instead of a Fat interface, so classes will fully implement only the methods they need.
- If a Fat interface is from a 3rd party, such certain .NET interfaces, then use an "adapter" in between, an interface that has only the components you need from the fat one, everywhere else in your code.
- Remember overall, you only need to refactor when a code smell becomes a pain point or a problem.

## The Dependency Inversion Principle

Would you solder a toaster directly into the wall? No, of course not, you would use an electrical plug and a wall outlet. This common interface allows us to the knowledge that we can implement anything with this type plug to the wall. Dependency Inversion allows us to do the same thing. It is writing our classes in such a way that our dependencies are exposed as interfaces, so then we can pass the implementations around just like plugs and an outlet.

**The Hollywood Principle:**
"Don't call us; we'll call you" Instead of a class asking for what it needs within it, the class goes out and fetches all it needs in the beginning.

**Three Primary Techniques**
Constructor Injection - instance of the strategy pattern where the class self-document what they need to perform work and classes are always in a valid state once constructed. Cons are that classes can have many parameters/dependencies, may require a default constructor such as serialized, and it effectively makes it so all methods require all dependencies even if that's not true since you are asking for all dependencies in order to create a class.
Property Injection
Parameter Injection















