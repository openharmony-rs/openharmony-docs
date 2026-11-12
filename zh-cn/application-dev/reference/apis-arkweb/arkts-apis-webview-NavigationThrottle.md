# Interface (NavigationThrottle)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @chenguanhao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

`NavigationThrottle`是ArkWeb提供的导航拦截器接口。应用实现该接口并通过[WebviewController](./arkts-apis-webview-WebviewController.md)的[setNavigationThrottle()](./arkts-apis-webview-WebviewController.md#setnavigationthrottle)方法注册后，Web组件的导航会在四个阶段回调应用，由应用决定放行、取消或挂起导航，可用于外跳管控、重定向检测、下载拦截、自定义错误页等场景。

四个阶段回调与Chromium导航管线的阶段对齐：

| 回调 | 触发时机 | NavigationInfo有效字段 |
| ---- | ---- | ---- |
| [willStartRequest](#willstartrequest) | 导航请求即将开始（如点击链接、修改location.href） | url、isMainFrame、hasUserGesture、pageTransition、requestMethod、isRendererInitiated |
| [willRedirectRequest](#willredirectrequest) | 导航被服务端重定向（301/302/307/308） | url（重定向目标）、isMainFrame、hasUserGesture、isRedirect、pageTransition、requestMethod、isRendererInitiated、statusCode |
| [willProcessResponse](#willprocessresponse) | 导航收到服务端响应头 | url、isMainFrame、statusCode、mimeType、contentDisposition |
| [willFailRequest](#willfailrequest) | 导航失败（如网络断开、证书错误） | url、isMainFrame、errorCode、errorDescription |

每个回调返回一个[NavigationThrottleAction](./arkts-apis-webview-e.md#navigationthrottleaction)动作：

- 返回PROCEED：允许导航继续，行为与未注册拦截器时一致。
- 返回CANCEL：取消本次导航，页面保持当前文档。
- 返回DEFER：挂起导航，应用稍后通过[DeferThrottleCallback](./arkts-apis-webview-DeferThrottleCallback.md)异步恢复或取消。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 每个WebviewController至多注册一个生效的NavigationThrottle，重复调用[setNavigationThrottle()](./arkts-apis-webview-WebviewController.md#setnavigationthrottle)会替换旧实例。
>
> - 若回调未实现或返回无效值（如undefined），默认按PROCEED处理。
>
> - 回调在应用进程内同步调用，应用应快速返回；长耗时决策请返回DEFER。
>
> - same-document导航（如hash变更）不触发任何回调。

**系统能力：** SystemCapability.Web.Webview.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

## 导入模块

```ts
import { webview } from '@kit.ArkWeb';
```

## willStartRequest

willStartRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction

导航请求即将开始时回调。

**系统能力：** SystemCapability.Web.Webview.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| info | [NavigationInfo](./arkts-apis-webview-NavigationInfo.md) | 是 | 导航信息。 |
| callback | [DeferThrottleCallback](./arkts-apis-webview-DeferThrottleCallback.md) | 是 | 异步决策句柄。回调返回DEFER时，通过该句柄恢复或取消导航。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [NavigationThrottleAction](./arkts-apis-webview-e.md#navigationthrottleaction) | 对本次导航执行的动作。 |

## willRedirectRequest

willRedirectRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction

导航被服务端重定向时回调。

**系统能力：** SystemCapability.Web.Webview.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| info | [NavigationInfo](./arkts-apis-webview-NavigationInfo.md) | 是 | 导航信息。url字段为重定向目标URL，isRedirect为true，statusCode为3xx状态码。 |
| callback | [DeferThrottleCallback](./arkts-apis-webview-DeferThrottleCallback.md) | 是 | 异步决策句柄。回调返回DEFER时，通过该句柄恢复或取消导航。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [NavigationThrottleAction](./arkts-apis-webview-e.md#navigationthrottleaction) | 对本次导航执行的动作。 |

## willProcessResponse

willProcessResponse(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction

导航收到服务端响应头时回调。

**系统能力：** SystemCapability.Web.Webview.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| info | [NavigationInfo](./arkts-apis-webview-NavigationInfo.md) | 是 | 导航信息。statusCode、mimeType、contentDisposition为本次响应的有效值。 |
| callback | [DeferThrottleCallback](./arkts-apis-webview-DeferThrottleCallback.md) | 是 | 异步决策句柄。回调返回DEFER时，通过该句柄恢复或取消导航。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [NavigationThrottleAction](./arkts-apis-webview-e.md#navigationthrottleaction) | 对本次导航执行的动作。 |

## willFailRequest

willFailRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction

导航失败时回调。

**系统能力：** SystemCapability.Web.Webview.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| info | [NavigationInfo](./arkts-apis-webview-NavigationInfo.md) | 是 | 导航信息。errorCode、errorDescription为本次失败的有效值。 |
| callback | [DeferThrottleCallback](./arkts-apis-webview-DeferThrottleCallback.md) | 是 | 异步决策句柄。本回调返回DEFER时按PROCEED处理（失败导航无挂起语义），该句柄不生效。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [NavigationThrottleAction](./arkts-apis-webview-e.md#navigationthrottleaction) | 对本次导航执行的动作。返回CANCEL时抑制系统默认错误页，应用可自行展示自定义错误页；返回PROCEED时按系统默认失败行为处理。 |
