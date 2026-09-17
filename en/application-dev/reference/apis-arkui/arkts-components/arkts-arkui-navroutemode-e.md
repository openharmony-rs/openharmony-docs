# NavRouteMode

Defines the routing policy.

> **NOTE:** 

**Since:** 10

**Deprecated since:** 13

**Substitutes:** NavPathStack and navDestination

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PUSH_WITH_RECREATE

```TypeScript
PUSH_WITH_RECREATE
```

The new navigation destination page replaces the current one. The current page is destroyed, but the information about this page is retained in the navigation stack.

**Since:** 10

**Deprecated since:** 13

**Substitutes:** LaunchMode

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PUSH

```TypeScript
PUSH
```

The new navigation destination page overwrites the current one. The current page is not destroyed, and the information about this page is retained in the navigation stack.

**Since:** 10

**Deprecated since:** 13

**Substitutes:** LaunchMode

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## REPLACE

```TypeScript
REPLACE
```

The new navigation destination page replaces the current one. The current page is destroyed, and the information about this page is removed from the navigation stack.

**Since:** 10

**Deprecated since:** 13

**Substitutes:** LaunchMode

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
