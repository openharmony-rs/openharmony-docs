# VideoElement

```TypeScript
export interface VideoElement extends Element
```

The &lt;video&gt; component provides a video player.

@extends Element @interface VideoElement

**Inheritance/Implementation:** VideoElement extends [Element](arkts-arkui-viewmodel-element-i.md)

**Since:** 4

<!--Device-unnamed-export interface VideoElement extends Element--><!--Device-unnamed-export interface VideoElement extends Element-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## exitFullscreen

```TypeScript
exitFullscreen(): void
```

Requests to exit the full screen mode.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-VideoElement-exitFullscreen(): void--><!--Device-VideoElement-exitFullscreen(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause(): void
```

Requests to pause a video.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-VideoElement-pause(): void--><!--Device-VideoElement-pause(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## requestFullscreen

```TypeScript
requestFullscreen(param: { screenOrientation: "default" }): void
```

Requests to enter the full screen mode.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-VideoElement-requestFullscreen(param: { screenOrientation: "default" }): void--><!--Device-VideoElement-requestFullscreen(param: { screenOrientation: "default" }): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | { screenOrientation: "default" } | Yes |  |

## setCurrentTime

```TypeScript
setCurrentTime(param: { currenttime: number }): void
```

Specifies the video playing position.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-VideoElement-setCurrentTime(param: { currenttime: number }): void--><!--Device-VideoElement-setCurrentTime(param: { currenttime: number }): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | { currenttime: number } | Yes |  |

## start

```TypeScript
start(): void
```

Requests to start playing a video.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-VideoElement-start(): void--><!--Device-VideoElement-start(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stop

```TypeScript
stop(): void
```

Requests to stop playing a video.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-VideoElement-stop(): void--><!--Device-VideoElement-stop(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
