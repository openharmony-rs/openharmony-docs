# HttpAuthHandler

HttpAuthHandler是Web组件用于处理HTTP认证请求的处理类。当服务器返回401 Unauthorized要求身份认证时，Web组件通过onHttpAuthRequest事件回调获取HttpAuthHandler实例，由 应用决定是否提供认证凭据。示例代码参考[onHttpAuthRequest](arkts-arkweb-web-attribute.md#onhttpauthrequest)事件。

**起始版本：** 9

<!--Device-unnamed-declare class HttpAuthHandler--><!--Device-unnamed-declare class HttpAuthHandler-End-->

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

通知Web组件用户取消HTTP认证操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpAuthHandler-cancel(): void--><!--Device-HttpAuthHandler-cancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## confirm

```TypeScript
confirm(userName: string, password: string): boolean
```

使用用户名和密码进行HTTP认证操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpAuthHandler-confirm(userName: string, password: string): boolean--><!--Device-HttpAuthHandler-confirm(userName: string, password: string): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userName | string | 是 | HTTP认证用户名，需为非空字符串。 |
| password | string | 是 | HTTP认证密码，需为非空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 认证成功时返回true，失败返回false。 |

## constructor

```TypeScript
constructor()
```

HttpAuthHandler的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpAuthHandler-constructor()--><!--Device-HttpAuthHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isHttpAuthInfoSaved

```TypeScript
isHttpAuthInfoSaved(): boolean
```

检查当前主机存储的凭据是否适用，如果凭据在当前请求中曾被服务器拒绝过，则不适用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpAuthHandler-isHttpAuthInfoSaved(): boolean--><!--Device-HttpAuthHandler-isHttpAuthInfoSaved(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 存储的凭据适用时返回true，其他返回false。 |

