# AudioHapticPlayer

Implements audio-haptic playback. Before calling any API in AudioHapticPlayer, you must use [createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer) to create an AudioHapticPlayer instance.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

## Modules to Import

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## enableHapticsInSilentMode

```TypeScript
enableHapticsInSilentMode(enable: boolean): void
```

Enable haptics when the ringer mode is silent mode. This function should be called before player start or after stop, and before release.

**Since:** 20

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | use `true` if application want to enable this feature. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operate not permit in current state. |

## isHapticsIntensityAdjustmentSupported

```TypeScript
isHapticsIntensityAdjustmentSupported(): boolean
```

Check whether the device supports haptics intensity adjustment.

**Since:** 20

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | `true` means supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

## isHapticsRampSupported

```TypeScript
isHapticsRampSupported(): boolean
```

Check whether the device supports haptics intensity ramp effect.

**Since:** 20

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | `true` means supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

## setHapticsIntensity

```TypeScript
setHapticsIntensity(intensity: number): Promise<void>
```

Set haptics intensity for this player. This method uses a promise to return the result. This function should be called before player release, and can only set once for each starting process.

**Since:** 20

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| intensity | number | Yes | Target Haptics intensity value. The value ranges from 0.00 to 1.00. 1.00 indicates the maximum intensity (100%). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Function is not supported in current device. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operate not permit in current state. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter out of range. |

## setHapticsRamp

```TypeScript
setHapticsRamp(duration: number, startIntensity: number, endIntensity: number): Promise<void>
```

Set haptics intensity ramp effect for this player. This method uses a promise to return the result. This function should be called before player start or after stop, and before release.

**Since:** 20

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| duration | number | Yes | ramp duration to set, unit is milliseconds. The value should be an integer, and not less than 100. |
| startIntensity | number | Yes | Starting intensity for Haptics ramp to set. The value ranges from 0.00 to 1.00. 1.00 indicates the maximum intensity (100%). |
| endIntensity | number | Yes | End intensity for haptics ramp to set. The value ranges from 0.00 to 1.00. 1.00 indicates the maximum intensity (100%). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Function is not supported in current device. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operate not permit in current state. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter out of range. |
