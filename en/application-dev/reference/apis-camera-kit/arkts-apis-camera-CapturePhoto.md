# Interface (CapturePhoto)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

**CapturePhoto** provides APIs for obtaining the objects of the full-quality image and the uncompressed image.

> **NOTE**
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## Properties

**Model constraint**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Multimedia.Camera.Core

| Name  | Type                          |   Read-Only   |   Optional  | Description      |
| ------ | ----------------------------- | --------  |  ------ | ---------- |
| main | [ImageType](arkts-apis-camera-t.md#imagetype) |    No  |    No   | Object of the full-quality image and the uncompressed image.|

## release

release(): Promise\<void\>

Releases output resources. This API uses a promise to return the result.

**Model constraint**: This API can be used only in the stage model.

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
