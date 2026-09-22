# AudioHapticPlayer

```TypeScript
interface AudioHapticPlayer
```

音振播放器，提供音振协同播放功能。在调用AudioHapticPlayer的接口前，需要先通过[createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer)创建实例。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## 导入模块

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## enableHapticsInSilentMode

```TypeScript
enableHapticsInSilentMode(enable: boolean): void
```

设置静音模式下是否开启振动。

> **注意：**
> 
> 该方法必须在释放音振播放器前使用，不能在播放中调用。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否在静音模式下开启振动。true表示在静音模式下开启振动，false表示在静音模式下不开启振动。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit in current state. |

## isHapticsIntensityAdjustmentSupported

```TypeScript
isHapticsIntensityAdjustmentSupported(): boolean
```

查询设备是否可以调整振动幅度。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 设备是否可以调整振动幅度。true表示可以调整振动幅度，false表示不可以调整振动幅度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## isHapticsRampSupported

```TypeScript
isHapticsRampSupported(): boolean
```

查询设备是否可以设置振动渐变。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 设备是否可以设置振动渐变。true表示设备可以设置振动渐变，false表示设备不可以设置振动渐变。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## setHapticsIntensity

```TypeScript
setHapticsIntensity(intensity: number): Promise<void>
```

设置音振播放器的振幅。使用Promise异步回调。

> **注意：**
> 
> 该方法需在音振播放器释放前调用，且每次播放仅支持调用一次。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intensity | number | 是 | 取值范围为[0.00, 1.00]，其中1.00表示最大振幅（100%）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

设置音振播放器渐变播放。使用Promise异步回调。

> **注意：**
> 
> - 该方法需在音振协同播放器播放前/后，以及释放前使用。
> 
> - 该方法仅能调用一次。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | number | 是 | 渐变时间段，单位为毫秒（ms），值必须为整数，且不能小于100ms。 |
| startIntensity | number | 是 | 起始振动幅度，取值范围为[0.00, 1.00]，其中1.00表示最大振幅（100%）。 |
| endIntensity | number | 是 | 结束振动幅度，取值范围为[0.00, 1.00]，其中1.00表示最大振幅（100%）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Function is not supported in current device. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit in current state. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-参数超过取值范围) | Parameter out of range. |
