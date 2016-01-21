# Introduction to Programming with C#   
## by Svetlin Nakov, Veselin Kolev and team  
**free ebook link:** http://www.introprogramming.info/english-intro-csharp-book/read-online  
**free online .NET compiler to practice your code:** https://dotnetfiddle.net/

###Ch. 11 Creating and Using Objects
**reading link:** http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-11-creating-and-using-objects/
**.NET Compiler:** https://dotnetfiddle.net/  
<br/>

**Classes** are the abstract representation of the thing, while **objects** is the instance or the thing itself. For example, a dog is a class, but Lassie is an instance of dog.  
<br/>
**attributes:** characteristics of objects, defined by member variables. Data is stored in fields, and properties extend the functionality of these fields with extra data management.  
**behaviors**  actions performed by the object, defined by methods

####System Classes
Classes that are defined by system libraries from .NET framework. Often these are not made public because programmers need only to know what they do, not the inner workings of the implementation. Thus, they are encapsulated to prevent modification.

####Creating and releasing Objects
**new** an operator used to create an object from an instance. When this happens, member is set aside for the oncoming data and the data members are initialized through a constructor.
```C#
Dog DogCopter = new Dog();
```
We can also create an object that already has some parameters, and these parameters go through the constructor to be initialized.
```C#
Dog DogCopter = new Dog("Lassie", "Collie");
```
Here is an example of making a Dog class and using the new property to create two dogs, one generic and one special with added parameters.
```C#
using System;
					
public class Dog
{
	//field names
	private string name;
	private string type;
	
	//public properties that outside code can interact with
	public string Name {
		get{ return this.name;}
		set {this.name = value;}
	}
	
	public string Type {
		get {return this.type;}
		set {this.type = value;}
	}
	
	//default constructor
	public Dog(){
		this.Name = "Generic Dogg";
		this.Type = "Generic Mutt";
	}
	
	//constructor with parameters
	public Dog(string name, string type){
		this.Name = name;
		this.Type = type;
	}
	
	// Method Bark
    public void Bark()
    {
		Console.WriteLine("I am {0} the {1} Dog and I say Woof!", name, type);
    }
	
}

public class Program
{
	
	public static void Main()
	{
		Dog someDog = new Dog();
		someDog.Bark();
		
		Dog specialDog = new Dog("Lassie", "Collie");
		specialDog.Bark();
	}
}
============
Output:
I am Generic Dogg the Generic Mutt Dog and I say Woof!
I am Lassie the Collie Dog and I say Woof!
```
####Static Fields and Methods
If a class is a category of objects, static fields and methods relate to the category itself. Static members do not need an instance of the object to be created. They are actually created when the class is used for the first time during the execution of the program. A "utility" class is a class that only has static members.

```C#
using System;
					
public class Program
{
	public class Sequence
{
    // Static field, holding the current sequence value
    private static int currentValue = 0;
 
    // Intentionally deny instantiation of this class
    private Sequence()
    {
    }
 
    // Static method for taking the next sequence value
    public static int NextValue()
    {
        currentValue++;
        return currentValue;
    }
}
	public static void Main()
	{
		 Console.WriteLine("Sequence: {0}, {1}, {2}",
            Sequence.NextValue(), Sequence.NextValue(),
            Sequence.NextValue());
	}
}
========
Output:
Sequence: 1, 2, 3
```

####What are Namespaces?
**namespaces** are logical groupings of classes. If they are nested within each other than they are described using a "Namespace.NestedNamespace" manner. You can give another class access to a particular namespace with a "using". Note that inclusion of a namespace is not recursive. Just because your using says Animal.Dogs does not give you access to Animal.Dogs.Poodles or any nested namespaces within Dogs.






