# WhiteBalanceQuery

WhiteBalanceQuery provides APIs to check whether a white balance mode is supported and obtain the white balance mode range supported.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getColorTintRange

```TypeScript
getColorTintRange(): Array<number>
```

Obtains the supported white balance hue adjustment range.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Hue adjustment range. If the API call fails, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

## getWhiteBalanceRange

```TypeScript
getWhiteBalanceRange(): Array<number>
```

Obtains the range of white balance values in manual white balance mode.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Range of white balance values, for example, [2800, ...,10000], in units of K (Kelvin). The actual value depends on the bottom-layer capability. If the API call fails, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 12 - 19 |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

## isWhiteBalanceModeSupported

```TypeScript
isWhiteBalanceModeSupported(mode: WhiteBalanceMode): boolean
```

Checks whether a white balance mode is supported.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [WhiteBalanceMode](arkts-camera-camera-whitebalancemode-e.md) | Yes | White balance mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the white balance mode. **true** if supported, **false** otherwise. If the API call fails, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 12 - 19 |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |
