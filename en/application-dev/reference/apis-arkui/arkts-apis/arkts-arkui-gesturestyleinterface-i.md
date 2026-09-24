# GestureStyleInterface

```TypeScript
declare interface GestureStyleInterface
```

Defines the Gesture Events.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

Callback for click events.

**Type:** Callback&lt;[ClickEvent](../arkts-components/arkts-arkui-common-comp-clickevent-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<GestureEvent>
```

Callback for long press events.

**Type:** Callback&lt;[GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTouch

```TypeScript
onTouch?: Callback<TouchEvent>
```

Callback for touch events.

**Type:** Callback&lt;[TouchEvent](../arkts-components/arkts-arkui-common-comp-touchevent-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
