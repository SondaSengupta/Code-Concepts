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
- the constructor's task is to initialize the memory where the fields will be stored.
- Use 'base' when there is inheritance, and a parent class already provides the functionality that you're trying to achieve.
- Use 'this' when you want to reference its own class when you don't want to duplicate functionality that is already defined in another constructor.
- Basically, using 'base' and 'this' in a constructor's header is to keep your code DRY, making it more maintainable and less verbose.

```C#
using System;

public class Person
{

    public Person(string name)
    {
        Console.WriteLine("My name is " + name + ".");
    }
}

public class Employee : Person
{
	//'base' calls an inheriting constructor, the Person constructor in this case.
	//then Employee constructor can add onto this with food.
    public Employee(string name, string food)
        : base(name)
    {
        Console.WriteLine("My name is " + name + " and I love " + food + ".");
    }

	//'this' calls a constructor within its own class that matches the same number/type of paramaters
	// thus, an empty employee constructor can produce an instance with default values by reusing a constructor already made.

	//1) The empty Employee() constructor is called from the program.
	//2) Noticing the 'this' constructor, the compiler matches these parameters to a known constructor, which is Employee(name, food) above.
	//3) Going to Employee(name, food), the compiler sees that it is using 'base' inherited constructor, so goes to Person(name).
	//4) The compiler executes Person(name) with name being James Bond.
	//5) The compiler then can execute Employee(name, food) which is James Bond and Martinis, specified from 'this'
	//6) Then, the compiler goes back to Employee() constructor and executes what is within these brackets last.
    public Employee() : this("James Bond", "Martinis")
    {
		Console.WriteLine("Shaken not stirred.");
    }
}

public class Program
{
	public void Main(){
		var Amy = new Person("Amy");
		var TheDoctor = new Employee ("The Doctor", "Jelly Babies");
		var Jeff = new Employee();
	}
}
=========
OUTPUT:
My name is Amy.
My name is The Doctor.
My name is The Doctor and I love Jelly Babies.
My name is James Bond.
My name is James Bond and I love Martinis.
Shaken not stirred.
```

#### Parameterless Constructor versus Default Constructor
- If we declare at least one constructor in a given class, the compiler will not create a default constructor for us.
- The default implicit constructor is created by the compiler, if we do not declare any constructor in our class, but a parameterless constructor is created by us.
- The default constructor will always have access level protected or public, depending on the access modifier of the class, while the level of access of the constructor without parameters all depends on us – we define it.

### Properties
- Properties are elements that are somewhere in between methods and fields. Like fields, they are used to help store data, but do so by ensuring the data is encapsulated and validated before stored. Like methods, they have up to two methods/actions within themselves for getting and setting fields.
- A getter always has a return value.
- A setter always uses a hidden "value" to assign it to some field.
- For simple classes, fields do not have to be defined. You can define only properties, called automatic properties, and the compiler will make the fields for you. However, if you expressly define fields yourself, you will have more control over the data's use.

```C#
public class Dog
{
	private int age;

	public int Age {
		get { return this.age; }
		set {
			// Take precaution: perform check for correctness
			if (value < 0)
			{
				throw new ArgumentException(
					"Invalid argument: Age should be a positive number.");
			}
			// Assign the new correct value
			this.age = value;
		}
	}

	public Dog (int howOld)
	{
		this.Age = howOld;
	}
}

public class Program
{
	public void Main()
	{
		Dog dog2 = new Dog(-5);
	}
}
====
// OUTPUT:
//Run-time exception (line 17): Invalid argument: Age should be //a positive number.

//Stack Trace:

//[System.ArgumentException: Invalid argument: Age should be a //positive number.]
//  at Dog.set_Age(Int32 value): line 17
//  at Dog..ctor(Int32 howOld): line 23
//  at Program.Main(): line 31
````

### Static Classes and Static Members
- **static elements** are properties, fields, and methods within a class with the static keyword in front. The behavior is not dependent on the object state.
- Normally, each created object will have its own copy of fields, methods, and properties and will not be able to access each other's elements. Objects have no way of sharing information.
- Static elements of the class can be used without creating an object of the given class. If objects are created, then there will be one copy of these elements and these will be shared among all objects of its class.
- Static elements and methods cannot access non-static elements because static elements deal on the class-level and do not "know" about individual data of objects. Thus, "this" keyword will error out on static methods.
- Static properties can be accessed only through dot notation, applied to the name of the class in which they are declared.
- When all the members are static, you can define a whole class as being static. If a class is static, it can have a static constructor in which the constructor is used only once when the object of a class is created or one of the members is accessed.

```C#
using System;

public class Kids
{
	static int ClassNumber = 0;
	public string Name;
	public int Age;


	public Kids(string name, int age){
	this.Name = name;
	this.Age = age;
	}

	public static int AddtoClass(){
		ClassNumber++;
		return ClassNumber;
	}

	public void SayHello() {
		Console.WriteLine("Hello, my name is {0} and I am {1} years old.", Name, Age);
	}

	public static void Count(){
		Console.WriteLine("There are {0} kids in this class.", ClassNumber);
	}

	public void ShowClassSize(){
		Console.WriteLine("My class is {0} big.", ClassNumber);
		//nonstatic elements can still access static elements.
	}

	public void SelfAddingtoClass(){
		//non-static methods can still access static methods.
		AddtoClass();
	}

