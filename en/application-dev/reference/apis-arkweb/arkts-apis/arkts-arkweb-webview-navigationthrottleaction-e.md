# NavigationThrottleAction

```TypeScript
enum NavigationThrottleAction
```

NavigationThrottle callback action enumeration.

**Since:** 26.1.0

<!--Device-webview-enum NavigationThrottleAction--><!--Device-webview-enum NavigationThrottleAction-End-->

**System capability:** SystemCapability.Web.Webview.Core

## CANCEL

```TypeScript
CANCEL = 1
```

Cancel navigation. Use when navigation should be blocked.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationThrottleAction-CANCEL = 1--><!--Device-NavigationThrottleAction-CANCEL = 1-End-->

**System capability:** SystemCapability.Web.Webview.Core

## DEFER

```TypeScript
DEFER = 2
```

:: Suspend decision-making. Navigation pauses until `proceed()` or `cancel()` is called on [DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationThrottleAction-DEFER = 2--><!--Device-NavigationThrottleAction-DEFER = 2-End-->

**System capability:** SystemCapability.Web.Webview.Core

## PROCEED

```TypeScript
PROCEED = 0
```

Allow navigation to continue. This action is used by default when the callback is not implemented or an invalid value is returned.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationThrottleAction-PROCEED = 0--><!--Device-NavigationThrottleAction-PROCEED = 0-End-->

**System capability:** SystemCapability.Web.Webview.Core
