# HttpRequestOptions

```TypeScript
export interface HttpRequestOptions
```

Defines the options for initiating an HTTP request.

**Since:** 6

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## addressFamily

```TypeScript
addressFamily?: AddressFamily
```

IP address family. You can specify an address type for domain name resolution.

**Type:** [AddressFamily](arkts-network-http-addressfamily-e.md)

**Since:** 15

**System capability:** SystemCapability.Communication.NetStack

## body

```TypeScript
body?: string | Object | ArrayBuffer
```

HTTP request body. After this field is set, the framework preferentially sends this field as the request body.

- The value can be a string, an object, or an **ArrayBuffer**. A string is sent as the original value, an object  
is serialized before being sent, and an **ArrayBuffer** is sent in binary format.  
- If both **body** and **extraData** are configured, **body** takes precedence and **extraData** will be ignored.  
- This field can be used with any request method to explicitly specify the request body.

**Since**: 26.0.0

**Type:** string &#124; Object &#124; ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## caData

```TypeScript
caData?: string
```

CA certificate data. If this parameter is set and the certificate is valid, the system uses the specified CA certificate and the preset CA certificate. Otherwise, the system uses only the preset CA certificate. If both **caPath** and **caData** are set, **caData** is ignored by the system. Currently, only certificates in **.pem** format are supported. The maximum length is 8000 bytes. Only one certificate can be specified. A certificate chain is not allowed.

The preset CA certificate is available at **\/etc/ssl/certs/cacert.pem**. This path is the sandbox mapping path, which can be obtained by using **UIAbilityContext** APIs.

**Type:** string

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Communication.NetStack

## caPath

```TypeScript
caPath?: string
```

CA certificate data. If this parameter is set and the certificate is valid, the system uses the specified CA certificate and the preset CA certificate. Otherwise, the system uses only the preset CA certificate. The CA certificate path is the sandbox mapping path, which can be obtained by using **UIAbilityContext** APIs. Currently, only **.pem** certificates are supported.

The preset CA certificate is available at **\/etc/ssl/certs/cacert.pem**.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## certificatePinning

```TypeScript
certificatePinning?: CertificatePinning[]
```

Dynamic configuration of certificate pinning. One or more certificate PINs can be specified.

**Type:** [CertificatePinning](arkts-network-http-certificatepinning-i.md)[]

**Since:** 12

**System capability:** SystemCapability.Communication.NetStack

## clientCert

```TypeScript
clientCert?: ClientCert
```

Client certificate.

