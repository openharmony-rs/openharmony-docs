# OISQuery

```TypeScript
interface OISQuery
```

OIS (Optical Image Stabilization) query interface.

**Since:** 24

<!--Device-camera-interface OISQuery--><!--Device-camera-interface OISQuery-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getCurrentCustomOISBias

```TypeScript
getCurrentCustomOISBias(oisAxis: OISAxes): number
```

Gets the current custom bias value for the specified OIS axis.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-OISQuery-getCurrentCustomOISBias(oisAxis: OISAxes): double--><!--Device-OISQuery-getCurrentCustomOISBias(oisAxis: OISAxes): double-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| oisAxis | [OISAxes](arkts-camera-camera-oisaxes-e.md) | Yes | The OIS axis |

**Return value:**

| Type | Description |
| --- | --- |
| number | The current bias value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getCurrentOISMode

```TypeScript
getCurrentOISMode(): OISMode
```

Gets the current OIS mode.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-OISQuery-getCurrentOISMode(): OISMode--><!--Device-OISQuery-getCurrentOISMode(): OISMode-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [OISMode](arkts-camera-camera-oismode-e.md) | The current OIS mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getSupportedOISBiasRange

```TypeScript
getSupportedOISBiasRange(oisAxis: OISAxes): Array<number>
```

Gets the supported bias range for the specified OIS axis.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-OISQuery-getSupportedOISBiasRange(oisAxis: OISAxes): Array<double>--><!--Device-OISQuery-getSupportedOISBiasRange(oisAxis: OISAxes): Array<double>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| oisAxis | [OISAxes](arkts-camera-camera-oisaxes-e.md) | Yes | The OIS axis. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | The bias range. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getSupportedOISBiasStep

```TypeScript
getSupportedOISBiasStep(oisAxis: OISAxes): number
```

Gets the bias step for the specified OIS axis.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-OISQuery-getSupportedOISBiasStep(oisAxis: OISAxes): double--><!--Device-OISQuery-getSupportedOISBiasStep(oisAxis: OISAxes): double-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| oisAxis | [OISAxes](arkts-camera-camera-oisaxes-e.md) | Yes | The OIS axis. |

**Return value:**

| Type | Description |
| --- | --- |
| number | The bias step value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## isOISModeSupported

```TypeScript
isOISModeSupported(mode: OISMode): boolean
```

Checks if the specified OIS mode is supported.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-OISQuery-isOISModeSupported(mode: OISMode): boolean--><!--Device-OISQuery-isOISModeSupported(mode: OISMode): boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [OISMode](arkts-camera-camera-oismode-e.md) | Yes | The OIS mode to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the mode is supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
