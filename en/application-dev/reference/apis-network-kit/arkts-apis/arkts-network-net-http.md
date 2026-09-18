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

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```