**Type:** [ClientCert](arkts-network-http-clientcert-i.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## clientEncCert

```TypeScript
clientEncCert?: ClientCert
```

Client certificate, which is used by the server to verify the client identity.

**Type:** [ClientCert](arkts-network-http-clientcert-i.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Communication.NetStack

## connectTimeout

```TypeScript
connectTimeout?: number
```

Connection timeout interval. The default value is **60000**, in ms. The input value must be an uint32_t integer.

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## customMethod

```TypeScript
customMethod?: string
```

Custom request method. For example, when the WebDAV extension protocol is implemented, **customMethod** has a higher priority than **method**.

- The default value is an empty string. The value can contain a maximum of 128 characters. If the value exceeds 1  
28 characters, the setting does not take effect.  
- If **customMethod** meets the WebDAV extension protocol request requirements but the server does not support  
the request, the server response code of the request is usually 405 or 501 (the actual result depends on the server behavior).  
- If **customMethod** does not meet the WebDAV extension protocol request requirements, the server response code  
of the request is usually 400 or 405 (the actual result depends on the server behavior).

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Communication.NetStack

## dnsOverHttps

```TypeScript
dnsOverHttps?: string
```

Whether to use an HTTPS server for DNS resolution.

- The value must be URL-encoded in the following format: "https:// host:port/path".

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## dnsServers

```TypeScript
dnsServers?: Array<string>
```

Array of DNS servers used for DNS resolution.

- A maximum of three DNS servers can be set. If there are more than three DNS servers, only the first three DNS  
servers are used.  
- The DNS servers must be expressed as IPv4 or IPv6 addresses.

**Type:** Array&lt;string&gt;

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## enablePartialChain

```TypeScript
enablePartialChain?: boolean
```

Indicates whether to enable partial chain verification. The default value is true when SslType is set to TLS, and false when SslType is set to TLCP. If set to false, the certificate chain must verify up to a trusted root CA. If set to true, the verification succeeds if the chain builds to a trusted intermediate CA, without requiring a path to a trusted root CA.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## expectDataType

```TypeScript
expectDataType?: HttpDataType
```

Type of the returned data. This parameter is not used by default. If this parameter is set, the system returns the specified type of data preferentially. If the specified type is **Object**, the value can contain a maximum of 65536 characters.

**Type:** [HttpDataType](arkts-network-http-httpdatatype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## extraData

```TypeScript
extraData?: string | Object | ArrayBuffer
```

Additional data for sending a request. This parameter is not used by default. Since API version 26, you are advised to use the **body** and **queryParams** parameters preferentially.

**Note:**  Do not add this parameter if no extra data is available. If this parameter must be added, set it to **undefined** or **null**. Do not pass the parameter as "".

- If the HTTP request uses a POST, PUT, or DELETE method, this field serves as the content of the HTTP request  
and is encoded in UTF-8 format.

Example:

(1) If **content-Type** is **application/x-www-form-urlencoded**, the data in the request body must be encoded in the format of **key1=value1&key2=value2&key3=value3** after URL transcoding (**encodeURIComponent/encodeURI**) and this field is usually in the String format.

(2) If **content-Type** is **text/xml**, this field is usually in the String format.

(3) If **content-Type** is **application/json**, this field is usually in the Object format.

(4) If **content-Type** is **application/octet-stream**, this field is usually in the ArrayBuffer format.

(5) If **content-Type** is **multipart/form-data** and the content to be uploaded is a file, this field is usually in the ArrayBuffer format.

The preceding information is for reference only and may vary according to the actual situation.

- If the HTTP request uses the GET, OPTIONS, TRACE, or CONNECT method, this parameter serves as a supplement to  
HTTP request parameters. Parameters of the string type need to be encoded before being passed to the HTTP request. Parameters of the object type do not need to be precoded and will be directly concatenated to the URL. Parameters of the ArrayBuffer type will not be concatenated to the URL.

**Type:** string &#124; Object &#124; ArrayBuffer

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## header

```TypeScript
header?: Object
```

HTTP request header. If the request method is POST, PUT, DELETE, or null, the default value is {'content-Type': 'application/json'}. Otherwise, the default value is {'content-Type': 'application/x-www-form-urlencoded'}.

If the header contains fields of numeric type, the maximum value must be an int64 integer.

The header field supports the JSON format (as shown in [Example](../../../reference/apis-network-kit/js-apis-http.md#example)) and the Record&lt;string, string&gt; format.

**Type:** Object

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## inactivityMs

```TypeScript
inactivityMs?: number
```

Maximum idle time of a connection in the connection pool. If this value is exceeded, the connection is closed. The unit is ms. The default value is 118s. The system calculates the connection idle time, rounds it down to seconds, and then compares it with the configured value.

- The value range is (0, 2147483647]. If a value less than or equal to 0 is passed, the system uses the default  
value 118s. This parameter does not take effect when **reuseConnections** is set to **false**.

**Since**: 26.0.0

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## maxLimit

```TypeScript
maxLimit?: number
```

Maximum number of bytes in a response.

The default value is 5*1024*1024, in bytes. The maximum value is **100*1024*1024**.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## maxRedirects

```TypeScript
maxRedirects?: number
```

The maximum number of redirections can be specified for HttpRequest.

- The default value is 30.  
- The value range is [0, 2147483647]. If the value is set to **0**, redirection is disabled. If the number of  
redirections on the server exceeds the maximum number of redirections, error code 2300047 is returned. If the value is out of the range, the default value **30** takes effect.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.Communication.NetStack

## method

```TypeScript
method?: RequestMethod
```

Request method. The default value is **GET**.

**Type:** [RequestMethod](arkts-network-http-requestmethod-e.md)

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## multiFormDataList

```TypeScript
multiFormDataList?: Array<MultiFormData>
```

Form data list. This field is valid when **content-Type** is set to **multipart/form-data**.

**Type:** Array&lt;[MultiFormData](arkts-network-http-multiformdata-i.md)&gt;

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## pathPreference

```TypeScript
pathPreference?: PathPreference
```

Used to specify the network to be activated in an HTTP request.

**Type:** [PathPreference](arkts-network-http-pathpreference-t.md)

**Since:** 23

**System capability:** SystemCapability.Communication.NetStack

## priority

```TypeScript
priority?: number
```

Priority of concurrent HTTP/HTTPS requests. A larger value indicates a higher priority. The value range is [1, 1000]. The default value is **1**.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## queryParams

```TypeScript
queryParams?: string | QueryParamObject
```

Request parameters appended to the URL.

- The value can be a string or a **QueryParamObject**. A string is directly appended to the URL (without repeated  
encoding). A **QueryParamObject** is automatically encoded and serialized by the system.  
- When a string is used, the leading **?** is not required. Use **&** to separate multiple parameters.  
- If both **queryParams** and **extraData** are configured, **queryParams** takes precedence, and the URL  
parameter supplementation logic in **extraData** is ignored.

**Since**: 26.0.0

**Type:** string &#124; [QueryParamObject](arkts-network-http-queryparamobject-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## readTimeout

```TypeScript
readTimeout?: number
```

Read timeout duration. The default value is **60000**, in ms. The input value must be an uint32_t integer.

The value **0** indicates no timeout.

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## remoteValidation

```TypeScript
remoteValidation?: RemoteValidation
```

Certificate authority (CA), which is used to verify the identity of a remote server. If the parameter is not set, the default value is used. The options are as follows:

**Type:** [RemoteValidation](arkts-network-http-remotevalidation-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.NetStack

## resumeFrom

```TypeScript
resumeFrom?: number
```

Download start position. This field can be used only for the GET method. As stipulated in section 3.1 of RFC 7233, servers are allowed to ignore range requests.

- If the HTTP PUT method is used, do not use this option because it may conflict with other options.  
- The value ranges from **1** to **4294967296** (4 GB). If the value is out of this range, this field does not  
take effect.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## resumeTo

```TypeScript
resumeTo?: number
```

Download end position. This field can be used only for the GET method. As stipulated in section 3.1 of RFC 7233, servers are allowed to ignore range requests.

- If the HTTP PUT method is used, do not use this option because it may conflict with other options.  
- The value ranges from **1** to **4294967296** (4 GB). If the value is out of this range, this field does not  
take effect.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## reuseConnections

```TypeScript
reuseConnections?: boolean
```

Whether to reuse the connection for an HTTP request. The default value is **true**, meaning to reuse the existing connection. The value **false** means the opposite. This field can be used together with the **inactivityMs** field to customize the connection timeout interval.

- Connection reuse means that after an HTTP request is completed, the underlying TCP connection is not  
immediately closed. Instead, it remains in the connection pool. If subsequent HTTP requests have the same target address, the connection can be reused, reducing the overhead of TCP and TLS handshakes and improving performance.

**Since**: 26.0.0

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## serverAuthentication

```TypeScript
serverAuthentication?: ServerAuthentication
```

Whether to verify the server identity during a secure connection. The identity is not verified by default.

**Type:** [ServerAuthentication](arkts-network-http-serverauthentication-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.NetStack

## sniHostName

```TypeScript
sniHostName?: string
```

Used to allow the client to declare the target domain name to the server in the TLS handshake phase by configuring the server name indication (SNI). In this way, the server can select the corresponding SSL/TLS certificate based on the domain name for encrypted communication.

- The default value is an empty string. The value of **sniHostName** can contain a maximum of 255 characters. If  
the length limit is exceeded or the value is an empty string, the setting does not take effect.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Communication.NetStack

## sslType

```TypeScript
sslType?: SslType
```

Security communication protocol. You can use TLS (default) or TLCP. If TLCP is used, the related options (such as **caPath**, **clientCert**, and **clientEncCert**) must be set to valid values.

**Type:** [SslType](arkts-network-http-ssltype-t.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Communication.NetStack

## tlsOptions

```TypeScript
tlsOptions?: TlsOptions
```

TLS configuration.

**Type:** [TlsOptions](arkts-network-http-tlsoptions-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.NetStack

## usingCache

```TypeScript
usingCache?: boolean
```

Whether to use the cache. The value **true** indicates that the cache is preferentially read when a request is initiated, and the value **false** indicates that the cache is not used. The default value is **true**. The cache function takes effect when the process is started. The new cached data will replace the existing cached data.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## usingProtocol

```TypeScript
usingProtocol?: HttpProtocol
```

Protocol. The default value is automatically specified by the system.

**Type:** [HttpProtocol](arkts-network-http-httpprotocol-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## usingProxy

```TypeScript
usingProxy?: boolean | HttpProxy
```

HTTP proxy configuration. If this item is not configured, the system proxy is used by default.

- If **usingProxy** is set to **true**, the default network proxy is used. If **usingProxy** is set to **false**,  
no proxy is used.  
- If **usingProxy** is of the **HttpProxy** type, the specified network proxy is used. The HttpProxy supports the  
**username** and **password** fields from API version 22.

**Type:** boolean &#124; [HttpProxy](arkts-network-http-httpproxy-t.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## usingSocks5Proxy

```TypeScript
usingSocks5Proxy?: Socks5Proxy
```

Specifies the use of a SOCKS5 proxy. Note that this configuration takes precedence over usingProxy. It is recommended not to configure both simultaneously.

**Type:** [Socks5Proxy](arkts-network-http-socks5proxy-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack
