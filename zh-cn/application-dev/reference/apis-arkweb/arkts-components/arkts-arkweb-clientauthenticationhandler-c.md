# ClientAuthenticationHandler

ClientAuthenticationHandler是Web组件中处理SSL客户端证书认证请求的类。当服务器请求客户端证书进行TLS双向认证时，该处理器通过`onClientAuthenticationRequest`事件回调提供给 应用，允许应用选择合适的证书凭据进行响应。示例代码参考[onClientAuthenticationRequest](arkts-arkweb-web-attribute.md#onclientauthenticationrequest)事件。

**起始版本：** 9

<!--Device-unnamed-declare class ClientAuthenticationHandler--><!--Device-unnamed-declare class ClientAuthenticationHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## cancel

```TypeScript
cancel(): void
```

通知Web组件取消客户端证书请求事件。对来自相同host和port服务器的后续请求，不再重复上报该事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-cancel(): void--><!--Device-ClientAuthenticationHandler-cancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## confirm

```TypeScript
confirm(priKeyFile: string, certChainFile: string): void
```

通知Web组件使用指定的私钥和客户端证书链。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-confirm(priKeyFile: string, certChainFile: string): void--><!--Device-ClientAuthenticationHandler-confirm(priKeyFile: string, certChainFile: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKeyFile | string | 是 | 存放私钥文件的完整路径。 |
| certChainFile | string | 是 | 存放证书链文件的完整路径。 |

## confirm

```TypeScript
confirm(authUri: string): void
```

通知Web组件使用指定的凭据（从证书管理模块获得）。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-confirm(authUri: string): void--><!--Device-ClientAuthenticationHandler-confirm(authUri: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authUri | string | 是 | 凭据的关键值。 |

## confirm

```TypeScript
confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void
```

通知Web组件使用从证书管理模块获取的指定凭据和凭据类型。

**起始版本：** 22

<!--Device-ClientAuthenticationHandler-confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void--><!--Device-ClientAuthenticationHandler-confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identity | string | 是 | 用于识别凭据的唯一标识值。 |
| credentialTypeOrCertChainFile | [CredentialType](arkts-arkweb-credentialtype-e.md) \| string | 是 | 类型为CredentialType时，代表凭据类型；类型为string时，表示证书链文件路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## constructor

```TypeScript
constructor()
```

ClientAuthenticationHandler的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-constructor()--><!--Device-ClientAuthenticationHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ignore

```TypeScript
ignore(): void
```

通知Web组件忽略本次请求。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClientAuthenticationHandler-ignore(): void--><!--Device-ClientAuthenticationHandler-ignore(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

