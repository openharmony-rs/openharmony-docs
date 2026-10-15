# VisibilityChangeReason

```TypeScript
declare enum VisibilityChangeReason
```

Enumerates reasons for **NavDestination** visibility changes.

**Since:** 21

<!--Device-unnamed-declare enum VisibilityChangeReason--><!--Device-unnamed-declare enum VisibilityChangeReason-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## APP_STATE

```TypeScript
APP_STATE = 2
```

Visibility changes due to switching between the foreground and background states.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-VisibilityChangeReason-APP_STATE = 2--><!--Device-VisibilityChangeReason-APP_STATE = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_COVER

```TypeScript
CONTENT_COVER = 1
```

Visibility changes due to the opening or closing of a modal page.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-VisibilityChangeReason-CONTENT_COVER = 1--><!--Device-VisibilityChangeReason-CONTENT_COVER = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TRANSITION

```TypeScript
TRANSITION = 0
```

Visibility changes due to page navigation.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-VisibilityChangeReason-TRANSITION = 0--><!--Device-VisibilityChangeReason-TRANSITION = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
