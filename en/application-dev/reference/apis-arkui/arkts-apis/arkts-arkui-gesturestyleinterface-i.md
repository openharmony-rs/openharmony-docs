# GestureStyleInterface

```TypeScript
declare interface GestureStyleInterface
```

Defines the Gesture Events.

**Since:** 12

<!--Device-unnamed-declare interface GestureStyleInterface--><!--Device-unnamed-declare interface GestureStyleInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

Click event.

**Type:** Callback&lt;[ClickEvent](../arkts-components/arkts-arkui-common-comp-clickevent-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureStyleInterface-onClick?: Callback<ClickEvent>--><!--Device-GestureStyleInterface-onClick?: Callback<ClickEvent>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<GestureEvent>
```

Long press event.

**Type:** Callback&lt;[GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureStyleInterface-onLongPress?: Callback<GestureEvent>--><!--Device-GestureStyleInterface-onLongPress?: Callback<GestureEvent>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTouch

```TypeScript
onTouch?: Callback<TouchEvent>
```

Touch event.

**Type:** Callback&lt;[TouchEvent](../arkts-components/arkts-arkui-common-comp-touchevent-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-GestureStyleInterface-onTouch?: Callback<TouchEvent>--><!--Device-GestureStyleInterface-onTouch?: Callback<TouchEvent>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
