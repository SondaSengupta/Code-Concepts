# Ch. 16 Linear Data Structures

**reading link:** http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-16-linear-data-structures/  
**.NET Compiler:** https://dotnetfiddle.net/

###Exercises:
- Use the list class to find all prime numbers within a range. For example, all prime numbers between 200-300.
- Use stack to write a program that checks whether the correct amount of brackets are placed for this expression: "1 + (3 + 2 - (2+3)*4 - ((3+1)*(4-2)))"

### Abstract Data Structures
- a **data structure** is an ordered set of data organized based on logical and mathematical expressions, done in order to efficiently complete tasks (adding, removing, sorting, etc.) and save memory space.
- an **abstract data type (adt)** provides the definition of a data structure by defining its operations and properties.

#### Basic Data Structures in Programming
-     Linear – these include lists, stacks and queues
-     Tree-like – different types of trees like binary trees, B-trees and balanced trees
-     Dictionaries – key-value pairs organized in hash tables
-     Sets – unordered bunches of unique elements
-     Others – multi-sets, bags, multi-bags, priority queues, graphs, etc...

### Static versus Dynamic Implementation of Data Structures
- a static implementation of a data structure is when the size of it is fixed and memory is allocated at compile time. When the structure is filled, under-the-hood it must create a new structure that is usually twice the original size and move all elements over. There is the risk of using memory inefficiently since an unused buffer may be large (such as an array-based implementation). Most data structures such as list, queue, stack are done in a static, array based implementation.
- a dynamic implementation of a data structure is when the size is calculated during execution and the structure only uses the amount of memory/size it needs. This is more difficult to code since the program must keep up with its items and location at all times (such as linked list). In C#, you would have to make your own custom class of queue, stack, and list utilizing the LinkedList class in order to get a dynamic implementation of these data structures. C# natively supports linked list, which is a double linked list.

### List Data Structures
- a list is an ordered sequence of elements. A list data structure is arranged consequetively and has a property length, which is a count of the elements within it.  
- arrays have a fixed size that you have to specify before you create the array. If you want to expand the array than you will have to make a new array that is larger in size and then copy the information over.

### List Class
- it keeps its elements in an array. The list already has a certain size, and when it grows it doubles in size, so there is always a used and unused buffer
- search by index is very fast because it's just an array underneath. Search by value is very slow. Adding and removing elements is also slow because we have to shift elements over.
- adding a new element is generally very fast


### Linked List Class
- This class is a dynamic implementation of a doubly linked list built in .NET Framework. Its elements contain a certain value and a pointer to the previous and the next element.
- The append operation is very fast, because the list always knows its last element (tail).
- Inserting a new element at a random position in the list is very fast (unlike List<T>) if we have a pointer to this position, e.g. if we insert at the list start or at the list end.
- Searching for elements by index or by value in LinkedList is a slow operation, as we have to scan all elements consecutively by beginning from the start of the list.
- Removing elements is a slow operation, because it includes searching.
- Using LinkedList<T> is preferable when we have to add / remove elements at both ends of the list and when the access to the elements is consequential. However, when we have to access the elements by index, then List<T> is a more appropriate choice.
-LinkedLists generally take up more memory than lists because in addition to the data being stored, you also have to store pointers.

### Stacks
- The stack is a data structure, which implements the behavior "last in – first out" (LIFO). 
- ADT stack provides 3 major operations: push (add an element at the top of the stack), pop (take the last added element from the top of the stack) and peek (get the element form the top of the stack without removing it).

### Queue
- In queues we can add elements only on the back and retrieve elements only at the front.  "first in – first out" (FIFO).
- Queue<T> class provides the basic operations, specific for the data structure queue. Here are some of the most frequently used: Enqueue(T) – inserts an element at the end of the queue; Dequeue() – retrieves the element from the beginning of the queue and removes it; Peek() – returns the element from the beginning of the queue without removing it; Clear() – removes all elements from the queue; Contains(T) – checks if the queue contains the element; Count – returns the amount of elements in the queue


