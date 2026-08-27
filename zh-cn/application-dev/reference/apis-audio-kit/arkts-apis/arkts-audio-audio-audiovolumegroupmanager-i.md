# AudioVolumeGroupManager

管理音频组音量。在调用AudioVolumeGroupManager的接口前，需要先通过 [getVolumeGroupManager](arkts-audio-audio-audiovolumemanager-i.md#getvolumegroupmanager) 创建实例。

**起始版本：** 9

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

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 获取最大电平值的设备信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回对应设备的电平值，大小在[0, 1]之间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // 音源类型：Mic音频源。根据业务场景配置，参考SourceType。
  capturerFlags: 0 // 音频采集器标志。
};

audio.getAudioManager().getRoutingManager().getPreferredInputDeviceForCapturerInfo(capturerInfo).then((data) => {
  audioVolumeGroupManager.getMaxAmplitudeForInputDevice(data[0]).then((maxAmplitude) => {
    console.info(`Succeeded in obtaining the maximum amplitude for input device, maxAmplitude: ${maxAmplitude}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain the maximum amplitude for input device. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the preferred input device for capturer info. Code: ${err.code}, message: ${err.message}`);
});
```

## getMaxAmplitudeForOutputDevice

```TypeScript
getMaxAmplitudeForOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<number>
```

获取输出设备音频流的最大电平值，取值范围为[0, 1]。使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 获取最大电平值的设备信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回对应设备的电平值，大小在[0, 1]之间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // 音频流使用类型：音乐。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};

audio.getAudioManager().getRoutingManager().getPreferOutputDeviceForRendererInfo(rendererInfo).then((data) => {
  audioVolumeGroupManager.getMaxAmplitudeForOutputDevice(data[0]).then((maxAmplitude) => {
    console.info(`Succeeded in obtaining the maximum amplitude for output device, maxAmplitude: ${maxAmplitude}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain the maximum amplitude for output device. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the preferred output device for renderer info. Code: ${err.code}, message: ${err.message}`);
});
```

## getMaxVolume

```TypeScript
getMaxVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void
```

获取指定流的最大音量等级。使用callback异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [getMaxVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getmaxvolumebystream)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [getMaxVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getmaxvolumebystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取指定流的最大音量成功，err为undefined，data为获取到的指定流的最大音量等级；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.getMaxVolume(audio.AudioVolumeType.MEDIA, (err: BusinessError, value: number) => {
  if (err) {
    console.error(`Failed to obtain the maximum volume. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the maximum volume, maxVolume: ${value}.`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getMaxVolume(audio.AudioVolumeType.MEDIA, (err: BusinessError, maxVolume: number) => {
  if (err) {
    console.error(`Failed to obtain the maximum volume. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the maximum volume, maxVolume: ${maxVolume}.`);
});
```

## getMaxVolume

```TypeScript
getMaxVolume(volumeType: AudioVolumeType): Promise<number>
```

获取指定流的最大音量等级。使用Promise异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [getMaxVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getmaxvolumebystream)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [getMaxVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getmaxvolumebystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回最大音量等级。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.getMaxVolume(audio.AudioVolumeType.MEDIA).then((data: number) => {
  console.info(`Succeeded in obtaining the maximum volume, maxVolume: ${data}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the maximum volume. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getMaxVolume(audio.AudioVolumeType.MEDIA).then((maxVolume: number) => {
  console.info(`Succeeded in obtaining the maximum volume, maxVolume: ${maxVolume}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the maximum volume. Code: ${err.code}, message: ${err.message}`);
});
```

## getMaxVolumeSync

```TypeScript
getMaxVolumeSync(volumeType: AudioVolumeType): number
```

获取指定流的最大音量等级。同步返回结果。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃，建议使用
> [getMaxVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getmaxvolumebystream)替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [getMaxVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getmaxvolumebystream)

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let maxVolume: number = audioVolumeGroupManager.getMaxVolumeSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in obtaining the maximum volume, maxVolume: ${maxVolume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the maximum volume. Code: ${error.code}, message: ${error.message}`);
}
```

## getMinVolume

```TypeScript
getMinVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void
```

获取指定流的最小音量等级。使用callback异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [getMinVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getminvolumebystream)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [getMinVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getminvolumebystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取指定流的最小音量成功，err为undefined，data为获取到的指定流的最小音量等级；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.getMinVolume(audio.AudioVolumeType.MEDIA, (err: BusinessError, value: number) => {
  if (err) {
    console.error(`Failed to obtain the minimum volume. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the minimum volume, minVolume: ${value}.`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getMinVolume(audio.AudioVolumeType.MEDIA, (err: BusinessError, minVolume: number) => {
  if (err) {
    console.error(`Failed to obtain the minimum volume. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the minimum volume, minVolume: ${minVolume}.`);
});
```

## getMinVolume

```TypeScript
getMinVolume(volumeType: AudioVolumeType): Promise<number>
```

获取指定流的最小音量等级。使用Promise异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [getMinVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getminvolumebystream)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [getMinVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getminvolumebystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回最小音量等级。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.getMinVolume(audio.AudioVolumeType.MEDIA).then((value: number) => {
  console.info(`Succeeded in obtaining the minimum volume, minVolume: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the minimum volume. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getMinVolume(audio.AudioVolumeType.MEDIA).then((minVolume: number) => {
  console.info(`Succeeded in obtaining the minimum volume, minVolume: ${minVolume}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the minimum volume. Code: ${err.code}, message: ${err.message}`);
});
```

## getMinVolumeSync

```TypeScript
getMinVolumeSync(volumeType: AudioVolumeType): number
```

获取指定流的最小音量等级。同步返回结果。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃，建议使用
> [getMinVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getminvolumebystream)替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [getMinVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getminvolumebystream)

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let minVolume: number = audioVolumeGroupManager.getMinVolumeSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in obtaining the minimum volume, minVolume: ${minVolume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the minimum volume. Code: ${error.code}, message: ${error.message}`);
}
```

## getRingerMode

```TypeScript
getRingerMode(callback: AsyncCallback<AudioRingMode>): void
```

获取铃声模式。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioRingMode](arkts-audio-audio-audioringmode-e.md)&gt; | 是 | 回调函数。当获取铃声模式成功，err为undefined，data为获取到的铃声模式；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.getRingerMode((err: BusinessError, value: audio.AudioRingMode) => {
  if (err) {
    console.error(`Failed to obtain the ringer mode. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the ringer mode, ringerMode: ${value}.`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getRingerMode((err: BusinessError, ringerMode: audio.AudioRingMode) => {
  if (err) {
    console.error(`Failed to obtain the ringer mode. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the ringer mode, ringerMode: ${ringerMode}.`);
});
```

## getRingerMode

```TypeScript
getRingerMode(): Promise<AudioRingMode>
```

获取铃声模式。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioRingMode](arkts-audio-audio-audioringmode-e.md)&gt; | Promise对象，返回系统的铃声模式。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.getRingerMode().then((value: audio.AudioRingMode) => {
  console.info(`Succeeded in obtaining the ringer mode, ringerMode: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the ringer mode. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getRingerMode().then((ringerMode: audio.AudioRingMode) => {
  console.info(`Succeeded in obtaining the ringer mode, ringerMode: ${ringerMode}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the ringer mode. Code: ${err.code}, message: ${err.message}`);
});
```

## getRingerModeSync

```TypeScript
getRingerModeSync(): AudioRingMode
```

获取铃声模式。同步返回结果。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | 返回系统的铃声模式。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let ringerMode: audio.AudioRingMode = audioVolumeGroupManager.getRingerModeSync();
  console.info(`Succeeded in obtaining the ringer mode, ringerMode: ${ringerMode}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the ringer mode. Code: ${error.code}, message: ${error.message}`);
}
```

## getSystemVolumeInDb

```TypeScript
getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType, callback: AsyncCallback<number>): void
```

获取音量增益dB值。使用callback异步回调。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃，建议使用
> [getVolumeInUnitOfDbByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumeinunitofdbbystream)
> 替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [getVolumeInUnitOfDbByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumeinunitofdbbystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| volumeLevel | number | 是 | 音量等级。 |
| device | DeviceType | 是 | 设备类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取音量增益dB值成功，err为undefined，data为获取到的音量增益dB值；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by callback. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getSystemVolumeInDb(audio.AudioVolumeType.MEDIA, 3, audio.DeviceType.SPEAKER, (err: BusinessError, volumeDb: number) => {
  if (err) {
    console.error(`Failed to obtain the system volume in dB. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the system volume in dB, volumeDb: ${volumeDb}.`);
});
```

## getSystemVolumeInDb

```TypeScript
getSystemVolumeInDb(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType): Promise<number>
```

获取音量增益dB值。使用Promise异步回调。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃，建议使用
> [getVolumeInUnitOfDbByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumeinunitofdbbystream)
> 替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [getVolumeInUnitOfDbByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumeinunitofdbbystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| volumeLevel | number | 是 | 音量等级。 |
| device | DeviceType | 是 | 设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回对应的音量增益dB值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getSystemVolumeInDb(audio.AudioVolumeType.MEDIA, 3, audio.DeviceType.SPEAKER).then((volumeDb: number) => {
  console.info(`Succeeded in obtaining the system volume in dB, volumeDb: ${volumeDb}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the system volume in dB. Code: ${err.code}, message: ${err.message}`);
});
```

## getSystemVolumeInDbSync

```TypeScript
getSystemVolumeInDbSync(volumeType: AudioVolumeType, volumeLevel: number, device: DeviceType): number
```

获取音量增益dB值。同步返回结果。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃，建议使用
> [getVolumeInUnitOfDbByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumeinunitofdbbystream)
> 替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [getVolumeInUnitOfDbByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumeinunitofdbbystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| volumeLevel | number | 是 | 音量等级。 |
| device | DeviceType | 是 | 设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回对应的音量增益dB值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let volumeDb: number = audioVolumeGroupManager.getSystemVolumeInDbSync(audio.AudioVolumeType.MEDIA, 3, audio.DeviceType.SPEAKER);
  console.info(`Succeeded in obtaining the system volume in dB, volumeDb: ${volumeDb}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the system volume in dB. Code: ${error.code}, message: ${error.message}`);
}
```

## getVolume

```TypeScript
getVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void
```

获取指定流的音量等级。使用callback异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [getVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumebystream)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [getVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumebystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取指定流的音量成功，err为undefined，data为获取到的指定流的音量等级；否则为错误对象。指定流的音量等级范围可通过 [getMinVolume](#getminvolume) 和 [getMaxVolume](#getmaxvolume) 获取。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.getVolume(audio.AudioVolumeType.MEDIA, (err: BusinessError, value: number) => {
  if (err) {
    console.error(`Failed to obtain the volume. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the volume, volume: ${value}.`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getVolume(audio.AudioVolumeType.MEDIA, (err: BusinessError, volume: number) => {
  if (err) {
    console.error(`Failed to obtain the volume. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the volume, volume: ${volume}.`);
});
```

## getVolume

```TypeScript
getVolume(volumeType: AudioVolumeType): Promise<number>
```

获取指定流的音量等级。使用Promise异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [getVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumebystream)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [getVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumebystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回指定流的音量等级。指定流的音量等级范围可通过 [getMinVolume]{ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.getVolume(audio.AudioVolumeType.MEDIA).then((value: number) => {
  console.info(`Succeeded in obtaining the volume, volume: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the volume. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.getVolume(audio.AudioVolumeType.MEDIA).then((volume: number) => {
  console.info(`Succeeded in obtaining the volume, volume: ${volume}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the volume. Code: ${err.code}, message: ${err.message}`);
});
```

## getVolumeSync

```TypeScript
getVolumeSync(volumeType: AudioVolumeType): number
```

获取指定流的音量等级。同步返回结果。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃，建议使用
> [getVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumebystream)替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [getVolumeByStream](arkts-audio-audio-audiovolumemanager-i.md#getvolumebystream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定流的音量等级。指定流的音量等级范围可通过 [getMinVolume]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let volume: number = audioVolumeGroupManager.getVolumeSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in obtaining the volume, volume: ${volume}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume. Code: ${error.code}, message: ${error.message}`);
}
```

## isMicrophoneMute

```TypeScript
isMicrophoneMute(callback: AsyncCallback<boolean>): void
```

获取麦克风静音状态。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当获取麦克风静音状态成功，err为undefined，data为true表示静音，false表示非静音；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.isMicrophoneMute((err: BusinessError, value: boolean) => {
  if (err) {
    console.error(`Failed to check whether the microphone is muted. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the microphone is muted, isMuted: ${value}.`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.isMicrophoneMute((err: BusinessError, isMute: boolean) => {
  if (err) {
    console.error(`Failed to check whether the microphone is muted. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the microphone is muted, isMuted: ${isMute}.`);
});
```

## isMicrophoneMute

```TypeScript
isMicrophoneMute(): Promise<boolean>
```

获取麦克风静音状态。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象。返回true表示麦克风被静音；返回false表示麦克风未被静音。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.isMicrophoneMute().then((value: boolean) => {
  console.info(`Succeeded in checking whether the microphone is muted, isMuted: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the microphone is muted. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.isMicrophoneMute().then((isMute: boolean) => {
  console.info(`Succeeded in checking whether the microphone is muted, isMuted: ${isMute}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the microphone is muted. Code: ${err.code}, message: ${err.message}`);
});
```

## isMicrophoneMuteSync

```TypeScript
isMicrophoneMuteSync(): boolean
```

获取麦克风静音状态。同步返回结果。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 系统麦克风静音状态。返回true表示静音，返回false表示非静音。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isMute: boolean = audioVolumeGroupManager.isMicrophoneMuteSync();
  console.info(`Succeeded in checking whether the microphone is muted, isMuted: ${isMute}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the microphone is muted. Code: ${error.code}, message: ${error.message}`);
}
```

## isMute

```TypeScript
isMute(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void
```

获取指定音量流静音状态。使用callback异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [isSystemMutedForStream](arkts-audio-audio-audiovolumemanager-i.md#issystemmutedforstream)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [isSystemMutedForStream](arkts-audio-audio-audiovolumemanager-i.md#issystemmutedforstream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当获取指定音量流静音状态成功，err为undefined，data为true表示静音，false表示非静音；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.isMute(audio.AudioVolumeType.MEDIA, (err: BusinessError, value: boolean) => {
  if (err) {
    console.error(`Failed to check whether the stream is muted. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the stream is muted, isMuted: ${value}.`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.isMute(audio.AudioVolumeType.MEDIA, (err: BusinessError, isMute: boolean) => {
  if (err) {
    console.error(`Failed to check whether the stream is muted. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the stream is muted, isMuted: ${isMute}.`);
});
```

## isMute

```TypeScript
isMute(volumeType: AudioVolumeType): Promise<boolean>
```

获取指定音量流是否被静音。使用Promise异步回调。

> **说明：**
> 
> 从API version 9开始支持，从API version 20开始废弃，建议使用
> [isSystemMutedForStream](arkts-audio-audio-audiovolumemanager-i.md#issystemmutedforstream)替代。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** [isSystemMutedForStream](arkts-audio-audio-audiovolumemanager-i.md#issystemmutedforstream)

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象。返回true表示静音；返回false表示非静音。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.isMute(audio.AudioVolumeType.MEDIA).then((value: boolean) => {
  console.info(`Succeeded in checking whether the stream is muted, isMuted: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the stream is muted. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.isMute(audio.AudioVolumeType.MEDIA).then((isMute: boolean) => {
  console.info(`Succeeded in checking whether the stream is muted, isMuted: ${isMute}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the stream is muted. Code: ${err.code}, message: ${err.message}`);
});
```

## isMuteSync

```TypeScript
isMuteSync(volumeType: AudioVolumeType): boolean
```

获取指定音量流是否被静音。同步返回结果。

> **说明：**
> 
> 从API version 10开始支持，从API version 20开始废弃，建议使用
> [isSystemMutedForStream](arkts-audio-audio-audiovolumemanager-i.md#issystemmutedforstream)替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [isSystemMutedForStream](arkts-audio-audio-audiovolumemanager-i.md#issystemmutedforstream)

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isMute: boolean = audioVolumeGroupManager.isMuteSync(audio.AudioVolumeType.MEDIA);
  console.info(`Succeeded in checking whether the stream is muted, isMuted: ${isMute}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the stream is muted. Code: ${error.code}, message: ${error.message}`);
}
```

## isVolumeUnadjustable

```TypeScript
isVolumeUnadjustable(): boolean
```

获取固定音量模式开关状态，打开时进入固定音量模式，此时音量固定无法被调节。同步返回结果。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 固定音量模式开关状态。返回true表示固定音量模式，返回false表示非固定音量模式。 |

**示例**

```TypeScript
let isVolumeUnadjustable: boolean = audioVolumeGroupManager.isVolumeUnadjustable();
console.info(`Succeeded in checking whether the volume is unadjustable, isVolumeUnadjustable: ${isVolumeUnadjustable}.`);
```

## off('ringerModeChange')

```TypeScript
off(type: 'ringerModeChange', callback?: Callback<AudioRingMode>): void
```

取消监听铃声模式变化事件。使用callback异步回调。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'ringerModeChange' | 是 | 事件回调类型，支持的事件为'ringerModeChange'，当取消监听铃声模式变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioRingMode](arkts-audio-audio-audioringmode-e.md)&gt; | 否 | 回调函数，返回变化后的铃音模式。 |

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

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'micStateChange' | 是 | 事件回调类型，支持的事件为'micStateChange'，当取消监听系统麦克风状态更改事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MicStateChangeEvent](arkts-audio-audio-micstatechangeevent-i.md)&gt; | 否 | 回调函数，返回变更后的麦克风状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters missing; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('ringerModeChange')

```TypeScript
on(type: 'ringerModeChange', callback: Callback<AudioRingMode>): void
```

监听铃声模式变化事件（当[AudioRingMode](arkts-audio-audio-audioringmode-e.md)发生变化时触发）。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'ringerModeChange' | 是 | 事件回调类型，支持的事件为'ringerModeChange'，当铃声模式发生变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioRingMode](arkts-audio-audio-audioringmode-e.md)&gt; | 是 | 回调函数，返回变化后的铃音模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('micStateChange')

```TypeScript
on(type: 'micStateChange', callback: Callback<MicStateChangeEvent>): void
```

监听系统麦克风状态更改事件（当检测到系统麦克风状态发生改变时触发）。使用callback异步回调。 目前此订阅接口在单进程多AudioManager实例的使用场景下，仅最后一个实例的订阅生效，其他实例的订阅会被覆盖（即使最后一个实例没有进行订阅）。因此，推荐使用单一AudioManager实例进行开发。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'micStateChange' | 是 | 事件回调类型，支持的事件为'micStateChange'，当检测到系统麦克风状态发生改变时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MicStateChangeEvent](arkts-audio-audio-micstatechangeevent-i.md)&gt; | 是 | 回调函数，返回变更后的麦克风状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
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

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 是否设置麦克风为静音状态。true表示静音，false表示非静音。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置麦克风静音状态成功，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.setMicrophoneMute(true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to mute the microphone. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in muting the microphone.');
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.setMicrophoneMute(true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to mute the microphone. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in muting the microphone.');
});
```

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

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 是否设置麦克风为静音状态。true表示静音，false表示非静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.setMicrophoneMute(true).then(() => {
  console.info('Succeeded in muting the microphone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to mute the microphone. Code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.setMicrophoneMute(true).then(() => {
  console.info('Succeeded in muting the microphone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to mute the microphone. Code: ${err.code}, message: ${err.message}`);
});
```
