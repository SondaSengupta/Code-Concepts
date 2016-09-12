**Coding Journeyman:** https://codingjourneyman.com/2015/03/23/tell-dont-ask-principle/

"The Tell Don’t Ask principle helps you focus on the behavior of your classes and the functionalities you want them to expose. Remember that you don’t have to **ask** your components about their state in order to do an operation, just **tell** them to do it."

In other words, instead of a class calling on the components of another class to do its own work, what you should do is have the other class house the actions of its own components and expose those methods for use.

This is a huge difference between procedural and OO languages. Procedural code expects that you take in variable states and do something with them in a function. OO code expects you to just call the method of the object you are interested in to perform an action since objects own their own components and methods.



