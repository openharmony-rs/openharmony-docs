# @ohos.net.http(数据请求)

本模块提供HTTP数据请求能力。应用可以通过HTTP发起一个数据请求，支持常见的GET、POST、OPTIONS、HEAD、PUT、DELETE、PATCH、TRACE、CONNECT方法。

**起始版本：** 6

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createHttp](arkts-network-http-createhttp-f.md) | 创建一个HTTP请求，里面包括发起请求、中断请求、订阅/取消订阅HTTP Response Header事件。当发起多个HTTP请求时，需为每个HTTP请求创建对应HttpRequest对象。每一个HttpRequest对象对应一个HTTP请求。 |
| [createHttpResponseCache](arkts-network-http-createhttpresponsecache-f.md) | 创建一个HttpResponseCache对象，可用于存储HTTP请求的响应数据。对象中可调用[flush](arkts-network-http-httpresponsecache-i.md#flush)与[delete](arkts-network-http-httpresponsecache-i.md#delete)方法，cacheSize指定缓存大小。 |

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
| [HttpRequestContext](arkts-network-http-httprequestcontext-i.md) | HTTP请求上下文数据。该对象实例在拦截器的[interceptorHandle](arkts-network-http-httpinterceptor-i.md#interceptorhandle)方法中作为参数传入，开发者可以通过该对象获取和修改HTTP请求的相关信息。 |
| [HttpRequestOptions](arkts-network-http-httprequestoptions-i.md) | 发起HTTP请求时，可选配置信息。 |
| [HttpResponse](arkts-network-http-httpresponse-i.md) | request方法回调函数的返回值类型。 |
| [HttpResponseCache](arkts-network-http-httpresponsecache-i.md) | 存储HTTP访问请求响应的对象。在调用HttpResponseCache的方法前，需要先通过[createHttpResponseCache()](arkts-network-http-createhttpresponsecache-f.md)创建一个任务。 |
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
| [HttpDataType](arkts-network-http-httpdatatype-e.md) | HTTP的数据类型。 |
| [HttpProtocol](arkts-network-http-httpprotocol-e.md) | HTTP协议版本。 |
| [InterceptorType](arkts-network-http-interceptortype-e.md) | HTTP拦截器的类型枚举。 |
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
| [ValidationCallback](arkts-network-http-validationcallback-t.md) | 自定义远程验证。该API使用Promise异步返回结果。 |
| [X509Cert](arkts-network-http-x509cert-t.md) | X509证书 |
