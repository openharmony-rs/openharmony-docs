# PosterOptions

```TypeScript
declare interface PosterOptions
```

Defines display options for the first frame of the video.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentTransitionEffect

```TypeScript
contentTransitionEffect?: ContentTransitionEffect
```

Transition effect when the preview image content of the current video changes. This field does not take effect when **showFirstFrame** is set to true (that is, first-frame display is enabled) or when no valid **previewUri** is configured in the [VideoOptions object](arkts-arkui-video-comp-videooptions-i.md).

Default value: **ContentTransitionEffect.IDENTITY**

When set to **undefined** or **null**, the value is **ContentTransitionEffect.IDENTITY**.

**Type:** [ContentTransitionEffect](arkts-arkui-common-comp-contenttransitioneffect-c.md)

**Default:** ContentTransitionEffect.IDENTITY

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showFirstFrame

```TypeScript
showFirstFrame?: boolean
```

Whether to configure first-frame display for the current video. When first-frame display is enabled, the previewUri field in the [VideoOptions object](arkts-arkui-video-comp-videooptions-i.md) does not take effect.

**true**: enables first-frame display; **false**: disables first-frame display.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
