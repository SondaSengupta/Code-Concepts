Started: 4:41pm

##Ch. 13 Strings and Text Processing

**string** - a series of characters in a specific address in memory. Each character is from a Unicode table of 100,000 characters, which replaces the former ASCII table that only had 128 characters that it could fit.

####The System.String Class
We use the System.String class to use strings, and strings are stored in memory as an array of chars. We can also use char[] instead of string, but the disadvantages is that you must know the length of the array beforehand and it is manually processed char by char. Chars are a value type so the value itself, and not the reference is stored in memory. For strings, it is stored in dynamic memory (managed heap) which keeps a reference of the object created from the string class.

```C#
string aString = "hello!";
char[] anArray = {'h', 'e', 'l', 'l', 'o', '!'};
```

 - strings are immutable. If a value inside were to change, the reference would change to the new value. They cannot be modified. You can use an indexer to such as aString[2] (which is 'e') to read it, but you can't say aString[2] = 's' to make it something else.
 
####String Escaping
- use an escape slash  followed by the escaping character
```C#
string aString = "This is Sonda\'s site"; // notice the backlash followed by escaping character
```
 
####Declaring a String
```C#
string Declaration;
```
- Note you are just saying that I'm going to have a string. You are not setting it to a variable or allocating memory just yet! Right now, the value is null (equavalent to no value). If you try to manipulate this null value, it will give you a null reference exception.

####Initializing a String
**instatiating** the process of allocating memory when creating a variable from a class. You can do this by literally setting the string, by providing an expression that outputs to a string, or referencing something that is a string.

- When you instatiate one string by equating it to another string, what you are actually saving is a reference. 


 
 
 




