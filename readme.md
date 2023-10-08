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
import "Srl/String";
import "Srl/Net";
import "Apm";
Apm.importFile("Alusus/ExtendedNet");
use Srl;
def networkObject : Net.Request(String("https://example.org"));
networkObject.get();
Console.print("\n%s\n",networkObject.responseBody.buf);
```

## Classes

### Request class 

This class deal with the http request

Class Properties:

`url` the url of the site we want to send request to.

`authKey` the authentication key .

`authType` the authentication type "Bearer" for example.

`contentType` the contentType of the request.

`responseBody` the response from the website.

`responseHttpStatus` the response status code.

'httpHeaderArray' array to store Http Headers.

#### addHeader

```
func addHeader(header: String)
```

This method add http header to http header array.

`header` the header to be added to the array.

#### putFile

```
func putFile(filename: String): Bool
```

This method upload file the website

`filename` the path of the file.

Returns true if file uploaded.

#### post

```
func post(postedData: ptr[array[Char]]): Bool
```

This method make post request with the posted Data to the website.

`postedData` the data to be sended to the website.

Returns true if data sent.

```
func post(postedData: ptr[array[Char]], outputFilename: ptr[array[Char]]): Bool
```

This method make post request with the posted Data to the website and store server response in a file.

`postedData` the data to be sended to the website.

`outputFilename` the path of the file to store response.

Returns true if data sent.

#### sendEmail

```
func sendEmail(
    receivers: Srl.Array[Srl.String],
    sender: Srl.String,
    subject: Srl.String,
    body: Srl.String,
    bodyType: Srl.String,
    password: Srl.String
): Bool
```

This method send e-mail via smtp request.

`receivers` array of the receivers emails.

`sender` the sender email.

`subject` the subject of the email.

`body` the body of the email.

`bodyType` the type of the email body. Either `html` or `text`.

`password` the password of the sender.

Returns true if e-mail sent.

#### get

```
func get(): Bool
```

This method send get request.

Returns true if get request sent.

#### delete

```
func delete(): Bool
```

This method send delete request.

Returns true if delete request sent.

