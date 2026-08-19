# HttpRequestOptions

发起HTTP请求时，可选配置信息。

**起始版本：** 23

<!--Device-http-export interface HttpRequestOptions--><!--Device-http-export interface HttpRequestOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## addressFamily

```TypeScript
addressFamily?: AddressFamily
```

支持解析目标域名时限定地址类型。

**类型：** [AddressFamily](arkts-network-http-addressfamily-e.md)

**起始版本：** 15

<!--Device-HttpRequestOptions-addressFamily?: AddressFamily--><!--Device-HttpRequestOptions-addressFamily?: AddressFamily-End-->

**系统能力：** SystemCapability.Communication.NetStack

## body

```TypeScript
body?: string | Object | ArrayBuffer
```

HTTP请求体内容。设置该字段后，框架会优先将该字段作为请求体发送。 - 支持string、Object、ArrayBuffer三种类型：string按原值发送，Object会序列化后发送，ArrayBuffer按二进制发送。 - 当body与extraData同时配置时，body优先，extraData会被忽略。 - 可与任意请求方法搭配使用，用于显式指定请求体。

**类型：** string \| Object \| ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HttpRequestOptions-body?: string | Object | ArrayBuffer--><!--Device-HttpRequestOptions-body?: string | Object | ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NetStack

## caData

```TypeScript
caData?: string
```

如果设置了此参数且证书有效，系统将使用用户指定的CA证书和系统预设的CA证书；否则仅使用系统预设的CA证书。如果同时设置了caPath和caData，caData将被系统忽略。目前仅支持传入.pem格式的证书内容，最大长度为8 000字节。仅支持传入单证书，不支持证书链传入。 系统预设CA证书位置：/etc/ssl/certs/cacert.pem。证书路径为沙箱映射路径（开发者可通过UIAbilityContext提供的能力获取应用沙箱路径）。

**类型：** string

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-caData?: string--><!--Device-HttpRequestOptions-caData?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## caPath

```TypeScript
caPath?: string
```

如果设置了此参数且证书有效，系统将使用用户指定的CA证书和系统预设的CA证书；否则仅使用系统预设的CA证书。CA证书路径为沙箱映射路径（开发者可通过 [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md)提供的能力获取应用沙箱路径）。目前仅支持后缀名为.pem的文本格式证书。 系统预设CA证书位置：/etc/ssl/certs/cacert.pem。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-caPath?: string--><!--Device-HttpRequestOptions-caPath?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## certificatePinning

```TypeScript
certificatePinning?: CertificatePinning | CertificatePinning[]
```

支持动态设置证书锁定配置，可以传入单个或多个证书PIN码。

**类型：** [CertificatePinning](arkts-network-http-certificatepinning-i.md) \| [CertificatePinning](arkts-network-http-certificatepinning-i.md)[]

**起始版本：** 12

<!--Device-HttpRequestOptions-certificatePinning?: CertificatePinning | CertificatePinning[]--><!--Device-HttpRequestOptions-certificatePinning?: CertificatePinning | CertificatePinning[]-End-->

**系统能力：** SystemCapability.Communication.NetStack

## clientCert

```TypeScript
clientCert?: ClientCert
```

支持传输客户端证书。

**类型：** ClientCert

**起始版本：** 23

<!--Device-HttpRequestOptions-clientCert?: ClientCert--><!--Device-HttpRequestOptions-clientCert?: ClientCert-End-->

**系统能力：** SystemCapability.Communication.NetStack

## clientEncCert

```TypeScript
clientEncCert?: ClientCert
```

支持应用程序传入客户端证书，使服务器能够进行验证客户端的加密身份。

**类型：** ClientCert

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-clientEncCert?: ClientCert--><!--Device-HttpRequestOptions-clientEncCert?: ClientCert-End-->

**系统能力：** SystemCapability.Communication.NetStack

## connectTimeout

```TypeScript
connectTimeout?: int
```

