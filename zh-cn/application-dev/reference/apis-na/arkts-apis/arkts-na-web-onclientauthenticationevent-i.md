# OnClientAuthenticationEvent

Defines the triggered callback when needs ssl client certificate from the user.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface OnClientAuthenticationEvent--><!--Device-unnamed-export declare interface OnClientAuthenticationEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: ClientAuthenticationHandler
```

Notifies the user of the operation behavior of the web component.

**类型：** [ClientAuthenticationHandler](arkts-na-web-clientauthenticationhandler-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnClientAuthenticationEvent-handler: ClientAuthenticationHandler--><!--Device-OnClientAuthenticationEvent-handler: ClientAuthenticationHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## host

```TypeScript
host: string
```

The hostname of the requesting certificate server.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnClientAuthenticationEvent-host: string--><!--Device-OnClientAuthenticationEvent-host: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## issuers

```TypeScript
issuers: Array<string>
```

Certificates that match the private key are acceptable to the issuer.

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnClientAuthenticationEvent-issuers: Array<string>--><!--Device-OnClientAuthenticationEvent-issuers: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## keyTypes

```TypeScript
keyTypes: Array<string>
```

Acceptable asymmetric key types.

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnClientAuthenticationEvent-keyTypes: Array<string>--><!--Device-OnClientAuthenticationEvent-keyTypes: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## port

```TypeScript
port: int
```

The port number of the request certificate server.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnClientAuthenticationEvent-port: int--><!--Device-OnClientAuthenticationEvent-port: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

