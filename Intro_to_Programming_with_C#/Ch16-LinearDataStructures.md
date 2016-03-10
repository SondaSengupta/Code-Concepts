# Ch. 16 Linear Data Structures

**reading link:** http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-16-linear-data-structures/
**.NET Compiler:** https://dotnetfiddle.net/

### Abstract Data Structures
- a **data structure** is an ordered set of data organized based on logical and mathematical expressions, done in order to efficiently complete tasks (adding, removing, sorting, etc.) and save memory space.
- an **abstract data type (adt)** provides the definition of a data structure by defining its operations and properties.

#### Basic Data Structures in Programming
-     Linear – these include lists, stacks and queues
-     Tree-like – different types of trees like binary trees, B-trees and balanced trees
-     Dictionaries – key-value pairs organized in hash tables
-     Sets – unordered bunches of unique elements
-     Others – multi-sets, bags, multi-bags, priority queues, graphs, etc...

### List Data Structures
- a list is an ordered sequence of elements. A list data structure is arranged consequetively and has a property length, which is a count of the elements within it.  
- arrays have a fixed size that you have to specify before you create the array. If you want to expand the array than you will have to make a new array that is larger in size and then copy the information over.

### List Class
- it keeps its elements in an array. The list already has a certain size, and when it grows it doubles in size, so there is always a used and unused buffer
- search by index is very fast because it's just an array underneath. Search by value is very slow. Adding and removing elements is also slow because we have to shift elements over.
- adding a new element is generally very fast
- 
