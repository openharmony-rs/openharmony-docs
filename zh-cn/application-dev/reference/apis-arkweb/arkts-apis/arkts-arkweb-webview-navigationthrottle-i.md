# NavigationThrottle

```TypeScript
interface NavigationThrottle
```

在多个阶段拦截导航请求的接口。

通过[setNavigationThrottle](arkts-arkweb-webview-webviewcontroller-c.md#setnavigationthrottle)为 Web 组件设置 NavigationThrottle。每个回调接收一个[NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md)和一个[DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md)，并返回一个[NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md)。

> **说明：** 
> 
> - 回调未实现或返回无效值（如 undefined）时，默认使用 PROCEED。
> - 回调返回 DEFER 时导航暂停，使用[DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md)异步恢复或取消。

**起始版本：** 26.1.0

<!--Device-webview-interface NavigationThrottle--><!--Device-webview-interface NavigationThrottle-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## willFailRequest

```TypeScript
willFailRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction
```

导航失败时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationThrottle-willFailRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction--><!--Device-NavigationThrottle-willFailRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md) | 是 | 导航信息。**errorCode**和**errorDescription**有效。 |
| callback | [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md) | 是 | 用于异步决策的 DeferThrottleCallback，返回 DEFER 时使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md) | 要执行的动作。 |

## willProcessResponse

```TypeScript
willProcessResponse(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction
```

收到导航的服务端响应时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationThrottle-willProcessResponse(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction--><!--Device-NavigationThrottle-willProcessResponse(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md) | 是 | 导航信息。**statusCode**、**mimeType**、**contentDisposition**有效。 |
| callback | [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md) | 是 | 用于异步决策的 DeferThrottleCallback，返回 DEFER 时使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md) | 要执行的动作。 |

## willRedirectRequest

```TypeScript
willRedirectRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction
```

导航被服务端重定向时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationThrottle-willRedirectRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction--><!--Device-NavigationThrottle-willRedirectRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md) | 是 | 导航信息。**url**字段是重定向目标。 |
| callback | [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md) | 是 | 用于异步决策的 DeferThrottleCallback，返回 DEFER 时使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md) | 要执行的动作。 |

## willStartRequest

```TypeScript
willStartRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction
```

导航请求即将开始时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationThrottle-willStartRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction--><!--Device-NavigationThrottle-willStartRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md) | 是 | 导航信息。 |
| callback | [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md) | 是 | 用于异步决策的 DeferThrottleCallback，返回 DEFER 时使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md) | 要执行的动作。 |
