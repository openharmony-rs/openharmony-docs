# NavigationConfiguration

```TypeScript
declare interface NavigationConfiguration
```

Provides the navigation configuration item.

**Since:** 26.0.0

<!--Device-unnamed-declare interface NavigationConfiguration--><!--Device-unnamed-declare interface NavigationConfiguration-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## clearContentStackOnPrimaryNavigation

```TypeScript
clearContentStackOnPrimaryNavigation?: boolean
```

Whether to clear the content stack when navigation is triggered from the primary side.

In Navigation split mode, when enabled, navigaiton triggered from the primary side clears old NavDestination after the Primary/Home node while preserving all NavDestinations created by the current operation.

**Type:** boolean

**Default:** false

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-NavigationConfiguration-clearContentStackOnPrimaryNavigation?: boolean--><!--Device-NavigationConfiguration-clearContentStackOnPrimaryNavigation?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## recyclePagesOnLowMemory

```TypeScript
recyclePagesOnLowMemory?: boolean
```

Whether to recycle invisible pages when a low memory signal is received.

When enabled, Navigation recycles invisible NavDestination page instance after receiving low memory pressure notifications. NavPathInfo is preserved, and the page can be reconstructed later.

**Type:** boolean

**Default:** false

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-NavigationConfiguration-recyclePagesOnLowMemory?: boolean--><!--Device-NavigationConfiguration-recyclePagesOnLowMemory?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stackSizeLimit

```TypeScript
stackSizeLimit?: number
```

Maximum number of active page nodes in the navigation routing stack.

Default value: **0**, indicating that the routing stack size is not limited.

If the value is less than or equal to 0, the routing stack size is not limited.

If the value is greater than 0, the number of active page nodes is limited to the specified value. If the number exceeds the limit, the system automatically destroys the page nodes that are pushed to the stack earlier in the first-in-first-out (FIFO) order. The **NavPathInfo** of the pages is completely retained in the routing stack, so that the pages can be recreated later.

**Type:** number

**Default:** 0 (no limit)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NavigationConfiguration-stackSizeLimit?: int--><!--Device-NavigationConfiguration-stackSizeLimit?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
