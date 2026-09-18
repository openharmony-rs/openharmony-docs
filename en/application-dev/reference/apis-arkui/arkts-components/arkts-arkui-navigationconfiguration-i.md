# NavigationConfiguration

Navigation configuration options.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## clearContentStackOnPrimaryNavigation

```TypeScript
clearContentStackOnPrimaryNavigation?: boolean
```

Whether to clear the content stack when navigation is triggered from the primary side.

In Navigation split mode, when enabled, navigaiton triggered from the primary side clears old NavDestination after the Primary/Home node while preserving all NavDestinations created by the current operation.

**Type:** boolean

**Default:** false

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## recyclePagesOnLowMemory

```TypeScript
recyclePagesOnLowMemory?: boolean
```

Whether to recycle invisible pages when a low memory signal is received.

When enabled, Navigation recycles invisible NavDestination page instance after receiving low memory pressure notifications. NavPathInfo is preserved, and the page can be reconstructed later.

**Type:** boolean

**Default:** false

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stackSizeLimit

```TypeScript
stackSizeLimit?: number
```

Navigation page stack size limit.

Description:  
- Limits to maximum number of active page nodes in Navigation page stack.  
- When limit is exceeded, oldest page nodes are automatically destroyed  
in FIFO (First-In-First-Out) order.  
- NavPathInfo of pages is completely retained, supporting page recreation.  
- value &lt;=0 No limit on page stack size (default value).  
- value &gt;0 Limit stack size to specified value.

**Type:** number

**Default:** 0 (nolimit)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
