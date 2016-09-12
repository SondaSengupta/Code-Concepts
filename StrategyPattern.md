## Links
**StackOverflow:** http://stackoverflow.com/questions/91932/how-does-the-strategy-pattern-work


From Wikipedia:
A strategy pattern is useful when you need to dynamically swap algorithms used in an applciation. That is to say, when there are conditional logic going on, you stash the separate logic for each choice as a seperate class, make them interchangeable and contractual through interfaces to abstract it out, and then have a larger method that will call upon those separate behaviors.

### When Needed:
The strategy pattern has a strong similarity to passing a function (or functions) to another function. In the strategy this is done by wrapping said function in an object followed by passing the object. Some languages can pass functions directly, so they don't need the pattern at all. But other languages can't pass functions, but can pass objects; the pattern then applies.

