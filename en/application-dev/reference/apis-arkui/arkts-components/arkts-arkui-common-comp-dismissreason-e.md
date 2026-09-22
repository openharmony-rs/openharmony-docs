# DismissReason

```TypeScript
declare enum DismissReason
```

Enumerates the reasons for popup dismissal.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PRESS_BACK

```TypeScript
PRESS_BACK = 0
```

Touching the **Back** button, swiping left or right on the screen, or pressing the **Esc** key.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TOUCH_OUTSIDE

```TypeScript
TOUCH_OUTSIDE = 1
```

Touching the mask.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CLOSE_BUTTON

```TypeScript
CLOSE_BUTTON = 2
```

Touching the close button.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_DOWN

```TypeScript
SLIDE_DOWN = 3
```

Swiping down.

**NOTE:** 

This API is effective only in sheet transition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDE

```TypeScript
SLIDE = 4
```

Swiping left or right on the screen. By default, swiping right dismisses the popup, while swiping left is used in the mirror scenario. This setting is not user-defined.

**NOTE:** 

This API is effective only in sheet transition.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