	public static void Main()
	{
		Kids Sally = new Kids("Sally", 5);
		Sally.SayHello();
		Kids.AddtoClass();
		Kids.Count();

		Kids Robby = new Kids("Robby", 6);
		Robby.SayHello();
		Kids.AddtoClass();

		//Robby.Count();
		//Since Count() is a static method, it cannot be accessed with an instance
		//of the object (Robby). Can only be accessed by the type, Kids.

		Kids.Count();

		Kids Lisa = new Kids("Lisa", 3);

		//But you can call an instance method that which itself calls that static method.
		Lisa.SelfAddingtoClass();
		Lisa.ShowClassSize();


	}
}
==========
// OUTPUT:
// Hello, my name is Sally and I am 5 years old.
// There are 1 kids in this class.
// Hello, my name is Robby and I am 6 years old.
// There are 2 kids in this class.
// My class is 3 big.
```
### Constants
**constants** are elements that always have the same value once they are initialized. There are two types: compile time constants and runtime constants called with readonly.
- Constants are in PascalCase. Sometimes people use ALL_CAPS.
- Values, which occur more than once in the program or are likely to change over time, must be declared as constants. That way you have one place to change the constant for the whole program.

Compile Time Constants:
- Example: public const double PI = 3.141592653589793;
- Can only be created at the same time they are declared.
- Constants declared with modifier const must be of primitive, enumeration or reference type, and if they are of reference type, this type must be either a string or the value, that we assign to the constant, or it must be null. Meaning, the compiler must be able to assign it a value right upon creation. No looking up classes and going through a constructor to figure it out.
- These constants are only assigned during compilation.

RunTime Constants (ReadOnly):
- To declare reference type constants, you must use "static readonly". Example: public static readonly Color White = new Color(255, 255, 255);
- These constants are assigned when the program is running.

### Structures
- classes are reference types that store addresses in its stack and the values in heap memory.
- structures or structs use only value types. Thus, it can result in very interesting behavior. For example, for method parameters, the method will create a copy of the arguments and then use it, instead of using the address and passing it in.
-Classes are used more often than structures. Use structs as exception, and only if you know well what are you doing!

### Enumerations
- **Enumerated Types** are logically connected constants. An enumeration is a class whose members are only constants.
- Each constant in one enumeration is actually a textual representation of an integer. By default this number is the constant’s index in the list of constants of a particular enumeration type.
- When we modify the list of constants in an existing enumeration, we should be careful not to break the logic of the code that already exists and uses the constants, declared so far.

```C#
using System;

namespace Diner
{
	public enum Size
	{
		small = 6,
		medium = 8,
		large = 16,
		mega = 32
	}

	public class Drink
	{
		public string Name;
		public Size oz;
		public Drink(string name)
		{
			this.Name = name;
		}

		//Using the Size enum ensures the user can only pick a valid Size from that enum.
		public Drink(string name, Size oz): this (name)
		{
			this.oz = oz;
		}
	}

	public class Program
	{
		public static void Main()
		{
			Drink martini = new Drink("Martini");
			Console.WriteLine("I want to order a {0} drink.", Size.small);
			Console.WriteLine("The large drink is {0} ounces!", (int)Size.large);
			Drink tea = new Drink("tea", Size.small);
			Console.WriteLine("I ordered a {0} which is the {1} size.", tea.Name, tea.oz);
			Console.WriteLine("The {0} is {1} ounces.", tea.Name, (int)tea.oz);
		}
	}
}
==========
OUTPUT:
I want to order a small drink.
The large drink is 16 ounces!
I ordered a tea which is the small size.
The tea is 6 ounces.
// https://dotnetfiddle.net/1cLSCD
```

### Inner Classes (Nested Classes)
- nested classes are used sparingly but they are created for two reasons. The first reason is that there is a logical relationship between the outer and inner classes, such that it may not make sense to have an inner class all on its own. Second, you may want to hide elements by putting them in a nested class.
- Within a nested class, "this" will only represent the object of the nested class, not any outer class elements.

Example:
``` C#
using System;
using System.Collections.Generic;

public class House
{
	string address;
	List<Room> room;

	House(string address, List<Room> room) {
		this.address = address;
		this.room = room;
	}

	enum Location {
		urban,
		rural,
		suburban,
	}

	public class Room {

		string color;
		string name;

		public Room (string color, string name) {
			this.color = color;
			this.name = name;
		}

	}


	public static void Main()
	{
		List<Room> rooms = new List<Room>();
		Room livingRoom = new Room("yellow", "living room");
		rooms.Add(livingRoom);
		Room kitchen = new Room("white", "kitchen");
		rooms.Add(kitchen);
		Room bedroom = new Room("blue", "bedroom");
		rooms.Add(bedroom);


		House FirstListing = new House("123 Elm Street", rooms);

		var numberOfRooms = FirstListing.room.Count;
		Console.WriteLine("The house on {0} has {1} rooms.", FirstListing.address, numberOfRooms);
	}
}
====
OUTPUT:
The house on 123 Elm Street has 3 rooms.
link: https://dotnetfiddle.net/Mr4fsM
```
=======
### Generics
- **generics** are special classes that allow the compiler to ready the class without knowing the type of objects inside initially.
- once an object of that generic class is created, that object's type are only of that type and cannot be changed.
- Typifying a class (creating a generic class) means to add to the declaration of a class a parameter (replacement) of unknown type, which the class will use during its operation. Subsequently, when the class is instantiated, this parameter is replaced with the name of some specific type.

#### Declaring a Generic Class
- The <> is obligatory to specify parameters for the class. The "T" represents what type we'll be passing in upon instantiation.

``` C#
class AnimalShelter<T>
{
    // Class body here …
}

//
AnimalShelter<Dog> dogsShelter = new AnimalShelter<Dog>();
AnimalShelter<Cat> catsShelter = new AnimalShelter<Cat>();
```
