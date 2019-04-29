# Splunk HEC (HTTP Event Collector)

> The HTTP Event Collector (HEC) is a fast and efficient way to send data to Splunk Enterprise and Splunk Cloud. Notably, HEC enables you to send data over HTTP (or HTTPS) directly to Splunk Enterprise or Splunk Cloud from your application. 


# Sample Code!

## Curl

```bash

curl -X POST \
  http://aa-hack-wars.splunk.link:8088/services/collector \
  -H 'Authorization: Splunk _token_value_' \
  -H 'Content-Type: application/json' \
  -d '{
    "host": "mydummyhost",
    "event": {
        "field1": "value1",
        "field2": "value2"
    }
}'
```


## Java

```java

OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n    \"host\": \"mydummyhost\",\n    \"event\": {\n        \"field1\": \"value1\",\n        \"field2\": \"value2\"\n    }\n}");
Request request = new Request.Builder()
  .url("http://aa-hack-wars.splunk.link:8088/services/collector")
  .post(body)
  .addHeader("Content-Type", "application/json")
  .addHeader("Authorization", "Splunk _token_value_")
  .build();

Response response = client.newCall(request).execute();
```

or

```java
HttpResponse<String> response = Unirest.post("http://aa-hack-wars.splunk.link:8088/services/collector")
  .header("Content-Type", "application/json")
  .header("Authorization", "Splunk _token_value_")
  .body("{\n    \"host\": \"mydummyhost\",\n    \"event\": {\n        \"field1\": \"value1\",\n        \"field2\": \"value2\"\n    }\n}")
  .asString();
```

## Nodejs

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'http://aa-hack-wars.splunk.link:8088/services/collector',
  headers: 
   { Authorization: 'Splunk _token_value_',
     'Content-Type': 'application/json' },
  body: 
   { host: 'mydummyhost',
     event: { field1: 'value1', field2: 'value2' } },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

## Go

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "http://aa-hack-wars.splunk.link:8088/services/collector"

	payload := strings.NewReader("{\n    \"host\": \"mydummyhost\",\n    \"event\": {\n        \"field1\": \"value1\",\n        \"field2\": \"value2\"\n    }\n}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("Content-Type", "application/json")
	req.Header.Add("Authorization", "Splunk _token_value_")
	req.Header.Add("cache-control", "no-cache")
	req.Header.Add("Postman-Token", "02d16df8-5fee-4666-b942-d0c76ab6797a")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

### Python

```python
import requests
import json

url = "http://aa-hack-wars.splunk.link:8088/services/collector"
payload = {
    "host": "mydummyhost",
    "event": {
        "field1": "value1",
        "field2": "value2"
    }
}
headers = {
    'Content-Type': "application/json",
    'Authorization': "Splunk _token_value_"
    }
response = requests.request("POST", url, data=json.dumps(payload), headers=headers)
print(response.text)
```

### Ruby

```ruby
require 'uri'
require 'net/http'

url = URI("http://aa-hack-wars.splunk.link:8088/services/collector")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Splunk _token_value_'
request.body = "{\n    \"host\": \"mydummyhost\",\n    \"event\": {\n        \"field1\": \"value1\",\n        \"field2\": \"value2\"\n    }\n}"

response = http.request(request)
puts response.read_body
```

### Swift (NSURL)

```swift
import Foundation

let headers = [
  "Content-Type": "application/json",
  "Authorization": "Splunk _token_value_",
  "cache-control": "no-cache",
  "Postman-Token": "9c22afde-e0c9-46dd-81a0-49fd959e7415"
]
let parameters = [
  "host": "mydummyhost",
  "event": [
    "field1": "value1",
    "field2": "value2"
  ]
] as [String : Any]

let postData = JSONSerialization.data(withJSONObject: parameters, options: [])

let request = NSMutableURLRequest(url: NSURL(string: "http://aa-hack-wars.splunk.link:8088/services/collector")! as URL,
                                        cachePolicy: .useProtocolCachePolicy,
                                    timeoutInterval: 10.0)
request.httpMethod = "POST"
request.allHTTPHeaderFields = headers
request.httpBody = postData as Data

let session = URLSession.shared
let dataTask = session.dataTask(with: request as URLRequest, completionHandler: { (data, response, error) -> Void in
  if (error != nil) {
    print(error)
  } else {
    let httpResponse = response as? HTTPURLResponse
    print(httpResponse)
  }
})

dataTask.resume()
```



## Logging Library

### Java

* Get started: http://dev.splunk.com/view/splunk-logging-java/SP-CAAAE2K

* Supports Framework: log4j, java.util.logging, Logback, etc

  - Preprocessor Script

# Contributor
  - Mayur Pipaliya
  - Steven Hanna


### DOT NET

* http://dev.splunk.com/view/splunk-loglib-dotnet/SP-CAAAEX4


### Logging with JavaScript

* http://dev.splunk.com/view/splunk-logging-javascript/SP-CAAAE6U
