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



