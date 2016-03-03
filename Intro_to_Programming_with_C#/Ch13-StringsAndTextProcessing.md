# Ch. 13 Strings and Text Processing

**reading link:** http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-13-strings-and-text-processing/
**.NET Compiler:** https://dotnetfiddle.net/


**string** - a series of characters in a specific address in memory. Each character is from a Unicode table of 100,000 characters, which replaces the former ASCII table that only had 128 characters that it could fit.

## The System.String Class
We use the System.String class to use strings, and strings are stored in memory as an array of chars. We can also use char[] instead of string, but the disadvantages is that you must know the length of the array beforehand and it is manually processed char by char. Chars are a value type so the value itself, and not the reference is stored in memory. For strings, it is stored in dynamic memory (managed heap) which keeps a reference of the object created from the string class.

```C#
string aString = "hello!";
char[] anArray = {'h', 'e', 'l', 'l', 'o', '!'};
```

- strings are immutable. If a value inside were to change, the reference would change to the new value. They cannot be modified. You can use an indexer to such as aString[2] (which is 'e') to read it, but you can't say aString[2] = 's' to make it something else.

## String Escaping
- use an escape slash  followed by the escaping character
- string aString = "This is Sonda\'s site"; // notice the backlash followed by escaping character

## Declaring a String

```C#
string Declaration;
```

- Note you are just saying that I'm going to have a string. You are not setting it to a variable or allocating memory just yet! Right now, the value is null (equavalent to no value). If you try to manipulate this null value, it will give you a null reference exception.

## Initializing a String
**instatiating** the process of allocating memory when creating a variable from a class. You can do this by literally setting the string, by providing an expression that outputs to a string, or referencing something that is a string.

- When you instatiate one string by equating it to another string, what you are actually saving is the address. Since strings are immutable, when you modify a string, a copy of the changed string is created and this address change only affects <i>itself</i>.

```C#
using System;
using System.IO;

public class Program
{
	static string first = "First address";
	string copy = first;

	public void Main(){
		Console.WriteLine(first);
		Console.WriteLine(copy);


		first = "The first address has moved!";
		Console.WriteLine(first);
		Console.WriteLine(copy);
	}
}
===============
OUTPUT:
First address
First address
The first address has moved!
First address //the copy still retains original address
```
Note: This is not true for the rest of the reference types (the normal, mutable types) because with them the changes are made directly in the address in memory and all references point to this changed address.

#### Reading and Printing to the Console

```C#
using System;
using System.IO;

public class Program
{
	public void Main(){
		Console.WriteLine("Input Something:");
		string input = Console.ReadLine();
		Console.WriteLine(input);
	}
}
======
OUTPUT:
> Input Something:
Hello //that's my input
Hello //that's my output
```
### String Operations

- **Equals()** : StringA.Equals(StringB) : Returns true/false, checking letter by letter including casing.
- **Equals(,  StringComparison.CurrentCultureIgnoreCase)** : StringA.Equals(StringB,  StringComparison.CurrentCultureIgnoreCase) : Returns true/false, checking letter by letter ignoring casing.
- **CompareTo() and Compare()**: Compares two strings showing alphabetical order. Small letters come before capital letters by default, unless you choose to ignore case.
  - (-1) If first string is alphabetically before second string
  - (0) Like Equals() in that it matches letter by letter, including casing and length.
  - (+1) If second string is alphabetically before first string.

### String Interning
```C#
using System;
using System.IO;

public class Program
{
	string first = "Word";

	static string firstpart = "Wo";
	string second = firstpart + "rd";

	public void Main(){
		Console.WriteLine(first.Equals(second));
	}
}
====
OUTPUT:
True
```

Considering that string first and string second have different addresses in dynamic memory, they should be false right? So why does the above program output true? It is because of interning.

**string interning** : In .NET, for memory optimization the compiler prevents the creation of duplicate strings in memory by giving strings that have the exact same values the same address. During <i> initialization </i> the memory checks invisibly whether the string already exists and if it does, it assigns it the same address. If the string is not initialized (say if using as StringBuilder), then it will be false, until initialization.

```C#
using System.Text;
using System;

public class Program
{
	string declared = "Intern pool";
	static string built = new StringBuilder("Intern pool").ToString();
	string interned = string.Intern(built);

	public void Main(){
		Console.WriteLine(object.ReferenceEquals(declared, built));
		Console.WriteLine(object.ReferenceEquals(declared, interned));
	}
}
====
OUTPUT:
False
True
```
#### Operations for Manipulating strings
To be continued...


#### Binary and Text Streams

