# Video properties/events

```TypeScript
declare class VideoAttribute extends CommonMethod<VideoAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp-commonmethod-c.md), the following events are supported.

**Inheritance/Implementation:** VideoAttribute extends CommonMethod<VideoAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## analyzerConfig

```TypeScript
analyzerConfig(config: ImageAnalyzerConfig)
```

Sets the AI image analysis types, including subject recognition, text recognition, and object lookup. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ImageAnalyzerConfig](../arkts-apis/arkts-arkui-imageanalyzerconfig-i.md) | Yes | AI image analysis types. |

## autoPlay

```TypeScript
autoPlay(value: boolean)
```

Sets whether to enable autoplay. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable autoplay.<br>The value **true** means to enable autoplay, and **false** means to disable autoplay. <br>Default value: **false** |

## controls

```TypeScript
controls(value: boolean)
```

Sets whether to display the video playback control bar. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

> **NOTE:** 
> 
> The style of the control bar built into the **Video** component cannot be customized. To customize the control
> bar, set the **controls** attribute to **false** and implement the style or functions of the control bar by
> yourself. For details, see
> [Video Playback](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/VideoPlay).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the control bar for video playback. <br>**true**: the control bar is displayed; **false**: the control bar is not displayed. <br>Default value: **true** <br>**Note:** To use the [enableAnalyzer](#enableanalyzer) function for AI analysis, set this parameter to **false** and use a custom control bar. |

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

Sets whether to enable the AI image analyzer, which supports subject recognition, text recognition, and object lookup. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

After this feature is enabled, the video automatically enters an analysis state to process the current frame when playback is paused, and exits the analysis state when playback is resumed.

This attribute cannot be used together with the [overlay](arkts-arkui-common-comp-commonmethod-c.md#overlay) attribute. If both are set, the [CustomBuilder](../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8) attribute in [overlay](arkts-arkui-common-comp-commonmethod-c.md#overlay) becomes invalid.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

> **NOTE:** 
> 
> This feature is available only when the custom control bar is used (that is, when the
> [controls](#controls) attribute is set to **false**).
> This feature depends on device capabilities.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the AI analysis function. <br>**true**: enables the AI analysis function; **false**: disables the AI analysis function. <br>Default value: **false** <br>**Note:** <br>This attribute cannot be used together with [overlay](arkts-arkui-common-comp-commonmethod-c.md#overlay). When both are set, the [CustomBuilder](../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8) attribute in [overlay](arkts-arkui-common-comp-commonmethod-c.md#overlay) does not take effect. |

## enableShortcutKey

```TypeScript
enableShortcutKey(enabled: boolean)
```

Sets whether the component responds to keyboard shortcuts when it has focus. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

Currently, the component can respond to the following keys when it is in focus: spacebar for playing or pausing the video, up or down arrow key for adjusting the video volume, and left or right arrow key for fast forwarding or rewinding the video.

> **NOTE:** 
> 
> When **enabled** is set to **false** and **controls** is set to **true**, you can still use the left and
> right arrow keys to fast-forward or rewind the progress bar.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable shortcut key response.<br>The value **true** means to enable shortcut key response, and **false** means to disable it. <br>Default value: **false** |

## loop

```TypeScript
loop(value: boolean)
```

Sets whether to loop the video. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to loop a single video.<br>The value **true** means to enable loop playback, and **false** means to disable loop playback. <br>Default value: **false** |

## muted

```TypeScript
muted(value: boolean)
```

Sets whether to mute the video. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

> **NOTE:** 
> 
> When not muted, the **Video** component acquires audio focus when playback starts. To play without acquiring
> audio focus, mute the component before starting playback.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the video is muted.<br>The value **true** means to enable muting, and **false** means to disable muting. <br>Default value: **false** |

## objectFit

```TypeScript
objectFit(value: ImageFit)
```

Sets the fill mode for the video content. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md) | Yes | Video fill mode. <br>Default value: **ImageFit.Cover** <br>Restriction: The enum value **MATRIX** in the **ImageFit** type is not supported. If it is set, the effect is the same as that of **ImageFit.Cover**. <br>Abnormal value: If an abnormal value such as **undefined** or **null**, or a value outside the [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md) enum range is set, the effect is the same as that of **ImageFit.Cover**. |

## onError

```TypeScript
onError(event: VoidCallback | import('../api/@ohos.base').ErrorCallback)
```

Triggered when video playback fails. Dynamic property modification using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) &#124; import('../api/@ohos.base').ErrorCallback | Yes | Callback invoked when video playback fails. The callback of the [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) type is used to receive exception information. For details about the error codes returned by the callback, see [Video Component Error Codes](../../../reference/apis-arkui/errorcode-video.md) and [Media Error Codes](../../../reference/apis-media-kit/errorcode-media.md).<br>**Since:** 20 |

## onFinish

```TypeScript
onFinish(event: VoidCallback)
```

Triggered when video playback is finished. Dynamic property modification using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when video playback is finished.<br>**Since:** 18 |

## onFullscreenChange

```TypeScript
onFullscreenChange(callback: Callback<FullscreenInfo>)
```

Triggered when video playback is switched between full-screen mode and non-full-screen mode. Dynamic property modification using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[FullscreenInfo](arkts-arkui-video-comp-fullscreeninfo-i.md)&gt; | Yes | Callback invoked when switching between full-screen playback and non -full-screen playback states.<br>**Since:** 18 |

## onPause

```TypeScript
onPause(event: VoidCallback)
```

Triggered when video playback is paused. Dynamic property modification using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when video playback is paused.<br>**Since:** 18 |

## onPrepared

```TypeScript
onPrepared(callback: Callback<PreparedInfo>)
```

Triggered when video preparation is complete. Dynamic property modification using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[PreparedInfo](arkts-arkui-video-comp-preparedinfo-i.md)&gt; | Yes | Callback invoked when video preparation is complete.<br>**Since:** 18 |

## onSeeked

```TypeScript
onSeeked(callback: Callback<PlaybackInfo>)
```

Triggered to report the time information while seeking is completed. Dynamic property modification using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[PlaybackInfo](arkts-arkui-video-comp-playbackinfo-i.md)&gt; | Yes | Callback invoked when the operation progress bar is completed.<br>**Since:** 18 |

## onSeeking

```TypeScript
onSeeking(callback: Callback<PlaybackInfo>)
```

Triggered to report the time information while seeking is in progress (the progress bar is being dragged). Dynamic property modification using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[PlaybackInfo](arkts-arkui-video-comp-playbackinfo-i.md)&gt; | Yes | Callback invoked when the progress bar is operated.<br>**Since:** 18 |

## onStart

```TypeScript
onStart(event: VoidCallback)
```

Triggered when playback starts. This attribute supports dynamic setting through [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback triggered when video playback starts.<br>**Since:** 18 |

## onStop

```TypeScript
onStop(event: Callback<void>)
```

Triggered when the video playback is stopped (after **stop()** is called). Dynamic property modification using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | Yes | Callback invoked when video playback stops. |

## onUpdate

```TypeScript
onUpdate(callback: Callback<PlaybackInfo>)
```

Triggered when playback progress changes. Dynamic property modification using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[PlaybackInfo](arkts-arkui-video-comp-playbackinfo-i.md)&gt; | Yes | Callback invoked when the playback progress changes.<br>**Since:** 18 |
