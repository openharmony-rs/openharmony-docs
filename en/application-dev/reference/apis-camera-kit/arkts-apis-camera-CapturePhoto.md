# Interface (CapturePhoto)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=cfbdf7078f905314893a0975124c4a78ff4672a0 translatedAt=2026-11-18T03:28:25.039Z pushedAt=2026-11-19T11:49:02.000Z nl=1 -->

**CapturePhoto** provides APIs for obtaining the objects of the full-quality image and the uncompressed image.

> **NOTE**
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## Properties

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Camera.Core

| Name  | Type                          |   Read-Only   |   Optional  | Description      |
| ------ | ----------------------------- | --------  |  ------ | ---------- |
| main | [ImageType](arkts-apis-camera-t.md#imagetype) |    No    |    No    | Objects of full-quality and uncompressed images.<br>**Atomic service API**: This API can be used in atomic services since API version 23. |
| oxygenPhoto | [ImageType](arkts-apis-camera-t.md#imagetype) |    No    |    Yes    | Auxiliary image object for blood oxygen detection and analysis.<br>**Since**: 26.0.1<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.1. |
| pigmentationPhoto | [ImageType](arkts-apis-camera-t.md#imagetype) |    No    |    Yes    | Auxiliary image object for skin pigmentation analysis.<br>**Since**: 26.0.1<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.1. |

## release

release(): Promise\<void\>

Releases output resources. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Return value**

| Type           | Description                    |
| -------------- | ----------------------- |
| Promise\<void\> | Promise that returns no value.|

**Example**

```ts
import { camera } from '@kit.CameraKit';

async function releaseCapturePhoto(capturePhoto: camera.CapturePhoto): Promise<void> {
  await capturePhoto.release();
}
```
