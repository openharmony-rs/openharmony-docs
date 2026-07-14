# AudioHapticPlayer

音振播放器，提供音振协同播放功能。在调用AudioHapticPlayer的接口前，需要先通过
[createPlayer](arkts-audio-audiohapticmanager-i.md#createplayer-1)创建
实例。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## enableHapticsInSilentMode

```TypeScript
enableHapticsInSilentMode(enable: boolean): void
```

Enable haptics when the ringer mode is silent mode.
这个方法只能在播放器start前，或stop后release前调用

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | use { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit in current state. |

## isHapticsIntensityAdjustmentSupported

```TypeScript
isHapticsIntensityAdjustmentSupported(): boolean
```

Check whether the device supports haptics intensity adjustment.

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - {@code true} means supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## isHapticsRampSupported

```TypeScript
isHapticsRampSupported(): boolean
```

Check whether the device supports haptics intensity ramp effect.

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - {@code true} means supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## setHapticsIntensity

```TypeScript
setHapticsIntensity(intensity: number): Promise<void>
```

Set haptics intensity for this player. This method uses a promise to return the result.
这个方法只能在播放器释放前调用，并且每次播放过程只能设置一次。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intensity | number | 是 | Target Haptics intensity. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Function is not supported in current device. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit in current state. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-参数超过取值范围) | Parameter out of range. |

## setHapticsRamp

```TypeScript
setHapticsRamp(duration: number, startIntensity: number, endIntensity: number): Promise<void>
```

Set haptics intensity ramp effect for this player. This method uses a promise to return the result.
这个方法只能在播放器start前，或stop后release前调用

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | number | 是 | ramp duration to set, unit is milliseconds.The value should be an integer, and not less than 100. |
| startIntensity | number | 是 | Starting intensity for Haptics ramp to set.The value ranges from 0.00 to 1.00. 1.00 indicates the maximum intensity (100%). |
| endIntensity | number | 是 | End intensity for haptics ramp to set.The value ranges from 0.00 to 1.00. 1.00 indicates the maximum intensity (100%). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Function is not supported in current device. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit in current state. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-参数超过取值范围) | Parameter out of range. |

