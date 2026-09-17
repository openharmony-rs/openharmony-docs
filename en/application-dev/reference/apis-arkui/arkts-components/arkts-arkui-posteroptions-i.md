# PosterOptions

Defines display options for the first frame of the video.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentTransitionEffect

```TypeScript
contentTransitionEffect?: ContentTransitionEffect
```

Transition effect to apply when the video preview image changes. This parameter does not take effect if **showFirstFrame** is **true**, or if a valid **previewUri** in [VideoOptions](arkts-arkui-videooptions-i.md) is not provided.

Default value: **ContentTransitionEffect.IDENTITY**.

If this parameter is set to **undefined** or **null**, it defaults to **ContentTransitionEffect.IDENTITY**.

**Type:** [ContentTransitionEffect](arkts-arkui-contenttransitioneffect-c.md)

**Default:** ContentTransitionEffect.IDENTITY

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showFirstFrame

```TypeScript
showFirstFrame?: boolean
```

Whether to enable first frame display, showing the first frame of the video as a preview. When first frame display is enabled, the previewUri field in [VideoOptions](arkts-arkui-videooptions-i.md) has no effect.

**true**: Enable first frame display.

**false**: Disable first frame display.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
