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

#### Streams in .NET Basic Classes
- streams are located in "System.IO"
- Two main types: binary data and text data both instantiated from an abstract stream class. From these, there are streams that help with buffering, compressing data, etc.
- It is required to close all streams.

#### Binary and Text Streams
- Binary streams work with raw binary data which is used for all sorts of file types such as text, music, and pictures.
- Text stream only work with text

#### How to open a text file for reading:
```C#
// Create a StreamReader connected to a file
StreamReader reader = new StreamReader("test.txt");

// Read the file here …

// Close the reader resource after you've finished using it
reader.Close();
```
- Avoid full file paths and work with relative paths! This makes your application portable and easy for installation and maintenance.
- Make sure to use escaping slashes. Two ways: With double slashes (string fileName = "C:\\Temp\\work\\test.txt";) or with the @ symbol (string theSamefileName = @"C:\Temp\work\test.txt").
The @ symbol represents a verbatim string literal in which anything that could be thought of as an escape character is ignored and also allows for multiline strings.
- Remember that when you start the C# program, the current directory is the one, in which the executable (.exe) file is located. Most often this is the subdirectory bin\Debug or bin\Release directory to the root of the project. Therefore, to open the file example.txt from the root directory of your Visual Studio project, you should use a relative path ..\..\example.txt.

#### Automatic Closing of a Stream after using it
- the "using" statement will ensure that after leaving its body, the method Close() will automatically be called. This will happen even if an exception occurs when reading the file.
- Always use the using construct in C# in order to properly close files and streams!

#### File Encodings
- Everything is stored as binary data and the process of making it that way is called encoding files.
- The encoding process of text means replacing the text characters to binary values.
- The default for .NET reading a file is UTF-8.
- However, if a text file is under a different encoding, you will have to specify the schema to use like this:

```C#
Encoding win1251 = Encoding.GetEncoding("Windows-1251");
StreamReader reader = new StreamReader("test.txt", win1251);
```
#### Catching Exceptions
```C#
class HandlingExceptions
{
    static void Main()
    {
        string fileName = @"somedir\somefile.txt";
        try
        {
            StreamReader reader = new StreamReader(fileName);
            Console.WriteLine(
                "File {0} successfully opened.", fileName);
            Console.WriteLine("File contents:");
            using (reader)
            {
                Console.WriteLine(reader.ReadToEnd());
            }
        }
        catch (FileNotFoundException)
        {
            Console.Error.WriteLine(
                "Can not find file {0}.", fileName);
        }
        catch (DirectoryNotFoundException)
        {
            Console.Error.WriteLine(
                "Invalid directory in the file path.");
        }
        catch (IOException)
        {
            Console.Error.WriteLine(
                "Can not open the file {0}", fileName);
        }
    }
}
```
