# AudioVolumeGroupManager

管理音频组音量。

在使用AudioVolumeGroupManager的接口之前，需先通过
[getVolumeGroupManager](arkts-audio-audiovolumemanager-i.md#getvolumegroupmanager-1)
获取AudioVolumeGroupManager实例。

> **说明：**
>
> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## adjustSystemVolumeByStep

```TypeScript
adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void
```

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | Audio volume type. |
| adjustType | VolumeAdjustType | 是 | Volume adjustment type. |
| callback | AsyncCallback&lt;void&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by callback. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.adjustSystemVolumeByStep(audio.AudioVolumeType.MEDIA, audio.VolumeAdjustType.VOLUME_UP, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to adjust the system volume by step ${err}`);
  } else {
    console.info('Success to adjust the system volume by step.');
  }
});

```

## adjustSystemVolumeByStep

```TypeScript
adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType): Promise<void>
```

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | Audio volume type. |
| adjustType | VolumeAdjustType | 是 | Volume adjustment type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | *  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.adjustSystemVolumeByStep(audio.AudioVolumeType.MEDIA, audio.VolumeAdjustType.VOLUME_UP).then(() => {
  console.info('Success to adjust the system volume by step.');
}).catch((error: BusinessError) => {
  console.error('Fail to adjust the system volume by step.');
});

```

## adjustVolumeByStep

```TypeScript
adjustVolumeByStep(adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void
```

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adjustType | VolumeAdjustType | 是 | Volume adjustment type. |
| callback | AsyncCallback&lt;void&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by callback. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.adjustVolumeByStep(audio.VolumeAdjustType.VOLUME_UP, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to adjust the volume by step. ${err}`);
    return;
  } else {
    console.info('Success to adjust the volume by step.');
  }
});

```

## adjustVolumeByStep

```TypeScript
adjustVolumeByStep(adjustType: VolumeAdjustType): Promise<void>
```

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adjustType | VolumeAdjustType | 是 | Volume adjustment type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | *  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.adjustVolumeByStep(audio.VolumeAdjustType.VOLUME_UP).then(() => {
  console.info('Success to adjust the volume by step.');
}).catch((error: BusinessError) => {
  console.error('Fail to adjust the volume by step.');
});

```

## getActiveVolumeTypeSync

```TypeScript
getActiveVolumeTypeSync(uid: number): AudioVolumeType
```

Obtains the active volume type in the calling moment. This method returns in sync mode.

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | The target uid's active volume type or0 which means the global active volume type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioVolumeType | Current active volume type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters unspecified.2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例：**

```TypeScript
let uid: number = 20010041; // 应用ID。

let value = audioVolumeGroupManager.getActiveVolumeTypeSync(uid);

```

## isPersistentMicMute

```TypeScript
isPersistentMicMute(): boolean
```

**起始版本：** 12

**需要权限：** ohos.permission.MICROPHONE_CONTROL

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | *  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

**示例：**

```TypeScript
let value: boolean = audioVolumeGroupManager.isPersistentMicMute();

```

## mute

```TypeScript
mute(volumeType: AudioVolumeType, mute: boolean, callback: AsyncCallback<void>): void
```

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | Audio stream type. |
| mute | boolean | 是 | Mute status to set. The value true means to mute the stream, and false means the opposite. |
| callback | AsyncCallback&lt;void&gt; | 是 | Callback used to return the result. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.mute(audio.AudioVolumeType.MEDIA, true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to mute the stream. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the stream is muted.');
});

```

## mute

```TypeScript
mute(volumeType: AudioVolumeType, mute: boolean): Promise<void>
```

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** 
- SystemCapability.Multimedia.Audio.Volume
- SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | Audio stream type. |
| mute | boolean | 是 | Mute status to set. The value true means to mute the stream, and false means the opposite. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | *  |

**示例：**

```TypeScript
audioVolumeGroupManager.mute(audio.AudioVolumeType.MEDIA, true).then(() => {
  console.info('Promise returned to indicate that the stream is muted.');
});

```

## setMicMute

```TypeScript
setMicMute(mute: boolean): Promise<void>
```

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | Mute status to set. The value true means to mute the microphone, and false means the opposite. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | *  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例：**

```TypeScript
audioVolumeGroupManager.setMicMute(true).then(() => {
  console.info('Promise returned to indicate that the mic is muted.');
});

```

## setMicMutePersistent

```TypeScript
setMicMutePersistent(mute: boolean, type: PolicyType): Promise<void>
```

**起始版本：** 12

**需要权限：** ohos.permission.MICROPHONE_CONTROL

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | Mute status to set. The value true means to mute the microphone, and false means the opposite. |
| type | PolicyType | 是 | Mute status to set. This value represents the caller's type such as EDM or privacy. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | *  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters missing.2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例：**

```TypeScript
audioVolumeGroupManager.setMicMutePersistent(true, audio.PolicyType.PRIVACY).then(() => {
  console.info('Succeeded in setting mic mute.');
});

```

## setRingerMode

```TypeScript
setRingerMode(mode: AudioRingMode, callback: AsyncCallback<void>): void
```

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | AudioRingMode | 是 | Ringer mode. |
| callback | AsyncCallback&lt;void&gt; | 是 | Callback used to return the result. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.setRingerMode(audio.AudioRingMode.RINGER_MODE_NORMAL, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set the ringer mode. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate a successful setting of the ringer mode.');
});

```

## setRingerMode

```TypeScript
setRingerMode(mode: AudioRingMode): Promise<void>
```

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** 
- SystemCapability.Multimedia.Audio.Volume
- SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | AudioRingMode | 是 | Ringer mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | *  |

**示例：**

```TypeScript
audioVolumeGroupManager.setRingerMode(audio.AudioRingMode.RINGER_MODE_NORMAL).then(() => {
  console.info('Promise returned to indicate a successful setting of the ringer mode.');
});

```

## setVolume

```TypeScript
setVolume(volumeType: AudioVolumeType, volume: number, callback: AsyncCallback<void>): void
```

Sets the volume for a stream. This method uses an asynchronous callback to return the result.

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | Audio stream type. |
| volume | number | 是 | Volume to set. The value range can be obtained by calling getMinVolume and getMaxVolume. |
| callback | AsyncCallback&lt;void&gt; | 是 | Callback used to return the result. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.setVolume(audio.AudioVolumeType.MEDIA, 10, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set the volume. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate a successful volume setting.');
});

```

## setVolume

```TypeScript
setVolume(volumeType: AudioVolumeType, volume: number): Promise<void>
```

Sets the volume for a stream. This method uses a promise to return the result.

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | Audio stream type. |
| volume | number | 是 | Volume to set. The value range can be obtained by calling getMinVolume and getMaxVolume. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**示例：**

```TypeScript
audioVolumeGroupManager.setVolume(audio.AudioVolumeType.MEDIA, 10).then(() => {
  console.info('Promise returned to indicate a successful volume setting.');
});

```

## setVolumeWithFlag

```TypeScript
setVolumeWithFlag(volumeType: AudioVolumeType, volume: number, flags: number): Promise<void>
```

Sets the volume for a stream. This method uses a promise to return the result.

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | Audio stream type. |
| volume | number | 是 | Volume to set. The value range can be obtained by calling getMinVolume and getMaxVolume. |
| flags | number | 是 | volume flags used to enable different operations, can be union of {@link VolumeFlag} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

**示例：**

```TypeScript
audioVolumeGroupManager.setVolumeWithFlag(audio.AudioVolumeType.MEDIA, 10, 1).then(() => {
  console.info('Promise returned to indicate a successful volume setting.');
});

```

