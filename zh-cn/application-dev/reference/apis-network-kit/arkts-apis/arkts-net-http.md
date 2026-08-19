# @ohos.net.http

本模块提供HTTP数据请求能力。应用可以通过HTTP发起一个数据请求，支持常见的GET、POST、OPTIONS、HEAD、PUT、DELETE、PATCH、TRACE、CONNECT方法。

**起始版本：** 23

<!--Device-unnamed-declare namespace http--><!--Device-unnamed-declare namespace http-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createHttp](arkts-network-http-createhttp-f.md) | 创建一个HTTP请求，里面包括发起请求、中断请求、订阅/取消订阅HTTP Response Header事件。当发起多个HTTP请求时，需为每个HTTP请求创建对应HttpRequest对象。每一个HttpRequest对象对应一 个HTTP请求。 |
| [createHttpResponseCache](arkts-network-http-createhttpresponsecache-f.md) | 创建一个HttpResponseCache对象，可用于存储HTTP请求的响应数据。对象中可调用 [flush](arkts-network-http-httpresponsecache-i.md#flush)与 [delete](arkts-network-http-httpresponsecache-i.md#delete)方法，cacheSize指定缓存大小。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [HttpInterceptorChain](arkts-network-http-httpinterceptorchain-c.md) | HTTP拦截器链。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CertificatePinning](arkts-network-http-certificatepinning-i.md) | 由应用配置的证书。 |
| [ClientCert](arkts-network-http-clientcert-i.md) | 客户端证书类型。 |
| [ConnectionExtraInfo](arkts-network-http-connectionextrainfo-i.md) | HTTP请求交互的详细信息。 |
| [Credential](arkts-network-http-credential-i.md) | 会话中服务器身份验证设置所使用的身份验证凭据，包括用户名和密码。 |
| [DataReceiveProgressInfo](arkts-network-http-datareceiveprogressinfo-i.md) | 数据接收信息。 |
| [DataSendProgressInfo](arkts-network-http-datasendprogressinfo-i.md) | 数据发送信息。 |
| [HttpInterceptor](arkts-network-http-httpinterceptor-i.md) | HTTP拦截器接口。用户可以实现此接口来定义拦截处理函数。 |
| [HttpRequest](arkts-network-http-httprequest-i.md) | HTTP请求任务。在调用HttpRequest的方法前，需要先通过[createHttp()](arkts-network-http-createhttp-f.md)创建一个任务。 |
| [HttpRequestContext](arkts-network-http-httprequestcontext-i.md) | HTTP请求上下文数据。该对象实例在拦截器的[interceptorHandle](arkts-network-http-httpinterceptor-i.md#interceptorhandle)方法中作为参数传入，开发者可以通过该对象获取和修改 HTTP请求的相关信息。 |
| [HttpRequestOptions](arkts-network-http-httprequestoptions-i.md) | 发起HTTP请求时，可选配置信息。 |
| [HttpResponse](arkts-network-http-httpresponse-i.md) | request方法回调函数的返回值类型。 |
| [HttpResponseCache](arkts-network-http-httpresponsecache-i.md) | 存储HTTP访问请求响应的对象。在调用HttpResponseCache的方法前，需要先通过[createHttpResponseCache()](arkts-network-http-createhttpresponsecache-f.md)创建一个任 务。 **响应头中的相应关键字使用** - **`Cache-Control`**：用于指定缓存策略，如`no-cache`, `no-store`, `max-age`, `public`, `private`等。 - **`Expires`**：指定资源的过期时间，格式为GMT时间。 - **`ETag`**：用于资源版本标识，客户端可以使用`If-None-Match`请求头来验证资源是否已更改。 - **`Last-Modified`**：指定资源最后修改时间，客户端可以使用`If-Modified-Since`请求头来验证资源是否已更改。 - **`Vary`**：指定哪些请求头的值会影响缓存的响应，用于区分不同的缓存版本。 使用这些关键字时，服务器端需要正确配置响应头，客户端则需要根据这些响应头来决定是否使用缓存的资源，以及如何验证资源是否是最新的。正确的缓存策略可以显著提高应用的性能和用户体验。 **如何设置Cache-Control头** `Cache-Control`为通用报头，但通常是在服务器端进行的，允许定义一个响应资源应该何时、如何被缓存以及缓存多长时间。以下是一些常用的`Cache-Control`指令及其含义： - **`no-cache`**：表示在使用缓存前，必须先去源服务器校验资源的有效性。如果资源未变更，则响应状态码为304(Not Modified)，不发送资源内容，使用缓存中的资源。如果资源已经过期，则响应状态码为200(OK )，并发送资源内容。 - **`no-store`**：表示不允许缓存资源，每次请求都必须从服务器获取资源。 - **`max-age`**：指定缓存的最大时间(以秒为单位)。例如，`Cache-Control: max-age=3600`表示缓存的有效期为1小时。 - **`public`**：表明响应可以被任何对象(包括：发送请求的客户端，代理服务器等)缓存。 - **`private`**：表明响应只能被单个用户缓存，不能作为共享缓存(即代理服务器不能缓存)。 - **`must-revalidate`**：表示必须在使用缓存前验证旧资源的状态，并且在缓存过期后，需要重新验证资源。 - **`no-transform`**：表示不允许代理服务器修改响应内容。 - **`proxy-revalidate`**：与`must-revalidate`类似，但仅适用于共享缓存。 - **`s-maxage`**：类似于`max-age`，但仅适用于共享缓存。 |
| [MultiFormData](arkts-network-http-multiformdata-i.md) | 多部分表单数据的类型。 |
| [PerformanceTiming](arkts-network-http-performancetiming-i.md) | 性能打点(单位：ms)。 |
| [ServerAuthentication](arkts-network-http-serverauthentication-i.md) | HTTP服务器身份验证。 |
| [TlsConfig](arkts-network-http-tlsconfig-i.md) | TLS加密版本及套件配置。 |
| [ValidationContext](arkts-network-http-validationcontext-i.md) | [ValidationCallback](arkts-network-http-validationcallback-t.md)的验证上下文 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AddressFamily](arkts-network-http-addressfamily-e.md) | 枚举，解析目标域名时限定的地址类型。 |
| [CertType](arkts-network-http-certtype-e.md) | 枚举，证书类型。 |
| [HttpDataType](arkts-network-http-httpdatatype-e.md) | HTTP的数据类型。 \| 名称 \| 值 \| 说明 \| \| ------------------ \| -- \| ----------- \| \| STRING \| 0 \| 字符串类型。 \| \| OBJECT \| 1 \| 对象类型。 \| \| ARRAY_BUFFER \| 2 \| 二进制数组类型。\| |
| [HttpProtocol](arkts-network-http-httpprotocol-e.md) | HTTP协议版本。 |
| [InterceptorType](arkts-network-http-interceptortype-e.md) | HTTP拦截器的类型枚举。 \| 名称 \| 值 \|说明 \| \| ------ \| --\|-------------------------------------- \| \| INITIAL_REQUEST \|'INITIAL_REQUEST' \|在初始HTTP请求组装完成后拦截。\| \| REDIRECTION \| 'REDIRECTION' \|当收到重定向响应时拦截。\| \| CACHE_CHECKED \| 'READ_CACHE' \|在检查并且命中HTTP缓存时拦截。\| \| NETWORK_CONNECT \| 'CONNECT_NETWORK' \|在网络请求将要发出前拦截。\| \| FINAL_RESPONSE \| 'FINAL_RESPONSE' \|在获取最终HTTP响应时拦截。\| |
| [RequestMethod](arkts-network-http-requestmethod-e.md) | HTTP 请求方法。 |
| [ResponseCode](arkts-network-http-responsecode-e.md) | 发起请求返回的响应码。 |
| [TlsVersion](arkts-network-http-tlsversion-e.md) | 枚举，TLS版本号。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AuthenticationType](arkts-network-http-authenticationtype-t.md) | 在会话中的服务器身份验证时可以设置使用不同的身份验证机制。 |
| [ChainContinue](arkts-network-http-chaincontinue-t.md) | 是否继续处理拦截器链。 |
| [CipherSuite](arkts-network-http-ciphersuite-t.md) | 加密套件声明函数。 |
| [HttpProxy](arkts-network-http-httpproxy-t.md) | 网络代理配置信息。 |
| [PathPreference](arkts-network-http-pathpreference-t.md) | HTTP请求指定特定网络的类型枚举。 |
| [QueryParamObject](arkts-network-http-queryparamobject-t.md) | 用于构造URL查询参数的键值对象类型。 |
| [QueryParamValue](arkts-network-http-queryparamvalue-t.md) | QueryParamObject中允许使用的单个参数值类型。 |
| [RemoteValidation](arkts-network-http-remotevalidation-t.md) | 验证远程服务器身份的方式。 |
| [Socks5Proxy](arkts-network-http-socks5proxy-t.md) | SOCKS5代理配置信息。 |
| [SslType](arkts-network-http-ssltype-t.md) | 安全通信协议。 |
| [TlsOptions](arkts-network-http-tlsoptions-t.md) | TLS配置。 |
| [TlsV10CipherSuite](arkts-network-http-tlsv10ciphersuite-t.md) | TLS1.0的加密套件声明函数。 |
| [TlsV10SpecificCipherSuite](arkts-network-http-tlsv10specificciphersuite-t.md) | TLS1.0及以上版本支持的加密套件。 |
| [TlsV11CipherSuite](arkts-network-http-tlsv11ciphersuite-t.md) | TLS1.1的加密套件声明函数，与TLS1.0的加密套件相同。 |
| [TlsV12CipherSuite](arkts-network-http-tlsv12ciphersuite-t.md) | TLS1.2的加密套件声明函数，支持TLS1.2版本，兼容TLS1.1版本。 |
| [TlsV12SpecificCipherSuite](arkts-network-http-tlsv12specificciphersuite-t.md) | TLS1.2及以上版本支持的加密套件。 |
| [TlsV13CipherSuite](arkts-network-http-tlsv13ciphersuite-t.md) | TLS1.3的加密套件声明函数，支持TLS1.3版本，兼容TLS1.2版本。 |
| [TlsV13SpecificCipherSuite](arkts-network-http-tlsv13specificciphersuite-t.md) | TLS1.3及以上版本支持的加密套件。 |
| [ValidationCallback](arkts-network-http-validationcallback-t.md) | 自定义远程验证。 该API使用Promise异步返回结果。 |
| [X509Cert](arkts-network-http-x509cert-t.md) | X509证书 |

