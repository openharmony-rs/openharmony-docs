# OnClientAuthenticationEvent

定义当需要用户提供SSL客户端证书时触发回调。

**起始版本：** 12

<!--Device-unnamed-declare interface OnClientAuthenticationEvent--><!--Device-unnamed-declare interface OnClientAuthenticationEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler : ClientAuthenticationHandler
```

通知Web组件用户操作行为。

**类型：** ClientAuthenticationHandler

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnClientAuthenticationEvent-handler : ClientAuthenticationHandler--><!--Device-OnClientAuthenticationEvent-handler : ClientAuthenticationHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## host

```TypeScript
host : string
```

请求证书服务器的主机名。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnClientAuthenticationEvent-host : string--><!--Device-OnClientAuthenticationEvent-host : string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## issuers

```TypeScript
issuers : Array<string>
```

与私钥匹配的证书可接受颁发者。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnClientAuthenticationEvent-issuers : Array<string>--><!--Device-OnClientAuthenticationEvent-issuers : Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## keyTypes

```TypeScript
keyTypes : Array<string>
```

可接受的非对称密钥类型。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnClientAuthenticationEvent-keyTypes : Array<string>--><!--Device-OnClientAuthenticationEvent-keyTypes : Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## port

```TypeScript
port : number
```

请求证书服务器的端口号。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnClientAuthenticationEvent-port : number--><!--Device-OnClientAuthenticationEvent-port : number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

