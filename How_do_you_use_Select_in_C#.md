
###What does "Select" do in C#?  
**reading link:** https://msdn.microsoft.com/library/bb548891(v=vs.100).aspx  
**.NET Compiler:** https://dotnetfiddle.net/  
<br/>
```C#
public static IEnumerable<TResult> Select<TSource, TResult>(
	this IEnumerable<TSource> source,
	Func<TSource, TResult> selector
)
```

**Select** - a method given as part of the IEnumerable class that allows you to do something to each element within that Enumerable. Note that the select is deferred execution, meaning that when a select is made, the compiler keeps the information to do it, but it does not actually perform the execution unless there is a foreach loop. The Select Many has immediate execution.


```C#
using System;
using System.Linq;
using System.Collections.Generic;
					
public class Program
{
	public static void Main()
	{
		
		IEnumerable<int> squares = Enumerable.Range(1, 10).Select(x => x * x);
		
		foreach (int num in squares)
		{
			Console.WriteLine(num); //print out each item in squares
		}
	
	}
}
----------------------	
Output: 
4
9
16
25
36
49
64
81
100
```
