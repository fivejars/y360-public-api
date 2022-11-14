<!-- Generator: Widdershins v4.0.1 -->

<h1 id="ymca360-public-api-v1-0">YMCA360 Public API v1.0 v1.0.0-RC1</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

YMCA 360 Public API. Find out more about YMCA 360 at [https://ymca360.org/api](https://ymca360.org/api).

Base URLs:

* <a href="https://cms.ymca360.org/api/1.0">https://cms.ymca360.org/api/1.0</a>

<a href="https://ymca360.org/api/terms/">Terms of service</a>
Email: <a href="mailto:info@ymca360.org">Support</a> 
License: <a href="http://www.apache.org/licenses/LICENSE-2.0.html">Apache 2.0</a>

# Authentication

* API Key (apikey)
    - Parameter Name: **Authorization**, in: header. 

<h1 id="ymca360-public-api-v1-0-live-streams">Live Streams</h1>

Operations with live streams

## upcomingLiveStreams

<a id="opIdupcomingLiveStreams"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://cms.ymca360.org/api/1.0/live-streams \
  -H 'Accept: application/json' \
  -H 'Authorization: API_KEY'

```

```http
GET https://cms.ymca360.org/api/1.0/live-streams HTTP/1.1
Host: cms.ymca360.org
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'API_KEY'
};

fetch('https://cms.ymca360.org/api/1.0/live-streams',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'API_KEY'
}

result = RestClient.get 'https://cms.ymca360.org/api/1.0/live-streams',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'API_KEY'
}