连接超时时间。单位为毫秒（ms），默认为60000ms。传入值需为uint32_t范围内的整数。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-connectTimeout?: int--><!--Device-HttpRequestOptions-connectTimeout?: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## customMethod

```TypeScript
customMethod?: string
```

支持自定义请求方法，例如实现WebDAV扩展协议，当与method同时配置时，customMethod优先级更高。 - 默认值为空字符串，最大长度128个字符，超出则不生效。 - 当customMethod符合WebDAV扩展协议请求方式，但服务器不支持时，本次请求的服务器响应码通常为405或501（实际结果与服务器具体行为有关）。 - 当customMethod不符合WebDAV扩展协议请求方式时，本次请求的服务器响应码通常为400或405（实际结果与服务器具体行为有关）。

**类型：** string

**起始版本：** 23

<!--Device-HttpRequestOptions-customMethod?: string--><!--Device-HttpRequestOptions-customMethod?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## dnsOverHttps

```TypeScript
dnsOverHttps?: string
```

设置使用HTTPS协议的服务器进行DNS解析。 - 参数必须根据以下格式进行URL编码："https:// host:port/path"。

**类型：** string

**起始版本：** 11

<!--Device-HttpRequestOptions-dnsOverHttps?: string--><!--Device-HttpRequestOptions-dnsOverHttps?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## dnsServers

```TypeScript
dnsServers?: Array<string>
```

设置指定的DNS服务器进行DNS解析。 - 最多可以设置3个DNS解析服务器。如果有3个以上，只取前3个。 - 服务器必须是IPV4或者IPV6地址。

**类型：** Array&lt;string&gt;

**起始版本：** 11

<!--Device-HttpRequestOptions-dnsServers?: Array<string>--><!--Device-HttpRequestOptions-dnsServers?: Array<string>-End-->

**系统能力：** SystemCapability.Communication.NetStack

## enablePartialChain

```TypeScript
enablePartialChain?: boolean
```

是否允许在证书链验证时使用信任库中的中间CA证书作为信任锚点。设置为false时，证书链必须逐级验证至受信任的根CA证书。设置为true时，若信任库中存在中间CA证书，则证书链验证到该中间CA时即可视为通过，无需继续追溯至根 CA证书。当[SslType](arkts-network-http-ssltype-t.md)使用默认值或设置为TLS时，默认值为true；当[SslType](arkts-network-http-ssltype-t.md)设置为TLCP时，默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HttpRequestOptions-enablePartialChain?: boolean--><!--Device-HttpRequestOptions-enablePartialChain?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

## expectDataType

```TypeScript
expectDataType?: HttpDataType
```

指定返回数据的类型，默认无此字段。如果设置了此参数，系统将优先返回指定的类型。当指定其类型为Object时，最大长度为65536字符数。

