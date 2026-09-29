# UIState

```TypeScript
export enum UIState
```

Enumerates polymorphic style states, which are used to process polymorphic styles.

**Since:** 20

<!--Device-unnamed-export enum UIState--><!--Device-unnamed-export enum UIState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NORMAL

```TypeScript
NORMAL = 0
```

Normal state.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-UIState-NORMAL = 0--><!--Device-UIState-NORMAL = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PRESSED

```TypeScript
PRESSED = 1 << 0
```

Pressed state.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-UIState-PRESSED = 1 << 0--><!--Device-UIState-PRESSED = 1 << 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FOCUSED

```TypeScript
FOCUSED = 1 << 1
```

Focused state.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-UIState-FOCUSED = 1 << 1--><!--Device-UIState-FOCUSED = 1 << 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISABLED

```TypeScript
DISABLED = 1 << 2
```

Disabled state.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-UIState-DISABLED = 1 << 2--><!--Device-UIState-DISABLED = 1 << 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELECTED

```TypeScript
SELECTED = 1 << 3
```

Selected state.

Only supported by specific components: **Checkbox**, **Radio**, **Toggle**, **List**, **Grid**, **MenuItem**.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-UIState-SELECTED = 1 << 3--><!--Device-UIState-SELECTED = 1 << 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## HOVERED

```TypeScript
HOVERED = 1 << 4
```

Hovered state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-UIState-HOVERED = 1 << 4--><!--Device-UIState-HOVERED = 1 << 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
