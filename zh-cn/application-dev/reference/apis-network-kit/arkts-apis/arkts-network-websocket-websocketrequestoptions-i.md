# WebSocketRequestOptions

建立WebSocket连接时，可选参数的类型和说明。

**起始版本：** 6

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## caPath

```TypeScript
caPath?: string
```

如果设置了此参数，系统将使用用户指定路径的CA证书，(开发者需保证该路径下CA证书的可访问性)，否则将使用系统预设CA证书，系统预设CA证书位置：/etc/ssl/certs/cacert.pem。证书路径为沙箱映射路径（开发 者可通过UIAbilityContext提供的能力获取应用沙箱路径）。目前仅支持格式为pem的文本证书。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## clientCert

```TypeScript
clientCert?: ClientCert
```

支持传输客户端证书。

**类型：** ClientCert

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## header

```TypeScript
header?: Object
```

建立WebSocket连接可选参数，代表建立连接时携带的HTTP头信息。参数内容自定义，也可以不指定。

**类型：** Object

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## minSupportTlsProtocol

```TypeScript
minSupportTlsProtocol?: TlsProtocol
```

自定义支持的最低TLS协议版本。例如：设置该参数为TLS_V_1_1，则客户端可支持TLS协议版本有TLS1.1、TLS1.2、TLS1.3。

**类型：** [TlsProtocol](arkts-network-websocket-tlsprotocol-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## pingInterval

```TypeScript
pingInterval?: number
```

自定义[心跳检测](../../../network/websocket-connection.md#场景介绍)时间，默认为30s。每pingInterval周期会发起心跳检测，设置为0则表示关闭心跳检测。最大值：30000 s，最小值：0s。

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.Communication.NetStack

## pongTimeout

```TypeScript
pongTimeout?: number
```

自定义发起心跳检测后，超时断开时间，默认为30s。发起心跳检测后若pongTimeout时间未响应则断开连接。最大值：30000s，最小值：0s。pongTimeout须小于等于pingInterval。

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.Communication.NetStack

## protocol

```TypeScript
protocol?: string
```

自定义Sec-WebSocket-Protocol字段，默认为""。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetStack

## proxy

```TypeScript
proxy?: ProxyConfiguration
```

通信过程中的代理信息，默认使用系统网络代理。

**类型：** [ProxyConfiguration](arkts-network-websocket-proxyconfiguration-t.md)

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetStack

## skipServerCertVerification

```TypeScript
skipServerCertVerification?: boolean
```

是否跳过服务器证书验证。true表示跳过服务器证书验证，false表示不跳过服务器证书验证。默认为false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetStack

## supportOriginPort

```TypeScript
supportOriginPort?: boolean
```

支持源端口的选项。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack
