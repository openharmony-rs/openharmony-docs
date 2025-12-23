# Using HTTP for Network Access
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->

## When to Use

An application can initiate a data request over HTTP. Common HTTP methods include **GET**, **POST**, **OPTIONS**, **HEAD**, **PUT**, **DELETE**, **TRACE**, and **CONNECT**. Currently, two HTTP request methods are provided. If the amount of data sent or received by the request is small, you can use [HttpRequest.request](../reference/apis-network-kit/js-apis-http.md#request). If you are uploading or downloading a large file and care about the data sending and receiving progress, you can use [HttpRequest.requestInstream](../reference/apis-network-kit/js-apis-http.md#requestinstream10). From API version 22, if you need to insert custom logic at key nodes in the "HTTP request-response" lifecycle, you can use the [HTTP Interceptor](#http-interceptor).

<!--RP1-->

<!--RP1End-->

The following table lists the functions supported by the HTTP request. The options corresponding to these functions can be set in [HttpRequestOptions](../reference/apis-network-kit/js-apis-http.md#httprequestoptions) of the HTTP request.

| Category    | Function                          |Feature Description                     | Available Since        |
| ----------- | -----------------------------------|-----------------------------|------------------------|
| Basic    | Setting the request method                     | Specifies the request method, including **GET**, **POST**, **HEAD**, **PUT**, **DELETE**, **TRACE**, **CONNECT**, and **OPTIONS**. The default value is **GET**. |  API version 6  |
| Basic    | Setting additional data of the request                | Specifies additional data can be carried with the request. This parameter is not used by default.| API version 6    |
| Basic    | Setting the read timeout interval                | Specifies the total time from the start to the end of a request, including DNS resolution, connection setup, and transmission. The default value is **60000**, in ms.|  API version 6   |
| Basic    | Setting the connection timeout interval                | Specifies the connection timeout interval. The default value is **60000**, in ms.|  API version 6   |
| Basic    | Setting the HTTP request header                 | Specifies the HTTP request header. If the request method is **POST**, **PUT**, **DELETE**, or left empty, the default value is {'content-Type': 'application/json'}. Otherwise, the default value is {'content-Type': 'application/x-www-form-urlencoded'}.|  API version 6   |
| Basic    | Setting the response data type               | Specifies the type of the HTTP response data. This parameter is not used by default. If this parameter is set, the system returns the specified type of data preferentially.|  API version 9   |
| Basic    | Setting the priority of concurrent requests             |  Specifies the priority of concurrent HTTP/HTTPS requests. A larger value indicates a higher priority. The value ranges from 1 to 1000. The default value is **1**.|  API version 9   |
| Basic    | Enabling the cache               | Specifies whether to use the cache. The default value is **true**. The data in the cache is preferentially read. The cache takes effect with the current process. The new cache replaces the old cache. If this parameter is set to **false**, the cache is not used.|  API version 9   |
| Basic    | Setting the protocol type                | Specifies the protocol type. The default value is automatically assigned by the system. You can set it to **HTTP 1.1**, **HTTP 2**, or **HTTP 3**.|  API version 9   |
| Proxy setting    | Setting the HTTP request proxy                | Specifies whether to use the HTTP proxy. The default value is **false**, indicating that proxy is not used. If this parameter is set to **true**, the default proxy of the system is used. You can also configure a custom network proxy through **HttpProxy**.|  API version 10  |
| Certificate verification    | Setting the CA certificate path                  | Specifies the CA certificate path. If the CA certificate path is set, the system uses the CA certificate in the specified path. Otherwise, the system uses the preset CA certificate.| API version 10    |
| Certificate verification    | Setting the transmission of client certificates           | Specifies whether to enable the transmission of client certificates, which include the certificate path, certificate type, certificate key path, and password information.| API version 11    |
| Basic    | Setting the start and end positions of the download        | Specifies the data range to retrieve, which is commonly used in file download scenarios.|  API version 11  |
| Basic    | Setting the list of data fields to be uploaded       |Specifies the multipart form data, which is commonly used in file upload scenarios.|  API version 11   |
| DNS setting     | HTTPS server for DNS resolution. | Specifies whether to use an HTTPS server for DNS resolution. The value must be URL-encoded in the following format: 'https://host:port/path'.| API version 11    |
| DNS setting    | Specifies whether to use the specified DNS server for DNS resolution.<br>        | Specifies whether to use the specified DNS server for DNS resolution.<br> - You can set a maximum of three DNS servers. If there are more than three DNS servers, only the first three DNS servers are used.<br> The DNS servers must be expressed as IPv4 or IPv6 addresses.|  API version 11   |
| Basic    | Setting the maximum number of bytes in a response message           | Specifies the maximum number of bytes in a response message. The unit is byte. The default value is 5 x 1024 x 1024, and the maximum value is 100 x 1024 x 1024.|   API version 11  |
| Certificate verification    | Setting the certificate pinning configuration            | Specifies the certificate pinning configuration. One or more certificate PINs can be specified.|   API version 12  |
| Certificate verification    | Setting the IP address family       | Specifies the IP address family for resolving the target domain name. The address type can be set to follow the system network configuration, forcibly use only IPv4 addresses for resolution, or forcibly use only IPv6 addresses for resolution.|  API version 15   |
| Certificate verification    | Setting whether to skip SSL certificate verification                    | Specifies whether to skip SSL certificate verification.| API version 18    |
| Certificate verification    | Setting the certificate verification version and cipher suite            | Customizes the certificate verification version and cipher suite.|  API version 18  |
| Certificate verification    | Setting server authentication for secure connections       | Specifies server authentication for secure connections.|  API version 18   |

## Initiating HTTP Data Requests

> **NOTE**
>
> In the sample code provided in this topic, **this.context** is used to obtain the UIAbilityContext, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

Complete sample code: [Http_case](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case)

1. Import the **http**, **BusinessError**, and **common** modules.

<!-- @[HTTP_case_module_import_data_request](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case/entry/src/main/ets/pages/Index.ets) -->  

``` TypeScript
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
```

2. Create an **HttpRequest** object.

    Call **createHttp()** to create an **HttpRequest** object.

 <!-- @[HTTP_case_create_http_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
    // Each httpRequest corresponds to an HTTP request task and cannot be reused.
    let httpRequest = http.createHttp();
```

3. Subscribe to the HTTP response header events.

    Call **httpRequest.on()** to subscribe to HTTP response header events. This API returns a response earlier than the request. You can subscribe to HTTP response header events based on service requirements.

<!-- @[HTTP_case_http_request_on_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    // This API is used to listen for HTTP Response Header events, which is returned earlier than the result of the HTTP request. It is up to you whether to listen for HTTP response header events.
    // on('headerReceive', AsyncCallback) will be replaced by on('headersReceive', Callback) in API version 8.
    httpRequest.on('headersReceive', (header) => {
      console.info(`header: ${JSON.stringify(header)}`);
    });
```


4. Initiate an HTTP request, and parse the server response event.

    Call **request()** to initiate a network request. You need to pass in the URL and optional parameters of the HTTP request. Parse the returned result based on service requirements.

<!-- @[HTTP_case_http_request_request_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    httpRequest.request(
      // Customize EXAMPLE_URL in extraData on your own. It is up to you whether to add parameters to the URL.
      'EXAMPLE_URL',
      {
        method: http.RequestMethod.POST, // Optional. The default value is http.RequestMethod.GET. The GET method is used to retrieve data from the server while the POST method is used to submit data such as forms and files to the server.
        // You can add header fields based on service requirements.
        header: {
          'Content-Type': 'application/json'
        },
        // This field is used to transfer the request body when a POST request is used. Its format needs to be negotiated with the server.
        extraData: 'data to send',
        expectDataType: http.HttpDataType.STRING, // Optional. This parameter specifies the type of the return data.
        usingCache: true, // Optional. The default value is true.
        priority: 1, // Optional. The default value is 1.
        connectTimeout: 60000 // Optional. The default value is 60000, in ms.
        readTimeout: 60000, // Optional. The default value is 60000, in ms.
        usingProtocol: http.HttpProtocol.HTTP1_1, // Optional. The default protocol type is automatically specified by the system.
        usingProxy: false, // Optional. By default, network proxy is not used. This field is supported since API version 10.
        caPath: '/path/to/cacert.pem', // Optional. The prebuilt CA certificate is used by default. This field is supported since API version 10.
        clientCert: { // Optional. The client certificate is not used by default. This field is supported since API version 11.
          certPath: '/path/to/client.pem', // The client certificate is not used by default. This field is supported since API version 11.
          keyPath: '/path/to/client.key', // If the certificate contains key information, an empty string is passed. This field is supported since API version 11.
          certType: http.CertType.PEM, // Certificate type, optional. A certificate in the PEM format is used by default. This field is supported since API version 11.
          keyPassword: 'passwordToKey' // Password of the key file, optional. It is supported since API version 11.
        },
        // Optional. This field is valid only when content-Type in the header is multipart/form-data. It is supported since API version 11.
        // This field is used to upload binary data to the server. You can set the field based on the data type to be uploaded.
        multiFormDataList: [
          {
            name: 'Part1', // Data name. This field is supported since API version 11.
            contentType: 'text/plain', // Data type. This field is supported since API version 11. The data to upload must be a common text file.
            data: 'Example data', // Data content, optional. This field is supported since API version 11.
            remoteFileName: 'example.txt' // Optional. This field is supported since API version 11.
          }, {
          name: 'Part2', // Data name. This field is supported since API version 11.
          contentType: 'text/plain', // Data type. This field is supported since API version 11. The data to upload must be a common text file.
          // data/app/el2/100/base/com.example.myapplication/haps/entry/files/fileName.txt
          filePath: `${context.filesDir}/fileName.txt`, // File path, optional. This field is supported since API version 11.
          remoteFileName: 'fileName.txt' // Optional. This field is supported since API version 11.
          }, {
            name: 'Part3', // Data name. This field is supported since API version 11.
            contentType: 'image/png', // Data type. This field is supported since API version 11. The data to be uploaded must be a PNG image.
            // Example: data/app/el2/100/base/com.example.myapplication/haps/entry/files/fileName.png
            filePath: `${context.filesDir}/fileName.png`, // File path, optional. This field is supported since API version 11.
            remoteFileName: 'fileName.png' // Optional. This field is supported since API version 11.
          }, {
            name: 'Part4', // Data name. This field is supported since API version 11.
            contentType: 'audio/mpeg', // Data type. This field is supported since API version 11. The data to be uploaded must be an MPEG audio file.
            // Example: data/app/el2/100/base/com.example.myapplication/haps/entry/files/fileName.mpeg.
            filePath: `${context.filesDir}/fileName.mpeg`, // File path, optional. This field is supported since API version 11.
            remoteFileName: 'fileName.mpeg' // Optional. This field is supported since API version 11.
          }, {
            name: 'Part5', // Data name. This field is supported since API version 11.
            contentType: 'video/mp4', // Data type. This field is supported since API version 11. The data to be uploaded must be an MP4 video file.
            // Example: data/app/el2/100/base/com.example.myapplication/haps/entry/files/fileName.mp4.
            filePath: `${context.filesDir}/fileName.mp4`, // File path, optional. This field is supported since API version 11
            remoteFileName: 'fileName.mp4' // Optional. This field is supported since API version 11.
          }
        ]
      }, (err: BusinessError, data: http.HttpResponse) => {
      if (!err) {
		// ···
        // data.result carries the HTTP response. Parse the response based on service requirements.
        console.info(`Result: ${JSON.stringify(data.result)}`);
        console.info(`code: ${JSON.stringify(data.responseCode)}`);
        // data.header carries the HTTP response header. Parse the content based on service requirements.
        console.info(`header: ${JSON.stringify(data.header)}`);
        console.info(`cookies: ${JSON.stringify(data.cookies)}`);
        // Call destroy() to destroy the httpRequest object when it is no longer needed.
        httpRequest.destroy();
      } else {
		// ···
        console.error(`error: ${JSON.stringify(err)}`);
        // Unsubscribe from HTTP Response Header events.
        httpRequest.off('headersReceive');
        // Call the destroy() method to release resources after HttpRequest is complete.
        httpRequest.destroy();
      }
    }
    );
```


5. Unsubscribe from HTTP response header events.

    Call **off()** to unsubscribe from HTTP response header events.

    ```ts
    // Unsubscribe from HTTP response header events when the callback information is no longer needed. For details about how to use the API, see the sample code in step 4.
    httpRequest.off('headersReceive');
    ```
6. Call **destroy()** to destroy the **httpRequest** object when it is no longer needed.

    Call **httpRequest.destroy()** to release resources after the request is processed.

    ```ts
    // Call destroy to destroy the httpRequest when it is no longer needed. For details about how to use the API, see the sample code in step 4.
    httpRequest.destroy();
    ```
## Initiating an HTTP Streaming Request

HTTP streaming refers to the process where, when handling an HTTP response, only a small chunk of the response content is processed at a time, rather than loading the entire response into memory all at once. This is particularly useful for scenarios such as processing large files and real-time data streams, among others.

Complete sample code: [Http_case](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case)

1. Import the **http**, **BusinessError**, and **common** modules.

  <!-- @[HTTP_case_module_import_data_request](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
```

2. Create an **HttpRequest** object for HTTP streaming.

    Call **createHttp()** to create an **HttpRequest** object.

 <!-- @[request_in_stream_create_http_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    // Each httpRequest corresponds to an HTTP request task and cannot be reused.
    let httpRequest = http.createHttp();
```

3. Subscribe to HTTP streaming response events on demand.

	The server response is returned via the **dataReceive** callback. You can subscribe to this callback to obtain the server response. You can also subscribe to other streaming response events as needed.
  
<!-- @[request_in_stream_data_receive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    // Subscribe to events indicating receiving of HTTP streaming responses.
    let res = new ArrayBuffer(0);
	// ···
    // Register an observer for events indicating receiving of HTTP streaming responses.
    httpRequest.on('dataReceive', (data: ArrayBuffer) => {
      const newRes = new ArrayBuffer(res.byteLength + data.byteLength);
      const resView = new Uint8Array(newRes);
      resView.set(new Uint8Array(res));
      resView.set(new Uint8Array(data), res.byteLength);
      res = newRes;
      console.info(`res length: ${res.byteLength}`);
    });

    // Subscribe to events indicating completion of receiving HTTP streaming responses.
    httpRequest.on('dataEnd', () => {
      console.info(`No more data in response, data receive end`);
    });

    // Subscribe to events indicating progress of receiving HTTP streaming responses. When downloading data from the server, you can obtain the data download progress through this callback.
    httpRequest.on('dataReceiveProgress', (data: http.DataReceiveProgressInfo) => {
      console.info('dataReceiveProgress receiveSize:' + data.receiveSize + ', totalSize:' + data.totalSize);
    });

    // Subscribe to events indicating progress of sending HTTP streaming responses. When uploading data from the server, you can obtain the data upload progress through this callback.
    httpRequest.on('dataSendProgress', (data: http.DataSendProgressInfo) => {
      console.info('dataSendProgress receiveSize:' + data.sendSize + ', totalSize:' + data.totalSize);
    });
```

4. Initiate an HTTP streaming request to obtain server data.

<!-- @[request_in_stream_get_server_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let streamInfo: http.HttpRequestOptions = {
  method: http.RequestMethod.POST, // Optional. The default value is http.RequestMethod.GET. The GET method is used to retrieve data from the server while the POST method is used to submit data such as forms and files to the server.
  // You can add header fields based on service requirements.
  header: {
    'Content-Type': 'application/json'
  },
  // This field is used to transfer the request body when a POST request is used. Its format needs to be negotiated with the server.
  extraData: 'data to send', // Request body
  expectDataType: http.HttpDataType.STRING, // Optional. This parameter specifies the type of the return data.
  usingCache: true,  // Optional. The default value is true.
  priority: 1, // Optional. The default value is 1.
  connectTimeout: 60000 // Optional. The default value is 60000, in ms.
  readTimeout: 60000, // Optional. The default value is 60000, in ms. If a large amount of data needs to be transmitted, you are advised to set this parameter to a larger value to ensure normal data transmission.
  usingProtocol: http.HttpProtocol.HTTP1_1 // Optional. The default protocol type is automatically specified by the system.
};

// Customize EXAMPLE_URL in extraData on your own. It is up to you whether to add parameters to the URL.
httpRequest.requestInStream('EXAMPLE_URL', streamInfo)
  .then((data: number) => {
    // ···
    hilog.info(0x0000, 'testTag', `requestInStream OK!`);
    hilog.info(0x0000, 'testTag', `ResponseCode : ${JSON.stringify(data)}`);
    // Unsubscribe from the events subscribed in step 3, and call the destroy method to destroy the httpRequest object.
    this.destroyRequest(httpRequest);
    // ···
  }).catch((err: Error) => {
    // ···
    hilog.error(0x0000, 'testTag', `requestInStream ERROR : err = ${JSON.stringify(err)}`);
    // Unsubscribe from the events subscribed in step 3, and call the destroy method to destroy the httpRequest object.
    this.destroyRequest(httpRequest);
  })
```


5. Unsubscribe from the HTTP streaming response events subscribed in step 3, and call **destroy()** to destroy the **httpRequest** object.

    Call the **off()** API of the **httpRequest** object to unsubscribe from the events subscribed in step 3. When the request is complete, call **destroy()** to destroy the **httpRequest** object. For details about how to use this API, see the sample code in step 4.

<!-- @[request_in_stream_destroy_request_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
  public destroyRequest(httpRequest: http.HttpRequest) {
    // Unsubscribe from the events indicating receiving of HTTP streaming responses.
    httpRequest.off('dataReceive');
    // Unsubscribe from the events indicating progress of sending HTTP streaming responses.
    httpRequest.off('dataSendProgress');
    // Unsubscribe from the events indicating progress of receiving HTTP streaming responses.
    httpRequest.off('dataReceiveProgress');
    // Unsubscribe from the events indicating completion of receiving HTTP streaming responses.
    httpRequest.off('dataEnd');
    // Call destroy() to destroy the httpRequest object when it is no longer needed.
    httpRequest.destroy();
  }
```

## Configuring Certificate Verification

Certificate-related configurations are required for using the HTTPS protocol. The applications that provide services for Internet users only need to trust the system's prebuilt CA certificates. Currently, the HTTP module trusts the CA certificates preset in the system by default. No special setting is required. If an application needs to trust only the certificates specified by developers, or skip certificate verification, you can configure certificate pinning.

### Certificate Pinning

You can prebuild application-level certificates or a public key hash values for certificate pinning. This way, an HTTPS connection can be established only when the prebuilt certificate is used.

Both modes are configured through `src/main/resources/base/profile/network_config.json`. In the configuration file, you can create mapping between prebuilt certificates and network servers.

If you do not know the certificate mapping a server domain name, you can use the following command to obtain the certificate. When running the command, change `www.example.com` to the server domain name and `www.example.com.pem` to the name of the obtained certificate file.

```
openssl s_client -servername www.example.com -connect www.example.com:443 \
    < /dev/null | sed -n "/-----BEGIN/,/-----END/p" > www.example.com.pem
```

If you are using a Windows environment, you need to:

* Replace `/dev/null` with `NUL`.
* Press **Enter** to exit. This is different from OpenSSL of Linux, which may exit until the user enters a value.
* If the **sed** command is not present, copy the content between `-----BEGIN CERTIFICATE-----` and `-----END CERTIFICATE-----` (with these two lines included) in the command output and save it.

**Prebuilding Application-level Certificate**

Prebuilding application-level certificates means to embed the original certificate files in the application. Currently, certificate files in the **.crt** and **.pem** formats are supported.

> **NOTE**
>
> Currently, certificate pinning has been enabled for the ohos.net.http and Image components, and the hash values of all certificates in the certificate chain are matched. If any certificate is updated on the server, the verification fails. Therefore, if any certificate on the server has been updated, upgrade the application to the latest version as soon as possible. Otherwise, network connection may fail.

**Prebuilding Certificate Public Key Hash Values**

You can create mapping between public key hash values and domain name certificates in the configuration file. This way, access to the domain name is allowed only if the used domain name certificate matches the prebuilt public key hash value.

The public key hash value of the domain name certificate can be calculated using the following command. Assume that the domain name certificate is obtained using the preceding OpenSSL command and saved in the `www.example.com.pem` file. The line that starts with # is treated as a comment.

```
# Extract the public key from the certificate.
openssl x509 -in www.example.com.pem -pubkey -noout > www.example.com.pubkey.pem
# Convert the public key from the pem format to the der format.
openssl asn1parse -noout -inform pem -in www.example.com.pubkey.pem -out www.example.com.pubkey.der
# Calculate the SHA256 of the public key and convert it to Base64.
openssl dgst -sha256 -binary www.example.com.pubkey.der | openssl base64
```

**Example JSON Configuration File**

The following is an example of prebuilt application-level certificates. For details about the configuration path, see [Network Connection Security Configuration](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-network-ca-security#section5454123841911).

```json
{
  "network-security-config": {
    "base-config": {
      "trust-anchors": [
        {
          "certificates": "/etc/security/certificates"
        }
      ]
    },
    "domain-config": [
      {
        "domains": [
          {
            "include-subdomains": true,
            "name": "example.com"
          }
        ],
        "trust-anchors": [
          {
            "certificates": "/data/storage/el1/bundle/entry/resources/resfile"
          }
        ]
      }
    ]
  }
}
```

The following is an example of prebuilt certificate public key hash values:

```
{
  "network-security-config": {
    "domain-config": [
      {
        "domains": [
          {
            "include-subdomains": true,
            "name": "*.server.com"
          }
        ],
        "pin-set": {
          "expiration": "2024-11-08",
          "pin": [
            {
              "digest-algorithm": "sha256",
              "digest": "FEDCBA987654321"
            }
          ]
        }
      }
    ]
  }
}
```

The following is an example configuration of the certificate pin:

```
{
  "network-security-config": {
    "domain-config": [
      {
        "domains": [
          {
            "include-subdomains": true,
            "name": "*.server.com"
          }
        ],
        "pin-set": {
          "expiration": "2024-11-08",
          "pin": [
            {
              "digest-algorithm": "sha256",
              "digest": "FEDCBA987654321"
            }
          ]
        }
      }
    ]
  },
  "trust-global-user-ca": false,
  "trust-current-user-ca": false,
}
```

**Description of fields**

| Field                     | Type           | Description                                  |
| --------------------------| --------------- | -------------------------------------- |
|network-security-config    | object          |Network security configuration. The value can contain zero or one **base-config** and must contain one **domain-config**.|
|base-config                | object          |Application security configuration. The value must contain one **trust-anchors**.                         |
|domain-config              | array           |Domain security configuration. The value can contain any number of items. An item must contain one **domains** and can contain zero or one **trust-anchors** and **pin-set**.|
|trust-anchors              | array           |Trusted CA. The value can contain any number of items. An item must contain one **certificates**.|
|certificates               | string          |CA certificate path.|
|domains                    | array           |Domain. The value can contain any number of items. An item must contain one **name** (string: domain name) and can contain zero or one **include-subdomains**.|
|include-subdomains         | boolean         |Whether a rule applies to subdomains. Whether a rule applies to subdomains. The value **true** indicates that the rule applies to subdomains, and the value **false** indicates the opposite.|
|pin-set                    | object          |Certificate public key hash setting. The value must contain one **pin** and can contain zero or one **expiration**.|
|expiration                 | string          |Expiration time of the certificate public key hash.|
|pin                        | array           |Certificate public key hash. The value can contain any number of items. An item must contain one **digest-algorithm** and **digest**.|
|digest-algorithm           | string          |Digest algorithm used to generate hashes. Currently, only `sha256` is supported.                                   |
|digest                     | string          |Public key hash.|

### Configuring Untrusted User-Installed CA Certificates

By default, the system trusts the prebuilt CA certificates and user-installed CA certificates. To further improve security, you can configure untrusted user-installed CA certificates in **src/main/resources/base/profile/network_config.json**. For more network connection security configurations, see [Network Connection Security Configuration](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-network-ca-security#section5454123841911).

```
{
  "network-security-config": {
    ... ...
  },
  "trust-global-user-ca": false, // Set whether to trust the CA certificate manually installed by the enterprise MDM system or device administrator. The default value is true.
  "trust-current-user-ca" : false // Set whether to trust the certificate installed by the current user. The default value is true.
}
```
### Configuring Plaintext HTTP Access Permissions

This configuration item is used to control whether HTTP requests can be transmitted in plaintext. The following is an example of configuring plaintext HTTP access permissions (including application, component, and domain name configurations) and the description of each field. For more network connection security configurations, see [Network Connection Security Configuration](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-network-ca-security#section5454123841911).
> **NOTE**
>
> The configuration priority rules are as follows: **component-config** > **domain-config** > **base-config**. The configuration with a higher priority overrides the configuration with a lower priority.


```
// src/main/resources/base/profile/network_config.json
{
  "network-security-config": {
    "base-config": {
      "cleartextTrafficPermitted": true // Optional, supported since API 20.
    },
    "domain-config": [
      {
        "domains": [
          {
            "include-subdomains": true,
            "name": "example.com"
          }
        ],
        "cleartextTrafficPermitted": false // Optional, supported since API 20.
      }
    ],
    "component-config": {
    	"Network Kit": true, // Optional, supported since API 20.
    	"ArkWeb": false // Optional, supported since API 20.
    }
  }
}
```

**Description of fields**

| Field                     | Type           | Mandatory| Description                                  |
| --------------------------| --------------- |--------- |-------------------------------------- |
|base-config                     | array          | No| Indicates the plaintext configuration of the application scope. This field has the lowest priority.|
|cleartextTrafficPermitted  | boolean          |No| Whether plaintext HTTP is allowed. The value **true** indicates that plaintext HTTP is allowed, and the value **false** indicates the opposite.|
|domain-config                     | array          | No|  Indicates the plaintext configuration of each domain. The value can contain any number of items. Each item must contain one **domains**. If rules conflict in the same domain, the first matched rule is used. The priority is lower than that of **component-config**.|
|include-subdomains         | boolean         | No| Whether a rule applies to subdomains. The value **true** indicates that the rule applies to subdomains, and the value **false** indicates the opposite. The default value is **false**.|
|name         | string         | No| Main domain name.|
|component-config                    | array          |  No| Indicates the plaintext configuration of each component. This field has the highest priority.|
|Network Kit                 | boolean          |No| Whether plaintext transmission is disabled in Network Kit. The value **true** indicates that plaintext transmission is disabled, and the value **false** indicates the opposite. The default value is **true**.|
|ArkWeb                    | boolean          |No| Whether plaintext transmission is disabled in ArkWeb. The value **true** indicates that plaintext transmission is disabled, and the value **false** indicates the opposite. The default value is **false**.|

## HTTP Interceptor

From API version 22, the HTTP Interceptor module provides a powerful and customizable mechanism that allows developers to insert custom logic at key points in the "HTTP request-response" lifecycle. With interceptors, you can implement global features such as request header/body modification, cache policy, redirection, network monitoring, and response preprocessing without modifying the core network code.

### Intercept Point Description

| Point Name                       | Position Description                                                    | Output and Input Parameters of the interceptorHandle API for the Intercept Point                                                  |
| :-------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| INITIAL_REQUEST  | The first intercept point after the initial request is assembled. Suitable for adding global parameters, signing, and encrypting the request body.| The output parameter **true** indicates that the **request** value in the input parameter is the original value and can be modified, while the **response** value is empty and cannot be modified.<br>The output parameter **false** indicates that the **request** value in the input parameter is the original value and cannot be modified, while the **response** value is empty and can be modified.|
| CONNECT_NETWORK| Located before a network connection is established, for example, a TCP/TLS connection. Suitable for network link-related operations, such as recording the network connection start time.| The output parameter **true** indicates that the **request** value in the input parameter is the original value and can be modified, while the **response** value is empty and cannot be modified.<br>The output parameter **false** indicates that the **request** value in the input parameter is the original value and cannot be modified, while the **response** value is empty and can be modified.|
| CACHE_CHECKED      | Located after the cache check logic hits the cache and determined that the cache is available. Suitable for viewing the cache value or modifying the queried cache result.| The output parameter **true** indicates that the **request** value in the input parameter is the original value and cannot be modified, while the **response** value is the original value and cannot be modified.<br>The output parameter **false** indicates that the **request** value in the input parameter is the original value and cannot be modified, while the **response** value is the original value and can be modified.|
| REDIRECTION      | Located before a redirection response is received and a new request is ready to be sent. Allows the target URL or request information of redirection to be modified.| The output parameter **true** indicates that the **request** value in the input parameter is the original value and the URL can be modified. The **response** value is the original value and the modification is invalid.<br>The output parameter **false** indicates that the **request** value in the input parameter is the original value and cannot be modified, while the **response** value is the original value and can be modified.|
| FINAL_RESPONSE   | Located after the final response is obtained. The last intercept point, which is suitable for unified decryption, parsing, logging, and error handling of responses.| The output parameter **true** indicates that the **request** value in the input parameter is the original value and cannot be modified, while the **response** value is the original value and cannot be modified.<br>The output parameter **false** indicates that the **request** value in the input parameter is the original value and cannot be modified, while the **response** value is the original value and can be modified.|

**Sequential Execution**: The interceptor is triggered in the sequence specified by INITIAL_REQUEST > CACHE_CHECKED > NETWORK_CONNECT > (REDIRECTION) > FINAL_RESPONSE. (The bracket indicates that if the request involves redirection, it will go through the redirection interceptor.)

**Redirection Loop**: This is the most critical loop in the process. When the **REDIRECTION** interceptor is triggered, the process jumps back to the **NETWORK_CONNECT** phase and starts a new request cycle until no redirection occurs. This ensures that the new request after redirection can be correctly processed by all necessary interceptors (such as adding authentication headers and recording logs).

**Cache interception**: **CACHE_CHECKED** is a decision point. If the cache exists and is valid, the request is processed by **CACHE_CHECKED** and directly jumps to the **FINAL_RESPONSE** phase to return the cache data, avoiding unnecessary network operations.

### HTTP Interceptor Development Procedure

1.  Import the modules required by the HTTP request interceptor.

<!-- @[HTTP_interceptor_case_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case/entry/src/main/ets/pages/Index.ets) -->  

```typescript
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```

2.  Call [createHttp()](../reference/apis-network-kit/js-apis-http.md#httpcreatehttp) to create an **HttpRequest** object.

 <!-- @[HTTP_interceptor_case_creat_request](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case/entry/src/main/ets/pages/Index.ets) -->

```typescript
// Create an HTTP request.
let httpRequest: http.HttpRequest = http.createHttp();
```

3.  Call the **HttpInterceptorChain()** method to create an interceptor chain object.

<!-- @[HTTP_interceptor_case_chain](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case/entry/src/main/ets/pages/Index.ets) -->

```typescript
// Create an interceptor chain.
let chain: http.HttpInterceptorChain = new http.HttpInterceptorChain();
```

4.  Create an interceptor class to implement the **http.HttpInterceptor** API.

<!-- @[HTTP_interceptor_case_creat_http_interceptor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case/entry/src/main/ets/pages/Index.ets) -->

```typescript
enum InterceptorType {
  INITIAL_REQUEST = 'INITIAL_REQUEST',
  REDIRECTION = 'REDIRECTION',
  CACHE_CHECKED = 'READ_CACHE',
  NETWORK_CONNECT = 'CONNECT_NETWORK',
  FINAL_RESPONSE = 'FINAL_RESPONSE'
}

class InitialHttpInterceptor implements http.HttpInterceptor {
  interceptorType: InterceptorType = InterceptorType.INITIAL_REQUEST;
  result: boolean = false;

  constructor(interceptorType: InterceptorType, result: boolean) {
    this.interceptorType = interceptorType;
    this.result = result;
  }

  interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Perform operations on request packets and responses after the interceptor is hit.
    hilog.info(0xFF00, 'httpNormalRequest', `INITIAL_REQUEST, Original req: ${JSON.stringify(reqContext)}`);
    hilog.info(0xFF00, 'httpNormalRequest', `INITIAL_REQUEST, Original rsp: ${JSON.stringify(rspContext)}`);

    reqContext.url = EXAMPLE_INITIAL_URL;
    reqContext.header = { 'content-type': 'text/plain' };
    reqContext.body = { 'context': 'INITIAL_REQUEST' };

    rspContext.result = 'INITIAL_REQUEST';
    rspContext.responseCode = 200;
    rspContext.header =
      'content-encoding:br \r\n content-type:text/html\r\ncharset=UTF-8,cxy_all:+5c4ea5d1638626cbb796a7db10e0d663\r\ndate:Tue';

    hilog.info(0xFF00, 'httpNormalRequest', `INITIAL_REQUEST, Update req: ${JSON.stringify(reqContext)}`);
    hilog.info(0xFF00, 'httpNormalRequest', `INITIAL_REQUEST, Update rsp: ${JSON.stringify(rspContext)}`);
    return Promise.resolve(this.result);
  }
}

class NetworkHttpInterceptor implements http.HttpInterceptor {
  interceptorType: InterceptorType = InterceptorType.INITIAL_REQUEST;
  result: boolean = false;

  constructor(interceptorType: InterceptorType, result: boolean) {
    this.interceptorType = interceptorType;
    this.result = result;
  }

  interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Perform operations on request packets and responses after the interceptor is hit.
    hilog.info(0xFF00, 'httpNormalRequest', `NETWORK_CONNECT, Original req: ${JSON.stringify(reqContext)}`);
    hilog.info(0xFF00, 'httpNormalRequest', `NETWORK_CONNECT, Original rsp: ${JSON.stringify(rspContext)}`);

    reqContext.url = EXAMPLE_URL;
    reqContext.header = { 'content-type': 'text/xml' };
    reqContext.body = { 'context': 'NETWORK_CONNECT' };

    rspContext.result = 'NETWORK_CONNECT';
    rspContext.responseCode = 300;
    rspContext.header =
      'content-encoding:br \r\n content-type:text/html\r\ncharset=UTF-8,cxy_all:+5c4ea5d1638626cbb796a7db10e0d663\r\ndate:Tue';

    hilog.info(0xFF00, 'httpNormalRequest', `NETWORK_CONNECT, Update req: ${JSON.stringify(reqContext)}`);
    hilog.info(0xFF00, 'httpNormalRequest', `NETWORK_CONNECT, Update rsp: ${JSON.stringify(rspContext)}`);
    return Promise.resolve(this.result);
  }
}

class FinalHttpInterceptor implements http.HttpInterceptor {
  interceptorType: InterceptorType = InterceptorType.INITIAL_REQUEST;
  result: boolean = false;

  constructor(interceptorType: InterceptorType, result: boolean) {
    this.interceptorType = interceptorType;
    this.result = result;
  }

  interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Perform operations on request packets and responses after the interceptor is hit.
    hilog.info(0xFF00, 'httpNormalRequest', `FINAL_RESPONSE, Original req: ${JSON.stringify(reqContext)}`);
    hilog.info(0xFF00, 'httpNormalRequest', `FINAL_RESPONSE, Original rsp: ${JSON.stringify(rspContext)}`);

    reqContext.url = EXAMPLE_Final_URL;
    reqContext.header = { 'content-type': 'text/html' };
    reqContext.body = { 'context': 'FINAL_RESPONSE' };

    rspContext.result = 'FINAL_RESPONSE';
    rspContext.responseCode = 200;
    rspContext.header =
      'content-encoding:br \r\n content-type:text/html\r\ncharset=UTF-8,cxy_all:+5c4ea5d1638626cbb796a7db10e0d663\r\ndate:Tue';

    hilog.info(0xFF00, 'httpNormalRequest', `FINAL_RESPONSE, Update req: ${JSON.stringify(reqContext)}`);
    hilog.info(0xFF00, 'httpNormalRequest', `FINAL_RESPONSE, Update rsp: ${JSON.stringify(rspContext)}`);
    return Promise.resolve(this.result);
  }
}
```

5.  Call the **addChain()** method to add the required interceptor instance to the interceptor chain.

<!-- @[HTTP_interceptor_case_addChain](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Create the required interceptor object and add it to the interceptor chain.
chain.addChain([
  new InitialHttpInterceptor(InterceptorType.INITIAL_REQUEST, true),
  new NetworkHttpInterceptor(InterceptorType.NETWORK_CONNECT, true),
  new FinalHttpInterceptor(InterceptorType.FINAL_RESPONSE, true)
]);
```

6.  Call the **apply()** method to attach the configured interceptor chain to **httpRequest**.

<!-- @[HTTP_interceptor_case_apply](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case/entry/src/main/ets/pages/Index.ets) -->

```typescript
// Attach the configured interceptor chain to **httpRequest**.
chain.apply(httpRequest);
```

7.  Create request options.

<!-- @[HTTP_interceptor_case_options](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case/entry/src/main/ets/pages/Index.ets) -->

```typescript
// Create request options.
let options: http.HttpRequestOptions = {
  method: http.RequestMethod.POST,
  header: { 'content-type': 'text/html' } as Record<string, string>,
  extraData: { 'context': 'BODY' } as Record<string, string>,
};
```

8.  Call the **request()** method of this object to initiate a network request. You need to pass in the URL and optional parameters of the HTTP request. Parse the server response event as required.

<!-- @[HTTP_interceptor_case_request](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Initiate a request.
httpRequest.request(EXAMPLE_URL, options, (err: BusinessError, res: http.HttpResponse) => {
  if (err) {
    hilog.error(0xFF00, 'httpNormalRequest', `request fail, error code: ${err.code}, msg: ${err.message}`);
    // ···
  } else {
    hilog.info(0xFF00, 'httpNormalRequest', `res:${JSON.stringify(res)}`);
    // ···
  }
// ···
});
```

9.  Call the **destroy()** method to destroy the HTTP request.

<!-- @[HTTP_interceptor_case_request_destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case/entry/src/main/ets/pages/Index.ets) -->

```typescript
// Destroy the request.
httpRequest.destroy();
```

## 
## Samples

The following sample is provided to help you better understand how to develop the HTTP data request feature:

* [Upload and Download (ArkTS) (API10)] (https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Connectivity/UploadAndDownLoad)

* [Http (ArkTS) (API10) ](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Connectivity/Http)

* [Http_case](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_case)

* [HTTP_interceptor_case](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/HTTP_interceptor_case)
