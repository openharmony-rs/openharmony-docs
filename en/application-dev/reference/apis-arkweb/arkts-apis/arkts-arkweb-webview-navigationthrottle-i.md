# NavigationThrottle

```TypeScript
interface NavigationThrottle
```

Interface to intercept navigation requests at multiple stages.

Set the NavigationThrottle for the Web component through [setNavigationThrottle](arkts-arkweb-webview-webviewcontroller-c.md#setnavigationthrottle). Each callback receives one [NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md) and a [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md), and returns a [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md).

> **Description* *
> 
> - When the callback is not implemented or an invalid value(for example, undefined) is returned, the default value PROCEED is used.
> - Navigation pauses when the callback returns to DEFER, resumes or cancels asynchronously using [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md).

**Since:** 26.1.0

<!--Device-webview-interface NavigationThrottle--><!--Device-webview-interface NavigationThrottle-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## willFailRequest

```TypeScript
willFailRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction
```

Invoked when navigation fails.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationThrottle-willFailRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction--><!--Device-NavigationThrottle-willFailRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md) | Yes | Navigation information. **errorCode** and **errorDescription** are valid. |
| callback | [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md) | Yes | DeferThrottleCallback for asynchronous decision, used when DEFER is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md) | The action to be performed. |

## willProcessResponse

```TypeScript
willProcessResponse(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction
```

This interface is invoked when a response from the navigation server is received.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationThrottle-willProcessResponse(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction--><!--Device-NavigationThrottle-willProcessResponse(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md) | Yes | Navigation information. **statusCode**, **mimeType**, and **contentDisposition** are valid. |
| callback | [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md) | Yes | DeferThrottleCallback for asynchronous decision, used when DEFER is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md) | The action to be performed. |

## willRedirectRequest

```TypeScript
willRedirectRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction
```

This interface is invoked when the navigation is redirected by the server.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationThrottle-willRedirectRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction--><!--Device-NavigationThrottle-willRedirectRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md) | Yes | Navigation information. The **url** field is the redirect target. |
| callback | [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md) | Yes | DeferThrottleCallback for asynchronous decision, used when DEFER is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md) | The action to be performed. |

## willStartRequest

```TypeScript
willStartRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction
```

Called when the navigation request is about to start.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationThrottle-willStartRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction--><!--Device-NavigationThrottle-willStartRequest(info: NavigationInfo, callback: DeferThrottleCallback): NavigationThrottleAction-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [NavigationInfo](arkts-arkweb-webview-navigationinfo-i.md) | Yes | Navigation information. |
| callback | [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md) | Yes | DeferThrottleCallback for asynchronous decision, used when DEFER is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md) | The action to be performed. |
