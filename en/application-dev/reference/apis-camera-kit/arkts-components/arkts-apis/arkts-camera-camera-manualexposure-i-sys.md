# ManualExposure

ManualExposure extends [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md) Provides APIs to obtain and set the exposure duration.

**Inheritance/Implementation:** ManualExposure extends [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md)

**Since:** 24

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getExposure

```TypeScript
getExposure(): number
```

Obtains the manual exposure duration in use.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | The current exposure value, in units of ms |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
function getExposure(nightPhotoSession: camera.NightPhotoSession): number | undefined {
  let exposureRange: Array<number> = nightPhotoSession.getSupportedExposureRange();
  if (exposureRange === undefined || exposureRange.length <= 0) {
    return undefined;
  }
  let exposure: number = nightPhotoSession.getExposure();
  return exposure;
}
```

## setExposure

```TypeScript
setExposure(exposure: number): void
```

Sets the manual exposure duration. Before using this API, call [getSupportedExposureRange](arkts-camera-camera-manualexposurequery-i-sys.md#getsupportedexposurerange) to obtain the supported manual exposure durations, in ms.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| exposure | number | Yes | Manual exposure duration, which must be one of the supported durations obtained by running [getSupportedExposureRange](arkts-camera-camera-manualexposurequery-i-sys.md#getsupportedexposurerange). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed.<br>**Applicable version:** 12 and later |
