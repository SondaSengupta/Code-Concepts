# Introduction to Programming with C#   
## by Svetlin Nakov, Veselin Kolev and team  
**free ebook link:** http://www.introprogramming.info/english-intro-csharp-book/read-online  
**free online .NET compiler to practice your code:** https://dotnetfiddle.net/

###Ch. 12 Exception Handling
**reading link:** http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-12-exception-handling/
**.NET Compiler:** https://dotnetfiddle.net/  
<br/>

**Exception** a notification that something interrupts the normal program execution. The normal execution is saved and then control is passed to an exception handler. It is provided internally by CLR (runtime). 

An example of program that gives a file not found exception:
```C#
using System;
using System.IO;
					
public class Program
{
    public static void Main()
    {
        string fileName = "WrongTextFile.txt";
        ReadFile(fileName);
    }
 
    static void ReadFile(string fileName)
    {
        TextReader reader = new StreamReader(fileName);
        string line = reader.ReadLine();
        Console.WriteLine(line);
        reader.Close();
    }
}
========
OUTPUT:

Run-time exception (line 14): Could not find file 'C:\Resources\directory\878e888df5e74382bae17bafe6aed3c1.DotNetFiddle.Web.LocalResources\Sandbox\02624779-1eb2-4d4d-af08-ded23fd2d012\WrongTextFile.txt'.

Stack Trace:

[System.IO.FileNotFoundException: Could not find file 'C:\Resources\directory\878e888df5e74382bae17bafe6aed3c1.DotNetFiddle.Web.LocalResources\Sandbox\02624779-1eb2-4d4d-af08-ded23fd2d012\WrongTextFile.txt'.]
  at Program.ReadFile(String fileName): line 14
  at Program.Main(): line 9

```

####How to read a stack trace?
During normal execution, a new method is pushed to the top of the stack, as it gets implemented, the CLR goes back to the original method that the new method is called from and so on and so forth. Handling exceptions start with the closest method that produced the exception, then goes through the stack until it is handled by an exception handler or the CLR itself. 

For example, we found the exception was first produced by newing up a StreamReader, on line 14. Then this exception bubbles up to the method that called the ReadFile method, which was Main() on line 9.

Strack Trace lines follow this pattern:
at <namespace>.<class>.<method> in <source file> : line <line#>

For example:
```C#
System.IO.FileNotFoundException: Could not find file 
/// <namespace>.<class>.<fullExceptionName>. Since it is a .NET assembly, no line or source file is given.

at Program.ReadFile(String fileName): line 14 
at Program.Main(): line 9
///<namespace>.<class>.<method> in <sourceFile> : line <lineNumber>
```









