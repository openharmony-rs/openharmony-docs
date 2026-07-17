# AudioVolumeGroupManager

管理音频组音量。

在使用AudioVolumeGroupManager的接口之前，需先通过[getVolumeGroupManager](arkts-audio-audio-audiovolumemanager-i.md#getvolumegroupmanager-1)获取AudioVolumeGroupManager实例。

> **说明：**  
>  
> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

<!--Device-audio-interface AudioVolumeGroupManager--><!--Device-audio-interface AudioVolumeGroupManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getMaxAmplitudeForInputDevice

```TypeScript
getMaxAmplitudeForInputDevice(inputDevice: AudioDeviceDescriptor): Promise<number>
```

获取输入设备音频流的最大电平值，取值范围为[0, 1]。使用Promise异步回调。

**起始版本：** 12

<!--Device-AudioVolumeGroupManager-getMaxAmplitudeForInputDevice(inputDevice: AudioDeviceDescriptor): Promise<double>--><!--Device-AudioVolumeGroupManager-getMaxAmplitudeForInputDevice(inputDevice: AudioDeviceDescriptor): Promise<double>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 获取最大电平值的设备信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回对应设备的电平值，大小在[0, 1]之间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

## getMaxAmplitudeForOutputDevice

```TypeScript
getMaxAmplitudeForOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<number>
```

获取输出设备音频流的最大电平值，取值范围为[0, 1]。使用Promise异步回调。

**起始版本：** 12

<!--Device-AudioVolumeGroupManager-getMaxAmplitudeForOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<double>--><!--Device-AudioVolumeGroupManager-getMaxAmplitudeForOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<double>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 获取最大电平值的设备信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回对应设备的电平值，大小在[0, 1]之间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

## getMaxVolume

```TypeScript
getMaxVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void
```

获取指定流的最大音量等级。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getMaxVolumeByStream

<!--Device-AudioVolumeGroupManager-getMaxVolume(volumeType: AudioVolumeType, callback: AsyncCallback<int>): void--><!--Device-AudioVolumeGroupManager-getMaxVolume(volumeType: AudioVolumeType, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取指定流的最大音量成功，err为undefined，data为获取到的指定流的最大音量等级；否则为错误对象。 |

## getMaxVolume

```TypeScript
getMaxVolume(volumeType: AudioVolumeType): Promise<number>
```

获取指定流的最大音量等级。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getMaxVolumeByStream

<!--Device-AudioVolumeGroupManager-getMaxVolume(volumeType: AudioVolumeType): Promise<int>--><!--Device-AudioVolumeGroupManager-getMaxVolume(volumeType: AudioVolumeType): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回最大音量等级。 |

## getMaxVolumeSync

```TypeScript
getMaxVolumeSync(volumeType: AudioVolumeType): number
```

获取指定流的最大音量等级。同步返回结果。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getMaxVolumeByStream

<!--Device-AudioVolumeGroupManager-getMaxVolumeSync(volumeType: AudioVolumeType): int--><!--Device-AudioVolumeGroupManager-getMaxVolumeSync(volumeType: AudioVolumeType): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回最大音量等级。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getMinVolume

```TypeScript
getMinVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void
```

获取指定流的最小音量等级。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getMinVolumeByStream

<!--Device-AudioVolumeGroupManager-getMinVolume(volumeType: AudioVolumeType, callback: AsyncCallback<int>): void--><!--Device-AudioVolumeGroupManager-getMinVolume(volumeType: AudioVolumeType, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取指定流的最小音量成功，err为undefined，data为获取到的指定流的最小音量等级；否则为错误对象。 |

## getMinVolume

```TypeScript
getMinVolume(volumeType: AudioVolumeType): Promise<number>
```

获取指定流的最小音量等级。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getMinVolumeByStream

<!--Device-AudioVolumeGroupManager-getMinVolume(volumeType: AudioVolumeType): Promise<int>--><!--Device-AudioVolumeGroupManager-getMinVolume(volumeType: AudioVolumeType): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回最小音量等级。 |

## getMinVolumeSync

```TypeScript
getMinVolumeSync(volumeType: AudioVolumeType): number
```

获取指定流的最小音量等级。同步返回结果。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getMinVolumeByStream

<!--Device-AudioVolumeGroupManager-getMinVolumeSync(volumeType: AudioVolumeType): int--><!--Device-AudioVolumeGroupManager-getMinVolumeSync(volumeType: AudioVolumeType): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回最小音量等级。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getRingerMode

```TypeScript
getRingerMode(callback: AsyncCallback<AudioRingMode>): void
```

获取铃声模式。使用callback异步回调。

**起始版本：** 9

<!--Device-AudioVolumeGroupManager-getRingerMode(callback: AsyncCallback<AudioRingMode>): void--><!--Device-AudioVolumeGroupManager-getRingerMode(callback: AsyncCallback<AudioRingMode>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AudioRingMode> | 是 | 回调函数。当获取铃声模式成功，err为undefined，data为获取到的铃声模式；否则为错误对象。 |

## getRingerMode

```TypeScript
getRingerMode(): Promise<AudioRingMode>
```

获取铃声模式。使用Promise异步回调。

**起始版本：** 9

<!--Device-AudioVolumeGroupManager-getRingerMode(): Promise<AudioRingMode>--><!--Device-AudioVolumeGroupManager-getRingerMode(): Promise<AudioRingMode>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AudioRingMode> | Promise对象，返回系统的铃声模式。 |

## getRingerModeSync

```TypeScript
getRingerModeSync(): AudioRingMode
```

获取铃声模式。同步返回结果。

**起始版本：** 10

<!--Device-AudioVolumeGroupManager-getRingerModeSync(): AudioRingMode--><!--Device-AudioVolumeGroupManager-getRingerModeSync(): AudioRingMode-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | 返回系统的铃声模式。 |

## getSystemVolumeInDb

```TypeScript
getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType, callback: AsyncCallback<number>): void
```

获取音量增益dB值。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getVolumeInUnitOfDbByStream

<!--Device-AudioVolumeGroupManager-getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: int, device: DeviceType, callback: AsyncCallback<double>): void--><!--Device-AudioVolumeGroupManager-getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: int, device: DeviceType, callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| volumeLevel | number | 是 | 音量等级。 |
| device | [DeviceType](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-devicetype-e.md) | 是 | 设备类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取音量增益dB值成功，err为undefined，data为获取到的音量增益dB值；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by callback. |

## getSystemVolumeInDb

```TypeScript
getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType): Promise<number>
```

获取音量增益dB值。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getVolumeInUnitOfDbByStream

<!--Device-AudioVolumeGroupManager-getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: int, device: DeviceType): Promise<double>--><!--Device-AudioVolumeGroupManager-getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: int, device: DeviceType): Promise<double>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| volumeLevel | number | 是 | 音量等级。 |
| device | [DeviceType](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-devicetype-e.md) | 是 | 设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回对应的音量增益dB值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

## getSystemVolumeInDbSync

```TypeScript
getSystemVolumeInDbSync(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType): number
```

获取音量增益dB值。同步返回结果。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getVolumeInUnitOfDbByStream

<!--Device-AudioVolumeGroupManager-getSystemVolumeInDbSync(volumeType: AudioVolumeType, volumeLevel: int, device: DeviceType): double--><!--Device-AudioVolumeGroupManager-getSystemVolumeInDbSync(volumeType: AudioVolumeType, volumeLevel: int, device: DeviceType): double-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| volumeLevel | number | 是 | 音量等级。 |
| device | [DeviceType](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-devicetype-e.md) | 是 | 设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回对应的音量增益dB值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getVolume

```TypeScript
getVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void
```

获取指定流的音量等级。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getVolumeByStream

<!--Device-AudioVolumeGroupManager-getVolume(volumeType: AudioVolumeType, callback: AsyncCallback<int>): void--><!--Device-AudioVolumeGroupManager-getVolume(volumeType: AudioVolumeType, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取指定流的音量成功，err为undefined，data为获取到的指定流的音量等级；否则为错误对象。指定流的音量等级范围可通过[getMinVolume](arkts-audio-audio-audiovolumegroupmanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audio-audiovolumegroupmanager-i.md#getmaxvolume-1)获取。 |

## getVolume

```TypeScript
getVolume(volumeType: AudioVolumeType): Promise<number>
```

获取指定流的音量等级。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getVolumeByStream

<!--Device-AudioVolumeGroupManager-getVolume(volumeType: AudioVolumeType): Promise<int>--><!--Device-AudioVolumeGroupManager-getVolume(volumeType: AudioVolumeType): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回指定流的音量等级。指定流的音量等级范围可通过[getMinVolume](arkts-audio-audio-audiovolumegroupmanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audio-audiovolumegroupmanager-i.md#getmaxvolume-1)获取。 |

## getVolumeSync

```TypeScript
getVolumeSync(volumeType: AudioVolumeType): number
```

获取指定流的音量等级。同步返回结果。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getVolumeByStream

<!--Device-AudioVolumeGroupManager-getVolumeSync(volumeType: AudioVolumeType): int--><!--Device-AudioVolumeGroupManager-getVolumeSync(volumeType: AudioVolumeType): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定流的音量等级。指定流的音量等级范围可通过[getMinVolume](arkts-audio-audio-audiovolumegroupmanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audio-audiovolumegroupmanager-i.md#getmaxvolume-1)获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## isMicrophoneMute

```TypeScript
isMicrophoneMute(callback: AsyncCallback<boolean>): void
```

获取麦克风静音状态。使用callback异步回调。

**起始版本：** 9

<!--Device-AudioVolumeGroupManager-isMicrophoneMute(callback: AsyncCallback<boolean>): void--><!--Device-AudioVolumeGroupManager-isMicrophoneMute(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。当获取麦克风静音状态成功，err为undefined，data为true表示静音，false表示非静音；否则为错误对象。 |

## isMicrophoneMute

```TypeScript
isMicrophoneMute(): Promise<boolean>
```

获取麦克风静音状态。使用Promise异步回调。

**起始版本：** 9

<!--Device-AudioVolumeGroupManager-isMicrophoneMute(): Promise<boolean>--><!--Device-AudioVolumeGroupManager-isMicrophoneMute(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示麦克风被静音；返回false表示麦克风未被静音。 |

## isMicrophoneMuteSync

```TypeScript
isMicrophoneMuteSync(): boolean
```

获取麦克风静音状态。同步返回结果。

**起始版本：** 10

<!--Device-AudioVolumeGroupManager-isMicrophoneMuteSync(): boolean--><!--Device-AudioVolumeGroupManager-isMicrophoneMuteSync(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 系统麦克风静音状态。返回true表示静音，返回false表示非静音。 |

## isMute

```TypeScript
isMute(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void
```

获取指定音量流静音状态。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** isSystemMutedForStream

<!--Device-AudioVolumeGroupManager-isMute(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void--><!--Device-AudioVolumeGroupManager-isMute(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。当获取指定音量流静音状态成功，err为undefined，data为true表示静音，false表示非静音；否则为错误对象。 |

## isMute

```TypeScript
isMute(volumeType: AudioVolumeType): Promise<boolean>
```

获取指定音量流是否被静音。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** isSystemMutedForStream

<!--Device-AudioVolumeGroupManager-isMute(volumeType: AudioVolumeType): Promise<boolean>--><!--Device-AudioVolumeGroupManager-isMute(volumeType: AudioVolumeType): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示静音；返回false表示非静音。 |

## isMuteSync

```TypeScript
isMuteSync(volumeType: AudioVolumeType): boolean
```

获取指定音量流是否被静音。同步返回结果。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** isSystemMutedForStream

<!--Device-AudioVolumeGroupManager-isMuteSync(volumeType: AudioVolumeType): boolean--><!--Device-AudioVolumeGroupManager-isMuteSync(volumeType: AudioVolumeType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 流静音状态。返回true表示静音，返回false表示非静音。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## isVolumeUnadjustable

```TypeScript
isVolumeUnadjustable(): boolean
```

获取固定音量模式开关状态，打开时进入固定音量模式，此时音量固定无法被调节。同步返回结果。

**起始版本：** 10

<!--Device-AudioVolumeGroupManager-isVolumeUnadjustable(): boolean--><!--Device-AudioVolumeGroupManager-isVolumeUnadjustable(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 固定音量模式开关状态。返回true表示固定音量模式，返回false表示非固定音量模式。 |

## off('ringerModeChange')

```TypeScript
off(type: 'ringerModeChange', callback?: Callback<AudioRingMode>): void
```

取消监听铃声模式变化事件。使用callback异步回调。

**起始版本：** 18

<!--Device-AudioVolumeGroupManager-off(type: 'ringerModeChange', callback?: Callback<AudioRingMode>): void--><!--Device-AudioVolumeGroupManager-off(type: 'ringerModeChange', callback?: Callback<AudioRingMode>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'ringerModeChange' | 是 | 事件回调类型，支持的事件为'ringerModeChange'，当取消监听铃声模式变化事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioRingMode> | 否 | 回调函数，返回变化后的铃音模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('micStateChange')

```TypeScript
off(type: 'micStateChange', callback?: Callback<MicStateChangeEvent>): void
```

取消监听系统麦克风状态更改事件。使用callback异步回调。

**起始版本：** 12

<!--Device-AudioVolumeGroupManager-off(type: 'micStateChange', callback?: Callback<MicStateChangeEvent>): void--><!--Device-AudioVolumeGroupManager-off(type: 'micStateChange', callback?: Callback<MicStateChangeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'micStateChange' | 是 | 事件回调类型，支持的事件为'micStateChange'，当取消监听系统麦克风状态更改事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<MicStateChangeEvent> | 否 | 回调函数，返回变更后的麦克风状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters missing;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('ringerModeChange')

```TypeScript
on(type: 'ringerModeChange', callback: Callback<AudioRingMode>): void
```

监听铃声模式变化事件（当[AudioRingMode](arkts-audio-audio-audioringmode-e.md)发生变化时触发）。使用callback异步回调。

**起始版本：** 9

<!--Device-AudioVolumeGroupManager-on(type: 'ringerModeChange', callback: Callback<AudioRingMode>): void--><!--Device-AudioVolumeGroupManager-on(type: 'ringerModeChange', callback: Callback<AudioRingMode>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'ringerModeChange' | 是 | 事件回调类型，支持的事件为'ringerModeChange'，当铃声模式发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioRingMode> | 是 | 回调函数，返回变化后的铃音模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('micStateChange')

```TypeScript
on(type: 'micStateChange', callback: Callback<MicStateChangeEvent>): void
```

监听系统麦克风状态更改事件（当检测到系统麦克风状态发生改变时触发）。使用callback异步回调。

目前此订阅接口在单进程多AudioManager实例的使用场景下，仅最后一个实例的订阅生效，其他实例的订阅会被覆盖（即使最后一个实例没有进行订阅）。因此，推荐使用单一AudioManager实例进行开发。

**起始版本：** 9

<!--Device-AudioVolumeGroupManager-on(type: 'micStateChange', callback: Callback<MicStateChangeEvent>): void--><!--Device-AudioVolumeGroupManager-on(type: 'micStateChange', callback: Callback<MicStateChangeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'micStateChange' | 是 | 事件回调类型，支持的事件为'micStateChange'，当检测到系统麦克风状态发生改变时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<MicStateChangeEvent> | 是 | 回调函数，返回变更后的麦克风状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setMicrophoneMute

```TypeScript
setMicrophoneMute(mute: boolean, callback: AsyncCallback<void>): void
```

设置麦克风静音状态。使用callback异步回调。

> **说明：**  
>  
> 从API version 9开始支持，从API version 11开始废弃。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeGroupManager-setMicrophoneMute(mute: boolean, callback: AsyncCallback<void>): void--><!--Device-AudioVolumeGroupManager-setMicrophoneMute(mute: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 是否设置麦克风为静音状态。true表示静音，false表示非静音。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置麦克风静音状态成功，err为undefined，否则为错误对象。 |

## setMicrophoneMute

```TypeScript
setMicrophoneMute(mute: boolean): Promise<void>
```

设置麦克风静音状态。使用Promise异步回调。

> **说明：**  
>  
> 从API version 9开始支持，从API version 11开始废弃。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeGroupManager-setMicrophoneMute(mute: boolean): Promise<void>--><!--Device-AudioVolumeGroupManager-setMicrophoneMute(mute: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 是否设置麦克风为静音状态。true表示静音，false表示非静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

