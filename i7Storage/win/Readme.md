# Windows Binaries for i7Storage


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