**类型：** [HttpDataType](arkts-network-http-httpdatatype-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-expectDataType?: HttpDataType--><!--Device-HttpRequestOptions-expectDataType?: HttpDataType-End-->

**系统能力：** SystemCapability.Communication.NetStack

## extraData

```TypeScript
extraData?: string | Object | ArrayBuffer
```

发送请求的额外数据，默认无此字段。自API version 26开始，建议优先使用body和queryParams字段。 **说明：** 没有额外数据时，避免添加该参数；若必须添加，请填写undefined或者null，避免直接传入"。 1. 当HTTP请求为POST、PUT、DELETE等方法时，此字段为HTTP请求的content，以UTF-8编码形式作为请求体。 示例如下： (1) 当'content-Type'为'application/x-www-form-urlencoded'时，请求提交的信息主体数据必须在key和value进行URL转码后（encodeURIComponent/ encodeURI），按照键值对"key1=value1&key2=value2&key3=value3"的方式进行编码，该字段对应的类型通常为String。 (2) 当'content-Type'为'text/xml'时，该字段对应的类型通常为String。 (3) 当'content-Type'为'application/json'时，该字段对应的类型通常为Object。 (4) 当'content-Type'为'application/octet-stream'时，该字段对应的类型通常为ArrayBuffer。 (5) 当'content-Type'为'multipart/form-data'且需上传的字段为文件时，该字段对应的类型通常为ArrayBuffer。 以上信息仅供参考，并可能根据具体情况有所不同。 2. 当HTTP请求为GET、OPTIONS、TRACE、CONNECT等方法时，此字段为HTTP请求参数的补充。开发者需传入Encode编码后的string类型参数，Object类型的参数无需预编码，参数内容会拼接到URL中进行发送。ArrayBuffer类型的参数不会做拼接处理。

**类型：** string \| Object \| ArrayBuffer

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-extraData?: string | Object | ArrayBuffer--><!--Device-HttpRequestOptions-extraData?: string | Object | ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NetStack

## header

```TypeScript
header?: Object
```

HTTP请求头字段。当请求方式为"POST" "PUT" "DELETE" 或者""时，默认{'content-Type': 'application/json'}， 否则默认{'content-Type': ' application/x-www-form-urlencoded'}。 如果head中包含number类型的字段，最大支持int64的整数。 header字段支持JSON格式如 完整示例 和Record&lt;string, string&gt;格式输入。

**类型：** Object

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-header?: Object--><!--Device-HttpRequestOptions-header?: Object-End-->

**系统能力：** SystemCapability.Communication.NetStack

## inactivityMs

```TypeScript
inactivityMs?: int
```

连接池中的连接最大空闲时间，超过该时间后连接将被关闭。单位为毫秒（ms），默认配置值为118秒。系统内部比较时间时会先计算连接空闲时间的差值，然后向下取整到秒，再与配置的值进行比较。 - 取值范围是(0, 2147483647]，传入小于等于0的数值时系统使用默认值118秒。当reuseConnections配置为false时，该参数不生效。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HttpRequestOptions-inactivityMs?: int--><!--Device-HttpRequestOptions-inactivityMs?: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## maxLimit

```TypeScript
maxLimit?: int
```

响应消息的最大字节限制。 默认值为5*1024*1024，以Byte为单位。最大值为100*1024*1024，以Byte为单位。

**类型：** int

**起始版本：** 11

<!--Device-HttpRequestOptions-maxLimit?: int--><!--Device-HttpRequestOptions-maxLimit?: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## maxRedirects

```TypeScript
maxRedirects?: int
```

支持针对HttpRequest指定最大跳转次数。 - 默认值为30次。 - 取值范围是：[0，2147483647]，设置0即为关闭重定向，当服务器的重定向次数超过设置的最大重定向次数时会返回错误码2300047。超出此范围该配置不生效，配置默认值30。

**类型：** int

**起始版本：** 23

<!--Device-HttpRequestOptions-maxRedirects?: int--><!--Device-HttpRequestOptions-maxRedirects?: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## method

```TypeScript
method?: RequestMethod
```

请求方式，默认为GET。

**类型：** [RequestMethod](arkts-network-http-requestmethod-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-method?: RequestMethod--><!--Device-HttpRequestOptions-method?: RequestMethod-End-->

**系统能力：** SystemCapability.Communication.NetStack

## multiFormDataList

```TypeScript
multiFormDataList?: Array<MultiFormData>
```

当'content-Type'为'multipart/form-data'时，则上传该字段定义的数据字段表单列表。

**类型：** Array&lt;[MultiFormData](arkts-network-http-multiformdata-i.md)&gt;

**起始版本：** 23

<!--Device-HttpRequestOptions-multiFormDataList?: Array<MultiFormData>--><!--Device-HttpRequestOptions-multiFormDataList?: Array<MultiFormData>-End-->

**系统能力：** SystemCapability.Communication.NetStack

## pathPreference

```TypeScript
pathPreference?: PathPreference
```

支持HTTP请求指定特定激活的网络。

**类型：** [PathPreference](arkts-network-http-pathpreference-t.md)

**起始版本：** 23

<!--Device-HttpRequestOptions-pathPreference?: PathPreference--><!--Device-HttpRequestOptions-pathPreference?: PathPreference-End-->

**系统能力：** SystemCapability.Communication.NetStack

## priority

```TypeScript
priority?: int
```

HTTP/HTTPS请求并发优先级，值越大优先级越高，范围[1,1000]，默认为1，超出范围将设置为默认值。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-priority?: int--><!--Device-HttpRequestOptions-priority?: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## queryParams

```TypeScript
queryParams?: string | QueryParamObject
```

附加到URL中的请求参数。 - 支持string和QueryParamObject两种形式：string会按原样拼接到URL（不重复编码）；QueryParamObject会由系统自动编码并序列化。 - 使用string时不需要携带前导`?`，多个参数用`&`分隔。 - 当queryParams与extraData同时配置时，queryParams优先，extraData中的URL参数补充逻辑会被忽略。

**类型：** string \| [QueryParamObject](arkts-network-http-queryparamobject-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HttpRequestOptions-queryParams?: string | QueryParamObject--><!--Device-HttpRequestOptions-queryParams?: string | QueryParamObject-End-->

**系统能力：** SystemCapability.Communication.NetStack

## readTimeout

```TypeScript
readTimeout?: int
```

读取超时时间。单位为毫秒（ms），默认为60000ms。传入值需为uint32_t范围内的整数。 设置为0表示不会出现超时情况。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-readTimeout?: int--><!--Device-HttpRequestOptions-readTimeout?: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## remoteValidation

```TypeScript
remoteValidation?: RemoteValidation
```

证书颁发机构（CA），用于验证远程服务器的身份。如果未设置此字段，系统CA将用于验证远程服务器的标识。

**类型：** [RemoteValidation](arkts-network-http-remotevalidation-t.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-remoteValidation?: RemoteValidation--><!--Device-HttpRequestOptions-remoteValidation?: RemoteValidation-End-->

**系统能力：** SystemCapability.Communication.NetStack

## resumeFrom

```TypeScript
resumeFrom?: long
```

用于设置下载起始位置，该参数只能用于GET方法，不能用于其他。HTTP标准（RFC 7233第3.1节）允许服务器忽略范围请求。 - 使用HTTP PUT时，不能使用该选项，因为该选项可能与其他选项冲突。 - 取值范围是：[1，4294967296（4GB）]，超出范围则不生效。

**类型：** long

**起始版本：** 11

<!--Device-HttpRequestOptions-resumeFrom?: long--><!--Device-HttpRequestOptions-resumeFrom?: long-End-->

**系统能力：** SystemCapability.Communication.NetStack

## resumeTo

```TypeScript
resumeTo?: long
```

用于设置下载结束位置，该参数只能用于GET方法，不能用于其他。HTTP标准（RFC 7233第3.1节）允许服务器忽略范围请求。 - 使用HTTP PUT时，不能使用该选项，因为该选项可能与其他选项冲突。 - 取值范围是：[1，4294967296（4GB）]，超出范围则不生效。

**类型：** long

**起始版本：** 11

<!--Device-HttpRequestOptions-resumeTo?: long--><!--Device-HttpRequestOptions-resumeTo?: long-End-->

**系统能力：** SystemCapability.Communication.NetStack

## reuseConnections

```TypeScript
reuseConnections?: boolean
```

HTTP请求是否复用连接。默认值为true，表示复用已有的连接；设置为false时，每次请求将建立新的连接，不再复用已有连接。本字段可与inactivityMs字段搭配使用，自定义连接超时关闭时间。 - 连接复用是指在完成一次HTTP请求后，底层的TCP连接不会被立即关闭，而是保持在连接池中，后续的HTTP请求如果目标地址相同，可以重用该连接，从而减少TCP握手和TLS握手的开销，提高性能。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HttpRequestOptions-reuseConnections?: boolean--><!--Device-HttpRequestOptions-reuseConnections?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

## serverAuthentication

```TypeScript
serverAuthentication?: ServerAuthentication
```

安全连接期间的服务器身份验证配置。默认不认证。

**类型：** [ServerAuthentication](arkts-network-http-serverauthentication-i.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-serverAuthentication?: ServerAuthentication--><!--Device-HttpRequestOptions-serverAuthentication?: ServerAuthentication-End-->

**系统能力：** SystemCapability.Communication.NetStack

## sniHostName

```TypeScript
sniHostName?: string
```

支持客户端通过配置SNI（Server Name Indication，服务器名称指示）在TLS握手阶段向服务器声明目标域名，使服务器能够根据域名选择对应的SSL/TLS证书进行加密通信。 - 默认值为空字符串，sniHostName参数长度上限为255个字符。若超出长度限制或设置为空字符串，该设置将不会生效。

**类型：** string

**起始版本：** 23

<!--Device-HttpRequestOptions-sniHostName?: string--><!--Device-HttpRequestOptions-sniHostName?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## sslType

```TypeScript
sslType?: SslType
```

使用安全通信协议TLS（默认）或TLCP。如果使用TLCP，相关的选项（如caPath、clientCert和clientEncCert）必须赋有效值。

**类型：** SslType

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-sslType?: SslType--><!--Device-HttpRequestOptions-sslType?: SslType-End-->

**系统能力：** SystemCapability.Communication.NetStack

## tlsOptions

```TypeScript
tlsOptions?: TlsOptions
```

TLS配置。

**类型：** [TlsOptions](arkts-network-http-tlsoptions-t.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-tlsOptions?: TlsOptions--><!--Device-HttpRequestOptions-tlsOptions?: TlsOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## usingCache

```TypeScript
usingCache?: boolean
```

是否使用缓存，true表示请求时优先读取缓存，false表示不使用缓存；默认为true，请求时优先读取缓存。缓存跟随当前进程生效，新缓存会替换旧缓存。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-usingCache?: boolean--><!--Device-HttpRequestOptions-usingCache?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

## usingProtocol

```TypeScript
usingProtocol?: HttpProtocol
```

HTTP请求使用的协议版本。未指定时，由系统自动协商最适合的协议版本。若指定HTTP3，由于HTTP3协议的安全限制，需通过[TlsConfig](arkts-network-http-tlsconfig-i.md)指定TLS 版本为1.3，且目标域名 支持HTTP3协议，才能启用HTTP3，否则将协商降级。

**类型：** [HttpProtocol](arkts-network-http-httpprotocol-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-usingProtocol?: HttpProtocol--><!--Device-HttpRequestOptions-usingProtocol?: HttpProtocol-End-->

**系统能力：** SystemCapability.Communication.NetStack

## usingProxy

```TypeScript
usingProxy?: boolean | HttpProxy
```

HTTP代理配置，该项不配置时默认使用系统代理。 - 当usingProxy为布尔类型true时，使用默认网络代理，为false时，不使用代理。 - 当usingProxy为HttpProxy类型时，使用指定网络代理。从API version 22开始，HttpProxy支持指定username和password字段。 - 从API version 26.0.0开始，当usingSocks5Proxy被正确配置时，usingProxy项不生效。

**类型：** boolean \| HttpProxy

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpRequestOptions-usingProxy?: boolean | HttpProxy--><!--Device-HttpRequestOptions-usingProxy?: boolean | HttpProxy-End-->

**系统能力：** SystemCapability.Communication.NetStack

## usingSocks5Proxy

```TypeScript
usingSocks5Proxy?: Socks5Proxy
```

SOCKS5代理配置，该项不配置时不启动SOCKS5代理。 当该项被正确配置时，如果同时配置了usingProxy，usingProxy不生效。

**类型：** Socks5Proxy

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HttpRequestOptions-usingSocks5Proxy?: Socks5Proxy--><!--Device-HttpRequestOptions-usingSocks5Proxy?: Socks5Proxy-End-->

**系统能力：** SystemCapability.Communication.NetStack

