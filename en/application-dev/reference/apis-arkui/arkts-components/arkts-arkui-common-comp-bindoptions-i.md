# BindOptions

```TypeScript
declare interface BindOptions
```

Overlay module options

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAppear

```TypeScript
onAppear?: () => void
```

Callback for when the sheet is displayed (after the animation ends).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: () => void
```

Callback for when the sheet disappears (after the animation ends).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: () => void
```

Callback for when the sheet is about to be displayed (before the animation starts).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: () => void
```

Callback function before overlay popAnimation starts.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the sheet. <br>Default value: **Color.White**.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
