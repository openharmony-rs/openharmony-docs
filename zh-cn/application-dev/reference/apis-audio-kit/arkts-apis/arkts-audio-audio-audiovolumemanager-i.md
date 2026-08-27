# AudioVolumeManager

音量管理。在使用AudioVolumeManager的接口前，需要使用 [getVolumeManager](arkts-audio-audio-audiomanager-i.md#getvolumemanager)获取AudioVolumeManager实例。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAppVolumePercentage

```TypeScript
getAppVolumePercentage(): Promise<number>
```

获取应用的音量（范围为[0, 100]）。使用Promise异步回调。

**起始版本：** 19

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回应用的音量。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeManager.getAppVolumePercentage().then((value: number) => {
  console.info(`Succeeded in obtaining the app volume percentage, appVolumePercentage: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the app volume percentage. Code: ${err.code}, message: ${err.message}`);
});
```

## getMaxVolumeByStream

```TypeScript
getMaxVolumeByStream(streamUsage: StreamUsage): number
```

获取指定音频流的最大音量。

**起始版本：** 20

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 需要获取的最大音量值的音频流。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 音量值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取指定音频流的最大音量。
try {
  let volume: number = audio.getAudioManager().getVolumeManager().getMaxVolumeByStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in obtaining the maximum volume by stream, maxVolume: ${volume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the maximum volume by stream. Code: ${error.code}, message: ${error.message}`);
}
```

## getMinVolumeByStream

```TypeScript
getMinVolumeByStream(streamUsage: StreamUsage): number
```

获取指定音频流的最小音量。

**起始版本：** 20

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 需要获取的最小音量值的音频流。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 音量值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取指定音频流的最小音量。
try {
  let volume: number = audio.getAudioManager().getVolumeManager().getMinVolumeByStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in obtaining the minimum volume by stream, minVolume: ${volume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the minimum volume by stream. Code: ${error.code}, message: ${error.message}`);
}
```

## getVolumeByStream

```TypeScript
getVolumeByStream(streamUsage: StreamUsage): number
```

获取指定音频流的音量。

**起始版本：** 20

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 需要获取音量值的音频流。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 音量值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取指定音频流的音量值。
try {
  let volume: number = audio.getAudioManager().getVolumeManager().getVolumeByStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in obtaining the volume by stream, volume: ${volume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume by stream. Code: ${error.code}, message: ${error.message}`);
}
```

## getVolumeGroupManager

```TypeScript
getVolumeGroupManager(groupId: number, callback: AsyncCallback<AudioVolumeGroupManager>): void
```

获取音频组音量管理器实例。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupId | number | 是 | 音量组id，默认使用DEFAULT_VOLUME_GROUP_ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i.md)&gt; | 是 | 回调函数。当获取音频组音量管理器实例成功，err为undefined，data为获取到的音频组音量管理器实例；否则为错 误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let groupId: number = audio.DEFAULT_VOLUME_GROUP_ID;
let audioVolumeGroupManager: audio.AudioVolumeGroupManager;

audioVolumeManager.getVolumeGroupManager(groupId, (err: BusinessError, value: audio.AudioVolumeGroupManager) => {
  if (err) {
    console.error(`Failed to obtain the volume group manager. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  audioVolumeGroupManager = value;
  console.info('Succeeded in obtaining the volume group manager.');
});
```

## getVolumeGroupManager

```TypeScript
getVolumeGroupManager(groupId: number): Promise<AudioVolumeGroupManager>
```

获取音频组音量管理器实例。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupId | number | 是 | 音量组id，默认使用DEFAULT_VOLUME_GROUP_ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i.md)&gt; | Promise对象，返回音频组音量管理器实例。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let groupId: number = audio.DEFAULT_VOLUME_GROUP_ID;
let audioVolumeGroupManager: audio.AudioVolumeGroupManager;

audioVolumeManager.getVolumeGroupManager(groupId).then((value: audio.AudioVolumeGroupManager) => {
  audioVolumeGroupManager = value;
  console.info('Succeeded in obtaining the volume group manager.');
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the volume group manager. Code: ${err.code}, message: ${err.message}`);
});
```

## getVolumeGroupManagerSync

```TypeScript
getVolumeGroupManagerSync(groupId: number): AudioVolumeGroupManager
```

获取音频组音量管理器实例。同步返回结果。

**起始版本：** 10

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupId | number | 是 | 音量组id，默认使用DEFAULT_VOLUME_GROUP_ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i.md) | 音频组音量管理器实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioVolumeGroupManager: audio.AudioVolumeGroupManager = audioVolumeManager.getVolumeGroupManagerSync(audio.DEFAULT_VOLUME_GROUP_ID);
  console.info('Succeeded in obtaining the volume group manager.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume group manager. Code: ${error.code}, message: ${error.message}`);
}
```

## getVolumeInUnitOfDbByStream

```TypeScript
getVolumeInUnitOfDbByStream(streamUsage: StreamUsage, volumeLevel: number, device: DeviceType): number
```

获取系统通过音频流、音量等级和设备类型计算出的音量dB值。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流。 |
| volumeLevel | number | 是 | 音量等级。 |
| device | DeviceType | 是 | 设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 音频流的音量dB值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取系统通过音频流、音量等级和设备类型计算出的音量dB值。
try {
  let volumeInDb: number = audio.getAudioManager().getVolumeManager().getVolumeInUnitOfDbByStream(audio.StreamUsage.STREAM_USAGE_MUSIC, 5, audio.DeviceType.SPEAKER);
  console.info(`Succeeded in obtaining the volume in dB by stream, volumeInDb: ${volumeInDb}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume in dB by stream. Code: ${error.code}, message: ${error.message}`);
}
```

