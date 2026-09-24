# VideoOptions

```TypeScript
declare interface VideoOptions
```

Defines the options of the **Video** component.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: VideoController
```

Video controller, which can control the playback state of the video. When **controllerAsync** is set, the **controller** parameter does not take effect.

Default value: no video controller is set.

**Type:** [VideoController](arkts-arkui-video-comp-videocontroller-c.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controllerAsync

```TypeScript
controllerAsync?: VideoControllerAsync
```

Asynchronous video controller, which can control the playback state of the video and obtain the return result through a promise. When **controllerAsync** is set, **controller** is ignored.

Default value: empty

**Type:** [VideoControllerAsync](arkts-arkui-video-comp-videocontrollerasync-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## currentProgressRate

```TypeScript
currentProgressRate?: number | string | PlaybackSpeed
```

Video playback speed.

**NOTE:** 

The number format supports only the following values: 0.75, 1.0, 1.25, 1.75, and 2.0. Since API version 22, the values 0.5, 1.5, 3, 0.25, and 0.125 are also supported. Since API version 26.0.0, the supported value range is [0.125, 8].

The string format supports the string forms of the number values: "0.75", "1.0", "1.25", "1.75", and "2.0". Since API version 22, the values "0.5", "1.5", "3", "0.25", and "0.125" are also supported.

Other values, such as "abc" or "1.5+1.5", are processed as abnormal values.

Default value: **1.0 | PlaybackSpeed.Speed_Forward_1_00_X**

Abnormal value: processed as the default value.

**Type:** number &#124; string &#124; [PlaybackSpeed](arkts-arkui-video-comp-playbackspeed-e.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

Image AI analysis options, which can configure the analysis type or bind an analysis controller. After configuration, the image AI analysis function is enabled, and the analysis process can be controlled through the analysis controller. Pass this parameter when the AI analysis function is required. If it is not passed, the AI analysis function is disabled by default.

**Type:** [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## posterOptions

```TypeScript
posterOptions?: PosterOptions
```

First-frame display options for video playback, which can control whether the video supports first-frame display. Pass this parameter when the first-frame display function needs to be enabled. If it is not passed, first-frame display is disabled by default.

**Type:** [PosterOptions](arkts-arkui-video-comp-posteroptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## previewUri

```TypeScript
previewUri?: string | PixelMap | Resource
```

Path of the preview image displayed before the video is played.

The string format can be used to load local images and network images.

- Network image URLs are supported.  
- Relative paths are supported for referencing local images, for example, **previewUri: "common/test.jpg"**. When a  
relative path is used to reference a local image, cross-package or cross-module calls are not supported.  
- Strings with the file:// path prefix are supported, that is, the app sandbox URI (see [uriOrPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)): **file://&lt;bundleName&gt;/&lt;sandboxPath&gt;**. It is used to read resources in the app sandbox path. Ensure that the files in the directory package path have read permission.

The Resource format can access resource files across packages or modules.

- Resources in the rawfile directory are supported, that is, images referenced through **$rawfile**.  
- Images in system resources or app resources referenced through **$r** are supported.

Default value: empty string

Abnormal value: processed as the default value.

**Type:** string &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

## src

```TypeScript
src?: string | Resource
```

Data source of the video, which supports local videos and network videos.

The Resource format can access resource files across packages or modules and is commonly used to access local videos.

- Only resources in the rawfile directory are supported, that is, video files referenced through $rawfile.

The string format can be used to load network videos and local videos, and is commonly used to load network videos.

- Network video URLs are supported. For details about the formats supported by network video URLs, see [Formats Supported by Streaming Media](../../../media/media/streaming-media-playback-development-guide.md#formats-supported-by-streaming-media).  
- Strings with the file:// path prefix are supported, that is, the app sandbox URI (see [uriOrPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)): **file://&lt;bundleName&gt;/&lt;sandboxPath&gt;**. It is used to read resources in the app sandbox path. Ensure that the files in the directory package path have read permission.

Default value: empty string

Abnormal value: processed as the default value.

**NOTE:** 

The supported video formats are mp4, mkv, and TS.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
