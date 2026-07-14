# ClientAuthenticationHandler

Defines the client certificate request result, related to {@link onClientAuthenticationRequest} method.

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## cancel

```TypeScript
cancel(): void
```

取消证书请求事件。同时，相同host和port服务器的请求，不重复上报该事件。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## confirm

```TypeScript
confirm(priKeyFile: string, certChainFile: string): void
```

确认使用指定的私钥和客户端证书链。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKeyFile | string | 是 | The file that store private key. |
| certChainFile | string | 是 | The file that store client certificate chain. |

## confirm

```TypeScript
confirm(authUri: string): void
```

使用指定的凭据(从证书管理模块获得)。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authUri | string | 是 | is the key of credentials.The credentials contain sign info and client certificates info. |

## confirm

```TypeScript
confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void
```

确认使用从证书管理模块获取的指定凭据和凭据类型。

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identity | string | 是 | The identify of the credential. |
| credentialTypeOrCertChainFile | CredentialType \| string | 是 | The type of the credential or the file that storeclient certificate chain. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ignore

```TypeScript
ignore(): void
```

Ignore this certificate request temporarily.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

