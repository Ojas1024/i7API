# Windows Binaries for i7Storage

## Features
1. Easy to use
2. Can be used via any programming language
3. Help and documentation available
4. Maximum upload file size is 1.5 GB
5. Can be started with command line arguments
6. 7 levels of encryption and security 
7. Unlimited Storage for free 😍

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

## Functions
1. Authentication
2. Uploading file
3. Downloading file
4. Removing file

## Examples:
> 1. Node Js

First install **request-promise** using 

```npm install request-promise```

```node


var request = require('request-promise');
  
async function download() {
  
    // This variable contains the data
    // you want to send 
    let data = JSON.stringify({type: "download", api_key: "<YOUR API KEY>", api_password: '<YOUR API PASSWORD>', file_id: "<YOUR FILE ID>"});

  
    var options = {
        method: 'POST',
  
        // http:flaskserverurl:port/route
        uri: 'http://127.0.0.1:2707/nodejs',
        body: data,
  
        // Automatically stringifies
        // the body to JSON 
        json: true
    };
  
    var sendrequest = await request(options)
  
        // The parsedBody contains the data
        // sent back from the Flask server 
        .then(function (parsedBody) {
            console.log(parsedBody);
            let result;
            result = parsedBody['base64'];
            console.log("data ", result);
        })
        .catch(function (err) {
            console.log(err);
        });
}
  
download();
```

> 2. Python

Install **requests** using
```pip install requests```

Then:

```python
import requests
json_data = {"type": "download", "api_key": "<YOUR API KEY>", "api_password": "<YOUR API PASSWORD>", "file_id": "<YOUR FILE ID>"}
request = requests.post("http://127.0.0.1:2707/", json=json_data)


print(r.json())
```
