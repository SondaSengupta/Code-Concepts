# What is the difference between stack and heap memory for C#?

- When you declare a variable, .NET will allocate memory to with 3 things: its name, its data type, and its value. Depending upon the data type, it's stored in either stack or heap memory.

**Stack Memory** :
 - first-in, first out memory source in which values and references are added.
 - responsible for keeping track of the running memory needed in your application.
 - when an application exits, it clears its stack in FIFO method.
 - All value types (which is pretty much everything except strings and objects) use the stack and it is where all name and value of a variable are stored.

**Heap Memory** :
 - does not track running memory. More of a complex data store.
 - a pile of objects which can be reached at any moment of time.
 - used for dynamic memory allocation.
 - data is kept around to be garbage collected. If there are no references to it, then it is wiped by garbage collection.
 - strings and objects use the heap memory as where its value storage. A reference to itself is found in stack.


###### References
 http://www.codeproject.com/Articles/76153/Six-important-NET-concepts-Stack-heap-value-types