## isSystemMutedForStream

```TypeScript
isSystemMutedForStream(streamUsage: StreamUsage): boolean
```

检查指定音频流是否静音。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 检查是否为静音的音频流。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 音频流是否为静音状态，true表示音频流已静音，false表示音频流未静音。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 检查指定音频流是否静音。
try {
  let isMuted: boolean = audio.getAudioManager().getVolumeManager().isSystemMutedForStream(audio.StreamUsage.STREAM_USAGE_MUSIC);
  console.info(`Succeeded in checking whether the system is muted for the stream, isMuted: ${isMuted}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the system is muted for the stream. Code: ${error.code}, message: ${error.message}`);
}
```

## off('volumeChange')

```TypeScript
off(type: 'volumeChange', callback?: Callback<VolumeEvent>): void
```

取消监听系统音量变化事件。使用callback异步回调。

> **说明：**
> 
> 从API version 12开始支持，从API version 20开始废弃，建议使用
> [off('streamVolumeChange')](#offstreamvolumechange)替代。

**起始版本：** 12

**废弃版本：** 20

**替代接口：** streamVolumeChange

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'volumeChange' | 是 | 事件回调类型，支持的事件为'volumeChange'，当取消监听系统音量变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 否 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters missing; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('appVolumeChange')

```TypeScript
off(type: 'appVolumeChange', callback?: Callback<VolumeEvent>): void
```

取消监听当前应用的应用级音量变化事件。使用callback异步回调。

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'appVolumeChange' | 是 | 事件回调类型，支持的事件为'appVolumeChange'，当取消监听当前应用的应用级音量变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 否 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('streamVolumeChange')

```TypeScript
off(type: 'streamVolumeChange', callback?: Callback<StreamVolumeEvent>): void
```

取消监听系统音频流音量变化事件（当系统音频流音量发生变化时触发）。使用callback异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'streamVolumeChange' | 是 | 事件回调类型，支持的事件为'streamVolumeChange'，当取消监听系统音量变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StreamVolumeEvent](arkts-audio-audio-streamvolumeevent-i.md)&gt; | 否 | 回调函数，返回变化后的音量信息。 |

## on('volumeChange')

```TypeScript
on(type: 'volumeChange', callback: Callback<VolumeEvent>): void
```

监听系统音量变化事件（当系统音量发生变化时触发）。使用callback异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [on('streamVolumeChange')](#onstreamvolumechange)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** streamVolumeChange

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'volumeChange' | 是 | 事件回调类型，支持的事件为'volumeChange'，当系统音量发生变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 是 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('appVolumeChange')

```TypeScript
on(type: 'appVolumeChange', callback: Callback<VolumeEvent>): void
```

监听当前应用的应用级音量变化事件（当应用级音量发生变化时触发）。使用callback异步回调。

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'appVolumeChange' | 是 | 事件回调类型，支持的事件为'appVolumeChange'，当应用级音量发生变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 是 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('streamVolumeChange')

```TypeScript
on(type: 'streamVolumeChange', streamUsage: StreamUsage, callback: Callback<StreamVolumeEvent>): void
```

监听系统音频流音量变化事件（当系统音频流音量发生变化时触发）。使用callback异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'streamVolumeChange' | 是 | 事件回调类型，支持的事件为'streamVolumeChange'，当系统音量发生变化时，触发该事件。 |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | 音频流使用类型。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StreamVolumeEvent](arkts-audio-audio-streamvolumeevent-i.md)&gt; | 是 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setAppVolumePercentage

```TypeScript
setAppVolumePercentage(volume: number): Promise<void>
```

设置应用的音量（范围为[0, 100]）。使用Promise异步回调。

**起始版本：** 19

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 要设置的音量值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Crash or blocking occurs in system process. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeManager.setAppVolumePercentage(20).then(() => {
  console.info('Succeeded in setting the app volume percentage.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the app volume percentage. Code: ${err.code}, message: ${err.message}`);
});
```
