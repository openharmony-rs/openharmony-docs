# RichEditorGesture

Defines a user gesture event.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

Triggered when a click event occurs.

It is executed on completion of a single click.

For a double-click scenario, the first click triggers this callback.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[ClickEvent](arkts-arkui-clickevent-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<GestureEvent>
```

Triggered when a long press event occurs.

It is executed on completion of a long press.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
