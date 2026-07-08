# @ohos.net.http (Data Request)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=66333f405b8ba85b102d9221d24e54901f6cfbf8 translatedAt=2026-06-25T01:51:18.917Z pushedAt=2026-06-26T03:00:41.294Z -->

The **http** module provides APIs for implementing HTTP data request capabilities. An application can initiate a data request over HTTP. Common HTTP methods include **GET**, **POST**, **OPTIONS**, **HEAD**, **PUT**, **DELETE**, **PATCH**, **TRACE**, and **CONNECT**.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { http } from '@kit.NetworkKit';
```

## Example

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->

```ts
// Import modules.
import { http, connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
// Each httpRequest corresponds to an HTTP request task and cannot be reused.
let httpRequest = http.createHttp();
// This API is used to listen for HTTP response header events, which returns earlier than the request. You can listen for HTTP response header events as required.
// on('headerReceive', AsyncCallback) is replaced by on('headersReceive', Callback) since API version 8.
httpRequest.on('headersReceive', (header: Object) => {
  console.info('header: ' + JSON.stringify(header));
});

httpRequest.request(// Enter the URL of the HTTP request. The URL can contain parameters or not. The URL needs to be customized.
  "EXAMPLE_URL",
  {
    method: http.RequestMethod.POST, // Optional. The default value is http.RequestMethod.GET.
    // You are advised to use the body field to transfer the request body content. The specific format needs to be negotiated with the server.
    body: 'data to send', // Supported since API version 26.
    // You are advised to use the queryParams field to transfer URL parameters. The value can be a string or an object.
    queryParams: { scene: 'demo', tag: ['a', 'b'] }, // Supported since API version 26.
    expectDataType: http.HttpDataType.STRING, // Optional. This parameter specifies the type of the return data.
    usingCache: true, // Optional. The default value is true.
    priority: 1, // Optional. The default value is 1.
    // You can add the header field based on service requirements. Note that map objects cannot be passed to header fields.
    header: { 'Accept' : 'application/json' },
    readTimeout: 60000, // Optional. The default value is 60000, in ms.
    connectTimeout: 60000 // Optional. The default value is 60000, in ms.
    usingProtocol: http.HttpProtocol.HTTP1_1, // Optional. The default protocol type is automatically specified by the system.
    usingProxy: false, // Optional. The system proxy is used by default. If this parameter is set to false, no proxy is used. This property is supported since API version 10.
    caPath: '/path/to/cacert.pem', // Optional. The system preset CA certificate is used by default. This field is supported since API version 10.
    caData: '-----BEGIN CERTIFICATE-----\n' +
        'MIIDaTCCAlGgAwIBAgIICN287lmB2cMwDQYJKoZIhvcNAQELBQAwgYoxCzAJBgNV\n' +
        'BAYTAkNOMRMwEQYDVQQDDApleGFtcGxlLmNuMRAwDgYDVQQKDAdDb21wYW55MREw\n' +
        'DwYDVQQLDAhEaXZpc2lvbjEOMAwGA1UECAwFQW5IdWkxDjAMBgNVBAcMBUhlRmVp\n' +
        'MSEwHwYJKoZIhvcNAQkBFhJleGFtcGxlQGV4YW1wbGUuY24wHhcNMjUwNDEzMDAy\n' +
        'MjQxWhcNMjgwNDEzMDAyMjQxWjBeMQswCQYDVQQGEwJDTjESMBAGA1UEAwwJMTI3\n' +
        'LjAuMC4xMQkwBwYDVQQKDAAxCTAHBgNVBAsMADEJMAcGA1UECAwAMQkwBwYDVQQH\n' +
        'DAAxDzANBgkqhkiG9w0BCQEWADCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoC\n' +
        'ggEBANN/JrQC8dy7sxUk+TDJlGlq4h8lajdqSASkFbWVBadU4eMCbRrKejXuFX/n\n' +
        'Yu4J3wkgni0NKRejdWu/M+LLibQEIF9RUGNR/OgdlR4AKr8ZxmG44+7Ps2aiDcOy\n' +
        'Z95UcxYj59ctfFk63cacbBi19aq200spjl/H0jTVsQ2/JvwMVEH62WbyjIJ3KXgq\n' +
        'yyjf75rKbR9CdVdGk+OoR4S4c6nY5cTZP6T7iCupYR6MpKEtIR2bbams/N5GxQEh\n' +
        '9+7YxswTQn4EkVhi+UOFZolYLhtIdoLThmStN+WiSL5VDvchAkTUmwUBTGV21WnH\n' +
        'qo6J1t7XtwUpAZF6OuWl85R8D50CAwEAATANBgkqhkiG9w0BAQsFAAOCAQEAqjKq\n' +
        'gwR+4B6bwdAOZ6k0cutLqxvVgBaktX28omuYtoiYagM0zfB8/8WijXL8jT1VLEFx\n' +
        'wPaojwegqYWANfQkPd7A6rjsabgOH7oYBCDoCH52cjzGlJunC0BL6w5g3z6MCOB4\n' +
        'Ciz8rnYMvYqQJiMqrO7Po9onoFBHiRQGO4Wva3O8ErEmd2dKvXb3vN02P3T7CtwM\n' +
        'Z6D0rtZbzdsSOQfGcX08WFIfvfpz6tdU/X/6VqKrt5oiaNQH7ded6gJ3C6RM/Q/x\n' +
        'I2j/hSKy0yU7FoCFSOnlhxbm3TlbIvtjZKQ9ymK4x7iE0VKqExUAA6Z8qsIUBUt4\n' +
        'aqNDeZWXFBqrSujLJA==\n' +
        '-----END CERTIFICATE-----', // Optional. The system preset CA certificate is used by default. This field is supported since API version 20.
    clientCert: { // Optional. The client certificate is not used by default. This field is supported since API version 11.
      certPath: '/path/to/client.pem', // The client certificate is not used by default. This field is supported since API version 11.
      keyPath: '/path/to/client.key', // If the certificate contains key information, an empty string is passed. This field is supported since API version 11.
      certType: http.CertType.PEM, // Optional. A certificate in the PEM format is used by default. This field is supported since API version 11.
      keyPassword: "passwordToKey" // Optional. Password of the key file. This field is supported since API version 11.
    },
    certificatePinning: [ // Optional. Dynamic configuration of certificate pinning. This field is supported since API version 12.
      {
        publicKeyHash: 'Pin1', // Certificate PIN passed by the application. This field is supported since API version 12.
        hashAlgorithm: 'SHA-256' // Encryption algorithm. Currently, it can only be set to SHA-256. This field is supported since API version 12.
      }, {
        publicKeyHash: 'Pin2', // Certificate PIN passed by the application. This field is supported since API version 12.
        hashAlgorithm: 'SHA-256' // Encryption algorithm. Currently, it can only be set to SHA-256. This field is supported since API version 12.
      }
    ],
    multiFormDataList: [ // Optional. This field is valid only when content-Type in the header is multipart/form-data. It is supported since API version 11.
      {
        name: "Part1", // Data name. This field is supported since API version 11.
        contentType: 'text/plain', // Data type. This field is supported since API version 11.
        data: 'Example data', // Data content, optional. This field is supported since API version 11.
        remoteFileName: 'example.txt' // Optional. This field is supported since API version 11.
      }, {
        name: "Part2", // Data name. This field is supported since API version 11.
        contentType: 'text/plain', // Data type. This field is supported since API version 11.
        // data/app/el2/100/base/com.example.myapplication/haps/entry/files/fileName.txt
        filePath: `${context.filesDir}/fileName.txt`, // File path, optional. This field is supported since API version 11.
        remoteFileName: 'fileName.txt' // Optional. This field is supported since API version 11.
      }
    ],
    addressFamily: http.AddressFamily.DEFAULT // Optional. By default, the IPv4 or IPv6 address of the target domain name is selected. This field is supported since API version 15.
    customMethod: 'GET', // Optional. This field is supported since API version 23.
    maxRedirects: 30, // Optional. The default value is 30. This field is supported since API version 23.
    sniHostName: "www.example.com", // Optional. This field is supported since API version 23.
    reuseConnections: true, // Optional. The default value is **true**. This field is supported since API version 26.0.0.
    inactivityMs: 0, // Optional. The default value is 0, which means no limit. This filed is supported since API version 26.0.0.
    usingSocks5Proxy: { // Optional. The SOCKS5 proxy is not used by default. This filed is supported since API version 26.0.0. If this field is specified, the usingProxy field does not take effect.
      host: 'host', // Host name of the SOCKS5 proxy server. This field is supported since API version 26.0.0.
      port: 1080, // Port of the SOCKS5 proxy server. This field is supported since API version 26.0.0.
      username: 'username', // Optional. User name for SOCKS5 proxy authentication. This field is supported since API version 26.0.0.
      password: 'password', // Optional. Password for SOCKS5 proxy authentication. This field is supported since API version 26.0.0.
      dnsStrategy: connection.Socks5DnsStrategy.SYSTEM_MODE, // Optional. Used to specify whether DNS resolution is performed by the system or the SOCKS5 proxy server. The default value is performed by the system. This field is supported since API version 26.0.0.
      exclusionList: [ 'www.example.com' ] // Optional. Used to specify the domain names that do not use the SOCKS5 proxy. This field is supported since API version 26.0.0.
    }
  },
  (err: BusinessError, data: http.HttpResponse) => {
    if (!err) {
      // data.result is the HTTP response. Parse the response based on service requirements.
      console.info('Result:' + JSON.stringify(data.result));
      console.info('code:' + JSON.stringify(data.responseCode));
      console.info('type:' + JSON.stringify(data.resultType));
      // data.header is the HTTP response header. Parse the content based on service requirements.
      console.info('header:' + JSON.stringify(data.header));
      console.info('cookies:' + JSON.stringify(data.cookies)); // Cookies are supported since API version 8.
      // HTTP interaction information can be obtained since API version 24.
      console.info('connectionExtraInfo:' + JSON.stringify(data.connectionExtraInfo));
      // Unsubscribe from HTTP response header events.
      httpRequest.off('headersReceive');
      // Call destroy() to release resources when the request is no longer needed, preventing memory leaks.
      httpRequest.destroy();
    } else {
      console.error('error:' + JSON.stringify(err));
      // Unsubscribe from HTTP response header events.
      httpRequest.off('headersReceive');
      // Call destroy() to release resources when the request is no longer needed, preventing memory leaks.
      httpRequest.destroy();
    }
  });
```

> **NOTE**
> When the data output by **console.info()** contains line breaks, the line breaks are rendered as new lines for display.
>
> Since API version 12, HTTP responses compressed using the Brotli algorithm are supported.

## http.createHttp

createHttp(): HttpRequest

Creates an HTTP request. You can use this API to initiate or destroy an HTTP request, or enable or disable listening for HTTP Response Header events. To initiate multiple HTTP requests, you must create an **HttpRequest** object for each HTTP request. An **HttpRequest** object corresponds to an HTTP request.

> **NOTE**
> When the request is no longer needed, call destroy() to release resources. Otherwise, memory leaks may occur.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Return value**

| Type       | Description                                                        |
| :---------- | :----------------------------------------------------------- |
| HttpRequest | An **HttpRequest** object, which contains the **request**, **requestInStream**, **requestSync**, **enableAutoCookie**, **destroy**, **on**, and **off** methods.|

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
```

## HttpRequest

Defines an HTTP request task. Before invoking APIs provided by **HttpRequest**, you must call [createHttp()](#httpcreatehttp) to create an **HttpRequestTask** object.

### request

request(url: string, callback: AsyncCallback\<HttpResponse\>): void

Initiates an HTTP request to a given URL. This API uses an asynchronous callback to return the result. 

> **NOTE**
>
>(1) This API can receive only data whose size is less than 5 MB. If the data size exceeds 5 MB, you need to set **maxLimit** to a larger value in [HttpRequestOptions](#httprequestoptions) or call [requestInStream](#requestinstream10) to initiate a streaming request. Since API version 23, this API can receive a maximum of 50 MB data. In versions earlier than API version 23, this API can receive a maximum of 5 MB data, and any data exceeding this threshold will fail to be received.<br>
>(2) If you need to pass in cookies, add them to the **options** parameter.<br>
>(3) If the URL contains non-English characters, call **encodeURL(url)** to encode the URL before initiating an HTTP request.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                                          | Mandatory| Description                   |
| -------- | ---------------------------------------------- | ---- | ---------------------- |
| url      | string                                         | Yes   | URL for initiating the network request. Example: https://www.test.com |
| callback | AsyncCallback\<[HttpResponse](#httpresponse)\> | Yes  | Callback used to return the result.   |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [HTTP Error Codes](errorcode-net-http.md).<br>
The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

| ID  | Error Message                                                        |
|---------|----------------------------------------------------------------|
| 401     | Parameter error.                                               |
| 201     | Permission denied.                                             |
| 2300001 | Unsupported protocol.                                          |
| 2300003 | Invalid URL format or missing URL.                             |
| 2300005 | Failed to resolve the proxy name.                              |
| 2300006 | Failed to resolve the host name.                               |
| 2300007 | Failed to connect to the server.                               |
| 2300008 | Invalid server response.                                       |
| 2300009 | Access to the remote resource denied.                          |
| 2300016 | Error in the HTTP2 framing layer.                              |
| 2300018 | Transferred a partial file.                                    |
| 2300023 | Failed to write the received data to the disk or application.  |
| 2300025 | Upload failed.                                                 |
| 2300026 | Failed to open or read local data from the file or application.|
| 2300027 | Out of memory.                                                 |
| 2300028 | Operation timeout.                                             |
| 2300047 | The number of redirections reaches the maximum allowed.        |
| 2300052 | The server returned nothing (no header or data).               |
| 2300055 | Failed to send data to the peer.                               |
| 2300056 | Failed to receive data from the peer.                          |
| 2300058 | Local SSL certificate error.                                   |
| 2300059 | The specified SSL cipher cannot be used.                       |
| 2300060 | Invalid SSL peer certificate or SSH remote key.                |
| 2300061 | Invalid HTTP encoding format.                                  |
| 2300063 | Maximum file size exceeded.                                    |
| 2300070 | Remote disk full.                                              |
| 2300073 | Remote file already exists.                                    |
| 2300077 | The SSL CA certificate does not exist or is inaccessible.      |
| 2300078 | Remote file not found.                                         |
| 2300094 | Authentication error.                                          |
| 2300997 | Cleartext traffic not permitted.                               |
| 2300998 | It is not allowed to access this domain.                       |
| 2300999 | Internal error.                                                 |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.request("EXAMPLE_URL", (err: Error, data: http.HttpResponse) => {
  if (!err) {
    console.info('Result:' + data.result);
    console.info('code:' + data.responseCode);
    console.info('type:' + JSON.stringify(data.resultType));
    console.info('header:' + JSON.stringify(data.header));
    console.info('cookies:' + data.cookies); // Cookies are supported since API version 8.
  } else {
    console.error('error:' + JSON.stringify(err));
  }
});
```

### request

request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse\>):void

Initiates an HTTP request containing specified options to a given URL. This API uses an asynchronous callback to return the result.

> **NOTE**
>
>(1) This API can receive only data whose size is less than 5 MB. If the data size exceeds 5 MB, you need to set **maxLimit** to a larger value in [HttpRequestOptions](#httprequestoptions) or call [requestInStream](#requestinstream10) to initiate a streaming request. Since API version 23, this API can receive a maximum of 50 MB data. In versions earlier than API version 23, this API can receive a maximum of 5 MB data, and any data exceeding this threshold will fail to be received.<br>
>(2) If you need to pass in cookies, add them to the **options** parameter.<br>
>(3) If the URL contains non-English characters, call **encodeURL(url)** to encode the URL before initiating an HTTP request.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                                          | Mandatory| Description                                           |
| -------- | ---------------------------------------------- | ---- | ----------------------------------------------- |
| url      | string                                         | Yes  | URL for initiating an HTTP request.                        |
| options  | HttpRequestOptions                             | Yes  | Request options. For details, see [HttpRequestOptions](#httprequestoptions).|
| callback | AsyncCallback\<[HttpResponse](#httpresponse)\> | Yes  | Callback used to return the result. If the operation is successful, the callback content is an [HttpResponse](#httpresponse) object; otherwise, the callback content is undefined.                       |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [HTTP Error Codes](errorcode-net-http.md).<br>
The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

| ID  | Error Message                                                        |
|---------|----------------------------------------------------------------|
| 401     | Parameter error.                                               |
| 201     | Permission denied.                                             |
| 2300001 | Unsupported protocol.                                          |
| 2300003 | Invalid URL format or missing URL.                             |
| 2300005 | Failed to resolve the proxy name.                              |
| 2300006 | Failed to resolve the host name.                               |
| 2300007 | Failed to connect to the server.                               |
| 2300008 | Invalid server response.                                       |
| 2300009 | Access to the remote resource denied.                          |
| 2300016 | Error in the HTTP2 framing layer.                              |
| 2300018 | Transferred a partial file.                                    |
| 2300023 | Failed to write the received data to the disk or application.  |
| 2300025 | Upload failed.                                                 |
| 2300026 | Failed to open or read local data from the file or application.|
| 2300027 | Out of memory.                                                 |
| 2300028 | Operation timeout.                                             |
| 2300047 | The number of redirections reaches the maximum allowed.        |
| 2300052 | The server returned nothing (no header or data).               |
| 2300055 | Failed to send data to the peer.                               |
| 2300056 | Failed to receive data from the peer.                          |
| 2300058 | Local SSL certificate error.                                   |
| 2300059 | The specified SSL cipher cannot be used.                       |
| 2300060 | Invalid SSL peer certificate or SSH remote key.                |
| 2300061 | Invalid HTTP encoding format.                                  |
| 2300063 | Maximum file size exceeded.                                    |
| 2300070 | Remote disk full.                                              |
| 2300073 | Remote file already exists.                                    |
| 2300077 | The SSL CA certificate does not exist or is inaccessible.      |
| 2300078 | Remote file not found.                                         |
| 2300094 | Authentication error.                                          |
| 2300997 | Cleartext traffic not permitted.                               |
| 2300998 | It is not allowed to access this domain.                       |
| 2300999 | Internal error.                                                 |

**Example**

```ts
import { http } from '@kit.NetworkKit';

class Header {
  public contentType: string;

  constructor(contentType: string) {
    this.contentType = contentType;
  }
}

let httpRequest = http.createHttp();
let options: http.HttpRequestOptions = {
    method: http.RequestMethod.POST, // Optional. The default value is http.RequestMethod.GET.
  // You are advised to use the body field to transfer the request body content. The specific format needs to be negotiated with the server.
  body: 'data to send', // Supported since API version 26.
  // You are advised to use the queryParams field to transfer URL parameters. The value can be a string or an object.
  queryParams: { scene: 'request-demo', page: 1 }, // Supported since API version 26.
    expectDataType: http.HttpDataType.STRING, // Optional. This parameter specifies the type of the return data.
    usingCache: true, // Optional. The default value is true.
    priority: 1, // Optional. The default value is 1.
    // You can add the header field based on service requirements.
    header: new Header('application/json'),
    readTimeout: 60000, // Optional. The default value is 60000, in ms.
    connectTimeout: 60000 // Optional. The default value is 60000, in ms.
    usingProtocol: http.HttpProtocol.HTTP1_1, // Optional. The default protocol type is automatically specified by the system.
    usingProxy: false, // Optional. The system proxy is used by default. If this parameter is set to false, no proxy is used. This field is supported since API version 10.
};

httpRequest.request("EXAMPLE_URL", options, (err: Error, data: http.HttpResponse) => {
  if (!err) {
    console.info('Result:' + data.result);
    console.info('code:' + data.responseCode);
    console.info('type:' + JSON.stringify(data.resultType));
    console.info('header:' + JSON.stringify(data.header));
    console.info('cookies:' + data.cookies); // Cookies are supported since API version 8.
  } else {
    console.error('error:' + JSON.stringify(err));
  }
});
```

### request

request(url: string, options? : HttpRequestOptions): Promise\<HttpResponse\>

Initiates an HTTP request containing specified options to a given URL. This API uses a promise to return the result. 

> **NOTE**
>
>(1) This API can receive only data whose size is less than 5 MB. If the data size exceeds 5 MB, you need to set **maxLimit** to a larger value in [HttpRequestOptions](#httprequestoptions) or call [requestInStream](#requestinstream10) to initiate a streaming request. Since API version 23, this API can receive a maximum of 50 MB data. In versions earlier than API version 23, this API can receive a maximum of 5 MB data, and any data exceeding this threshold will fail to be received.<br>
>(2) If you need to pass in cookies, add them to the **options** parameter.<br>
>(3) If the URL contains non-English characters, call **encodeURL(url)** to encode the URL before initiating an HTTP request.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name | Type              | Mandatory| Description                                           |
| ------- | ------------------ | ---- | ----------------------------------------------- |
| url     | string             | Yes  | URL for initiating an HTTP request.                        |
| options | HttpRequestOptions | No  | Request options. For details, see [HttpRequestOptions](#httprequestoptions).|

**Return value**

| Type                                  | Description                             |
| :------------------------------------- | :-------------------------------- |
| Promise<[HttpResponse](#httpresponse)> | Promise used to return the response result of the request. |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [HTTP Error Codes](errorcode-net-http.md).<br>
The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

| ID  | Error Message                                                        |
|---------|----------------------------------------------------------------|
| 401     | Parameter error.                                               |
| 201     | Permission denied.                                             |
| 2300001 | Unsupported protocol.                                          |
| 2300003 | Invalid URL format or missing URL.                             |
| 2300005 | Failed to resolve the proxy name.                              |
| 2300006 | Failed to resolve the host name.                               |
| 2300007 | Failed to connect to the server.                               |
| 2300008 | Invalid server response.                                       |
| 2300009 | Access to the remote resource denied.                          |
| 2300016 | Error in the HTTP2 framing layer.                              |
| 2300018 | Transferred a partial file.                                    |
| 2300023 | Failed to write the received data to the disk or application.  |
| 2300025 | Upload failed.                                                 |
| 2300026 | Failed to open or read local data from the file or application.|
| 2300027 | Out of memory.                                                 |
| 2300028 | Operation timeout.                                             |
| 2300047 | The number of redirections reaches the maximum allowed.        |
| 2300052 | The server returned nothing (no header or data).               |
| 2300055 | Failed to send data to the peer.                               |
| 2300056 | Failed to receive data from the peer.                          |
| 2300058 | Local SSL certificate error.                                   |
| 2300059 | The specified SSL cipher cannot be used.                       |
| 2300060 | Invalid SSL peer certificate or SSH remote key.                |
| 2300061 | Invalid HTTP encoding format.                                  |
| 2300063 | Maximum file size exceeded.                                    |
| 2300070 | Remote disk full.                                              |
| 2300073 | Remote file already exists.                                    |
| 2300077 | The SSL CA certificate does not exist or is inaccessible.      |
| 2300078 | Remote file not found.                                         |
| 2300094 | Authentication error.                                          |
| 2300997 | Cleartext traffic not permitted.                               |
| 2300998 | It is not allowed to access this domain.                       |
| 2300999 | Internal error.                                                 |

**Example**

```ts
import { http } from '@kit.NetworkKit';

class Header {
  public contentType: string;

  constructor(contentType: string) {
    this.contentType = contentType;
  }
}

let httpRequest = http.createHttp();
let promise = httpRequest.request("EXAMPLE_URL", {
  method: http.RequestMethod.GET,
  connectTimeout: 60000,
  readTimeout: 60000,
  header: new Header('application/json')
});
promise.then((data:http.HttpResponse) => {
  console.info('Result:' + data.result);
  console.info('code:' + data.responseCode);
  console.info('type:' + JSON.stringify(data.resultType));
  console.info('header:' + JSON.stringify(data.header));
  console.info('cookies:' + data.cookies); // Cookies are supported since API version 8.
  console.info('header.content-Type:' + data.header);
  console.info('header.Status-Line:' + data.header);
}).catch((err:Error) => {
  console.error('error:' + JSON.stringify(err));
});
```

### destroy

destroy(): void

Stops an HTTP request task and releases system resources.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Example**

```ts
import { http } from '@kit.NetworkKit';
let httpRequest = http.createHttp();

httpRequest.destroy();
```

### requestInStream<sup>10+</sup>

requestInStream(url: string, callback: AsyncCallback\<number\>): void

Initiates an HTTP request containing specified options to a given URL. This API uses an asynchronous callback to return the result, which is a streaming response.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                                          | Mandatory| Description                                           |
| -------- | ---------------------------------------------- | ---- | ----------------------------------------------- |
| url      | string                                         | Yes  | URL for initiating an HTTP request.                        |
| callback | AsyncCallback\<number\>       | Yes   | Callback function. If the request is successful, err is undefined and the HTTP request response error code is returned. For details about the meaning, see [ResponseCode](#responsecode). Otherwise, it is an error object.                                      |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [HTTP Error Codes](errorcode-net-http.md).<br>
The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

| ID  | Error Message                                                        |
|---------|----------------------------------------------------------------|
| 401     | Parameter error.                                               |
| 201     | Permission denied.                                             |
| 2300001 | Unsupported protocol.                                          |
| 2300003 | Invalid URL format or missing URL.                             |
| 2300005 | Failed to resolve the proxy name.                              |
| 2300006 | Failed to resolve the host name.                               |
| 2300007 | Failed to connect to the server.                               |
| 2300008 | Invalid server response.                                       |
| 2300009 | Access to the remote resource denied.                          |
| 2300016 | Error in the HTTP2 framing layer.                              |
| 2300018 | Transferred a partial file.                                    |
| 2300023 | Failed to write the received data to the disk or application.  |
| 2300025 | Upload failed.                                                 |
| 2300026 | Failed to open or read local data from the file or application.|
| 2300027 | Out of memory.                                                 |
| 2300028 | Operation timeout.                                             |
| 2300047 | The number of redirections reaches the maximum allowed.        |
| 2300052 | The server returned nothing (no header or data).               |
| 2300055 | Failed to send data to the peer.                               |
| 2300056 | Failed to receive data from the peer.                          |
| 2300058 | Local SSL certificate error.                                   |
| 2300059 | The specified SSL cipher cannot be used.                       |
| 2300060 | Invalid SSL peer certificate or SSH remote key.                |
| 2300061 | Invalid HTTP encoding format.                                  |
| 2300063 | Maximum file size exceeded.                                    |
| 2300070 | Remote disk full.                                              |
| 2300073 | Remote file already exists.                                    |
| 2300077 | The SSL CA certificate does not exist or is inaccessible.      |
| 2300078 | Remote file not found.                                         |
| 2300094 | Authentication error.                                          |
| 2300997 | Cleartext traffic not permitted.                               |
| 2300998 | It is not allowed to access this domain.                       |
| 2300999 | Internal error.                                                 |

**Example**

```ts
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpRequest = http.createHttp();
httpRequest.requestInStream("EXAMPLE_URL", (err: BusinessError, data: number) => {
  if (!err) {
    console.info("requestInStream OK! ResponseCode is " + JSON.stringify(data));
  } else {
    console.error("requestInStream ERROR : err = " + JSON.stringify(err));
  }
})
```

### requestInStream<sup>10+</sup>

requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number\>): void

Initiates an HTTP request containing specified options to a given URL. This API uses an asynchronous callback to return the result, which is a streaming response.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                                          | Mandatory| Description                                           |
| -------- | ---------------------------------------------- | ---- | ----------------------------------------------- |
| url      | string                                         | Yes  | URL for initiating an HTTP request.                        |
| options  | HttpRequestOptions                             | Yes  | Request options. For details, see [HttpRequestOptions](#httprequestoptions).|
| callback | AsyncCallback\<number\>       | Yes  | Callback used to return the result. If the request is successful, **err** is **undefined**, and the HTTP request response error code is returned. For details about the meaning, see [ResponseCode](#responsecode). Otherwise, an error object is returned.                                    |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [HTTP Error Codes](errorcode-net-http.md).<br>
The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

| ID  | Error Message                                                        |
|---------|----------------------------------------------------------------|
| 401     | Parameter error.                                               |
| 201     | Permission denied.                                             |
| 2300001 | Unsupported protocol.                                          |
| 2300003 | Invalid URL format or missing URL.                             |
| 2300005 | Failed to resolve the proxy name.                              |
| 2300006 | Failed to resolve the host name.                               |
| 2300007 | Failed to connect to the server.                               |
| 2300008 | Invalid server response.                                       |
| 2300009 | Access to the remote resource denied.                          |
| 2300016 | Error in the HTTP2 framing layer.                              |
| 2300018 | Transferred a partial file.                                    |
| 2300023 | Failed to write the received data to the disk or application.  |
| 2300025 | Upload failed.                                                 |
| 2300026 | Failed to open or read local data from the file or application.|
| 2300027 | Out of memory.                                                 |
| 2300028 | Operation timeout.                                             |
| 2300047 | The number of redirections reaches the maximum allowed.        |
| 2300052 | The server returned nothing (no header or data).               |
| 2300055 | Failed to send data to the peer.                               |
| 2300056 | Failed to receive data from the peer.                          |
| 2300058 | Local SSL certificate error.                                   |
| 2300059 | The specified SSL cipher cannot be used.                       |
| 2300060 | Invalid SSL peer certificate or SSH remote key.                |
| 2300061 | Invalid HTTP encoding format.                                  |
| 2300063 | Maximum file size exceeded.                                    |
| 2300070 | Remote disk full.                                              |
| 2300073 | Remote file already exists.                                    |
| 2300077 | The SSL CA certificate does not exist or is inaccessible.      |
| 2300078 | Remote file not found.                                         |
| 2300094 | Authentication error.                                          |
| 2300997 | Cleartext traffic not permitted.                               |
| 2300998 | It is not allowed to access this domain.                       |
| 2300999 | Internal error.                                                 |

**Example**

```ts
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

class Header {
  public contentType: string;

  constructor(contentType: string) {
    this.contentType = contentType;
  }
}

let httpRequest = http.createHttp();
let options: http.HttpRequestOptions = {
    method: http.RequestMethod.POST, // Optional. The default value is http.RequestMethod.GET.
    // This field is used to transfer the request body when a POST request is used. Its format needs to be negotiated with the server.
    extraData: 'data to send', // Since API version 26, you are advised to use the body field to transfer the request body content. The specific format needs to be negotiated with the server.
    expectDataType: http.HttpDataType.STRING, // Optional. This field specifies the type of the return data.
    usingCache: true, // Optional. The default value is true.
    priority: 1, // Optional. The default value is 1.
    // You can add the header field based on service requirements.
    header: new Header('application/json'),
    readTimeout: 60000, // Optional. The default value is 60000, in ms.
    connectTimeout: 60000 // Optional. The default value is 60000, in ms.
    usingProtocol: http.HttpProtocol.HTTP1_1, // Optional. The default protocol type is automatically specified by the system.
    usingProxy: false, // Optional. The system proxy is used by default. If this parameter is set to false, no proxy is used. This field is supported since API version 10.
};
httpRequest.requestInStream("EXAMPLE_URL", options, (err: BusinessError<void> , data: number) => {
  if (!err) {
    console.info("requestInStream OK! ResponseCode is " + JSON.stringify(data));
  } else {
    console.error("requestInStream ERROR : err = " + JSON.stringify(err));
  }
})
```

### requestInStream<sup>10+</sup>

requestInStream(url: string, options? : HttpRequestOptions): Promise\<number\>

Initiates an HTTP request containing specified options to a given URL. This API uses a promise to return the result, which is a streaming response.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name | Type              | Mandatory| Description                                           |
| ------- | ------------------ | ---- | ----------------------------------------------- |
| url     | string             | Yes  | URL for initiating an HTTP request.                        |
| options | HttpRequestOptions | No  | Request options. For details, see [HttpRequestOptions](#httprequestoptions).|

**Return value**

| Type                                  | Description                             |
| :------------------------------------- | :-------------------------------- |
| Promise\<number\> | Promise used to return the result of initiating the request. For details, see [ResponseCode](#responsecode). |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [HTTP Error Codes](errorcode-net-http.md).<br>
The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

| ID  | Error Message                                                        |
|---------|----------------------------------------------------------------|
| 401     | Parameter error.                                               |
| 201     | Permission denied.                                             |
| 2300001 | Unsupported protocol.                                          |
| 2300003 | Invalid URL format or missing URL.                             |
| 2300005 | Failed to resolve the proxy name.                              |
| 2300006 | Failed to resolve the host name.                               |
| 2300007 | Failed to connect to the server.                               |
| 2300008 | Invalid server response.                                       |
| 2300009 | Access to the remote resource denied.                          |
| 2300016 | Error in the HTTP2 framing layer.                              |
| 2300018 | Transferred a partial file.                                    |
| 2300023 | Failed to write the received data to the disk or application.  |
| 2300025 | Upload failed.                                                 |
| 2300026 | Failed to open or read local data from the file or application.|
| 2300027 | Out of memory.                                                 |
| 2300028 | Operation timeout.                                             |
| 2300047 | The number of redirections reaches the maximum allowed.        |
| 2300052 | The server returned nothing (no header or data).               |
| 2300055 | Failed to send data to the peer.                               |
| 2300056 | Failed to receive data from the peer.                          |
| 2300058 | Local SSL certificate error.                                   |
| 2300059 | The specified SSL cipher cannot be used.                       |
| 2300060 | Invalid SSL peer certificate or SSH remote key.                |
| 2300061 | Invalid HTTP encoding format.                                  |
| 2300063 | Maximum file size exceeded.                                    |
| 2300070 | Remote disk full.                                              |
| 2300073 | Remote file already exists.                                    |
| 2300077 | The SSL CA certificate does not exist or is inaccessible.      |
| 2300078 | Remote file not found.                                         |
| 2300094 | Authentication error.                                          |
| 2300997 | Cleartext traffic not permitted.                               |
| 2300998 | It is not allowed to access this domain.                       |
| 2300999 | Internal error.                                                 |

**Example**

```ts
import { http } from '@kit.NetworkKit';

class Header {
  public contentType: string;

  constructor(contentType: string) {
    this.contentType = contentType;
  }
}

let httpRequest = http.createHttp();
let promise = httpRequest.requestInStream("EXAMPLE_URL", {
  method: http.RequestMethod.GET,
  connectTimeout: 60000,
  readTimeout: 60000,
  header: new Header('application/json')
});
promise.then((data: number) => {
  console.info("requestInStream OK!" + data);
}).catch((err: Error) => {
  console.error("requestInStream ERROR : err = " + JSON.stringify(err));
});
```

### requestSync

requestSync(url: string, options?: HttpRequestOptions): HttpResponse

Initiates an HTTP network request based on the URL and related configuration options (optional). This API returns the response synchronously.

> **NOTE**
>
 >(1) This API can receive data of up to 50 MB. To receive more than 50 MB of data, set the **maxLimit** parameter in [HttpRequestOptions](#httprequestoptions).<br>
 >(2) If you need to pass in cookies, add them to the **options** parameter.<br>
 >(3) If the URL contains non-English characters, call **encodeURL(url)** to encode the URL before initiating an HTTP request.<br>
 >(4) This API is synchronous and blocks the current thread until an HTTP response or error code is returned.

 **Since**: 26.0.0

**Required permission**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetStack

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type              | Mandatory| Description                                           |
| ------- | ------------------ | ---- | ----------------------------------------------- |
| url     | string             | Yes  | URL for initiating an HTTP request.                        |
| options | HttpRequestOptions | No  | Request options. For details, see [HttpRequestOptions](#httprequestoptions).|

**Return value**

| Type                                  | Description                             |
| -------------------------------------- | --------------------------------- |
| [HttpResponse](#httpresponse) | HTTP request response result that is returned synchronously.|

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [HTTP Error Codes](errorcode-net-http.md).<br>
The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

| ID  | Error Message                                                        |
|---------|----------------------------------------------------------------|
| 201     | Permission denied.                                             |
| 2300001 | Unsupported protocol.                                          |
| 2300003 | Invalid URL format or missing URL.                             |
| 2300005 | Failed to resolve the proxy name.                              |
| 2300006 | Failed to resolve the host name.                               |
| 2300007 | Failed to connect to the server.                               |
| 2300008 | Invalid server response.                                       |
| 2300009 | Access to the remote resource denied.                          |
| 2300016 | Error in the HTTP2 framing layer.                              |
| 2300018 | Transferred a partial file.                                    |
| 2300023 | Failed to write the received data to the disk or application.  |
| 2300025 | Upload failed.                                                 |
| 2300026 | Failed to open or read local data from the file or application.|
| 2300027 | Out of memory.                                                 |
| 2300028 | Operation timeout.                                             |
| 2300047 | The number of redirections reaches the maximum allowed.        |
| 2300052 | The server returned nothing (no header or data).               |
| 2300055 | Failed to send data to the peer.                               |
| 2300056 | Failed to receive data from the peer.                          |
| 2300058 | Local SSL certificate error.                                   |
| 2300059 | The specified SSL cipher cannot be used.                       |
| 2300060 | Invalid SSL peer certificate or SSH remote key.                |
| 2300061 | Invalid HTTP encoding format.                                  |
| 2300063 | Maximum file size exceeded.                                    |
| 2300070 | Remote disk full.                                              |
| 2300073 | Remote file already exists.                                    |
| 2300077 | The SSL CA certificate does not exist or is inaccessible.      |
| 2300078 | Remote file not found.                                         |
| 2300094 | Authentication error.                                          |
| 2300997 | Cleartext traffic not permitted.                               |
| 2300998 | It is not allowed to access this domain.                       |
| 2300999 | Internal error.                                                 |

**Example**

```ts
import { http } from '@kit.NetworkKit';

class Header {
  public contentType: string;

  constructor(contentType: string) {
    this.contentType = contentType;
  }
}

let httpRequest = http.createHttp();
let options: http.HttpRequestOptions = {
    method: http.RequestMethod.POST, // Optional. The default value is http.RequestMethod.GET.
    // This field is used to transfer the request body when a POST request is used. Its format needs to be negotiated with the server.
    extraData: 'data to send',
    expectDataType: http.HttpDataType.STRING, // Optional. This field specifies the type of the return data.
    usingCache: true, // Optional. The default value is true.
    priority: 1, // Optional. The default value is 1.
    // You can add the header field based on service requirements.
    header: new Header('application/json'),
    readTimeout: 60000, // Optional. The default value is 60000, in ms.
    connectTimeout: 60000 // Optional. The default value is 60000, in ms.
    usingProtocol: http.HttpProtocol.HTTP1_1, // Optional. The default protocol type is automatically specified by the system.
    usingProxy: false, // Optional. The system proxy is used by default. If this parameter is set to false, no proxy is used. This field is supported since API version 10.
};
let url = "EXAMPLE_URL"; // Access URL.
try {
  let data: http.HttpResponse = httpRequest.requestSync(url, options);
  console.info('Result:' + data.result);
  console.info('code:' + data.responseCode);
  console.info('type:' + JSON.stringify(data.resultType));
  console.info('header:' + JSON.stringify(data.header));
  console.info('cookies:' + data.cookies); // Cookies are supported since API version 8.
} catch (err) {
  console.error('error:' + JSON.stringify(err));
}
httpRequest.destroy();
```

### enableAutoCookie

enableAutoCookie(enable: boolean): void

Sets whether to automatically carry and share cookies. That is, whether to automatically reuse the cookies delivered by the server among multiple requests of the same **HttpRequest** instance.

> **NOTE**
>
> (1) The default value is **false**, which means cookies are not automatically carried by default.<br>
> (2) When the configuration is switched from **false** to **true**, it takes effect in subsequent requests initiated by calling the **request** API, and cookies are automatically shared.<br>
> (3) When the configuration is switched from **true** to **false**, the cookie sharing state saved in the current instance is cleared.<br>
> (4) Cookie handling in redirection scenarios: Cookies manually configured through the **header** field are not automatically sent to the target host after redirection. Only cookies delivered by the server through **Set-Cookie** are automatically carried based on domain name rules.<br>
> (5) Cross-domain cookie carrying rules: Automatic cookie carrying takes effect only between the same domain name or the same subdomain. Automatic cookie carrying is not supported between different domain names.

**Since**: 26.0.0

**System capability**: SystemCapability.Communication.NetStack

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| ------- | ------- | ---- | ----------------------------------------------- |
| enable | boolean | Yes| Whether to automatically carry cookies. **true**: yes; **false**: no.|

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
let url = "EXAMPLE_URL"; // Access URL. You need to define the URL based on the actual scenario.

// Enable automatic cookie sharing.
httpRequest.enableAutoCookie(true);

httpRequest.request(url, {
  method: http.RequestMethod.GET
}).then((data: http.HttpResponse) => {
  console.info('first request code:' + data.responseCode);
  // Subsequent requests will automatically reuse the cookies saved by this instance.
  return httpRequest.request(url, { method: http.RequestMethod.GET });
}).then((data: http.HttpResponse) => {
  console.info('second request code:' + data.responseCode);
}).catch((err: Error) => {
  console.error('error:' + JSON.stringify(err));
}).finally(() => {
  httpRequest.destroy();
});
```

### on("headerReceive")<sup>(deprecated)</sup>

on(type: "headerReceive", callback: AsyncCallback\<Object\>): void

Registers an observer for HTTP Response Header events.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 8. You are advised to use [on("headersReceive")](#onheadersreceive8) instead.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                   | Mandatory| Description                             |
| -------- | ----------------------- | ---- | --------------------------------- |
| type     | string                  | Yes  | Event type. The value is **headerReceive**.|
| callback | AsyncCallback\<Object\> | Yes  | Callback used to return the result. If the operation is successful, **error** is **undefined**, and **data** is the received HTTP response header. Otherwise, **error** is an error object.|

**Example**

```ts
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpRequest = http.createHttp();
httpRequest.on("headerReceive", (data: BusinessError) => {
  console.error("error:" + JSON.stringify(data));
});
```

### off("headerReceive")<sup>(deprecated)</sup>

off(type: "headerReceive", callback?: AsyncCallback\<Object\>): void

Unregisters the observer for HTTP Response Header events.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 8. You are advised to use [off("headersReceive")](#offheadersreceive8) instead.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                   | Mandatory| Description                                 |
| -------- | ----------------------- | ---- | ------------------------------------- |
| type     | string                  | Yes  | Event type. The value is **headerReceive**.|
| callback | AsyncCallback\<Object\> | No  | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.                          |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.off("headerReceive");
```

### on("headersReceive")<sup>8+</sup>

on(type: "headersReceive", callback: Callback\<Object\>): void

Registers an observer for HTTP Response Header events.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type              | Mandatory| Description                       |
| -------- | ------------------ | ---- |---------------------------|
| type     | string             | Yes  | Event type. The value is **headersReceive**.|
| callback | Callback\<Object\> | Yes  | Callback used to return the HTTP response header.        |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("headersReceive", (header: Object) => {
  console.info("header: " + JSON.stringify(header));
});
httpRequest.off("headersReceive");
```

### off("headersReceive")<sup>8+</sup>

off(type: "headersReceive", callback?: Callback\<Object\>): void

Unregisters the observer for HTTP Response Header events.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type              | Mandatory| Description                                  |
| -------- | ------------------ | ---- | -------------------------------------- |
| type     | string             | Yes  | Event type. The value is **headersReceive**.|
| callback | Callback\<Object\> | No  | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.                            |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("headersReceive", (header: Object) => {
  console.info("header: " + JSON.stringify(header));
});
httpRequest.off("headersReceive");
```

### once("headersReceive")<sup>8+</sup>

once(type: "headersReceive", callback: Callback\<Object\>): void

Registers a one-time observer for HTTP Response Header events. Once triggered, the observer will be removed. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type              | Mandatory| Description                              |
| -------- | ------------------ | ---- | ---------------------------------- |
| type     | string             | Yes   | Subscription event. The value is fixed to **'headersReceive'**, which indicates the response header receive event. |
| callback | Callback\<Object\> | Yes  | Callback used to return the HTTP response header.                        |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.once("headersReceive", (header: Object) => {
  console.info("header: " + JSON.stringify(header));
});
```

### on("dataReceive")<sup>10+</sup>

on(type: "dataReceive", callback: Callback\<ArrayBuffer\>): void

Registers an observer for events indicating receiving of HTTP streaming responses.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                   | Mandatory| Description                             |
| -------- | ----------------------- | ---- | --------------------------------- |
| type     | string                  | Yes  | Event type. The value is **dataReceive**.|
| callback | Callback\<ArrayBuffer\> | Yes | Callback used to return the result. If the subscription is successful, **err** is **undefined** and data is the received HTTP streaming data of the ArrayBuffer type. Otherwise, the value is an error object. |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("dataReceive", (data: ArrayBuffer) => {
  console.info("dataReceive length: " + JSON.stringify(data.byteLength));
});
httpRequest.off("dataReceive");
```

### off("dataReceive")<sup>10+</sup>

off(type: "dataReceive", callback?: Callback\<ArrayBuffer\>): void

Unregisters the observer for events indicating receiving of HTTP streaming responses.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type              | Mandatory| Description                                  |
| -------- | ------------------ | ---- | -------------------------------------- |
| type     | string             | Yes  | Event type. The value is **dataReceive**.|
| callback | Callback\<ArrayBuffer\> | No  | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.                            |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("dataReceive", (data: ArrayBuffer) => {
  console.info("dataReceive length: " + JSON.stringify(data.byteLength));
});
httpRequest.off("dataReceive");
```

### on("dataEnd")<sup>10+</sup>

on(type: "dataEnd", callback: Callback\<void\>): void

Registers an observer for events indicating completion of receiving HTTP streaming responses.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                   | Mandatory| Description                             |
| -------- | ----------------------- | ---- | --------------------------------- |
| type     | string                  | Yes  | Event type. The value is **dataEnd**.|
| callback | Callback\<void\>   | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an **Error** object.                       |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("dataEnd", () => {
  console.info("Receive dataEnd !");
});
httpRequest.off("dataEnd");
```

### off("dataEnd")<sup>10+</sup>

off(type: "dataEnd", callback?: Callback\<void\>): void

Unregisters the observer for events indicating completion of receiving HTTP streaming responses.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type              | Mandatory| Description                                  |
| -------- | ------------------ | ---- | -------------------------------------- |
| type     | string             | Yes  | Event type. The value is **dataEnd**.|
| callback | Callback\<void\>   | No  | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.                            |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("dataEnd", () => {
  console.info("Receive dataEnd !");
});
httpRequest.off("dataEnd");
```

### on('dataReceiveProgress')<sup>10+</sup>

on(type: 'dataReceiveProgress', callback: Callback\<DataReceiveProgressInfo\>): void

Registers an observer for events indicating progress of receiving HTTP streaming responses.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                   | Mandatory| Description                             |
| -------- | ----------------------- | ---- | --------------------------------- |
| type     | string                  | Yes  | Event type. The value is **dataReceiveProgress**.|
| callback | Callback\<[DataReceiveProgressInfo](#datareceiveprogressinfo11)\>   | Yes  | Callback used to return the result. If the operation is successful, the callback content is a [DataReceiveProgressInfo](#datareceiveprogressinfo11) object; otherwise, the callback content is **undefined**.|

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("dataReceiveProgress", (data: http.DataReceiveProgressInfo) => {
  console.info("dataReceiveProgress:" + JSON.stringify(data));
});
httpRequest.off("dataReceiveProgress");
```

### off('dataReceiveProgress')<sup>10+</sup>

off(type: 'dataReceiveProgress', callback?: Callback\<DataReceiveProgressInfo\>): void

Unregisters the observer for events indicating progress of receiving HTTP streaming responses.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type              | Mandatory| Description                                  |
| -------- | ------------------ | ---- | -------------------------------------- |
| type     | string             | Yes  | Event type. The value is **dataReceiveProgress**.|
| callback | Callback\<[DataReceiveProgressInfo](#datareceiveprogressinfo11)\>   | No  | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.   |

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("dataReceiveProgress", (data: http.DataReceiveProgressInfo) => {
  console.info("dataReceiveProgress:" + JSON.stringify(data));
});
httpRequest.off("dataReceiveProgress");
```

### on('dataSendProgress')<sup>11+</sup>

on(type: 'dataSendProgress', callback: Callback\<DataSendProgressInfo\>): void

Registers an observer for events indicating progress of sending HTTP requests.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                   | Mandatory| Description                             |
| -------- | ----------------------- | ---- | --------------------------------- |
| type     | string                  | Yes  | Event type. The value is **dataSendProgress**.|
| callback | Callback\<[DataSendProgressInfo](#datasendprogressinfo11)\>   | Yes  | Callback used to return the result. If the operation is successful, the callback content is a [DataSendProgressInfo](#datasendprogressinfo11) object; otherwise, the callback content is **undefined**.|

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("dataSendProgress", (data: http.DataSendProgressInfo) => {
  console.info("dataSendProgress:" + JSON.stringify(data));
});
httpRequest.off("dataSendProgress");
```

### off('dataSendProgress')<sup>11+</sup>

off(type: 'dataSendProgress', callback?: Callback\<DataSendProgressInfo\>): void

Unregisters the observer for events indicating progress of sending HTTP requests.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type              | Mandatory| Description                                  |
| -------- | ------------------ | ---- | -------------------------------------- |
| type     | string             | Yes  | Event type. The value is **dataSendProgress**.|
| callback | Callback\<[DataSendProgressInfo](#datasendprogressinfo11)\>  | No| Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.|

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
httpRequest.on("dataSendProgress", (data: http.DataSendProgressInfo) => {
  console.info("dataSendProgress:" + JSON.stringify(data));
});
httpRequest.off("dataSendProgress");
```

## HttpRequestOptions

Defines the options for initiating an HTTP request.

**System capability**: SystemCapability.Communication.NetStack

<!--Table: 12%; 14%; 8%; 8%; 58%-->

| Name        | Type                                         | Read Only| Optional| Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| -------------- | --------------------------------------------- | ---- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| method         | [RequestMethod](#requestmethod)               | No | Yes | Request method. The default value is **GET**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| extraData      | string \| Object \| ArrayBuffer | No | Yes | Additional data for sending a request. This parameter is not used by default. Since API version 26, you are advised to use the **body** and **queryParams** parameters preferentially.<br>**Note**: Do not add this parameter if no extra data is available. If this parameter must be added, set it to **undefined** or **null**. Do not pass the parameter as "".<br>- If the HTTP request uses a POST, PUT, or DELETE method, this field serves as the content of the HTTP request and is encoded in UTF-8 format.<br>Example:<br>  (1) If **content-Type** is **application/x-www-form-urlencoded**, the data in the request body must be encoded in the format of **key1=value1&key2=value2&key3=value3** after URL transcoding (**encodeURIComponent/encodeURI**) and this field is usually in the String format.<br>(2) If **content-Type** is **text/xml**, this field is usually in the String format.<br>(3) If **content-Type** is **application/json**, this field is usually in the Object format.<br>(4) If **content-Type** is **application/octet-stream**, this field is usually in the ArrayBuffer format.<br>(5) If **content-Type** is **multipart/form-data** and the content to be uploaded is a file, this field is usually in the ArrayBuffer format.<br>The preceding information is for reference only and may vary according to the actual situation.<br>- If the HTTP request uses the GET, OPTIONS, TRACE, or CONNECT method, this parameter serves as a supplement to HTTP request parameters. Parameters of the string type need to be encoded before being passed to the HTTP request. Parameters of the object type do not need to be precoded and will be directly concatenated to the URL. Parameters of the ArrayBuffer type will not be concatenated to the URL.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| body | string \| Object \| ArrayBuffer | No| Yes| HTTP request body. After this field is set, the framework preferentially sends this field as the request body.<br>- The value can be a string, an object, or an **ArrayBuffer**. A string is sent as the original value, an object is serialized before being sent, and an **ArrayBuffer** is sent in binary format.<br>- If both **body** and **extraData** are configured, **body** takes precedence and **extraData** will be ignored.<br>- This field can be used with any request method to explicitly specify the request body.<br>**Since**: 26.0.0<br>**Model restriction:** This API can be used only in the stage model.|
| queryParams | string \| [QueryParamObject](#queryparamobject) | No| Yes| Request parameters appended to the URL.<br>- The value can be a string or a **QueryParamObject**. A string is directly appended to the URL (without repeated encoding). A **QueryParamObject** is automatically encoded and serialized by the system.<br>- When a string is used, the leading **?** is not required. Use **&** to separate multiple parameters.<br>- If both **queryParams** and **extraData** are configured, **queryParams** takes precedence, and the URL parameter supplementation logic in **extraData** is ignored.<br>**Since**: 26.0.0<br>**Model restriction:** This API can be used only in the stage model.|
| expectDataType<sup>9+</sup>  | [HttpDataType](#httpdatatype9)  | No | Yes | Type of the returned data. This parameter is not used by default. If this parameter is set, the system returns the specified type of data preferentially. If the specified type is **Object**, the value can contain a maximum of 65536 characters.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| usingCache<sup>9+</sup>      | boolean                         | No | Yes | Whether to use the cache. The value **true** indicates that the cache is preferentially read when a request is initiated, and the value **false** indicates that the cache is not used. The default value is **true**. The cache function takes effect when the process is started. The new cached data will replace the existing cached data.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| priority<sup>9+</sup>        | number                          | No  | Yes  | Priority of HTTP/HTTPS requests. A larger value indicates a higher priority. The value range is [1,1000], and the default value is **1**. If the value is out of range, the default value will be used.<br>**Atomic service API:** This API can be used in atomic services since API version 11.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| header                       | Object                          | No | Yes | HTTP request header. If the request method is POST, PUT, DELETE, or null, the default value is {'content-Type': 'application/json'}. Otherwise, the default value is {'content-Type': 'application/x-www-form-urlencoded'}.<br>If the header contains fields of numeric type, the maximum value must be an int64 integer.<br>The header field supports the JSON format (as shown in [Example](js-apis-http.md#example)) and the Record<string, string> format.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| readTimeout                  | number                          | No | Yes | Read timeout duration. The default value is **60000**, in ms. The input value must be an uint32_t integer.<br>The value **0** indicates no timeout.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| connectTimeout               | number                          | No | Yes | Connection timeout interval. The default value is **60000**, in ms. The input value must be an uint32_t integer.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| usingProtocol<sup>9+</sup>   | [HttpProtocol](#httpprotocol9)  | No  | Yes  | Protocol version used for the HTTP request. If this parameter is not specified, the system automatically negotiates the most suitable protocol version. If HTTP3 is specified, due to the security restrictions of the HTTP3 protocol, the TLS version must be set to 1.3 through [TlsConfig](js-apis-http.md#tlsconfig18) and the target domain name must support the HTTP3 protocol to enable HTTP3. Otherwise, the protocol will be downgraded through negotiation.<br>**Atomic service API:** This API can be used in atomic services since API version 11.|
| usingProxy<sup>10+</sup>     | boolean \| [HttpProxy](js-apis-net-connection.md#httpproxy10)               | No  | Yes  | HTTP proxy configuration. If this parameter is not configured, the system proxy is used by default.<br />- When **usingProxy** is of the boolean type and set to **true**, the default network proxy is used. When set to **false**, no proxy is used.<br />- When **usingProxy** is of the HttpProxy type, the specified network proxy is used. Since API version 22, HttpProxy supports specifying the **username** and **password** fields.<br>- Since API version 26.0.0, when **usingSocks5Proxy** is correctly configured, the **usingProxy** parameter does not take effect.<br>**Atomic service API:** This API can be used in atomic services since API version 11.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| caPath<sup>10+</sup>     | string               | No  | Yes  | If this parameter is set and the certificate is valid, the system uses the user-specified CA certificate and the system-preset CA certificate. Otherwise, only the system-preset CA certificate is used. The CA certificate path is a sandbox mapping path (you can obtain the application sandbox path through the capabilities provided by [UIAbilityContext](../apis-ability-kit/js-apis-app-ability-common.md#uiabilitycontext)). Currently, only text-format certificates with the .pem extension are supported.<br> System-preset CA certificate location: **/etc/ssl/certs/cacert.pem**.<br>**Atomic service API:** This API can be used in atomic services since API version 11.                                                                                                                                                                                                                                                                                                                               |
| caData<sup>20+</sup>     | string               | No | Yes | CA certificate data. If this parameter is set and the certificate is valid, the system uses the specified CA certificate and the preset CA certificate. Otherwise, the system uses only the preset CA certificate. If both **caPath** and **caData** are set, **caData** is ignored by the system. Currently, only certificates in **.pem** format are supported. The maximum length is 8000 bytes. Only one certificate can be specified. A certificate chain is not allowed.<br>The preset CA certificate is available at **/etc/ssl/certs/cacert.pem**. This path is the sandbox mapping path, which can be obtained by using **UIAbilityContext** APIs.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| resumeFrom<sup>11+</sup> | number | No| Yes| Download start position. This field can be used only for the GET method. As stipulated in section 3.1 of RFC 7233, servers are allowed to ignore range requests.<br>- If the HTTP PUT method is used, do not use this option because it may conflict with other options.<br>- The value ranges from **1** to **4294967296** (4 GB). If the value is out of this range, this field does not take effect.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| resumeTo<sup>11+</sup> | number | No| Yes| Download end position. This field can be used only for the GET method. As stipulated in section 3.1 of RFC 7233, servers are allowed to ignore range requests.<br>- If the HTTP PUT method is used, do not use this option because it may conflict with other options.<br>- The value ranges from **1** to **4294967296** (4 GB). If the value is out of this range, this field does not take effect.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| clientCert<sup>11+</sup> | [ClientCert](#clientcert11) | No| Yes| Client certificate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| dnsOverHttps<sup>11+</sup> | string | No| Yes| Whether to use an HTTPS server for DNS resolution.<br>- The value must be URL-encoded in the following format: "https:// host:port/path".                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| dnsServers<sup>11+</sup> | Array\<string\> | No| Yes| Array of DNS servers used for DNS resolution.<br>- A maximum of three DNS servers can be set. If there are more than three DNS servers, only the first three DNS servers are used.<br>- The DNS servers must be expressed as IPv4 or IPv6 addresses.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| maxLimit<sup>11+</sup>   | number   | No | Yes | Maximum byte limit of the response message.<br />The default value is **5\*1024\*1024**, in bytes. The maximum value is **100\*1024\*1024**, in bytes.<br />                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| multiFormDataList<sup>11+</sup> | Array<[MultiFormData](#multiformdata11)> | No| Yes| Form data list. This field is valid when **content-Type** is set to **multipart/form-data**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| certificatePinning<sup>12+</sup> | [CertificatePinning](#certificatepinning12) \| CertificatePinning[] | No| Yes| Dynamic configuration of certificate pinning. One or more certificate PINs can be specified.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| addressFamily<sup>15+</sup> | [AddressFamily](#addressfamily15) | No| Yes| IP address family. You can specify an address type for domain name resolution.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| remoteValidation<sup>18+</sup> | [RemoteValidation](#remotevalidation18)                             | No| Yes| Certificate authority (CA), which is used to verify the identity of a remote server. If the parameter is not set, the default value is used. The options are as follows:<br>**Atomic service API**: This API can be used in atomic services since API version 18.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| tlsOptions<sup>18+</sup> | [TlsOptions](#tlsoptions18)                                         | No| Yes| TLS configuration.<br>**Atomic service API**: This API can be used in atomic services since API version 18.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| serverAuthentication<sup>18+</sup> | [ServerAuthentication](#serverauthentication18)                     | No| Yes| Whether to verify the server identity during a secure connection. The identity is not verified by default.<br>**Atomic service API**: This API can be used in atomic services since API version 18.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| sslType<sup>20+</sup> | [SslType](#ssltype20) | No| Yes| Security communication protocol. You can use TLS (default) or TLCP. If TLCP is used, the related options (such as **caPath**, **clientCert**, and **clientEncCert**) must be set to valid values.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| clientEncCert<sup>20+</sup> | [ClientCert](#clientcert11) | No| Yes| Client certificate, which is used by the server to verify the client identity.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| customMethod<sup>23+</sup> | string | No| Yes| Custom request method. For example, when the WebDAV extension protocol is implemented, **customMethod** has a higher priority than **method**.<br>- The default value is an empty string. The value can contain a maximum of 128 characters. If the value exceeds 128 characters, the setting does not take effect.<br>- If **customMethod** meets the WebDAV extension protocol request requirements but the server does not support the request, the server response code of the request is usually 405 or 501 (the actual result depends on the server behavior).<br>- If **customMethod** does not meet the WebDAV extension protocol request requirements, the server response code of the request is usually 400 or 405 (the actual result depends on the server behavior).|
| maxRedirects<sup>23+</sup> | number | No| Yes| The maximum number of redirections can be specified for HttpRequest.<br>- The default value is 30.<br>- The value range is [0, 2147483647]. If the value is set to **0**, redirection is disabled. If the number of redirections on the server exceeds the maximum number of redirections, error code 2300047 is returned. If the value is out of the range, the default value **30** takes effect.|
| sniHostName<sup>23+</sup> | string | No| Yes| Used to allow the client to declare the target domain name to the server in the TLS handshake phase by configuring the server name indication (SNI). In this way, the server can select the corresponding SSL/TLS certificate based on the domain name for encrypted communication.<br>- The default value is an empty string. The value of **sniHostName** can contain a maximum of 255 characters. If the length limit is exceeded or the value is an empty string, the setting does not take effect.|
| pathPreference<sup>23+</sup> |[PathPreference](#pathpreference23) | No| Yes|Used to specify the network to be activated in an HTTP request.|
| reuseConnections | boolean | No| Yes| Whether to reuse the connection for an HTTP request. The default value is **true**, meaning to reuse the existing connection. The value **false** means the opposite. This field can be used together with the **inactivityMs** field to customize the connection timeout interval.<br>- Connection reuse means that after an HTTP request is completed, the underlying TCP connection is not immediately closed. Instead, it remains in the connection pool. If subsequent HTTP requests have the same target address, the connection can be reused, reducing the overhead of TCP and TLS handshakes and improving performance.<br>**Since**: 26.0.0<br>**Model restriction:** This API can be used only in the stage model.|
| inactivityMs | number | No| Yes| Maximum idle time of a connection in the connection pool. If this value is exceeded, the connection is closed. The unit is ms. The default value is 118s. The system calculates the connection idle time, rounds it down to seconds, and then compares it with the configured value.<br>- The value range is (0, 2147483647]. If a value less than or equal to 0 is passed, the system uses the default value 118s. This parameter does not take effect when **reuseConnections** is set to **false**.<br>**Since**: 26.0.0<br>**Model restriction:** This API can be used only in the stage model.|
| usingSocks5Proxy | [Socks5Proxy](#socks5proxy) | No | Yes | SOCKS5 proxy configuration. If this parameter is not configured, the SOCKS5 proxy is not started.<br />When this parameter is correctly configured, if **usingProxy** is also configured, **usingProxy** does not take effect.<br />**Since:** 26.0.0 <br/>**Model restriction:** This API can be used only in the stage model.|
| enablePartialChain | boolean | No | Yes | Whether to allow the use of an intermediate CA certificate in the trust store as a trust anchor during certificate chain verification. When this parameter set to **false**, the certificate chain must be verified step by step up to a trusted root CA certificate. When set to **true**, if an intermediate CA certificate exists in the trust store, the certificate chain verification can be considered passed when it reaches this intermediate CA, without needing to trace back to the root CA certificate. When [SslType](#ssltype20) uses the default value or is set to TLS, the default value is **true**; when [SslType](#ssltype20) is set to TLCP, the default value is **false**.<br/>**Since:** 26.0.0 <br/>**Model restriction:** This API can be used only in the stage model.|

## RequestMethod

Defines an HTTP request method.

**System capability**: SystemCapability.Communication.NetStack

| Name   | Value     | Description               |
| :------ | ------- | :------------------ |
| OPTIONS | "OPTIONS" | Describes the communication options for the target resource.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| GET     | "GET"     | Requests a representation of the specified resource. Requests using **GET** should only retrieve data and should not contain a request body.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| HEAD    | "HEAD"    | Requests or a response identical to that of a **GET** request, but without the response body.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| POST    | "POST"    | Submits an entity to the specified resource, often causing a change in state on the server.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| PUT     | "PUT"     | Replaces all current representations of the target resource with the request content.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| DELETE  | "DELETE"  | Deletes the specified resource.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| TRACE   | "TRACE"   | Performs a message loop-back test along the path to the target resource.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| CONNECT | "CONNECT" | Establishes a tunnel to the server identified by the target resource.<br/>**Atomic service API:** This API can be used in atomic services since API version 11. |
| PATCH   | "PATCH"   | Applies partial modifications to a resource. <br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model.|

## ResponseCode

Enumerates the response codes for an HTTP request.

**System capability**: SystemCapability.Communication.NetStack

| Name             | Value  | Description                                                        |
| ----------------- | ---- | ------------------------------------------------------------ |
| OK                | 200  | The request is successful. This return code is generally used for GET and POST requests.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                           |
| CREATED           | 201  | "Created." The request has been successfully sent and a new resource is created.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                          |
| ACCEPTED          | 202  | "Accepted." The request has been accepted for processing, but the processing has not been completed.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                        |
| NOT_AUTHORITATIVE | 203  | "Non-Authoritative Information." The request is successful.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                      |
| NO_CONTENT        | 204  | "No Content." The server has successfully fulfilled the request but there is no additional content to send in the response payload body.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                      |
| RESET             | 205  | "Reset Content." The server has successfully fulfilled the request and desires that the user agent reset the content.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                  |
| PARTIAL           | 206  | "Partial Content." The server has successfully fulfilled the partial GET request for a given resource.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                     |
| MULT_CHOICE       | 300  | "Multiple Choices." The requested resource corresponds to any one of a set of representations.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                  |
| MOVED_PERM        | 301  | "Moved Permanently." The requested resource has been assigned a new permanent URI and any future references to this resource will be redirected to this URI.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| MOVED_TEMP        | 302  | "Moved Temporarily." The requested resource is moved temporarily to a different URI.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                  |
| SEE_OTHER         | 303  | "See Other." The response to the request can be found under a different URI.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                              |
| NOT_MODIFIED      | 304  | "Not Modified." The client has performed a conditional GET request and access is allowed, but the content has not been modified.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                    |
| USE_PROXY         | 305  | "Use Proxy." The requested resource can only be accessed through the proxy.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                  |
| BAD_REQUEST       | 400  | "Bad Request." The request could not be understood by the server due to incorrect syntax. <br>**Atomic service API**: This API can be used in atomic services since API version 11.                      |
| UNAUTHORIZED      | 401  | "Unauthorized." The request requires user authentication.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                    |
| PAYMENT_REQUIRED  | 402  |  "Payment Required." This code is reserved for future use.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                            |
| FORBIDDEN         | 403  | "Forbidden." The server understands the request but refuses to process it.<br>**Atomic service API**: This API can be used in atomic services since API version 11.            |
| NOT_FOUND         | 404  | "Not Found." The server does not find anything matching the Request-URI.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                |
| BAD_METHOD        | 405  | "Method Not Allowed." The method specified in the request is not allowed for the resource identified by the Request-URI.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                  |
| NOT_ACCEPTABLE    | 406  | "Not Acceptable." The server cannot fulfill the request according to the content characteristics of the request. <br>**Atomic service API**: This API can be used in atomic services since API version 11.                |
| PROXY_AUTH        | 407  | "Proxy Authentication Required." The request requires user authentication with the proxy.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                    |
| CLIENT_TIMEOUT    | 408  | "Request Timeout." The client fails to generate a request within the timeout period.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                        |
| CONFLICT          | 409  | "Conflict." The request cannot be fulfilled due to a conflict with the current state of the resource. Conflicts are most likely to occur in response to a PUT request. <br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| GONE              | 410  | "Gone." The requested resource has been deleted permanently and is no longer available. <br>**Atomic service API**: This API can be used in atomic services since API version 11.                                |
| LENGTH_REQUIRED   | 411  | "Length Required." The server refuses to process the request without a defined Content-Length.<br>**Atomic service API**: This API can be used in atomic services since API version 11.    |
| PRECON_FAILED     | 412  | "Precondition Failed." The precondition in the request is incorrect.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                              |
| ENTITY_TOO_LARGE  | 413  | "Request Entity Too Large." The server refuses to process a request because the request entity is larger than the server is able to process. <br>**Atomic service API**: This API can be used in atomic services since API version 11.          |
| REQ_TOO_LONG      | 414  | "Request-URI Too Long." The Request-URI is too long for the server to process. <br>**Atomic service API**: This API can be used in atomic services since API version 11.            |
| UNSUPPORTED_TYPE  | 415  | "Unsupported Media Type." The server is unable to process the media format in the request. <br>**Atomic service API**: This API can be used in atomic services since API version 11.                                  |
| RANGE_NOT_SATISFIABLE<sup>12+</sup> | 416  | "Range Not Satisfiable." The server cannot serve the requested ranges.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                 |
| INTERNAL_ERROR    | 500  | "Internal Server Error." The server encounters an unexpected error that prevents it from fulfilling the request.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                              |
| NOT_IMPLEMENTED   | 501  | "Not Implemented." The server does not support the function required to fulfill the request.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                      |
| BAD_GATEWAY       | 502  | "Bad Gateway." The server acting as a gateway or proxy receives an invalid response from the upstream server.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| UNAVAILABLE       | 503  | "Service Unavailable." The server is currently unable to process the request due to a temporary overload or system maintenance.<br>**Atomic service API**: This API can be used in atomic services since API version 11.      |
| GATEWAY_TIMEOUT   | 504  | "Gateway Timeout." The server acting as a gateway or proxy does not receive requests from the remote server within the timeout period.<br>**Atomic service API**: This API can be used in atomic services since API version 11.        |
| VERSION           | 505  | The server does not support the HTTP protocol version used in the client request.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                |

## HttpResponse

Defines the response to an HTTP request.

**System capability**: SystemCapability.Communication.NetStack

| Name  | Type                                          | Read Only| Optional|Description                   |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
| result               | string \| Object \| ArrayBuffer | No  | No  | Response content returned based on **Content-type** in the response header. If **HttpRequestOptions** does not contain the **expectDataType** field, the response content is returned according to the following rules:<br>- application/json: string in JSON format<br>- application/octet-stream: ArrayBuffer<br>- image: ArrayBuffer<br>- Others: string<br> If **HttpRequestOptions** contains the **expectDataType** field, the response content must be of the same type as the data returned by the server.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| resultType<sup>9+</sup> | [HttpDataType](#httpdatatype9)             | No  | No  | Type of the return value.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                          |
| responseCode         | [ResponseCode](#responsecode) \| number      | No  | No  | Result code for an HTTP request. If the callback function is successfully executed, a result code defined in [ResponseCode](#responsecode) will be returned. Otherwise, an error code will be returned in the **err** field in **AsyncCallback**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| header               | Object                                       | No  | No | Response header. The return value is a string in JSON format. If you want to use specific content in the response, you need to implement parsing of that content. Common fields and parsing methods are as follows:<br>- content-type: header['content-type']<br>- status-line: header['status-line']<br>- date: header.date/header['date']<br>- server: header.server/header['server']<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| cookies<sup>8+</sup> | string                                       | No  | No  | Original cookies returned by the server. How to process the cookies is up to your decision.<br>**Atomic service API**: This API can be used in atomic services since API version 11.              |
| performanceTiming<sup>11+</sup> | [PerformanceTiming](#performancetiming11) | No  | No| Time consumed in each phase of an HTTP request.|
| connectionExtraInfo<sup>24+</sup> | [ConnectionExtraInfo](#connectionextrainfo24) | No| Yes| Detailed information about the HTTP request interaction.|

## ClientCert<sup>11+</sup>

Defines the client certificate type.

**System capability**: SystemCapability.Communication.NetStack

| Name  | Type                                          | Read Only| Optional|Description                   |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
| certPath | string | No  | No| Path of the certificate file.|
| certType | [CertType](#certtype11) | No  | Yes| Certificate type. The default value is **PEM**.|
| keyPath | string | No  | No| Path of the certificate key file.|
| keyPassword | string | No  | Yes | Password of the certificate key file. The default value is an empty string.|

## PerformanceTiming<sup>11+</sup>

Defines the performance timing (unit: ms).

**System capability**: SystemCapability.Communication.NetStack

| Name  | Type                                          | Read Only| Optional|Description                   |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
| dnsTiming  | number | No  | No  | Duration from the time when the [request](#request) is sent to the time when the DNS resolution is complete.|
| tcpTiming  | number | No  | No  | Duration from the time when the [request](#request) is sent to the time when the TCP connection is complete.|
| tlsTiming  | number | No  | No  | Duration from the time when the [request](#request) is sent to the time when the TLS connection is complete.|
| firstSendTiming  | number | No  | No  | Duration from the time when the [request](#request) is sent to the time when the first byte is sent.|
| firstReceiveTiming  | number | No  | No  | Duration from the time when the [request](#request) is sent to the time when the first byte is received.|
| totalFinishTiming  | number | No  | No | Duration from the time when the [request](#request) is sent to the time when the request is complete.|
| redirectTiming  | number | No  | No | Duration from the time when the [request](#request) is sent to the time when all redirection steps are complete.|
| responseHeaderTiming  | number | No  | No  | Duration from the time when the [request](#request) is sent to the time when the header resolution is complete.|
| responseBodyTiming  | number | No  | No  | Duration from the time when the [request](#request) is sent to the time when the body resolution is complete.|
| totalTiming  | number | No  | No  | Duration from the time when the [request](#request) is sent to the time when a callback is returned to the application.|

## ConnectionExtraInfo<sup>24+</sup>

Defines the detailed information about the HTTP request interaction.

**System capability**: SystemCapability.Communication.NetStack

**Model constraint**: This API can be used only in the stage model.

| Name               | Type                         | Read Only| Optional| Description                                                        |
| ------------------- | ----------------------------- | ---- | ---- | ------------------------------------------------------------ |
| networkProtocolName | string                        | No  | No  | HTTP version used in the [request](#request), for example, 'HTTP/1.0', 'HTTP/1.1', 'HTTP/2', 'HTTP/2 over TLS', 'HTTP/3', or 'Unknown/Non-HTTP'.|
| tlsVersion          | [TlsVersion](#tlsversion18)   | No  | Yes  | TLS version used in the request. It is returned only when the TLS protocol is used.|
| cipherSuite         | [CipherSuite](#ciphersuite18) | No  | Yes  | Cipher suite used in the request. It is returned only when the TLS protocol is used.|
| localAddress        | string                        | No  | No  | IP address of the client in the request process.                           |
| remoteAddress       | string                        | No  | No  | IP address of the server in the request process.                           |
| localPort           | number                        | No  | No  | Port number of the client in the request process. The value ranges from 1 to 65535.          |
| remotePort          | number                        | No  | No  | Port number of the server in the request process. The value ranges from 1 to 65535.          |
| isReusedConnection  | boolean                       | No  | No  | Whether to reuse the connection in the request process. **true**: yes; **false**: no.|
| isProxyConnection   | boolean                       | No  | No  | Whether to use a proxy in the request process. **true**: yes; **false**: no.|
| isCacheHit          | boolean                       | No  | No  | Whether the local cache is hit in the request process. **true**: yes; **false**: no.|
| redirectCount       | number                        | No  | No  | Number of redirections in the request process.                             |

## DataReceiveProgressInfo<sup>11+</sup>

Defines the data receiving progress information.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

| Name  | Type                                          | Read Only| Optional|Description                   |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
|  receiveSize        | number | No  | No  | Amount of data received, in bytes.   |
| totalSize| number | No  | No | Total amount of data to be received, in bytes. |

## DataSendProgressInfo<sup>11+</sup>

Defines the data sending progress information.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetStack

### Attributes

| Name  | Type                                          | Read Only| Optional|Description                   |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
| sendSize        | number | No   | No  | Amount of data sent each time, in bytes.  |
| totalSize | number | No   | No | Total amount of data to be sent, in bytes. |

## MultiFormData<sup>11+</sup>

Defines the type of multi-form data.

**System capability**: SystemCapability.Communication.NetStack

| Name  | Type                                          | Read Only| Optional|Description                   |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
| name        | string | No| No| Data name.                                                                     |
| contentType | string | No| No| Data type, for example, **text/plain**, **image/png**, **image/jpeg**, **audio/mpeg**, or **video/mp4**.|
| remoteFileName | string | No| Yes| Name of the file uploaded to the server.<br>**Note**: If this field is specified, the **filename** field is added to the request header, indicating the name of the file uploaded to the server.<br>(1) If the data to be uploaded is a file and the file content is specified via the **data** field, the **remoteFileName** field usually needs to be set to specify the name of the file to be uploaded to the server (the actual result depends on the server). If the file path is specified via the **filePath** field, the **filename** field will be automatically added to the request header. Its default value is the file name in the **filePath** field. If a different name is required, it can also be changed via this field.<br>(2) When the data to be uploaded is in binary format, the **remoteFileName** field must be set.                                                |
| data | string \| Object \| ArrayBuffer | No| Yes| Form data content.                                              |
| filePath | string | No| Yes| File path of the form data. If **data** is not specified, **filePath** must be set.<br>**Note**: The file format supported by the file management module must be passed. You can call [access](../apis-core-file-kit/js-apis-file-fs.md#fileioaccess) to check whether the file exists and is accessible.|

## http.createHttpResponseCache<sup>9+</sup>

createHttpResponseCache(cacheSize?: number): HttpResponseCache

Creates an **HttpResponseCache** object that stores the response data of HTTP requests. You can call [flush](#flush9) and [delete](#delete9) in the object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                                   | Mandatory| Description      |
| -------- | --------------------------------------- | ---- | ---------- |
| cacheSize | number | No | Response cache size, in bytes. The value range is from **1\*1024\*1024** to **10\*1024\*1024**, that is, from 1 MB to 10 MB. The default value is 10 MB. If the value exceeds 10 MB, it is set to 10 MB; if the value is less than 1 MB, it is set to 1 MB. |

**Return value**

| Type       | Description                                                        |
| :---------- | :----------------------------------------------------------- |
| [HttpResponseCache](#httpresponsecache9) | Object that stores the response to the HTTP request.|

**Example**

```ts
import { http } from '@kit.NetworkKit';

let httpResponseCache = http.createHttpResponseCache();
```

## HttpResponseCache<sup>9+</sup>

Defines an object that stores the response to an HTTP request. Before invoking APIs provided by **HttpResponseCache**, you must call [createHttpResponseCache()](#httpcreatehttpresponsecache9) to create an **HttpRequestTask** object.

**Usage of Keywords in the Response Header**

- **`Cache-Control`**: specifies the cache policy, for example, `no-cache`, `no-store`, `max-age`, `public`, or `private`.

- **`Expires`**: specifies the expiration time of a resource. The value is in the GMT format.

- **`ETag`**: identifies the resource version. The client can use the `If-None-Match` request header to check whether the resource has been modified.

- **`Last-Modified`**: specifies the last modification time of a resource. The client can use the `If-Modified-Since` request header to check whether a resource has been modified.

- **`Vary`**: specifies the parts of the request header that affect the cached response. This field is used to distinguish different cache versions.

When using these keywords, ensure that the response header is correctly configured on the server. The client determines whether to use the cached resource and how to verify whether the resource is the latest based on the response header. Correct cache policies help to improve application performance and user experience.

**How to Set the Cache-Control Header**

`Cache-Control` is a common header, but it is usually used on the server. It allows you to define when, how, and how long a response should be cached. The following are some common `Cache-Control` directives:

- **`no-cache`**: indicates that the response can be stored in the cache, but it must be verified with the origin server before each reuse. If the resource remains unchanged, the response status code is 304 (Not Modified). In this case, the resource content is not sent, and the resource in the cache is used. If the resource has expired, the response status code is 200 and the resource content is sent.

- `no-store`: indicates that resources cannot be cached. Resources must be obtained from the server for each request.

- `max-age`: specifies the maximum cache duration, in seconds. For example, `Cache-Control: max-age=3600` indicates that the valid cache duration is 3,600 seconds (that is, 1 hour).

- `public`: indicates that the response can be cached by any object, for example, the client that sends the request or the proxy server.

- `private`: indicates that the response can be cached only by a single user and cannot be used as a shared cache (that is, the response cannot be cached by the proxy server).

- `must-revalidate`: indicates that a resource must be revalidated with the origin server once it has become stable.

- **`no-transform`**: indicates that the proxy server is not allowed to modify the response content.

- **`proxy-revalidate`**: works in a way similar to `must-revalidate`, but applies only to shared caches.

- **`s-maxage`**: works in a way similar to `max-age`, but applies only to shared caches.

### flush<sup>9+</sup>

flush(callback: AsyncCallback\<void\>): void

Flushes data in the cache to the file system so that the cached data can be accessed in the next HTTP request. This API uses an asynchronous callback to return the result. Cached data includes the response header (header), response body (result), cookies, request time (requestTime), and response time (responseTime).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                                   | Mandatory| Description      |
| -------- | --------------------------------------- | ---- | ---------- |
| callback | AsyncCallback\<void\> | Yes  | Callback used to return the result.  If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Example**

```ts
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpResponseCache = http.createHttpResponseCache();
let httpRequest = http.createHttp();
httpRequest.request("EXAMPLE_URL", (err: BusinessError, data: http.HttpResponse) => {
  if (!err) {
    httpResponseCache.flush((err: BusinessError) => {
      if (err) {
        console.error('flush fail');
      }
      console.info('flush success');
    });
    httpRequest.destroy();
  } else {
    console.error('error:' + JSON.stringify(err));
    // Call destroy() to release resources when the request is no longer needed, preventing memory leaks.
    httpRequest.destroy();
  }
});
```

### flush<sup>9+</sup>

flush(): Promise\<void\>

Flushes data in the cache to the file system so that the cached data can be accessed in the next HTTP request. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Return value**

| Type                             | Description                                 |
| --------------------------------- | ------------------------------------- |
| Promise\<void\> | Promise that returns no value.|

**Example**

```ts
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpRequest = http.createHttp();
let httpResponseCache = http.createHttpResponseCache();
let promise = httpRequest.request("EXAMPLE_URL");

promise.then((data: http.HttpResponse) => {
  httpResponseCache.flush().then(() => {
    console.error('flush success');
  }).catch((err: BusinessError) => {
    console.error('flush fail');
  });
}).catch((err: Error) => {
  console.error('error:' + JSON.stringify(err));
});
```

### delete<sup>9+</sup>

delete(callback: AsyncCallback\<void\>): void

Disables the cache and deletes the data in it. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type                                   | Mandatory| Description      |
| -------- | --------------------------------------- | ---- | ---------- |
| callback | AsyncCallback\<void\> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

```ts
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpRequest = http.createHttp();
httpRequest.request("EXAMPLE_URL").then(data => {
  const httpResponseCache = http.createHttpResponseCache();
  httpResponseCache.delete((err: BusinessError) => {
    try {
      if (err) {
        console.error('fail: ' + err);
      } else {
        console.info('success');
      }
    } catch (err) {
      console.error('error: ' + err);
    }
  });
  httpRequest.destroy();
}).catch((error: BusinessError) => {
  console.error("errcode" + JSON.stringify(error));
});
```

### delete<sup>9+</sup>

delete(): Promise\<void\>

Disables the cache and deletes the data in it. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

**Return value**

| Type                             | Description                                 |
| --------------------------------- | ------------------------------------- |
| Promise\<void\> | Promise that returns no value.|

**Example**

```ts
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpRequest = http.createHttp();
httpRequest.request("EXAMPLE_URL").then(data => {
  const httpResponseCache = http.createHttpResponseCache();
  httpResponseCache.delete().then(() => {
    console.info("success");
  }).catch((err: BusinessError) => {
    console.error("fail");
  });
  httpRequest.destroy();
}).catch((error: BusinessError) => {
  console.error("errcode" + JSON.stringify(error));
});
```

## HttpDataType<sup>9+</sup>

Enumerates HTTP data types.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

| Name| Value| Description    |
| ------------------  | -- | ----------- |
| STRING              | 0 | String type.|
| OBJECT              | 1 | Object type.   |
| ARRAY_BUFFER        | 2 | Binary array type.|

## HttpProtocol<sup>9+</sup>

Enumerates HTTP protocol versions.

**System capability**: SystemCapability.Communication.NetStack

| Name |   Value  | Description                                                                  |
| :-------- | :----------- |:---------------------------------------------------------------------|
| HTTP1_1   |   0   | HTTP1.1.<br>**Atomic service API**: This API can be used in atomic services since API version 11.      |
| HTTP2     |   1   | HTTP2.<br>**Atomic service API**: This API can be used in atomic services since API version 11.         |
| HTTP3<sup>11+</sup> |  2  | HTTP3. If the system or server does not support HTTP3, the HTTP protocol of an earlier version is used.<br>**Note**: This parameter takes effect only for HTTPS URLs. If this parameter is set to HTTP, the request will fail.|

## CertType<sup>11+</sup>

Enumerates certificate types.

**System capability**: SystemCapability.Communication.NetStack

| Name|   Value  | Description      |
| --- | ------ | ---------- |
| PEM | PEM | PEM certificate.|
| DER | DER | DER certificate.|
| P12 | P12 | P12 certificate.|

## CertificatePinning<sup>12+</sup>

Defines the dynamic configuration of certificate pinning.

**System capability**: SystemCapability.Communication.NetStack

| Name  | Type                                          | Read Only| Optional|Description                   |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
| publicKeyHash       | string | No  | No|Certificate PIN of the string type.|
| hashAlgorithm        | 'SHA-256' |  No  | No |Encryption algorithm. Currently, only SHA-256 is supported.|

## HttpProxy<sup>10+</sup>

type HttpProxy = connection.HttpProxy

Defines the network proxy configuration.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

|       Type      |            Description            |
| ---------------- | --------------------------- |
| connection.HttpProxy | Network proxy configuration.    |

## Socks5Proxy

type Socks5Proxy = connection.Socks5Proxy

Defines the SOCKS5 proxy configuration information.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Communication.NetStack

|       Type      |            Description            |
| ---------------- | --------------------------- |
| [connection.Socks5Proxy](js-apis-net-connection.md#socks5proxy) | SOCKS5 proxy configuration information.     |

## QueryParamValue

type QueryParamValue = string \| number \| boolean \| null \| undefined

Defines the single-value type that can be used in **QueryParamObject**.

**Since**: 26.0.0

**System capability**: SystemCapability.Communication.NetStack

**Model restriction:** This API can be used only in the stage model.

| Type| Description|
| ---------------- | --------------------------- |
| string | String type. |
| number | Number type. It will be converted to a string before encoding. |
| boolean | Boolean type. It will be converted to a string before encoding. |
| null | Null type. It will be serialized with only the key and no `=` value. |
| undefined | Undefined type. It will be serialized with only the key and no `=` value. |

## QueryParamObject

type QueryParamObject = Record\<string, QueryParamValue \| QueryParamValue[]\>

Defines the key-value object type used to construct URL query parameters.

**Since**: 26.0.0

**System capability**: SystemCapability.Communication.NetStack

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| ---------------- | --------------------------- |
| Record\<string, [QueryParamValue](#queryparamvalue) \| [QueryParamValue](#queryparamvalue)[]\> | Key-value object type used to construct URL query parameters. Each property name serves as the key of a URL parameter, and the property value serves as the parameter value.<br>**NOTE**<br>(1) Each property name of the object serves as the key of a URL parameter, and the property value serves as the parameter value. For example, `{ scene: 'demo', page: 1 }` is serialized to `scene=demo&page=1`.<br>(2) When the property value is an array, it is expanded into multiple parameters with the same name. For example, `{ tag: ['a', 'b'] }` is serialized to `tag=a&tag=b`.<br>(3) Keys and values are automatically URL-encoded by the system. You should pass in the original unencoded content.<br>(4) To strictly control the parameter order or the order of duplicate keys, you are advised to use the string form of **queryParams** directly. |

## AddressFamily<sup>15+</sup>

Enumerates IP address families of the target domain name.

**System capability**: SystemCapability.Communication.NetStack

|       Name      |     Value    |            Description            |
| ---------------- | --------------- | --------------------------- |
| DEFAULT | CURL_IPRESOLVE_WHATEVER | Automatically selects the IPv4 or IPv6 address of the target domain name.    |
| ONLY_V4 | CURL_IPRESOLVE_V4 | Resolves only the IPv4 address of the target domain name and ignores the IPv6 address.    |
| ONLY_V6 | CURL_IPRESOLVE_V6 | Resolves only the IPv6 address of the target domain name and ignores the IPv4 address.    |

## Credential<sup>18+</sup>

Represents the credential used for server identity verification in a session, including the user name and password.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|  Name |  Type |  Read Only | Optional |Description    |
| ------------------  |---- |-- | -- |----------- |
| username       | string | No|No|User name used for verification. The default value is **''**.|
| password        | string |  No |No|Password used for verification. The default value is **''**.|

## ServerAuthentication<sup>18+</sup>

Defines HTTP server identity verification information.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|  Name              |  Type                                           | Read Only   |    Optional    |Description    |
| ------------------  |-------------------------------------------------|-------- |------------ |---------------|
| credential          | [Credential](#credential18)                     | No     | No        |Server credential. The default value is **undefined**.    |
| authenticationType  | [AuthenticationType](#authenticationtype18)     | No     | Yes       | Server identity verification type. If the type is not set, negotiation with the server is required.    |

## TlsConfig<sup>18+</sup>

Defines the TLS configuration, including the version and cipher suite.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|  Name              |  Type                           | Read Only   |    Optional    |Description    |
| ------------------  |---------------------------------|-------- |-------- |---------------|
| tlsVersionMin       | [TlsVersion](#tlsversion18)     | No     |No      | Earliest TLS version.    |
| tlsVersionMax        | [TlsVersion](#tlsversion18)    | No     |No      | Latest TLS version.    |
| cipherSuites        | [CipherSuite](#ciphersuite18)[] | No     |Yes      | Array of cipher suite types. If no cipher suite type is set, all supported cipher suite types are carried by default. For details about the cipher suite types, see [TlsV13SpecificCipherSuite](#tlsv13specificciphersuite18), [TlsV12SpecificCipherSuite](#tlsv12specificciphersuite18) and [TlsV10SpecificCipherSuite](#tlsv10specificciphersuite18).|

## TlsVersion<sup>18+</sup>

Enumerates TLS versions.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

| Name       | Value| Description        |
|:----------|:--|:-----------|
| TLS_V_1_0 | 4 | TLS version 1.0.|
| TLS_V_1_1 | 5 | TLS version 1.1.|
| TLS_V_1_2 | 6 | TLS version 1.2.|
| TLS_V_1_3 | 7 | TLS version 1.3.|

## TlsOptions<sup>18+</sup>

type TlsOptions = 'system' | TlsConfig

Defines the TLS configuration.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

| Type                        | Description                                                                                |
|-------------------------------|------------------------------------------------------------------------------------|
| 'system'  | TLS version of the system. This field is defaulted to **system** when the value is not set.|
| TlsConfig | Custom TLS version and cipher suites.|

## RemoteValidation<sup>18+</sup>

type RemoteValidation = 'system' | 'skip'

Enumerates the identity verification modes of the remote server.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

| Type                        | Description                                                                                |
|-------------------------------|------------------------------------------------------------------------------------|
| 'system'  | Use of the system CA. This field is defaulted to **system** when the value is not set.|
| 'skip'   | Skipping of CA verification. This field has a fixed value of **skip**.|

## AuthenticationType<sup>18+</sup>

type AuthenticationType = 'basic' | 'ntlm' | 'digest'

Enumerates server authentication modes in a session.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|Type                         | Description                                                                                                |
|-------------------------------|----------------------------------------------------------------------------------------------------|
| 'basic'  | Basic authentication mode. This field has a fixed value of **basic**.|
| 'ntlm'   | NTLM authentication mode. This field has a fixed value of **ntlm**.|
| 'digest' | Digest authentication mode. This field has a fixed value of **digest**.|

## CipherSuite<sup>18+</sup>

type CipherSuite = TlsV13CipherSuite

Declares the cipher suite.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|       Type      | Description                                                               |
| ---------------- |-------------------------------------------------------------------|
| TlsV13CipherSuite | Cipher suite defined in [TlsV13CipherSuite](#tlsv13ciphersuite18).                |

## TlsV13CipherSuite<sup>18+</sup>

type TlsV13CipherSuite = TlsV12CipherSuite | TlsV13SpecificCipherSuite

Declares the cipher suite for TLS 1.3, which is also compatible with TLS 1.2.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|       Type      | Description                                                               |
| ---------------- |-------------------------------------------------------------------|
| TlsV12CipherSuite | [TlsV11CipherSuite](#tlsv11ciphersuite18).                |
| TlsV13SpecificCipherSuite | [TlsV13SpecificCipherSuite](#tlsv13specificciphersuite18).|

## TlsV12CipherSuite<sup>18+</sup>

type TlsV12CipherSuite = TlsV11CipherSuite | TlsV12SpecificCipherSuite

Declares the cipher suite for TLS 1.2, which is also compatible with TLS 1.1.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|       Type      | Description                                                               |
| ---------------- |-------------------------------------------------------------------|
| TlsV11CipherSuite | [TlsV11CipherSuite](#tlsv11ciphersuite18).                |
| TlsV12SpecificCipherSuite | [TlsV12SpecificCipherSuite](#tlsv12specificciphersuite18).|

## TlsV11CipherSuite<sup>18+</sup>

type TlsV11CipherSuite = TlsV10CipherSuite

Declares the cipher suite for TLS 1.1, which is the same as that for TLS1.0.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|       Type      | Description                                               |
| ---------------- |---------------------------------------------------|
| TlsV10CipherSuite | [TlsV10CipherSuite](#tlsv10ciphersuite18).|

## TlsV10CipherSuite<sup>18+</sup>

type TlsV10CipherSuite = TlsV10SpecificCipherSuite

Declares the cipher suite for TLS 1.0.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|       Type      | Description                                                               |
| ---------------- |-------------------------------------------------------------------|
| TlsV10SpecificCipherSuite | [TlsV10SpecificCipherSuite](#tlsv10specificciphersuite18).|

## TlsV13SpecificCipherSuite<sup>18+</sup>

type TlsV13SpecificCipherSuite = 'TLS_AES_128_GCM_SHA256' | 'TLS_AES_256_GCM_SHA384' | 'TLS_CHACHA20_POLY1305_SHA256'

Enumerates cipher suites supported by TLS 1.3 or later.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|       Type      | Description  |
| ---------------- |------|
| 'TLS_AES_128_GCM_SHA256' | Supported cipher suite: TLS_AES_128_GCM_SHA256. The value is a string.|
| 'TLS_AES_256_GCM_SHA384' | Supported cipher suite: TLS_AES_256_GCM_SHA384. The value is a string.|
| 'TLS_CHACHA20_POLY1305_SHA256' | Supported cipher suite: TLS_CHACHA20_POLY1305_SHA256. The value is a string.|

## TlsV12SpecificCipherSuite<sup>18+</sup>

type TlsV12SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256' | 'TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256' |
'TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384' | 'TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384' |
'TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256' | 'TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256' |
'TLS_RSA_WITH_AES_128_GCM_SHA256' | 'TLS_RSA_WITH_AES_256_GCM_SHA384'

Enumerates cipher suites supported by TLS 1.2 or later.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|       Type      | Description  |
| ---------------- |------|
| 'TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256' | Supported cipher suite: TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256. The value is a string.|
| 'TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256' | Supported cipher suite: TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256. The value is a string.|
| 'TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384' | Supported cipher suite: TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384. The value is a string.|
| 'TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384' | Supported cipher suite: TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384. The value is a string.|
| 'TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256' | Supported cipher suite: TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256. The value is a string.|
| 'TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256' | Supported cipher suite: TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256. The value is a string.|
| 'TLS_RSA_WITH_AES_128_GCM_SHA256' | Supported cipher suite: TLS_RSA_WITH_AES_128_GCM_SHA256. The value is a string.|
| 'TLS_RSA_WITH_AES_256_GCM_SHA384' | Supported cipher suite: TLS_RSA_WITH_AES_256_GCM_SHA384. The value is a string.|

## TlsV10SpecificCipherSuite<sup>18+</sup>

type TlsV10SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA' | 'TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA' |
'TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA' | 'TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA' | 'TLS_RSA_WITH_AES_128_CBC_SHA' |
'TLS_RSA_WITH_AES_256_CBC_SHA' | 'TLS_RSA_WITH_3DES_EDE_CBC_SHA'

Enumerates cipher suites supported by TLS 1.0 or later.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Communication.NetStack

|       Type      | Description  |
| ---------------- |------|
| 'TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA' | Supported cipher suite: TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA. The value is a string.|
| 'TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA' | Supported cipher suite: TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA. The value is a string.|
| 'TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA' | Supported cipher suite: TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA. The value is a string.|
| 'TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA' | Supported cipher suite: TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA. The value is a string.|
| 'TLS_RSA_WITH_AES_128_CBC_SHA' | Supported cipher suite: TLS_RSA_WITH_AES_128_CBC_SHA. The value is a string.|
| 'TLS_RSA_WITH_AES_256_CBC_SHA' | Supported cipher suite: TLS_RSA_WITH_AES_256_CBC_SHA. The value is a string.|
| 'TLS_RSA_WITH_3DES_EDE_CBC_SHA' | Supported cipher suite: TLS_RSA_WITH_3DES_EDE_CBC_SHA. The value is a string.|

## SslType<sup>20+</sup>

type SslType = 'TLS' | 'TLCP'

Defines the secure communications protocol.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Communication.NetStack

| Type  | Description                                  |
| ------ | -------------------------------------- |
| 'TLS' | TLS protocol. The value is fixed to **TLS**.  |
| 'TLCP' | TLCP protocol. The value is fixed to **TLCP**.<br>**NOTE**<br>(1) The certificate supports the following string specifications:<br> - UTF8String (English character set)<br> - PrintableString<br>  - IA5String<br>Supported since API Version 22:<br> - TeletexString<br>(2) The certificate supports the following extended specifications:<br> - BasicConstraints (OID 2.5.29.19)<br> - KeyUsage (OID2.5.29.15)<br> - SubjectKeyIdentifier (OID2.5.29.14)<br> - AuthorityKeyIdentifier (OID2.5.29.35)<br>Supported since API Version 22:<br> - SubjectAltName (OID 2.5.29.17)<br> - ExtendedKeyUsage (OID 2.5.29.37)<br>|

## InterceptorType<sup>22+</sup>

Enumerates the types of HTTP interceptors.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Communication.NetStack

| Name  | Value|Description                                  |
| ------ | --|-------------------------------------- |
| INITIAL_REQUEST |'INITIAL_REQUEST' |Intercepts after the initial HTTP request is assembled.|
| REDIRECTION | 'REDIRECTION' |Intercepts when a redirection response is received.|
| CACHE_CHECKED | 'READ_CACHE' |Intercepts when the HTTP cache is checked and hit.|
| NETWORK_CONNECT | 'CONNECT_NETWORK' |Intercepts before the network request is sent.|
| FINAL_RESPONSE | 'FINAL_RESPONSE' |Intercepts when the final HTTP response is obtained.|

## HttpRequestContext<sup>22+</sup>

Defines HTTP request context data. The object instance is passed as a parameter in the [interceptorHandle](#interceptorhandle22) method of the interceptor. You can use this object to obtain and modify the information about the HTTP request.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Communication.NetStack

### Attributes

| Name  | Type|Read Only|Optional|Description                     |
| --   | -- |-- |-- |--                      |
| url   | string |No|No|URL obtained by the HTTP interceptor from the HTTP request, which can be modified in the interceptor.|
| header   | Object |No|No|Request header obtained by the HTTP interceptor from the HTTP request, which can be modified in the interceptor.|
| body   | Object |No|No|Request body obtained by the HTTP interceptor from the HTTP request, which can be modified in the interceptor.|

## ChainContinue<sup>22+</sup>

type ChainContinue = boolean

Specifies whether to continue to process the interceptor chain.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Communication.NetStack

| Type  | Description                                   |
| ------ | -------------------------------------- |
| boolean | The value **true** indicates that the interceptor chain continues to be processed, and the value **false** indicates that the interceptor chain is terminated and an HTTP response is returned.                  |

## HttpInterceptor<sup>22+</sup>

Defines the HTTP interceptor API, which is used to define the interception processing function.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Communication.NetStack

### Attributes

| Name  | Type|Read Only|Optional|Description                     |
| --   | -- |-- |-- |--                      |
| interceptorType   | [InterceptorType](#interceptortype22)|No|No|Interceptor type, which defines when the interceptor is called.                     |

### interceptorHandle<sup>22+</sup>

interceptorHandle(reqContext: HttpRequestContext, rspContext: HttpResponse): Promise\<ChainContinue\>

Intercepts the HTTP processing and modifies it as required.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type| Mandatory|Description                     |
| --   | -- | -- | --                      |
| reqContext   | [HttpRequestContext](#httprequestcontext22) |Yes|Context of the request parameters passed through the HTTP interceptor.                     |
| rspContext   | [HttpResponse](#httpresponse) |Yes|Context of the return result passed through the HTTP interceptor.                     |

**Return value**

| Type  | Description                                  |
| ------ | -------------------------------------- |
| Promise\<[ChainContinue](#chaincontinue22)\> | Continues the HTTP processing or stops and returns an HTTP response.  |

**Example**

```ts
import { http } from '@kit.NetworkKit';

// Create a custom interceptor.
class CustomInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.INITIAL_REQUEST;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Add the authentication header in the initial request phase.
    reqContext.header['Authorization'] = 'Bearer token';
    console.info('Interceptor: Added authorization header');
    return true; // Continue to process the interceptor chain.
  }
}

let customInterceptor = new CustomInterceptor();
```

## HttpInterceptorChain<sup>22+</sup>

Defines HTTP interceptor chain.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Communication.NetStack

**Example**

```ts
import { http } from '@kit.NetworkKit';

let interceptorChain = new http.HttpInterceptorChain();
```

### addChain<sup>22+</sup>

addChain(chain: HttpInterceptor[]): boolean

Adds an interceptor to the HTTP client.

> **NOTE**
>
> An interceptor chain cannot contain interceptor instances of the same type. If interceptors of the same type are passed in, the error code **2300802** (Duplicated interceptor type in the chain) is reported.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type  |Mandatory  |Description  |
| ------ | ------ | ------ | ------ |
| chain | [HttpInterceptor](#httpinterceptor22)[] | Yes| Interception chain composed of interceptor instances. A single interceptor or multiple interceptors of different types can be passed in.|

**Return value**

| Type  | Description                                  |
| ------ | -------------------------------------- |
| boolean | Whether the interceptor is added successfully. The value **true** indicates that the interceptor is successfully added, and the value **false** indicates the opposite.                  |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [HTTP Error Codes](errorcode-net-http.md).<br>
The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

| ID   | Error Message                                              |
| ------      | --------------------------------------                |
| 2300801 | Parameter type not supported by the interceptor.          |
| 2300802 | Duplicated interceptor type in the chain.                 |
| 2300999 | Internal error.                                           |

**Example**

```ts
import { http } from '@kit.NetworkKit';

// Create an authentication interceptor.
class AuthInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.INITIAL_REQUEST;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Add the authentication header in the initial request phase.
    reqContext.header['Authorization'] = 'Bearer token';
    console.info('Interceptor: Added authorization header');
    return true; // Continue to process the interceptor chain.
  }
}

class LoggingInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.FINAL_RESPONSE;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Record logs in the final response phase.
    console.info(`LoggingInterceptor: Request to ${reqContext.url} completed with status ${rspContext.responseCode}`);
    return true; // Continue to process the interceptor chain.
  }
}

// Create an interceptor chain and apply the interceptor chain to the request.
let interceptorChain = new http.HttpInterceptorChain();
let authInterceptor = new AuthInterceptor();
let loggingInterceptor = new LoggingInterceptor();

// Add the interceptor to the chain.
try {
  let success = interceptorChain.addChain([authInterceptor, loggingInterceptor]);
  if (!success) {
    console.error('Failed to add interceptor chain');
  }
} catch (e) {
  console.error(`Interceptor chain add failed: code=${e.code}, message=${e.message}`);
}
```

### getChain<sup>22+</sup>

getChain(): HttpInterceptor[]

Obtains all interceptor instances in the current interceptor chain.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Communication.NetStack

**Return value**

| Type  | Description                                    |
| ------ | --------------------------------------   |
| [HttpInterceptor](#httpinterceptor22)[] | Returns all interceptor instances added by the [addChain](#addchain22) method.            |

**Example**

```ts
import { http } from '@kit.NetworkKit';

// Create a custom interceptor.
class CustomInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.INITIAL_REQUEST;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Add the authentication header in the initial request phase.
    reqContext.header['Authorization'] = 'Bearer token';
    console.info('Interceptor: Added authorization header');
    return true; // Continue to process the interceptor chain.
  }
}

// Create an interceptor chain and apply the interceptor chain to the request.
let interceptorChain = new http.HttpInterceptorChain();
let customInterceptor = new CustomInterceptor();

// Add the interceptor to the chain.
try {
  let success = interceptorChain.addChain([customInterceptor]);
  if (!success) {
    console.error('Failed to add interceptor chain');
  }
} catch (e) {
  console.error(`Interceptor chain add failed: code=${e.code}, message=${e.message}`);
}

// Obtain all interceptors in the current interceptor chain.
let chain = interceptorChain.getChain();
console.info(`Current interceptor chain has ${chain.length} interceptors`);
```

### apply<sup>22+</sup>

apply(httpRequest: HttpRequest): boolean

Adds an interceptor chain to the target HTTP request. Each HTTP request instance can have only one interceptor chain attached.

> **NOTE**
>
> After an interceptor chain is attached to an [HttpRequest](#httprequest) instance, when the instance initiates an HTTP request, interceptors of the corresponding type in the attached interceptor chain are triggered.<br>
> For more information about how to trigger interceptors using HTTP requests, see [HTTP Interceptor Function Code Example](../../network/http-request.md#http-interceptor).<br>
> The HTTP interceptor feature is supported only by [HttpRequest.request](#request) APIs, and is not supported by [HttpRequest.requestInStream](#requestinstream10) APIs (streaming transmission).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Communication.NetStack

**Parameters**

| Name  | Type  |Mandatory  |Description  |
| ------ | ------ | ------ | ------ |
| httpRequest | [HttpRequest](#httprequest) | Yes| [HttpRequest](#httprequest) that initiates an HTTP request.|

**Return value**

| Type  | Description                                  |
| ------ | -------------------------------------- |
| boolean | Whether the interceptor is attached successfully. The value **true** indicates that the interceptor is successfully added, and the value **false** indicates the opposite.                  |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [HTTP Error Codes](errorcode-net-http.md).<br>
The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

| ID   | Error Message                                              |
| ------      | --------------------------------------                |
| 2300801 | Parameter type not supported by the interceptor.          |
| 2300999 | Internal error.                                           |

**Example**

```ts
import { http } from '@kit.NetworkKit';

// Create an authentication interceptor.
class AuthInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.INITIAL_REQUEST;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Add the authentication header in the initial request phase.
    reqContext.header['Authorization'] = 'Bearer token';
    console.info('Interceptor: Added authorization header');
    return true; // Continue to process the interceptor chain.
  }
}

class LoggingInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.FINAL_RESPONSE;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Record logs in the final response phase.
    console.info(`LoggingInterceptor: Request to ${reqContext.url} completed with status ${rspContext.responseCode}`);
    return true; // Continue to process the interceptor chain.
  }
}

// Create an interceptor chain.
let interceptorChain = new http.HttpInterceptorChain();
let authInterceptor = new AuthInterceptor();
let loggingInterceptor = new LoggingInterceptor();

// Create an HTTP request.
let httpRequest = http.createHttp();

try {
  // Add the interceptor to the chain.
  let success = interceptorChain.addChain([authInterceptor, loggingInterceptor]);
  if (!success) {
    console.error('Failed to add interceptor chain');
  }

  // Apply the interceptor chain to the HTTP request.
  let applySuccess = interceptorChain.apply(httpRequest);
  if (!applySuccess) {
    console.error('Failed to apply interceptor chain');
  }
} catch (e) {
  console.error(`Interceptor chain add failed: code=${e.code}, message=${e.message}`);
}

// Initiate an HTTP request. If interception is required, the request can be initiated only through the request API.
httpRequest.request("EXAMPLE_URL", {
  method: http.RequestMethod.GET,
  header: { 'Content-Type': 'application/json' }
}, (err: Error, data: http.HttpResponse) => {
  if (!err) {
    console.info('Request completed with response code: ' + data.responseCode);
  } else {
    console.error('Request failed: ' + JSON.stringify(err));
  }
  httpRequest.destroy();
});
```

## PathPreference<sup>23+</sup>

type PathPreference = 'auto' | 'primaryCellular' | 'secondaryCellular'

Enumerates the types of networks specified in an HTTP request.

> **NOTE**
>
> It is recommended that this parameter be used in scenarios such as network concurrency.<br>
> If the specified network is not activated, the system uses the default network.

**System capability**: SystemCapability.Communication.NetStack

| Type  | Description                                  |
| ------ | -------------------------------------- |
| 'auto' |Specifies the default network connection in an HTTP request.|
| 'primaryCellular' |Specifies the default cellular network connection in an HTTP request when the cellular network is activated.|
| 'secondaryCellular' |Specifies the cellular network connection of the secondary SIM card in an HTTP request when dual cellular networks are activated.|