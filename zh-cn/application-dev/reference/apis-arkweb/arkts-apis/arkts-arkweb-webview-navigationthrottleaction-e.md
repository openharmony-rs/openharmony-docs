# NavigationThrottleAction

```TypeScript
enum NavigationThrottleAction
```

NavigationThrottle 回调可执行的动作枚举。

**起始版本：** 26.1.0

<!--Device-webview-enum NavigationThrottleAction--><!--Device-webview-enum NavigationThrottleAction-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CANCEL

```TypeScript
CANCEL = 1
```

取消导航。当导航应被阻止时使用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationThrottleAction-CANCEL = 1--><!--Device-NavigationThrottleAction-CANCEL = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DEFER

```TypeScript
DEFER = 2
```

暂缓决策。导航暂停，直到在[DeferThrottleCallback](arkts-arkweb-webview-deferthrottlecallback-i.md)上调用`proceed()`或`cancel()`。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationThrottleAction-DEFER = 2--><!--Device-NavigationThrottleAction-DEFER = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PROCEED

```TypeScript
PROCEED = 0
```

允许导航继续。当回调未实现或返回无效值时，默认使用此动作。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationThrottleAction-PROCEED = 0--><!--Device-NavigationThrottleAction-PROCEED = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core
