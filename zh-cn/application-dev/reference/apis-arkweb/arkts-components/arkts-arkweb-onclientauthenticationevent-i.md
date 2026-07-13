# OnClientAuthenticationEvent

定义当需要用户提供SSL客户端证书时触发回调。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler : ClientAuthenticationHandler
```

通知Web组件用户操作行为。

**类型：** ClientAuthenticationHandler

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## host

```TypeScript
host : string
```

请求证书服务器的主机名。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## issuers

```TypeScript
issuers : Array<string>
```

与私钥匹配的证书可接受颁发者。

**类型：** Array<string>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## keyTypes

```TypeScript
keyTypes : Array<string>
```

可接受的非对称密钥类型。

**类型：** Array<string>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## port

```TypeScript
port : number
```

请求证书服务器的端口号。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

