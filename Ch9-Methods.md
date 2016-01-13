# Introduction to Programming with C#   
## by Svetlin Nakov, Veselin Kolev and team  
**free ebook link:** http://www.introprogramming.info/english-intro-csharp-book/read-online  
**free online .NET compiler to practice your code:** https://dotnetfiddle.net/

###Ch. 9 Methods  
**reading link:** http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-9-methods/  
**.NET Compiler:** https://dotnetfiddle.net/  
<br/>
**params** - A method with a variable numnber of arguments uses the 'param' keyword. In the method declaration, you must specify 'params' with the type. Note: if you have multiple arguments, params variable should always be the last statement.

```C#
using System;


public class Program {

    static long CalcSum(params int[] elements) //specifiec variable number of element integers
    {
        long sum = 0;
        foreach (int element in elements)
        {
            sum += element;
        }
        return sum;
    }
    
    public static void Main()
    {
        long sum = CalcSum(2, 5);
        Console.WriteLine(sum);
    
        long sum2 = CalcSum(4, 0, -2, 12);
        Console.WriteLine(sum2);
    
        long sum3 = CalcSum();
        Console.WriteLine(sum3);
    }
};
----------------------	
Output: 
7
14
0
```
**optional paramaters** You can declare a method with optional parameters.  
```C#
static void SomeMethod(int x, int y = 5, int z = 7)
{
}

static void Main()
{
    // Normal call of SomeMethod
    SomeMethod(1, 2, 3);
    // Omitting z - equivalent to SomeMethod(1, 2, 7)
    SomeMethod(1, 2);
    // Omitting both y and z – equivalent to SomeMethod(1, 5, 7)
    SomeMethod(1);
}

```

**named arguments** You can name the arguments when passing it into a method and if so, can do your own ordering

```C#

static void SomeMethod(int x, int y = 5, int z = 7)
{
}

static void Main()
{
    // Passing z by name and x by position
    SomeMethod(1, z: 3);
    // Passing both x and z by name
    SomeMethod(x: 1, z: 3);
    // Reversing the order of the arguments passed by name, thus 3 will be computed before x
    SomeMethod(z: 3, x: 1);
}
```
**Best Practices**  
The most important rule is that a method should either do what it name says or throw an exception. If a method cannot perform its job (e.g. due to incorrect input), it should throw an exception, not return invalid or neutral result. How to throw an exception will be explained in the chapter “Exception Handling”, but for now you should remember that returning an incorrect result or having a side effect are bad practices. If a method cannot do its job, it should inform its caller about this by throwing appropriate exception. Methods should never return wrong result!
