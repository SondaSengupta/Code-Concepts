# Ch. 15 Text Files

**reading link:** http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-15-text-files/
**.NET Compiler:** https://dotnetfiddle.net/

### Streams
- **streams** are used whenever you need to input or output (read/write) data to an external source. They are a sequence of ordered data that is passed from one device to another.
- streams, essentially, are an ordered sequence of bytes.
- the data from streams can only be sequentially accessed, meaning you can't work on the second byte before the first has come in.
- closing a stream is very important because if not, data or the file may be damaged.

#### Basic Stream Operations
- creating a stream
- reading is a blocking operation.
- writing is sending data to the stream, a potentially blocking operation
- positioning, moving to the current position of a stream. Text files may save your position even if the network is out, but not all streams save position.
- closing or disconnecting a stream

### Streams in .NET Basic Classes
- streams are located in "System.IO"
- Two main types: binary data and text data both instantiated from an abstract stream class. From these, there are streams that help with buffering, compressing data, etc.
- It is required to close all streams.
