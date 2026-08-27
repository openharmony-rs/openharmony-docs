# TLSSecureOptions

TLS安全相关操作。当本地证书cert和私钥key不为空时，开启双向验证模式。cert和key其中一项为空时，开启单向验证模式。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## ca

```TypeScript
ca?: string | Array<string>
```

服务端的ca证书，用于认证校验服务端的数字证书。默认为系统预置CA证书&lt;sup&gt;12+&lt;/sup&gt;。最多支持设置1000本证书。

**类型：** string \| Array&lt;string&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## cert

```TypeScript
cert?: string | Array<string>
```

本地客户端的数字证书。从API Version 24开始支持传入数组，最多支持设置1000本证书。

**类型：** string \| Array&lt;string&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## cipherSuite

```TypeScript
cipherSuite?: string
```

通信过程中的加密套件，默认为"" 。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## isBidirectionalAuthentication

```TypeScript
isBidirectionalAuthentication?: boolean
```

用于设置双向认证，默认为false。true：设置双向认证；false：不设置双向认证。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetStack

## key

```TypeScript
key?: string
```

本地数字证书的私钥。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## password

```TypeScript
password?: string
```

读取私钥的密码。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## protocols

```TypeScript
protocols?: Protocol | Array<Protocol>
```

TLS的协议版本，默认为"TLSv1.2"。

**类型：** Protocol \| Array&lt;Protocol&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## signatureAlgorithms

```TypeScript
signatureAlgorithms?: string
```

通信过程中的签名算法，默认为"" 。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## useRemoteCipherPrefer

```TypeScript
useRemoteCipherPrefer?: boolean
```

优先使用对等方的密码套件。true：优先使用对等方的密码套件；false：不优先使用对等方的密码套件。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack
