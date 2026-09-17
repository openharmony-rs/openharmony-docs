# ConnectionExtraInfo

HTTP请求交互的详细信息。

**起始版本：** 24

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## cipherSuite

```TypeScript
cipherSuite?: CipherSuite
```

request请求过程中的加密套件。只有当使用TLS协议时返回相应的加密套件。

**类型：** [CipherSuite](arkts-network-http-ciphersuite-t.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## isCacheHit

```TypeScript
isCacheHit: boolean
```

request请求过程中是否命中本地缓存。true表示命中本地缓存，false表示未命中本地缓存。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## isProxyConnection

```TypeScript
isProxyConnection: boolean
```

request请求过程中是否使用代理。true表示使用代理，false表示未使用代理。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## isReusedConnection

```TypeScript
isReusedConnection: boolean
```

request请求过程中是否复用连接。true表示新建连接，false表示复用连接。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## localAddress

```TypeScript
localAddress: string
```

request请求过程中的客户端IP地址。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## localPort

```TypeScript
localPort: number
```

request请求过程中的客户端端口，取值范围[1, 65535]。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## networkProtocolName

```TypeScript
networkProtocolName: string
```

[request](arkts-network-http-httprequest-i.md#request)请求过程中的HTTP协议版本，如'HTTP/1.0'，'HTTP/1.1'，'HTTP/2'，'HTTP/2 over TLS'，'HTTP/3'，'Unknown/Non-HTTP'等。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## redirectCount

```TypeScript
redirectCount: number
```

request请求过程中的重定向次数。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## remoteAddress

```TypeScript
remoteAddress: string
```

request请求过程中的服务端IP地址。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## remotePort

```TypeScript
remotePort: number
```

request请求过程中的服务端端口，取值范围[1, 65535]。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## tlsVersion

```TypeScript
tlsVersion?: TlsVersion
```

request请求过程中的TLS协议版本。只有当使用TLS协议时返回相应的TLS版本。

**类型：** [TlsVersion](arkts-network-http-tlsversion-e.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack
