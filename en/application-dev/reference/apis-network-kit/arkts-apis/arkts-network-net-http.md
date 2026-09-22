# @ohos.net.http(Data Request)

The **http** module provides APIs for implementing HTTP data request capabilities. An application can initiate a data request over HTTP. Common HTTP methods include **GET**, **POST**, **OPTIONS**, **HEAD**, **PUT**, **DELETE**, **PATCH**, **TRACE**, and **CONNECT**.

**Since:** 6

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createHttp](arkts-network-http-createhttp-f.md) | Creates an HTTP request. You can use this API to initiate or destroy an HTTP request, or enable or disable listening for HTTP Response Header events. To initiate multiple HTTP requests, you must create an **HttpRequest** object for each HTTP request. An **HttpRequest** object corresponds to an HTTP request. |
| [createHttpResponseCache](arkts-network-http-createhttpresponsecache-f.md) | Creates an **HttpResponseCache** object that stores the response data of HTTP requests. You can call [flush](arkts-network-http-httpresponsecache-i.md#flush) and [delete](arkts-network-http-httpresponsecache-i.md#delete) in the object. |

### Classes

| Name | Description |
| --- | --- |
| [HttpInterceptorChain](arkts-network-http-httpinterceptorchain-c.md) | Defines HTTP interceptor chain. |

### Interfaces

| Name | Description |
| --- | --- |
| [CertificatePinning](arkts-network-http-certificatepinning-i.md) | Defines the dynamic configuration of certificate pinning. |
| [ClientCert](arkts-network-http-clientcert-i.md) | Defines the client certificate type. |
| [ConnectionExtraInfo](arkts-network-http-connectionextrainfo-i.md) | Defines the detailed information about the HTTP request interaction. |
| [Credential](arkts-network-http-credential-i.md) | Represents the credential used for server identity verification in a session, including the user name and password. |
| [DataReceiveProgressInfo](arkts-network-http-datareceiveprogressinfo-i.md) | Defines the data receiving progress information. |
| [DataSendProgressInfo](arkts-network-http-datasendprogressinfo-i.md) | Defines the data sending progress information. |
| [HttpInterceptor](arkts-network-http-httpinterceptor-i.md) | Defines the HTTP interceptor API, which is used to define the interception processing function. |
| [HttpRequest](arkts-network-http-httprequest-i.md) | Defines an HTTP request task. Before invoking APIs provided by **HttpRequest**, you must call [createHttp()](arkts-network-http-createhttp-f.md) to create an **HttpRequestTask** object. |
| [HttpRequestContext](arkts-network-http-httprequestcontext-i.md) | Defines HTTP request context data. The object instance is passed as a parameter in the [interceptorHandle](arkts-network-http-httpinterceptor-i.md#interceptorhandle) method of the interceptor. You can use this object to obtain and modify the information about the HTTP request. |
| [HttpRequestOptions](arkts-network-http-httprequestoptions-i.md) | Defines the options for initiating an HTTP request. |
| [HttpResponse](arkts-network-http-httpresponse-i.md) | Defines the response to an HTTP request. |
| [HttpResponseCache](arkts-network-http-httpresponsecache-i.md) | Defines an object that stores the response to an HTTP request. Before invoking APIs provided by **HttpResponseCache**, you must call [createHttpResponseCache()](arkts-network-http-createhttpresponsecache-f.md) to create an **HttpRequestTask** object. |
| [MultiFormData](arkts-network-http-multiformdata-i.md) | Defines the type of multi-form data. |
| [PerformanceTiming](arkts-network-http-performancetiming-i.md) | Configures the timing for performance tracing, in ms. |
| [ServerAuthentication](arkts-network-http-serverauthentication-i.md) | Defines HTTP server identity verification information. |
| [TlsConfig](arkts-network-http-tlsconfig-i.md) | Defines the TLS configuration, including the version and cipher suite. |
| [ValidationContext](arkts-network-http-validationcontext-i.md) | The validation context of [ValidationCallback](arkts-network-http-validationcallback-t.md) |

### Enums

| Name | Description |
| --- | --- |
| [AddressFamily](arkts-network-http-addressfamily-e.md) | Enumerates IP address families of the target domain name. |
| [CertType](arkts-network-http-certtype-e.md) | Enumerates certificate types. |
| [HttpDataType](arkts-network-http-httpdatatype-e.md) | Enumerates HTTP data types. |
| [HttpProtocol](arkts-network-http-httpprotocol-e.md) | Enumerates HTTP protocol versions. |
| [InterceptorType](arkts-network-http-interceptortype-e.md) | Enumerates the types of HTTP interceptors. |
| [RequestMethod](arkts-network-http-requestmethod-e.md) | Defines an HTTP request method. |
| [ResponseCode](arkts-network-http-responsecode-e.md) | Enumerates the response codes for an HTTP request. |
| [TlsVersion](arkts-network-http-tlsversion-e.md) | Enumerates TLS versions. |

### Types

| Name | Description |
| --- | --- |
| [AuthenticationType](arkts-network-http-authenticationtype-t.md) | Enumerates server authentication modes in a session. |
| [ChainContinue](arkts-network-http-chaincontinue-t.md) | Specifies whether to continue to process the interceptor chain. |
| [CipherSuite](arkts-network-http-ciphersuite-t.md) | Declares the cipher suite. |
| [HttpProxy](arkts-network-http-httpproxy-t.md) | Defines the network proxy configuration. |
| [PathPreference](arkts-network-http-pathpreference-t.md) | Enumerates the types of networks specified in an HTTP request. |
| [QueryParamObject](arkts-network-http-queryparamobject-t.md) | Defines the key-value object type used to construct URL query parameters. |
| [QueryParamValue](arkts-network-http-queryparamvalue-t.md) | Defines the single-value type that can be used in **QueryParamObject**. |
| [RemoteValidation](arkts-network-http-remotevalidation-t.md) | Enumerates the identity verification modes of the remote server. |
| [Socks5Proxy](arkts-network-http-socks5proxy-t.md) | Socks5 Proxy Configuration Information. |
| [SslType](arkts-network-http-ssltype-t.md) | Defines the secure communications protocol. |
| [TlsOptions](arkts-network-http-tlsoptions-t.md) | Defines the TLS configuration. |
| [TlsV10CipherSuite](arkts-network-http-tlsv10ciphersuite-t.md) | Declares the cipher suite for TLS 1.0. |
| [TlsV10SpecificCipherSuite](arkts-network-http-tlsv10specificciphersuite-t.md) | Enumerates cipher suites supported by TLS 1.0 or later. |
| [TlsV11CipherSuite](arkts-network-http-tlsv11ciphersuite-t.md) | Declares the cipher suite for TLS 1.1, which is the same as that for TLS1.0. |
| [TlsV12CipherSuite](arkts-network-http-tlsv12ciphersuite-t.md) | Declares the cipher suite for TLS 1.2, which is also compatible with TLS 1.1. |
| [TlsV12SpecificCipherSuite](arkts-network-http-tlsv12specificciphersuite-t.md) | Enumerates cipher suites supported by TLS 1.2 or later. |
| [TlsV13CipherSuite](arkts-network-http-tlsv13ciphersuite-t.md) | Declares the cipher suite for TLS 1.3, which is also compatible with TLS 1.2. |
| [TlsV13SpecificCipherSuite](arkts-network-http-tlsv13specificciphersuite-t.md) | Enumerates cipher suites supported by TLS 1.3 or later. |
| [ValidationCallback](arkts-network-http-validationcallback-t.md) | Self defined remote validation. This API uses a promise to return the result. |
| [X509Cert](arkts-network-http-x509cert-t.md) | X509 certificate. |

## Examples

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
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
    addressFamily: http.AddressFamily.DEFAULT, // Optional. By default, the IPv4 or IPv6 address of the target domain name is selected. This field is supported since API version 15.
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
