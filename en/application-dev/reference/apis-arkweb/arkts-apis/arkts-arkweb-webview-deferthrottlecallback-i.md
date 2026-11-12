# DeferThrottleCallback

```TypeScript
interface DeferThrottleCallback
```

Provide asynchronous decision capabilities for [NavigationThrottle](arkts-arkweb-webview-navigationthrottle-i.md) callbacks that return DEFER.

Navigation pauses when the NavigationThrottle callback returns [NavigationThrottleAction](arkts-arkweb-webview-navigationthrottleaction-e.md).DEFER. Second of NavigationThrottle callback method The parameter is DeferThrottleCallback. Call `proceed()` to resume navigation, or call `cancel()` to cancel navigation.

**Since:** 26.1.0

<!--Device-webview-interface DeferThrottleCallback--><!--Device-webview-interface DeferThrottleCallback-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## cancel

```TypeScript
cancel(): void
```

Unsuspended navigation. Repeated calls, or after `proceed()`, have no effect.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeferThrottleCallback-cancel(): void--><!--Device-DeferThrottleCallback-cancel(): void-End-->

**System capability:** SystemCapability.Web.Webview.Core

## proceed

```TypeScript
proceed(): void
```

Resumes suspended navigation. Repeated calls, or after `cancel()`, are invalid.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeferThrottleCallback-proceed(): void--><!--Device-DeferThrottleCallback-proceed(): void-End-->

**System capability:** SystemCapability.Web.Webview.Core
