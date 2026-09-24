# NavigationInterception

```TypeScript
declare interface NavigationInterception
```

Describes the object to be intercepted during navigation redirection.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## didShow

```TypeScript
didShow?: InterceptionShowCallback
```

Callback after page redirection. The setting takes effect in the next redirection.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## interception

```TypeScript
interception?: InterceptionCallback
```

Callback invoked before a page transition, allowing for stack operations, which take effect immediately for the current transition. The intercepted page will not be created.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## modeChange

```TypeScript
modeChange?: InterceptionModeCallback
```

Callback invoked when the display mode of the **Navigation** component switches between single-column and split- column.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## willShow

```TypeScript
willShow?: InterceptionShowCallback
```

Callback invoked before a page transition, allowing for stack operations, which take effect immediately for the current transition. The intercepted page will be created.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
