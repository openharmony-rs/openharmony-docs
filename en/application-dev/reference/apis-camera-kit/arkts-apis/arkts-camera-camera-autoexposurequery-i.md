# AutoExposureQuery

AutoExposureQuery provides APIs to query the automatic exposure feature of a camera device.  
> 
> - In this version, a compatibility change was made that preserved the initial version information of inner elements. As a result, you might see outer element's

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getExposureBiasRange

```TypeScript
getExposureBiasRange(): Array<number>
```

Obtains the exposure compensation values of the camera device.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Array of compensation values. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

## isExposureMeteringModeSupported

```TypeScript
isExposureMeteringModeSupported(aeMeteringMode: ExposureMeteringMode): boolean
```

Checks whether the specified exposure metering mode is supported.

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aeMeteringMode | [ExposureMeteringMode](arkts-camera-camera-exposuremeteringmode-e.md) | Yes | Exposure metering mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the exposure metering mode is supported. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 12 - 23 |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect.<br>**Applicable version:** 12 - 23 |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

## isExposureModeSupported

```TypeScript
isExposureModeSupported(aeMode: ExposureMode): boolean
```

Checks whether an exposure mode is supported.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aeMode | [ExposureMode](arkts-camera-camera-exposuremode-e.md) | Yes | Exposure mode. If the input parameter is null or undefined, it is treated as 0 and exposure is locked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the exposure mode. **true** if supported, **false** otherwise. If the operation fails, undefined is returned and an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |
