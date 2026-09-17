# ManualIsoQuery

Provides APIs to check whether a camera device supports manual ISO setting and obtain the ISO range supported by the device.

**Since:** 24

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getIsoRange

```TypeScript
getIsoRange(): Array<number>
```

Obtains the supported ISO range.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | ISO range. The value range is [50, 100, ..., 6400]. The actual value depends on the bottom-layer capability. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getIsoRange(professionalPhotoSession: camera.ProfessionalPhotoSession): Array<number> {
  let isoRange: Array<number> = [];
  try {
    isoRange = professionalPhotoSession.getIsoRange();
  } catch (error) {
    // Return the error code error.code and handle it on failure.
    let err = error as BusinessError;
    console.error(`The getIsoRange call failed. error code: ${err.code}`);
  }
  return isoRange;
}
```

## isManualIsoSupported

```TypeScript
isManualIsoSupported(): boolean
```

Checks whether manual ISO setting is supported.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of manual ISO setting. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isManualIsoSupported(professionalPhotoSession: camera.ProfessionalPhotoSession): boolean {
  let status: boolean = false;
  try {
    status = professionalPhotoSession.isManualIsoSupported();
  } catch (error) {
    // Return the error code error.code and handle it on failure.
    let err = error as BusinessError;
    console.error(`The isManualIsoSupported call failed. error code: ${err.code}`);
  }
  return status;
}
```
