# ClientAuthenticationHandler

Defines the client certificate request result, related to {@link onClientAuthenticationRequest} method.

**起始版本：** 9

<!--Device-unnamed-declare class ClientAuthenticationHandler--><!--Device-unnamed-declare class ClientAuthenticationHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="cancel"></a>
## cancel

```TypeScript
cancel(): void
```

取消证书请求事件。同时，相同host和port服务器的请求，不重复上报该事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-cancel(): void--><!--Device-ClientAuthenticationHandler-cancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="confirm"></a>
## confirm

```TypeScript
confirm(priKeyFile: string, certChainFile: string): void
```

确认使用指定的私钥和客户端证书链。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-confirm(priKeyFile: string, certChainFile: string): void--><!--Device-ClientAuthenticationHandler-confirm(priKeyFile: string, certChainFile: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKeyFile | string | 是 | The file that store private key. |
| certChainFile | string | 是 | The file that store client certificate chain. |

<a id="confirm-1"></a>
## confirm

```TypeScript
confirm(authUri: string): void
```

使用指定的凭据(从证书管理模块获得)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-confirm(authUri: string): void--><!--Device-ClientAuthenticationHandler-confirm(authUri: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authUri | string | 是 | is the key of credentials.The credentials contain sign info and client certificates info. |

<a id="confirm-2"></a>
## confirm

```TypeScript
confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void
```

确认使用从证书管理模块获取的指定凭据和凭据类型。

**起始版本：** 22

<!--Device-ClientAuthenticationHandler-confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void--><!--Device-ClientAuthenticationHandler-confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identity | string | 是 | The identify of the credential. |
| credentialTypeOrCertChainFile | [CredentialType](arkts-arkweb-credentialtype-e.md) \| string | 是 | The type of the credential or the file that store client certificate chain. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-constructor()--><!--Device-ClientAuthenticationHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="ignore"></a>
## ignore

```TypeScript
ignore(): void
```

Ignore this certificate request temporarily.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-ignore(): void--><!--Device-ClientAuthenticationHandler-ignore(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

