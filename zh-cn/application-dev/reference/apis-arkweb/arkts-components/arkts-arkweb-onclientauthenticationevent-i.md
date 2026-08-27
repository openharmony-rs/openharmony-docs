# OnClientAuthenticationEvent

定义需要提供SSL客户端证书时触发的回调信息，包括主机、端口和密钥类型。适用于需要处理客户端证书认证的场景，提升认证流程的灵活性和安全性。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## handler

```TypeScript
handler : ClientAuthenticationHandler
```

通知Web组件用户操作行为。

**类型：** [ClientAuthenticationHandler](arkts-arkweb-clientauthenticationhandler-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## host

```TypeScript
host : string
```

请求证书服务器的主机名。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## issuers

```TypeScript
issuers : Array<string>
```

与私钥匹配的证书可接受颁发者。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## keyTypes

```TypeScript
keyTypes : Array<string>
```

可接受的非对称密钥类型。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## port

```TypeScript
port : number
```

请求证书服务器的端口号。有效范围为0-65535，超出范围时抛出异常。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
