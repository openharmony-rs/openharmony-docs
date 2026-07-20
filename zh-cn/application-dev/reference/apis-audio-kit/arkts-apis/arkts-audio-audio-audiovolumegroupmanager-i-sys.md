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

<a id="adjustsystemvolumebystep"></a>
## adjustSystemVolumeByStep

```TypeScript
adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void
```

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void--><!--Device-AudioVolumeGroupManager-adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | 是 | Audio volume type. |
| adjustType | [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | 是 | Volume adjustment type. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

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

<a id="adjustsystemvolumebystep-1"></a>
## adjustSystemVolumeByStep

```TypeScript
adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType): Promise<void>
```

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType): Promise<void>--><!--Device-AudioVolumeGroupManager-adjustSystemVolumeByStep(volumeType: AudioVolumeType, adjustType: VolumeAdjustType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | 是 | Audio volume type. |
| adjustType | [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | 是 | Volume adjustment type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | * |

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

<a id="adjustvolumebystep"></a>
## adjustVolumeByStep

```TypeScript
adjustVolumeByStep(adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void
```

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-adjustVolumeByStep(adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void--><!--Device-AudioVolumeGroupManager-adjustVolumeByStep(adjustType: VolumeAdjustType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adjustType | [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | 是 | Volume adjustment type. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

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

<a id="adjustvolumebystep-1"></a>
## adjustVolumeByStep

```TypeScript
adjustVolumeByStep(adjustType: VolumeAdjustType): Promise<void>
```

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-adjustVolumeByStep(adjustType: VolumeAdjustType): Promise<void>--><!--Device-AudioVolumeGroupManager-adjustVolumeByStep(adjustType: VolumeAdjustType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adjustType | [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | 是 | Volume adjustment type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | * |

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

<a id="getactivevolumetypesync"></a>
## getActiveVolumeTypeSync

```TypeScript
getActiveVolumeTypeSync(uid: number): AudioVolumeType
```

Obtains the active volume type in the calling moment. This method returns in sync mode.

**起始版本：** 13

<!--Device-AudioVolumeGroupManager-getActiveVolumeTypeSync(uid: int): AudioVolumeType--><!--Device-AudioVolumeGroupManager-getActiveVolumeTypeSync(uid: int): AudioVolumeType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | The target uid's active volume type or0 which means the global active volume type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | Current active volume type. |

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

<a id="ispersistentmicmute"></a>
## isPersistentMicMute

```TypeScript
isPersistentMicMute(): boolean
```

**起始版本：** 12

**需要权限：** ohos.permission.MICROPHONE_CONTROL

<!--Device-AudioVolumeGroupManager-isPersistentMicMute(): boolean--><!--Device-AudioVolumeGroupManager-isPersistentMicMute(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | * |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

**示例：**

```TypeScript
let value: boolean = audioVolumeGroupManager.isPersistentMicMute();

```

<a id="mute"></a>
## mute

```TypeScript
mute(volumeType: AudioVolumeType, mute: boolean, callback: AsyncCallback<void>): void
```

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-mute(volumeType: AudioVolumeType, mute: boolean, callback: AsyncCallback<void>): void--><!--Device-AudioVolumeGroupManager-mute(volumeType: AudioVolumeType, mute: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | 是 | Audio stream type. |
| mute | boolean | 是 | Mute status to set. The value true means to mute the stream, and false means the opposite. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

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

<a id="mute-1"></a>
## mute

```TypeScript
mute(volumeType: AudioVolumeType, mute: boolean): Promise<void>
```

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-mute(volumeType: AudioVolumeType, mute: boolean): Promise<void>--><!--Device-AudioVolumeGroupManager-mute(volumeType: AudioVolumeType, mute: boolean): Promise<void>-End-->

**系统能力：** 
- SystemCapability.Multimedia.Audio.Volume
- SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | 是 | Audio stream type. |
| mute | boolean | 是 | Mute status to set. The value true means to mute the stream, and false means the opposite. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | * |

**示例：**

```TypeScript
audioVolumeGroupManager.mute(audio.AudioVolumeType.MEDIA, true).then(() => {
  console.info('Promise returned to indicate that the stream is muted.');
});

```

<a id="setmicmute"></a>
## setMicMute

```TypeScript
setMicMute(mute: boolean): Promise<void>
```

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeGroupManager-setMicMute(mute: boolean): Promise<void>--><!--Device-AudioVolumeGroupManager-setMicMute(mute: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | Mute status to set. The value true means to mute the microphone, and false means the opposite. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | * |

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

<a id="setmicmutepersistent"></a>
## setMicMutePersistent

```TypeScript
setMicMutePersistent(mute: boolean, type: PolicyType): Promise<void>
```

**起始版本：** 12

**需要权限：** ohos.permission.MICROPHONE_CONTROL

<!--Device-AudioVolumeGroupManager-setMicMutePersistent(mute: boolean, type: PolicyType): Promise<void>--><!--Device-AudioVolumeGroupManager-setMicMutePersistent(mute: boolean, type: PolicyType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | Mute status to set. The value true means to mute the microphone, and false means the opposite. |
| type | [PolicyType](../../apis-mdm-kit/arkts-apis/arkts-mdm-systemmanager-policytype-e.md) | 是 | Mute status to set. This value represents the caller's type such as EDM or privacy. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | * |

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

<a id="setringermode"></a>
## setRingerMode

```TypeScript
setRingerMode(mode: AudioRingMode, callback: AsyncCallback<void>): void
```

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-setRingerMode(mode: AudioRingMode, callback: AsyncCallback<void>): void--><!--Device-AudioVolumeGroupManager-setRingerMode(mode: AudioRingMode, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | 是 | Ringer mode. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

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

<a id="setringermode-1"></a>
## setRingerMode

```TypeScript
setRingerMode(mode: AudioRingMode): Promise<void>
```

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-setRingerMode(mode: AudioRingMode): Promise<void>--><!--Device-AudioVolumeGroupManager-setRingerMode(mode: AudioRingMode): Promise<void>-End-->

**系统能力：** 
- SystemCapability.Multimedia.Audio.Volume
- SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | 是 | Ringer mode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | * |

**示例：**

```TypeScript
audioVolumeGroupManager.setRingerMode(audio.AudioRingMode.RINGER_MODE_NORMAL).then(() => {
  console.info('Promise returned to indicate a successful setting of the ringer mode.');
});

```

<a id="setvolume"></a>
## setVolume

```TypeScript
setVolume(volumeType: AudioVolumeType, volume: number, callback: AsyncCallback<void>): void
```

Sets the volume for a stream. This method uses an asynchronous callback to return the result.

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-setVolume(volumeType: AudioVolumeType, volume: int, callback: AsyncCallback<void>): void--><!--Device-AudioVolumeGroupManager-setVolume(volumeType: AudioVolumeType, volume: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | 是 | Audio stream type. |
| volume | number | 是 | Volume to set. The value range can be obtained by calling getMinVolume and getMaxVolume. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

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

<a id="setvolume-1"></a>
## setVolume

```TypeScript
setVolume(volumeType: AudioVolumeType, volume: number): Promise<void>
```

Sets the volume for a stream. This method uses a promise to return the result.

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-setVolume(volumeType: AudioVolumeType, volume: int): Promise<void>--><!--Device-AudioVolumeGroupManager-setVolume(volumeType: AudioVolumeType, volume: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | 是 | Audio stream type. |
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

<a id="setvolumewithflag"></a>
## setVolumeWithFlag

```TypeScript
setVolumeWithFlag(volumeType: AudioVolumeType, volume: number, flags: number): Promise<void>
```

Sets the volume for a stream. This method uses a promise to return the result.

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeGroupManager-setVolumeWithFlag(volumeType: AudioVolumeType, volume: int, flags: int): Promise<void>--><!--Device-AudioVolumeGroupManager-setVolumeWithFlag(volumeType: AudioVolumeType, volume: int, flags: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | 是 | Audio stream type. |
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

