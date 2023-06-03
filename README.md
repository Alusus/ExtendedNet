# ExtendedNet
[[عربي]](readme.ar.md)
Extension to SRL"s Net module.

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

### post function

```
func post(url: ptr[array[Char]], postedData: ptr[array[Char]], result: ptr[ptr], resultCount: ptr[Int], auth: ptr[array[Char]]): Bool
```

This function send post request with data and get the server response into the result ptr.

`url` the url of the server  we want to send the data to.

`postedData` the data we want to send.

`result` the response from the server.

`resultCount` the length of  the response.

`auth` the auth token to send it to the server.

Returns true if the request send correctly.

```
func post(url: ptr[array[Char]], postedData: ptr[array[Char]], outputFilename: ptr[array[Char]], auth: ptr[array[Char]]): Bool
```

This function does the same work as the previous function but it store the server response into file.

`url` the url of the server  we want to send the data to.

`postedData` the data we want to send.

`outputFilename` the path of the file to store the  response.

`auth` the auth token to send it to the server.

Returns true if the request send correctly.

```
func post(url: ptr[array[Char]], postedData: ptr[array[Char]], outputFilename: ptr[array[Char]]): Bool
```

This function does the same work as the previous function but it doesn't have auth in it.

`url` the url of the server  we want to send the data to.

`postedData` the data we want to send.

`outputFilename` the path of the file to store the  response.

Returns true if the request send correctly.

```
func post(url: ptr[array[Char]], postedData: ptr[array[Char]], result: ptr[ptr], resultCount: ptr[Int]): Bool
```

This function does the same work as the previous function but it store the server response into result ptr.

`url` the url of the server  we want to send the data to.

`postedData` the data we want to send.

`result` the response from the server.

`resultCount` the length of  the response.

Returns true if the request send correctly.

```

### putFile function

```
func putFile(url: ptr[array[Char]], filename: ptr[array[Char]], auth: ptr[array[Char]]): Bool
```

This function send put request with file to the server.

`url` the url of the server  we want to send the file to.

`filename` the path of the file we want to send.

`auth` the auth token to send it to the server.

Returns true if the request send correctly.

```
func putFile(url: ptr[array[Char]], filename: ptr[array[Char]]): Bool
```

This function does the same work as the previous function but it doesn't have auth in it.

`url` the url of the server  we want to send the file to.

`filename` the path of the file we want to send.

Returns true if the request send correctly.

```

### smtp function

```
func smtp(url: ptr[array[Char]], emailArray: Array[Srl.String], password: ptr[array[Char]]): Bool
```

this function send email via smtp protocol.

`url` the url of the server  we want to send the email to.

'emailArray' the email we want to send as returned from 'buildEmailString' function.

'password' the password of the sender email.

Returns true if the request send correctly.

```
func buildEmailString(reseviers: Srl.Array[Srl.String], sender: Srl.String, 
                        subject: Srl.String, body: Srl.String, textType: Srl.String): Array[Srl.String]
```

this function build the email and return the email array to use it later to send the email.

`reseviers` array of the reseviers emails.

'sender' the sender email.

'subject' the subject of the email.

'body' the body of the email.

'textType' the type of the email 'html , text'.

Returns string array with the email data to send the email using smtp function.

```


