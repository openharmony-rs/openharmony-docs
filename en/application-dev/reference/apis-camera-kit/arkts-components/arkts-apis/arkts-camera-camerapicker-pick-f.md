# pick

## Modules to Import

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
```

## pick

```TypeScript
function pick(context: Context, mediaTypes: Array<PickerMediaType>, pickerProfile: PickerProfile): Promise<PickerResult>
```

Starts the camera picker and enters the corresponding mode based on the media type. This API uses a promise to return the result.

> **NOTE:** 
> 
> When an application is running on a widescreen foldable device and the camera picker is launched while the device
> is unfolded, switching the device from unfolded to folded will automatically move the camera picker to the
> background.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. |
| mediaTypes | Array&lt;[PickerMediaType](arkts-camera-camerapicker-pickermediatype-e.md)&gt; | Yes | Media type. |
| pickerProfile | [PickerProfile](arkts-camera-camerapicker-pickerprofile-c.md) | Yes | Profile of the camera picker. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PickerResult](arkts-camera-camerapicker-pickerresult-c.md)&gt; | Promise used to return the processing result ([PickerResult](arkts-camera-camerapicker-pickerresult-c.md)) of the camera picker. |

**Examples**

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
import { camera } from '@kit.CameraKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function demo(context: Context) {
  try {
    let pickerProfile: cameraPicker.PickerProfile = {
      cameraPosition: camera.CameraPosition.CAMERA_POSITION_BACK
    };
    let pickerResult: cameraPicker.PickerResult = await cameraPicker.pick(context,
      [cameraPicker.PickerMediaType.PHOTO, cameraPicker.PickerMediaType.VIDEO], pickerProfile);
    console.info("the pick pickerResult is:" + JSON.stringify(pickerResult));
  } catch (error) {
    let err = error as BusinessError;
    console.error(`the pick call failed. error code: ${err.code}`);
  }
}
```
