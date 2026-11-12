# DeferThrottleCallback

```TypeScript
interface DeferThrottleCallback
```

为返回 DEFER 的[NavigationThrottle](arkts-arkweb-webview-navigationthrottle-i.md)回调提供异步决策能力。

当 NavigationThrottle 回调返回[NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md).DEFER 时，导航暂停。NavigationThrottle 回调方法的第二个参数为 DeferThrottleCallback。调用`proceed()`恢复导航，或调用`cancel()`取消导航。

**起始版本：** 26.1.0

<!--Device-webview-interface DeferThrottleCallback--><!--Device-webview-interface DeferThrottleCallback-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## cancel

```TypeScript
cancel(): void
```

取消暂缓的导航。重复调用，或在`proceed()`之后调用，均无效。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeferThrottleCallback-cancel(): void--><!--Device-DeferThrottleCallback-cancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## proceed

```TypeScript
proceed(): void
```

恢复暂缓的导航。重复调用，或在`cancel()`之后调用，均无效。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeferThrottleCallback-proceed(): void--><!--Device-DeferThrottleCallback-proceed(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core
