# FetchResponse

```TypeScript
export interface FetchResponse
```

**Table 2** Mapping between responseType and data in success callback

| responseType | data | Description|  
| -------- | -------- | -------- |  
| N/A| string | When the type in the header returned by the server is **text/\***, **application/json**, **application/javascript**, or **application/xml**, the value is the text content.|
| text | string | Text content.|
| [json](../../apis-arkts/arkts-apis/arkts-arkts-util-json.md) | Object | A JSON object.|

**Since:** 3

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
```

## code

```TypeScript
code: number
```

Server status code.

**Type:** number

**Since:** 3

**System capability:** SystemCapability.Communication.NetStack

## data

```TypeScript
data: string | object
```

The type of the returned data is determined by **responseType**. For details, see the mapping between **responseType** and **data** in **success** callback.

**Type:** string &#124; object

**Since:** 3

**System capability:** SystemCapability.Communication.NetStack

## headers

```TypeScript
headers: Object
```

All headers in the response from the server.

**Type:** Object

**Since:** 3

**System capability:** SystemCapability.Communication.NetStack

**Examples**

ArkTS example:

```TypeScript
fetch.fetch({
  url: 'test_url',
  success: (response) => {
    console.info('fetch success');
    console.info(JSON.stringify(response));
  },
  fail: () => {
    console.error('fetch failed');
  }
});
```

JS example:

```TypeScript
<!-- index.hml -->
<div class="container">
    <text class="title">Test Network Connection</text>
    <input type="button" value="Click to test" style="width: 240px; height: 50px;margin: 5px;" onclick="usingFetch"></input>
    <text class="title" style="color: {{fontColor}};">{{result}}</text>
</div>
```

```TypeScript
/* index.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// index.js
import fetch from '@system.fetch';

export default {
    data: {
        fontColor: '#FFF',
        result: '',
    },
    usingFetch: function() {
        const that = this;
        fetch.fetch({
            url: 'test_url',
            success: function(response) {
                that.fontColor = '#00FF00';
                that.result = 'SUCCESS';
                console.info('fetch success');
                console.info(JSON.stringify(response));
            },
            fail: function() {
                that.fontColor = '#FF0000';
                that.result = 'FAILED';
                console.error('fetch failed');
            }
        });
    }
};
```

> NOTEHTTPS is supported by default. To support HTTP, you need to add "network" to the config.json file, and set the attribute "cleartextTraffic" to true.

```TypeScript
{
  "deviceConfig": {
    "default": {
      "network": {
        "cleartextTraffic": true
      }
      // Other configuration information
      // ...
    }
  }
  // Other configuration information
  // ...
}
```
