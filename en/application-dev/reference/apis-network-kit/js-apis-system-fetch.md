# @system.fetch (Data Request)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

This module provides the network data request capability. It allows you to initiate HTTP/HTTPS requests through URLs and obtain data returned by the server. You can customize the request header, request method, and response class. This module is applicable to scenarios where an application needs to access network resources or interact with backend services, meeting the network communication requirements within the application.

> **NOTE**
> - The APIs of this module are deprecated since API version 6. You are advised to use the new API [@ohos.net.http](js-apis-http.md) instead.
> 
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import


```ts
import fetch from '@system.fetch';
```


## fetch.fetch<sup>3+</sup>

```ts
fetch(options:{
  url: string;
  data?: string | object;
  header?: Object;
  method?: string;
  responseType?: string;
  success?: (data: FetchResponse) => void;
  fail?: (data: any, code: number) => void;
  complete?: () => void;
}): void
```

Obtains data through a network.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| url | string | Yes| Resource URL.|
| data | string \| Object | No| Request parameter, which can be a string or a JSON object. For details, see the mapping between **data** and **Content-Type**.|
| header | Object | No| Request header.|
| method | string | No| Request method. The default value is **GET**. The value can be **OPTIONS**, **GET**, **HEAD**, **POST**, **PUT**, **DELETE **or **TRACE**.|
| responseType | string | No| Response type. The return type can be text or JSON. By default, the return type is determined based on **Content-Type** in the header returned by the server. For details, see return values in the **success** callback.|
| success | Function | No| Called when the API call is successful. The return value is defined by [FetchResponse](#fetchresponse3).|
| fail | Function | No| Called when the API call fails. The return value is **data, code**. The value of **data** is always **undefined**, and **code** is an error code. For details, see [curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).|
| complete | Function | No| Called when an API call is complete.|

**Table 1** Mapping between data and Content-Type

| data | Content-Type | Description|
| -------- | -------- | -------- |
| string | Left unspecified| The default value of Content-Type is **text/plain**, and the value of data is used as the request body.|
| string | Any type| The value of data is used as the request body.|
| Object | Left unspecified| The default value of **Content-Type** is **application/x-www-form-urlencoded**. The **data** value is encoded based on the URL rule and appended in the request body.|
| Object | application/x-www-form-urlencoded | The value of data is encoded based on the URL rule and is used as the request body.|

## FetchResponse<sup>3+</sup>

**System capability**: SystemCapability.Communication.NetStack

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| code | number | No| No| Server status code.|
| data | string \| Object | No| No| The type of the returned data is determined by **responseType**. For details, see the mapping between **responseType** and **data** in **success** callback.|
| headers | Object | No| No| All headers in the response from the server.|

**Table 2** Mapping between responseType and data in success callback

| responseType | data | Description|
| -------- | -------- | -------- |
| N/A| string | When the type in the header returned by the server is **text/\***, **application/json**, **application/javascript**, or **application/xml**, the value is the text content.|
| text | string | Text content.|
| json | Object | A JSON object.|

**Example**

ArkTS example:

```ts
fetch.fetch({
  url: 'test_url',
  success: (response) => {
    console.info('fetch success');
    console.info(JSON.stringify(response));
  },
  fail: (data: Object, code) => {
    console.error('fetch failed, data: ' + JSON.stringify(data) + ', code: =' + code);
  }
});
```

JS example:

```xml
<!-- index.hml -->
<div class="container">
    <text class="title">Test Network Connection</text>
    <input type="button" value="Click to test" style="width: 240px; height: 50px;margin: 5px;" onclick="usingFetch"></input>
    <text class="title" style="color: {{fontColor}};">{{result}}</text>
</div>
```

```css
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

```js
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
            fail: function(data, code) {
                that.fontColor = '#FF0000';
                that.result = 'FAILED code ' + code;
                console.error('fetch failed');
            }
        });
    }
};
```


> **NOTE**
>   HTTPS is supported by default. To support HTTP, you need to add **"network"** to the **config.json** file, and set the attribute **"cleartextTraffic"** to **true**.
>   
```json5
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
