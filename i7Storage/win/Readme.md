# Windows Binaries for i7StorageEngine


## Installation
1. Download the zip file
2. Extract the zip file
3. Run the file directly or type 

```

i7storage.exe -i <host address> -p <port>

```

## Usage:

Use JSON POST request APIs to make the requests.
For documentation, go to /documentation end point 
## Limitations
1. This is under Alpha phase, so you may encounter errors
2. Your feedback is very essential for its development

## Functions:
1. Authentication
2. Uploading file
3. Downloading file
4. Removing file
5. Getting File_IDs of the uploaded file

## Examples:

### Node Js

Install **request-promise** using 

```npm install request-promise```

Then:

> 1. Sign in
```node

var request = require('request-promise');
  
async function signin() {
    let data = JSON.stringify({type: "signin", username: "your email", password: "your password"});
  
    var options = {
        method: 'POST',
        uri: 'http://127.0.0.1:2707/nodejs',
        body: data,
        json: true
    };
  
    var sendrequest = await request(options)
        .then(function (parsedBody) {
            console.log(parsedBody);
        })
        .catch(function (err) {
            console.log(err);
        });
}
  
signin();
```

> 2. Sign up

```node


var request = require('request-promise');
  
async function signup() {
    let data = JSON.stringify({type: "signup", username: "your email", password: "your password"});
  
    var options = {
        method: 'POST',
        uri: 'http://127.0.0.1:2707/nodejs',
        body: data,
        json: true
    };
  
    var sendrequest = await request(options)
        .then(function (parsedBody) {
            console.log(parsedBody);
        })
        .catch(function (err) {
            console.log(err);
        });
}
  
signup();
```

> 3. Upload

```node

const fs = require('fs');
var request = require('request-promise');

const b64_bytes = fs.readFileSync("<PATH TO FILE>", {encoding: 'base64'});

async function upload() {
    let data = JSON.stringify({type: "upload", api_key: "<YOUR API KEY>", api_password: '<YOUR API PASSWORD>', bytes: b64_bytes, file_name: "<FILENAME.EXTENSION>"});
    var options = {
        method: 'POST',
        uri: 'http://127.0.0.1:2707/nodejs',
        body: data,
        json: true
    };
  
    var sendrequest = await request(options)
        .then(function (parsedBody) {
            console.log(parsedBody);
            let result;
            file_id = parsedBody['file_id'];
            console.log("File ID is ", file_id);
        })
        .catch(function (err) {
            console.log(err);
        });
}
  
upload();

```


> 4. Download

```node


var request = require('request-promise');
  
async function download() {
    let data = JSON.stringify({type: "download", api_key: "<YOUR API KEY>", api_password: '<YOUR API PASSWORD>', file_id: "<YOUR FILE ID>"});

  
    var options = {
        method: 'POST',
        uri: 'http://127.0.0.1:2707/nodejs',
        body: data,
        json: true
    };
  
    var sendrequest = await request(options)
        .then(function (parsedBody) {
            console.log(parsedBody);
            let result;
            result = parsedBody['base64'];
            console.log("Base64 Data: ", result);
        })
        .catch(function (err) {
            console.log(err);
        });
}
  
download();
```
> 5. Delete a file

```node
var request = require('request-promise');
  
async function delete() {
    let data = JSON.stringify({type: "delete", api_key: "<YOUR API KEY>", api_password: "<YOUR API PASSWORD>", file_id: "<YOUR FILE ID>"});
  
    var options = {
        method: 'POST',
        uri: 'http://127.0.0.1:2707/nodejs',
        body: data,
        json: true
    };
  
    var sendrequest = await request(options)
        .then(function (response) {
            console.log(response);
        })
        .catch(function (err) {
            console.log(err);
        });
}
  
delete();
```

> 6. Get All file_ids:

```node
var request = require('request-promise');
  
async function getfileid() {
    let data = JSON.stringify({type: "getfileid", api_key: "<YOUR API KEY>", api_password: "<YOUR API PASSWORD>"});
  
    var options = {
        method: 'POST',
        uri: 'http://127.0.0.1:2707/nodejs',
        body: data,
        json: true
    };
  
    var sendrequest = await request(options)
        .then(function (response) {
            console.log(response);
        })
        .catch(function (err) {
            console.log(err);
        });
}
  
getfileid();
```


### Python
Install **requests** using
```pip install requests```

Then:

> 1. Sign in

```python
import requests
r = requests.post("http://localhost:2707/", json={"type":"signin", "username": "your email", "password": "your password"})
```

> 2. Sign Up

```python
import requests
r = requests.post("http://localhost:2707/", json={"type":"signup", "username": "your email", "password": "your password"})
```

> 3. Upload

```python
import requests
import base64
f = open("<SOME FILE>", "rb")
data = f.read()
f.close()
data_b64 = base64.b64encode(data).decode()
r = requests.post("http://localhost:2707/", json={"type": "upload", "api_key": "<YOUR API KEY>", 'api_password': '<YOUR API PASSWORD>', "file_name": "<FILENAME.EXTENSION>", "bytes": data_b64})

file_id = r.json()["file_id"] 
# To download the file, file_id is required
    

```

> 4. Download

```python
import requests
json_data = {"type": "download", "api_key": "<YOUR API KEY>", "api_password": "<YOUR API PASSWORD>", "file_id": "<YOUR FILE ID>"}
request = requests.post("http://127.0.0.1:2707/", json=json_data)


print(r.json()['base64'])
```

> 5. Delete a file

```python
import requests
json_data = {"type": "delete", "api_key": "<YOUR API KEY>", "api_password": "<YOUR API PASSWORD>", "file_id": "<YOUR FILE ID>"}
request = requests.post("http://127.0.0.1:2707/", json=json_data)
print(request.json())
```

> 6. Get all file_ids

```python
import requests
json_data = {"type": "getallid", "api_key": "<YOUR API KEY>", "api_password": "<YOUR API PASSWORD>"}
request = requests.post("http://127.0.0.1:2707/", json=json_data)
print(request.json())
```
