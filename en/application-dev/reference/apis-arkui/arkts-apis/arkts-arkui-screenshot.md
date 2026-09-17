# @ohos.screenshot

Provides the screen capture capability.

**Since:** 12

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [capture](arkts-arkui-screenshot-capture-f.md) | Takes a screenshot of the entire screen. This API uses a promise to return the result. |
| [pick](arkts-arkui-screenshot-pick-f.md) | Obtains this screenshot. Currently, only the screenshot of the display whose ID is **0** can be obtained. (If a screenshot of the extended screen is needed, you can use the [capture](arkts-arkui-screenshot-capture-f.md) API.) This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [save](arkts-arkui-screenshot-save-f-sys.md) | Obtains a screenshot. This API uses an asynchronous callback to return the result. |
| [save](arkts-arkui-screenshot-save-f-sys.md) | Obtains a screenshot. This API uses an asynchronous callback to return the result. |
| [save](arkts-arkui-screenshot-save-f-sys.md) | Obtains a screenshot. This API uses a promise to return the result. |
| [saveHdrPicture](arkts-arkui-screenshot-savehdrpicture-f-sys.md) | Obtains a screenshot. This API uses a promise to return the result. SDR stands for Standard Dynamic Range, and HDR stands for High Dynamic Range. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CaptureOption](arkts-arkui-screenshot-captureoption-i.md) | Describes the capture options. |
| [PickInfo](arkts-arkui-screenshot-pickinfo-i.md) | Describes the screenshot options. |
| [Rect](arkts-arkui-screenshot-rect-i.md) | Describes the region of the screen to capture. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HdrScreenshotOptions](arkts-arkui-screenshot-hdrscreenshotoptions-i-sys.md) | Describes the HDR screenshot options. |
| [ScreenshotOptions](arkts-arkui-screenshot-screenshotoptions-i-sys.md) | Describes the screenshot options. |
| [Size](arkts-arkui-screenshot-size-i-sys.md) | Describes the size of the screen region to capture. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DisplayIntentType](arkts-arkui-screenshot-displayintenttype-e-sys.md) | Enumerates the screenshot display intent type. |
<!--DelEnd-->
