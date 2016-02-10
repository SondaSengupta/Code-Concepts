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
