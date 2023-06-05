# ExtendedNet
[[عربي]](readme.ar.md)

Extension to `Srl.Net` module.

## Adding to the Project

We can install this library using the following statements:

```
import "Srl/Console";
import "Apm";
Apm.importFile("Alusus/ExtendedNet");
```

## Example

```
import "Srl/Console";
import "Apm";
Apm.importFile("Alusus/ExtendedNet");

use Srl;
// to get the response from the server
def data: ptr;
def size: Int;
//check if there is an error !
if Net.post("https://example.org","the posted data go here", data~ptr, size~ptr) {
  Console.print("%s\n", data);
  Memory.free(data);
} else {
  Console.print("Error!\n");
}
```

## Functions

### post

```
func post(url: CharsPtr, postedData: CharsPtr, result: ptr[ptr], resultCount: ptr[Int], auth: CharsPtr): Bool
```

This function send post request with data and get the server response into the result ptr.

`url` the url of the server  we want to send the data to.

`postedData` the data we want to send.

`result` the response from the server.

`resultCount` the length of  the response.

`auth` the auth token to send it to the server.

Returns true on success.

```
func post(url: CharsPtr, postedData: CharsPtr, outputFilename: CharsPtr, auth: CharsPtr): Bool
```

This function does the same work as the previous function but it store the server response into file.

`url` the url of the server  we want to send the data to.

`postedData` the data we want to send.

`outputFilename` the path of the file to store the  response.

`auth` the auth token to send it to the server.

Returns true on success.

```
func post(url: CharsPtr, postedData: CharsPtr, outputFilename: CharsPtr): Bool
```

This function does the same work as the previous function but it doesn't have auth in it.

`url` the url of the server  we want to send the data to.

`postedData` the data we want to send.

`outputFilename` the path of the file to store the  response.

Returns true on success.

```
func post(url: CharsPtr, postedData: CharsPtr, result: ptr[ptr], resultCount: ptr[Int]): Bool
```

This function does the same work as the previous function but it store the server response into result ptr.

`url` the url of the server  we want to send the data to.

`postedData` the data we want to send.

`result` the response from the server.

`resultCount` the length of  the response.

Returns true on success.

### putFile

```
func putFile(url: CharsPtr, filename: CharsPtr, auth: CharsPtr): Bool
```

This function send put request with file to the server.

`url` the url of the server  we want to send the file to.

`filename` the path of the file we want to send.

`auth` the auth token to send it to the server.

Returns true on success.

```
func putFile(url: CharsPtr, filename: CharsPtr): Bool
```

This function does the same work as the previous function but it doesn't have auth in it.

`url` the url of the server  we want to send the file to.

`filename` the path of the file we want to send.

Returns true on success.

### smtp

```
func smtp(url: CharsPtr, emailData: Array[Srl.String], password: CharsPtr): Bool
```

this function send email via smtp protocol.

`url` the url of the server  we want to send the email to.

`emailData` the email we want to send as returned from `prepareEmailData` function.

`password` the password of the sender email.

Returns true on success.

### prepareEmailData

```
func prepareEmailData(
    receivers: Array[String],
    sender: String, 
    subject: String,
    body: String,
    bodyType: String
): Array[String]
```

This function builds the email and returns the email array to use for sending the email.

`receivers` array of the receivers emails.

`sender` the sender email.

`subject` the subject of the email.

`body` the body of the email.

`bodyType` the type of the email body. Either `html` or `text`.

Returns string array with the email data to send the email using smtp function.

