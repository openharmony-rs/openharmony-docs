# FocusQuery

FocusQuery provides APIs to check whether a focus mode is supported.

> **NOTE:** 
> 
> - This interface was first introduced in API version 12. In this version, a compatibility change was made that preserved the initial version information of inner elements. As a result, you might see outer element's

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isFocusAssistSupported

```TypeScript
isFocusAssistSupported(): boolean
```

Checks whether the focus assist is supported.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the focus assist. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isFocusAssistSupported(professionalPhotoSession: camera.ProfessionalPhotoSession): boolean {
  let status: boolean = false;
  try {
    status = professionalPhotoSession.isFocusAssistSupported();
  } catch (error) {
    // Return the error code error.code and handle it on failure.
    let err = error as BusinessError;
    console.error(`The isFocusAssistSupported call failed. error code: ${err.code}`);
  }
  return status;
}
```

## isFocusDrivenTypeSupported

```TypeScript
isFocusDrivenTypeSupported(type: FocusDrivenType): boolean
```

Checks whether a focus drive type is supported.

**Since:** 15

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [FocusDrivenType](arkts-camera-camera-focusdriventype-e-sys.md) | Yes | Focus drive type. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the focus drive type. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isFocusDrivenTypeSupported(session: camera.VideoSessionForSys, type: camera.FocusDrivenType): boolean {
  let status: boolean = false;
  try {
    status = session.isFocusDrivenTypeSupported(type);
  } catch (error) {
    // Return the error code error.code and handle it on failure.
    let err = error as BusinessError;
    console.error(`The isFocusDrivenTypeSupported call failed. error code: ${err.code}`);
  }
  return status;
}
```

## isFocusRangeTypeSupported

```TypeScript
isFocusRangeTypeSupported(type: FocusRangeType): boolean
```

Checks whether a focus range type is supported.

**Since:** 15

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [FocusRangeType](arkts-camera-camera-focusrangetype-e-sys.md) | Yes | Focus range type. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the focus range type. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isFocusRangeTypeSupported(session: camera.VideoSessionForSys, type: camera.FocusRangeType): boolean {
  let status: boolean = false;
  try {
    status = session.isFocusRangeTypeSupported(type);
  } catch (error) {
    // Return the error code error.code and handle it on failure.
    let err = error as BusinessError;
    console.error(`The isFocusRangeTypeSupported call failed. error code: ${err.code}`);
  }
  return status;
}
```
