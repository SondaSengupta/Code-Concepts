## Introduction to Programming with C# by Svetlin Nakov, Veselin Kolev and team  
free ebook link: http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-9-methods/

###Ch. 9 Methods
A method with a variable numnber of arguments uses the 'param' keyword. In the method declaration, you must specify 'params' with the type. For example, below:
```C#
static long CalcSum(params int[] elements) //specifiec variable number of element integers
{
    long sum = 0;
    foreach (int element in elements)
    {
        sum += element;
    }
    return sum;
}
 
static void Main()
{
    long sum = CalcSum(2, 5);
    Console.WriteLine(sum);
 
    long sum2 = CalcSum(4, 0, -2, 12);
    Console.WriteLine(sum2);
 
    long sum3 = CalcSum();
    Console.WriteLine(sum3);
}
```
