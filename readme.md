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

```
some of this class properties
```

`url` the url of the site we want to send request to.

`authKey` the authentication key .

`authType` the authentication type "Bearer" for example.

`contentType` the contentType of the request.

`responseBody` the response from the website.

`responseHttpStatus` the response status code.

```
func putFile(filename: String): Bool
```

This function upload file the website

`filename` the path of the file.

Returns true if file uploaded.

```
func post(postedData: ptr[array[Char]]): Bool
```

This function make post request with the posted Data to the website.

`postedData` the data to be sended to the website.

Returns true if data sent.

```
func post(postedData: ptr[array[Char]], outputFilename: ptr[array[Char]]): Bool
```

This function make post request with the posted Data to the website and store server response in a file.

`postedData` the data to be sended to the website.

`outputFilename` the path of the file to store response.

Returns true if data sent.

```
func sendEmail(receivers: Srl.Array[Srl.String],sender: Srl.String,subject: Srl.String,body: Srl.String,
                bodyType: Srl.String,password: Srl.String): bool
```

This function send e-mail via smtp request.

`receivers` array of the receivers emails.

`sender` the sender email.

`subject` the subject of the email.

`body` the body of the email.

`bodyType` the type of the email body. Either `html` or `text`.

`password` the password of the sender.

Returns true if e-mail sent.

```
func get(): Bool
```

This function send get request.

Returns true if get request sent.