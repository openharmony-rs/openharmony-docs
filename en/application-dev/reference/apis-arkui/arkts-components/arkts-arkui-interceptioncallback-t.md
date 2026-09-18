# InterceptionCallback

```TypeScript
declare type InterceptionCallback = (from: NavPathInfo|NavBar, to: NavPathInfo|NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void
```

Defines the callback triggered before a navigation page is redirected.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | [NavPathInfo](arkts-arkui-navpathinfo-c.md) &#124; [NavBar](arkts-arkui-navbar-t.md) | Yes | Information about the exit page. The value **navBar** indicates that the top page is the home page. |
| to | [NavPathInfo](arkts-arkui-navpathinfo-c.md) &#124; [NavBar](arkts-arkui-navbar-t.md) | Yes | Information about the enter page. The value **navBar** indicates that the top page is the home page. |
| pathStack | [NavPathStack](arkts-arkui-navpathstack-c.md) | Yes | Page stack. |
| operation | [NavigationOperation](arkts-arkui-navigationoperation-e.md) | Yes | Current page redirection type. |
| isAnimated | boolean | Yes | Whether to enable the transition animation.<br>**true**: Enable the transition animation.<br>**false**: Disable the transition animation. |
