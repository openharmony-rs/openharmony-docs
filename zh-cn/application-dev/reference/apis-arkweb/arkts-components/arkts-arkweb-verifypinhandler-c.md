# VerifyPinHandler

VerifyPinHandler是Web组件中处理PIN码验证请求的类，用于在Web页面中需要身份认证的场景（如安全支付、敏感操作确认等）增强应用安全性。当需要用户PIN码认证时，该处理器通过onVerifyPin事件回调提供给应用， 允许应用响应PIN码验证结果，有效防止未授权访问并保护用户隐私。示例代码参考[onVerifyPin](arkts-arkweb-web-attribute.md#onverifypin)。

**起始版本：** 22

<!--Device-unnamed-declare class VerifyPinHandler--><!--Device-unnamed-declare class VerifyPinHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## confirm

```TypeScript
confirm(result: PinVerifyResult): void
```

通知Web组件PIN码认证结果。应用通过调用此方法将PIN码验证结果返回给Web组件，Web组件根据结果继续后续的认证流程。如果验证通过，Web组件将允许访问受保护内容；如果验证失败，Web组件将拒绝访问并可能提示用户重试。

**起始版本：** 22

<!--Device-VerifyPinHandler-confirm(result: PinVerifyResult): void--><!--Device-VerifyPinHandler-confirm(result: PinVerifyResult): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | [PinVerifyResult](arkts-arkweb-pinverifyresult-e.md) | 是 | PIN码认证结果。成功表示Web组件将允许后续页面操作；失败则可能导致页面导航或内容加载被拦截。 |

## constructor

```TypeScript
constructor()
```

VerifyPinHandler的构造函数。

**起始版本：** 22

<!--Device-VerifyPinHandler-constructor()--><!--Device-VerifyPinHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

