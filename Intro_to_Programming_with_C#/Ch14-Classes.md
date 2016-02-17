# Ch. 14 Defining Classes

**reading link:** http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-14-defining-classes/
<br/>
**.NET Compiler:** https://dotnetfiddle.net/

### Custom Classes
**class** : a given definition (specification) or pattern that describes a concept in the real world.
**object** : a copy or an instance of the class that has a state.
For example, the object "Pug" is of Type "Dog". Dog is the class and a type of dog is pug.

#### What does a class contain?
- objects of a class hold its data and the data define's an object's state.
- the class defines the behavior of an object, represented by actions or methods that objects can do

### Elements of a class
- class declaration with a class body that contains methods, constructors, properties, and fields.

```C#
using System;

public class Lion //class declaration
{
	private string color; //field

	public string Color {  //property
		get {return color;}
		set	{color = value;}
	}
	public string Name {get; set;} //property

	public Lion(){ //parameterless constructor
	}

	public Lion(string color, string name){ //parametered constructor

		this.Color = color;
		this.Name = name;
	}

	public void Speak(){ //method
		Console.WriteLine("{0} goes Rawr!", Name);
	}

}

//an example program below that uses the Lion class to create two lions.
public class LionFactory
{
	public void Main(){
		Lion Leo = new Lion("yellow", "Leo");
		Leo.Speak();

		Lion Unnamed = new Lion();
		Unnamed.Speak();
	}
}
===============
OUTPUT:
Leo goes Rawr!
 goes Rawr! <--Without a name, the subject is left blank.
```

#### Nature of Objects
- an object has two parts: the data which stores state and the reference, a variable that stores the object's address of where the data is stored.
- an object's data is stored in dynamic heap memory and its reference is stored as a primitive value in program's stack memory.
- When an object has a null reference, it means that the object has been declared, but it has a null value: a null address because and no data in heap memory to point to.

### Organizing Classes in Files and Namespaces
- classes must be saved with file extension ".cs"
- Recommended that one class is stored in one file named the name of the class.

#### Organizing Classes in Namespaces
**namespace** : a named group of classes that logically go together. There is no code requirement of which classes belong to a namespace; the programmer decides.

- If you want to use a particular namespace, then you need to have a "using" directive in order to reference it within another namespace.
- Since .NET compiled code is represented as Unicode, it is possible to code more than just English and Latin. However, if one wishes do this and make the Visual Studio file readable, you will have to change the character encoding away from its default (which is usually your local region) to another character encoding such as UTF-8 for Arabic letters or Chinese. English is the most common coding language though.

### Modifiers and Access Levels
**public** : element can be accessed from any class
**private** : element can only be accessed from the class it is defined. No other classes can access it, even if other classes exist within the same namespace.
**internal** : element can only be accessed from the same assembly, i.e. the same project within Visual Studio.
**protected** : elements that are not visible to users of the class (other classes that initialize it or use it), but are visible to the inheriting classes.
**protected internal** : an element that can be accessed within the same Visual Studio project and visible to inheriting classes, even outside assemblies.
**sealed**: element that cannot be inherited by other classes.

#### What is an assembly?
**assembly** : a collection of compiled types (classes and other types) which their resources, which are stored in one large binary file called an .exe or .dll file. Every time you compile a .NET application, one or several assemblies or made by the compiler and stored as an .exe or .dll file.

### Declaring Classes
- we say one class can access another when 1) an instance of the other object can be created 2) can access methods and elements of the other class.
- public classes can be used by all namespaces.
- private classes can only be accessed within the class its in.
- internal classes can only be used within the namespace it resides in.
- Classes are in PascalCase and are Nouns.

### The Reserved Word "This"
- **this** : a reserved word that means it is referencing the current object. The object changes depending upon where "this" is used.

### Fields
**fields** : member variables that hold the state of the object. The states are different depending on each instance of the class, each different object.

- the scope of a class field begins from where it is declared and ends at the last bracket of a class's body.
- local variables, such as seen in methods must be initialed with a value and leads to a compilation error since they are not given defaults.
- when a field is created, unless specified otherwise .NET sets it to a zeroed value or null if it's an object.

```C#
using System;

public class Dog
{
    string name;
    int age;
    int length;
    bool isMale;

    public static void Main()
    {
        Dog dog = new Dog();
        Console.WriteLine("Dog's name is: " + dog.name);
        Console.WriteLine("Dog's age is: " + dog.age);
        Console.WriteLine("Dog's length is: " + dog.length);
        Console.WriteLine("Dog is male: " + dog.isMale);
    }
}
=========
Dog's name is:
Dog's age is: 0
Dog's length is: 0
Dog is male: False
```
#### Fields "const" and "readonly"
- these are constants that have one value that is used several times.
- const fields are declared and initialized in one go and do not change afterwards. They are also called compile-time constants because code that includes this field is replaced by the value itself during compiling.
- readonly fields are either initialized during declaration or given a value in the constructor, and then cannot be changed. They are set during the execution of the program, or runtime, making it a runtime variable.

### Methods
```C#
// How a method is defined:
[<modifiers>] [<return_type>] <method_name>([<parameters_list>])
{
    // … Method's body …
    [<return_statement>];
}
```

### Accessing Non-Static Data of the Class
- The access to the non-static elements of a class (fields and methods) is done via the reserved word this and the operator for access – "dot".
- It is also possible not even use the word "this"

### Hiding Fields with Local Variables
- When using a method with a local variable, it will be used instead of a field of the same name.
- Sometimes, you have to use the field, even if there is a same name local variable, and in such cases, you can use "this" to refer to the object instance itself.

```C#
using System;

    public class OverlappingScopeTest
{
    int myValue = 3;

    void PrintMyValue()
    {
        Console.WriteLine("My value is: " + myValue);
    }

    public void Main()
    {
        OverlappingScopeTest instance = new OverlappingScopeTest();
        instance.PrintMyValue();

		int myValue = 5;
		Console.WriteLine("Using overlapping local variable, it is: " + myValue);

		Console.WriteLine("This will use the field instead of local: " + this.myValue);
    }
}
========
OUTPUT:
My value is: 3
Using overlapping local variable, it is: 5
This will use the field instead of local: 3
```

### Visibility of Fields and Methods
- If two classes are not visible one to other, then their members (fields and methods) are not visible also, regardless of what kind of access levels their elements have.

### Constructors (Ctors)