r = requests.get('https://cms.ymca360.org/api/1.0/live-streams', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://cms.ymca360.org/api/1.0/live-streams', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://cms.ymca360.org/api/1.0/live-streams");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://cms.ymca360.org/api/1.0/live-streams", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /live-streams`

*Upcoming live streams*

Lists upcoming live streams in chronological order

<h3 id="upcominglivestreams-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer|false|Page to retrieve, 0 indexed. If omitted defaults to `0`|
|limit|query|integer|false|Size of the page. If omitted defaults to `100`|
|from|query|integer|false|Limits the returned Live Streams `end time` be greater than the provided value (UNIX timestamp)|
|to|query|integer|false|Limits the returned Live Streams `start time` be less than the provided value (UNIX timestamp)|
|location|query|string|false|Live Stream host association name|

> Example responses

> 200 Response

```json
{
  "items": [
    {
      "id": 9696,
      "name": "Silver circuit",
      "description": "Improves overall health using low impact techniques that incorporate light cardio, strength, and balance. Designed for all fitness levels.",
      "status": "open",
      "url": "https://ymca360.org/live/9696",
      "startTime": 1668099600,
      "endTime": 1668102300,
      "duration": 2700,
      "thumbnail": "https://cms.ymca360.org/sites/default/files/styles/medium/public/2022-04/031021Y360_14.jpg",
      "category": "Boomers & Beyond",
      "association": "Greater Wichita YMCA",
      "level": "All Levels",
      "instructors": [
        "Shalen Scheltgen"
      ],
      "equipment": [
        "Chair",
        "Dumbbells",
        "Resistance Tube"
      ],
      "language": "English",
      "attachments": [
        {
          "title": "Nutrition Talk.pdf",
          "url": "https://cms.ymca360.org/sites/default/files/2022-10/YMCA360_NutritionTalk.pdf"
        }
      ],
      "restream": false
    }
  ],
  "summary": {
    "limit": 100,
    "page": 0,
    "total": 1234
  }
}
```

<h3 id="upcominglivestreams-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully retrieved|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Authentication failed|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|Inline|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Error|Inline|

<h3 id="upcominglivestreams-responseschema">Response Schema</h3>

Status Code **200**

*Upcoming Live Streams*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» items|[[livestream](#schemalivestream)]|true|none|Actual Live Streams|
|»» id|integer|true|none|Unique ID of the Live Stream|
|»» name|string|true|none|Name of the Live Stream|
|»» description|string|true|none|Live Stream description|
|»» status|string|true|none|Status:<br> * `open` - The Live Stream is going to take place.<br> * `cancelled` - The Live Stream has been cancelled.|
|»» url|string|true|none|Live Stream URL (at https://ymca360.org)|
|»» startTime|integer|true|none|Live Stream start time (UNIX timestamp)|
|»» endTime|integer|true|none|Live Stream end time (UNIX timestamp)|
|»» duration|integer|true|none|Live Stream duration in seconds|
|»» thumbnail|string|true|none|URL to a live stream thumbnail image|
|»» category|string|true|none|Live Stream category name|
|»» association|string|true|none|Live Stream hosting association name|
|»» level|string|true|none|Live Stream Workout level|
|»» instructors|[string]|true|none|Live Stream instructors|
|»» equipment|[string]|true|none|Recommended equipment|
|»» language|string|true|none|Live Stream langugage|
|»» attachments|[object]|true|none|File attachments|
|»»» title|string|false|none|Attachment title|
|»»» url|string|false|none|Attachment URL|
|»» restream|boolean|true|none|Indicates if the live stream is a restream|
|» summary|[pagesummary](#schemapagesummary)|true|none|Page summary|
|»» limit|integer|true|none|Page size|
|»» page|integer|true|none|Page number|
|»» total|integer|true|none|Total number of items|

#### Enumerated Values

|Property|Value|
|---|---|
|status|open|
|status|cancelled|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» message|string|false|none|Error message|

Status Code **403**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» message|string|false|none|Error message|

Status Code **500**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» message|string|false|none|Error message|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apikey
</aside>

# Schemas

<h2 id="tocS_livestream">livestream</h2>
<!-- backwards compatibility -->
<a id="schemalivestream"></a>
<a id="schema_livestream"></a>
<a id="tocSlivestream"></a>
<a id="tocslivestream"></a>

```json
{
  "id": 9696,
  "name": "Silver circuit",
  "description": "Improves overall health using low impact techniques that incorporate light cardio, strength, and balance. Designed for all fitness levels.",
  "status": "open",
  "url": "https://ymca360.org/live/9696",
  "startTime": 1668099600,
  "endTime": 1668102300,
  "duration": 2700,
  "thumbnail": "https://cms.ymca360.org/sites/default/files/styles/medium/public/2022-04/031021Y360_14.jpg",
  "category": "Boomers & Beyond",
  "association": "Greater Wichita YMCA",
  "level": "All Levels",
  "instructors": [
    "Shalen Scheltgen"
  ],
  "equipment": [
    "Chair",
    "Dumbbells",
    "Resistance Tube"
  ],
  "language": "English",
  "attachments": [
    {
      "title": "Nutrition Talk.pdf",
      "url": "https://cms.ymca360.org/sites/default/files/2022-10/YMCA360_NutritionTalk.pdf"
    }
  ],
  "restream": false
}

```

Live Stream object

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|true|none|Unique ID of the Live Stream|
|name|string|true|none|Name of the Live Stream|
|description|string|true|none|Live Stream description|
|status|string|true|none|Status:<br> * `open` - The Live Stream is going to take place.<br> * `cancelled` - The Live Stream has been cancelled.|
|url|string|true|none|Live Stream URL (at https://ymca360.org)|
|startTime|integer|true|none|Live Stream start time (UNIX timestamp)|
|endTime|integer|true|none|Live Stream end time (UNIX timestamp)|
|duration|integer|true|none|Live Stream duration in seconds|
|thumbnail|string|true|none|URL to a live stream thumbnail image|
|category|string|true|none|Live Stream category name|
|association|string|true|none|Live Stream hosting association name|
|level|string|true|none|Live Stream Workout level|
|instructors|[string]|true|none|Live Stream instructors|
|equipment|[string]|true|none|Recommended equipment|
|language|string|true|none|Live Stream langugage|
|attachments|[object]|true|none|File attachments|
|» title|string|false|none|Attachment title|
|» url|string|false|none|Attachment URL|
|restream|boolean|true|none|Indicates if the live stream is a restream|

#### Enumerated Values

|Property|Value|
|---|---|
|status|open|
|status|cancelled|

<h2 id="tocS_pagesummary">pagesummary</h2>
<!-- backwards compatibility -->
<a id="schemapagesummary"></a>
<a id="schema_pagesummary"></a>
<a id="tocSpagesummary"></a>
<a id="tocspagesummary"></a>

```json
{
  "limit": 100,
  "page": 0,
  "total": 1234
}

```

Page summary

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|limit|integer|true|none|Page size|
|page|integer|true|none|Page number|
|total|integer|true|none|Total number of items|
