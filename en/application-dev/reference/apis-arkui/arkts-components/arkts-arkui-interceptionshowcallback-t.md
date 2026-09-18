# InterceptionShowCallback

```TypeScript
declare type InterceptionShowCallback = (from: NavDestinationContext|NavBar, to: NavDestinationContext|NavBar, operation: NavigationOperation, isAnimated: boolean) => void
```

Represents the interception callback invoked before and after page redirection.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | [NavDestinationContext](arkts-arkui-navdestinationcontext-i.md) &#124; [NavBar](arkts-arkui-navbar-t.md) | Yes | Information about the top page in the routing stack after page redirection. The value **navBar** indicates that the top page is the home page. |
| to | [NavDestinationContext](arkts-arkui-navdestinationcontext-i.md) &#124; [NavBar](arkts-arkui-navbar-t.md) | Yes | Information about the top page in the routing stack after page redirection. The value **navBar** indicates that the top page is the home page. |
| operation | [NavigationOperation](arkts-arkui-navigationoperation-e.md) | Yes | Current page redirection type. |
| isAnimated | boolean | Yes | Whether to enable the transition animation.<br>**true**: Enable the transition animation.<br>**false**: Disable the transition animation. |
