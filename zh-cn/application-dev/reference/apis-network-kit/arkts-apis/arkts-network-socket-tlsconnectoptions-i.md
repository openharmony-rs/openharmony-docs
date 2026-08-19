# TLSConnectOptions

TLS连接的操作。

**起始版本：** 9

<!--Device-socket-export interface TLSConnectOptions--><!--Device-socket-export interface TLSConnectOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## ALPNProtocols

```TypeScript
ALPNProtocols?: Array<string>
```

ALPN协议，支持["spdy/1", "http/1.1"]，默认为[]。

**类型：** Array&lt;string&gt;

**起始版本：** 9

<!--Device-TLSConnectOptions-ALPNProtocols?: Array<string>--><!--Device-TLSConnectOptions-ALPNProtocols?: Array<string>-End-->

**系统能力：** SystemCapability.Communication.NetStack

## address

```TypeScript
address: NetAddress
```

网关地址。

**类型：** NetAddress

**起始版本：** 9

<!--Device-TLSConnectOptions-address: NetAddress--><!--Device-TLSConnectOptions-address: NetAddress-End-->

**系统能力：** SystemCapability.Communication.NetStack

## proxy

```TypeScript
proxy?: ProxyOptions
```

使用的代理信息，默认不使用代理。

**类型：** [ProxyOptions](arkts-network-socket-proxyoptions-i.md)

**起始版本：** 18

<!--Device-TLSConnectOptions-proxy?: ProxyOptions--><!--Device-TLSConnectOptions-proxy?: ProxyOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## secureOptions

```TypeScript
secureOptions: TLSSecureOptions
```

TLS安全相关操作。

**类型：** [TLSSecureOptions](arkts-network-socket-tlssecureoptions-i.md)

**起始版本：** 9

<!--Device-TLSConnectOptions-secureOptions: TLSSecureOptions--><!--Device-TLSConnectOptions-secureOptions: TLSSecureOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## skipRemoteValidation

```TypeScript
skipRemoteValidation?: boolean
```

是否跳过对服务端进行证书认证，默认为false。true：跳过对服务端进行证书认证；false：不跳过对服务端进行证书认证。

**类型：** boolean

**起始版本：** 12

<!--Device-TLSConnectOptions-skipRemoteValidation?: boolean--><!--Device-TLSConnectOptions-skipRemoteValidation?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

## timeout

```TypeScript
timeout?: int
```

连接超时时间，单位：ms，默认为0。传入值需为0-4294967295范围内的整数。TLSSocket连接在超时后会失败。

**类型：** int

**起始版本：** 22

<!--Device-TLSConnectOptions-timeout?: int--><!--Device-TLSConnectOptions-timeout?: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

