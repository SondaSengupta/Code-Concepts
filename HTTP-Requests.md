# What are the different HTTP Request Types?

**idempotent** - In computing, an idempotent operation is one that has no additional effect if it is called more than once with the same input parameters. Idempotent operations are often used in the design of network protocols, where a request to perform an operation is guaranteed to happen at least once, but might also happen more than once. If the operation is idempotent, then there is no harm in performing the operation two or more times. GET and PUT is idempotent and DELETE is technically idempotent as long as deleting something a second time does nothing, no 404. POST and Patch are not idempotent.

###Types of Requests:
**GET** - gets all data at a specified location. Idempotent.
**POST** -adds a new model at an unspecified place leaving it up to the server to create an address for it. Idempotent.
**PUT**  - goes to a specified location to completely replace the model at that location. Not idempotent.
**PATCH** - sends a request of what needs to be changed or deleted to a model in the database. Not Idempotent.
**DELETE** - removes all information at a specified location. Technically, idempotent when doing so a second time does nothing, not even 404 error.

###Links:
Idempotency - https://stackoverflow.com/questions/1077412/what-is-an-idempotent-operation  
When to use patch? - http://restcookbook.com/HTTP%20Methods/patch/
