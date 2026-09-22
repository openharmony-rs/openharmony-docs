# NavigationSystemTransitionType

```TypeScript
declare enum NavigationSystemTransitionType
```

Type of the system transition animation.

> **NOTE:** 

> System transition animations for the title bar and content area can be configured separately.

> The system transition animation of the title bar is only available for the push and pop animations of navigation
> destination pages in STANDARD mode, with the following constraints:

> When **NONE** or **TITLE** is set, no system transition animation is displayed. When **CONTENT** or **DEFAULT** is
> set, the system transition animation is displayed by default.

**Since:** 14

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default system transition animation.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 1
```

No system transition animation.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TITLE

```TypeScript
TITLE = 2
```

System transition animation of the title bar.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTENT

```TypeScript
CONTENT = 3
```

System transition animation of the content area.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FADE

```TypeScript
FADE = 4
```

Fade-type system transition animation.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EXPLODE

```TypeScript
EXPLODE = 5
```

Center-scale type system transition animation.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_RIGHT

```TypeScript
SLIDE_RIGHT = 6
```

Right-slide type system transition animation.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_BOTTOM

```TypeScript
SLIDE_BOTTOM = 7
```

Bottom-slide type system transition animation.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
