# AudioVolumeManager

音量管理。 在使用AudioVolumeManager的接口之前，需先通过[getVolumeManager](arkts-audio-audio-audiomanager-i.md#getVolumeManager)获取AudioVolumeManager实例。 > **说明：** > > - 本Interface首批接口从API version 9开始支持。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-audio-interface AudioVolumeManager--><!--Device-audio-interface AudioVolumeManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## forceVolumeKeyControlType

```TypeScript
forceVolumeKeyControlType(volumeType: AudioVolumeType, duration: int): void
```

Interface for forcibly setting the volume type by pressing the volume key.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MODIFY_AUDIO_SETTINGS

<!--Device-AudioVolumeManager-forceVolumeKeyControlType(volumeType: AudioVolumeType, duration: int): void--><!--Device-AudioVolumeManager-forceVolumeKeyControlType(volumeType: AudioVolumeType, duration: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type that the application expects to control using the volume key. |
| duration | int | 是 | Duration for continuing to control the volume type when no key is pressed. The forced volume type setting is released when the timer expires. Unit is second, the maximum duration is 10 seconds. If the duration is set to -1, the setting is canceled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Crash or blocking occurs in system process. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

let audioManager = audio.getAudioManager();
let audioVolumeManager = audioManager.getVolumeManager();

// 设置音量保持类型为响铃模式。
let volumeType = audio.AudioVolumeType.RINGTONE;
let duration = 10;
audioVolumeManager.forceVolumeKeyControlType(volumeType, duration);

// 取消音量保持类型，恢复默认音量控制。
let volumeTypeDefault = audio.AudioVolumeType.MEDIA;
let durationToCancel = -1;
audioVolumeManager.forceVolumeKeyControlType(volumeTypeDefault, durationToCancel);
```

## getActiveStreamsVolumeInfo

```TypeScript
getActiveStreamsVolumeInfo(): ActiveStreamsVolumeInfoArray
```

获取当前音频流的音量信息。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioVolumeManager-getActiveStreamsVolumeInfo(): ActiveStreamsVolumeInfoArray--><!--Device-AudioVolumeManager-getActiveStreamsVolumeInfo(): ActiveStreamsVolumeInfoArray-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ActiveStreamsVolumeInfoArray](arkts-audio-audio-activestreamsvolumeinfoarray-t-sys.md) | Returns the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error, crash or blocking occurs in system process. |

## getAppVolumePercentageForUid

```TypeScript
getAppVolumePercentageForUid(uid: int): Promise<int>
```

Get the volume for specified app with range from 0 to 100. Applications with same uid share the same volume.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeManager-getAppVolumePercentageForUid(uid: int): Promise<int>--><!--Device-AudioVolumeManager-getAppVolumePercentageForUid(uid: int): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | App's uid. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
let uid = 20010041; // 应用ID。

audioVolumeManager.getAppVolumePercentageForUid(20010041).then((value) => {
  console.info(`app volume is ${value}.`);
});
```

## getAudioVolumeTypeByStreamUsage

```TypeScript
getAudioVolumeTypeByStreamUsage(streamUsage: StreamUsage): AudioVolumeType
```

Obtains volume type by stream type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getAudioVolumeTypeByStreamUsage(streamUsage: StreamUsage): AudioVolumeType--><!--Device-AudioVolumeManager-getAudioVolumeTypeByStreamUsage(streamUsage: StreamUsage): AudioVolumeType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | [StreamUsage](arkts-audio-audio-streamusage-e.md) | 是 | Audio stream type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Return the audio volume type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## getMaxSystemVolume

```TypeScript
getMaxSystemVolume(volumeType: AudioVolumeType): int
```

Obtains the maximum volume allowed for a volume type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getMaxSystemVolume(volumeType: AudioVolumeType): int--><!--Device-AudioVolumeManager-getMaxSystemVolume(volumeType: AudioVolumeType): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Max volume level. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## getMinSystemVolume

```TypeScript
getMinSystemVolume(volumeType: AudioVolumeType): int
```

Obtains the minimum volume allowed for a volume type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getMinSystemVolume(volumeType: AudioVolumeType): int--><!--Device-AudioVolumeManager-getMinSystemVolume(volumeType: AudioVolumeType): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Min volume level. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## getMinSystemVolumePercentage

```TypeScript
getMinSystemVolumePercentage(volumeType: AudioVolumeType): int
```

Gets the minimum system volume percentage application can set for specified volume type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getMinSystemVolumePercentage(volumeType: AudioVolumeType): int--><!--Device-AudioVolumeManager-getMinSystemVolumePercentage(volumeType: AudioVolumeType): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type to get. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Returns the volume percentage, which is an interger with the range [0, 100]. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
try {
  let volume = audioVolumeManager.getMinSystemVolumePercentage(audio.AudioVolumeType.MEDIA);
  console.info(`MEDIA volume percentage obtained success.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume percentage, error: ${error}`);
}
```

## getStreamUsagesByVolumeType

```TypeScript
getStreamUsagesByVolumeType(volumeType: AudioVolumeType): StreamUsageArray
```

Obtains stream types by volume type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getStreamUsagesByVolumeType(volumeType: AudioVolumeType): StreamUsageArray--><!--Device-AudioVolumeManager-getStreamUsagesByVolumeType(volumeType: AudioVolumeType): StreamUsageArray-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio stream type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StreamUsageArray](arkts-audio-audio-streamusagearray-t-sys.md) | Return the audio stream types. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## getSupportedAudioVolumeTypes

```TypeScript
getSupportedAudioVolumeTypes(): Array<Readonly<AudioVolumeType>>
```

Obtains system supported volume types.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getSupportedAudioVolumeTypes(): Array<Readonly<AudioVolumeType>>--><!--Device-AudioVolumeManager-getSupportedAudioVolumeTypes(): Array<Readonly<AudioVolumeType>>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Readonly&lt;[AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)&gt;&gt; | Return the system volume type array. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## getSystemVolume

```TypeScript
getSystemVolume(volumeType: AudioVolumeType): int
```

Obtains the volume of a volume type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getSystemVolume(volumeType: AudioVolumeType): int--><!--Device-AudioVolumeManager-getSystemVolume(volumeType: AudioVolumeType): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Current system volume level. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## getSystemVolumeByUid

```TypeScript
getSystemVolumeByUid(volumeType: AudioVolumeType, callingUid: int): int
```

Obtains the volume of streams in specific uid application.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getSystemVolumeByUid(volumeType: AudioVolumeType, callingUid: int): int--><!--Device-AudioVolumeManager-getSystemVolumeByUid(volumeType: AudioVolumeType, callingUid: int): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type. |
| callingUid | int | 是 | Uid of the stream owner. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Current system volume level. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Crash or blocking occurs in system process. |

## getSystemVolumePercentage

```TypeScript
getSystemVolumePercentage(volumeType: AudioVolumeType): int
```

Gets the current system volume percentage for specified volume type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getSystemVolumePercentage(volumeType: AudioVolumeType): int--><!--Device-AudioVolumeManager-getSystemVolumePercentage(volumeType: AudioVolumeType): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type to get. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Returns the volume percentage, which is an integer with the range [0, 100]. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
try {
  let volume = audioVolumeManager.getSystemVolumePercentage(audio.AudioVolumeType.MEDIA);
  console.info(`MEDIA volume percentage obtained success.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volume percentage, error: ${error}`);
}
```

## getVolumeGroupInfos

```TypeScript
getVolumeGroupInfos(networkId: string, callback: AsyncCallback<VolumeGroupInfos>): void
```

Get the volume group list for a networkId. This method uses an asynchronous callback to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getVolumeGroupInfos(networkId: string, callback: AsyncCallback<VolumeGroupInfos>): void--><!--Device-AudioVolumeManager-getVolumeGroupInfos(networkId: string, callback: AsyncCallback<VolumeGroupInfos>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | Distributed deice net work id |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[VolumeGroupInfos](arkts-audio-audio-volumegroupinfos-t-sys.md)&gt; | 是 | Callback used to return the result. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeManager.getVolumeGroupInfos(audio.LOCAL_NETWORK_ID, (err: BusinessError, value: audio.VolumeGroupInfos) => {
  if (err) {
    console.error(`Failed to obtain the volume group infos list. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the volume group infos list is obtained.');
});
```

## getVolumeGroupInfos

```TypeScript
getVolumeGroupInfos(networkId: string): Promise<VolumeGroupInfos>
```

Get the volume group list for a networkId. This method uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getVolumeGroupInfos(networkId: string): Promise<VolumeGroupInfos>--><!--Device-AudioVolumeManager-getVolumeGroupInfos(networkId: string): Promise<VolumeGroupInfos>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | Distributed deice net work id |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[VolumeGroupInfos](arkts-audio-audio-volumegroupinfos-t-sys.md)&gt; | Promise used to return the result. |

## 示例

```TypeScript
async function getVolumeGroupInfos(){
  let volumegroupinfos: audio.VolumeGroupInfos = await audio.getAudioManager().getVolumeManager().getVolumeGroupInfos(audio.LOCAL_NETWORK_ID);
  console.info('Promise returned to indicate that the volumeGroup list is obtained.'+JSON.stringify(volumegroupinfos))
}
```

## getVolumeGroupInfosSync

```TypeScript
getVolumeGroupInfosSync(networkId: string): VolumeGroupInfos
```

Get the volume group list for a networkId.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getVolumeGroupInfosSync(networkId: string): VolumeGroupInfos--><!--Device-AudioVolumeManager-getVolumeGroupInfosSync(networkId: string): VolumeGroupInfos-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | Distributed deice net work id |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VolumeGroupInfos](arkts-audio-audio-volumegroupinfos-t-sys.md) | Volume group info list. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let volumegroupinfos: audio.VolumeGroupInfos = audioVolumeManager.getVolumeGroupInfosSync(audio.LOCAL_NETWORK_ID);
  console.info(`Indicate that the volumeGroup list is obtained. ${JSON.stringify(volumegroupinfos)}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the volumeGroup list ${error}`);
}
```

## getVolumeInUnitOfDb

```TypeScript
getVolumeInUnitOfDb(volumeType: AudioVolumeType, volumeLevel: int, device: DeviceType): double
```

Gets the volume db value that system calculate by volume type, volume level and device type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-getVolumeInUnitOfDb(volumeType: AudioVolumeType, volumeLevel: int, device: DeviceType): double--><!--Device-AudioVolumeManager-getVolumeInUnitOfDb(volumeType: AudioVolumeType, volumeLevel: int, device: DeviceType): double-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type. |
| volumeLevel | int | 是 | Volume level to set. |
| device | DeviceType | 是 | Output device type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | The system volume in dB. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## isAppVolumeMutedForUid

```TypeScript
isAppVolumeMutedForUid(uid: int, owned: boolean): Promise<boolean>
```

Checks whether the app volume is muted. If there are multiple callers setting muted states, only when all callers cancel muted state the volume of this app will be truly unmuted.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeManager-isAppVolumeMutedForUid(uid: int, owned: boolean): Promise<boolean>--><!--Device-AudioVolumeManager-isAppVolumeMutedForUid(uid: int, owned: boolean): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | App's uid. |
| owned | boolean | 是 | If true is passed, the result will be indicated your owned muted state settings to this app. Otherwise if false is passed, the result will be indicated the real muted state. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
let uid = 20010041; // 应用ID。

audioVolumeManager.isAppVolumeMutedForUid(uid, true).then((value: boolean) => {
  console.info(`app muted state is ${value}.`);
});
```

## isSystemMuted

```TypeScript
isSystemMuted(volumeType: AudioVolumeType): boolean
```

Checks whether a volume type is muted.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-isSystemMuted(volumeType: AudioVolumeType): boolean--><!--Device-AudioVolumeManager-isSystemMuted(volumeType: AudioVolumeType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | The mute status of the volume type. The value true means that the volume type is muted, and false means the opposite. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## offActiveVolumeTypeChange

```TypeScript
offActiveVolumeTypeChange(callback?: Callback<AudioVolumeType>): void
```

Unsubscribes from active volume type changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-offActiveVolumeTypeChange(callback?: Callback<AudioVolumeType>): void--><!--Device-AudioVolumeManager-offActiveVolumeTypeChange(callback?: Callback<AudioVolumeType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)&gt; | 否 | Callback used to return the active volume type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
audioVolumeManager.offActiveVolumeTypeChange();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let activeVolumeTypeChangeCallback = (volumeType: audio.AudioVolumeType) => {
  console.info(`VolumeType of stream: ${volumeType} `);
};

audioVolumeManager.onActiveVolumeTypeChange(activeVolumeTypeChangeCallback);

audioVolumeManager.offActiveVolumeTypeChange(activeVolumeTypeChangeCallback);
```

## offAppVolumeChangeForUid

```TypeScript
offAppVolumeChangeForUid(callback?: Callback<VolumeEvent>): void
```

Unsubscribes to the app volume change events..

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeManager-offAppVolumeChangeForUid(callback?: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-offAppVolumeChangeForUid(callback?: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 否 | Callback used to obtain the invoking volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
audioVolumeManager.offAppVolumeChangeForUid();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let appVolumeChangeForUidCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
};

audioVolumeManager.onAppVolumeChangeForUid(appVolumeChangeForUidCallback);

audioVolumeManager.offAppVolumeChangeForUid(appVolumeChangeForUidCallback);
```

## offSystemVolumeChange

```TypeScript
offSystemVolumeChange(callback?: Callback<VolumeEvent>): void
```

Unsubscribes to the system volume change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-offSystemVolumeChange(callback?: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-offSystemVolumeChange(callback?: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 否 | Callback used to obtain the invoking volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
audioVolumeManager.offSystemVolumeChange();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let systemVolumeChangeCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`Succeeded in using on or off function, VolumeEvent: ${volumeEvent}.`);
};

audioVolumeManager.onSystemVolumeChange(systemVolumeChangeCallback);

audioVolumeManager.offSystemVolumeChange(systemVolumeChangeCallback);
```

## offSystemVolumeChangeByFilter

```TypeScript
offSystemVolumeChangeByFilter(callback?: Callback<VolumeEvent>): void
```

取消订阅系统音量变化事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioVolumeManager-offSystemVolumeChangeByFilter(callback?: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-offSystemVolumeChangeByFilter(callback?: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 否 | 订阅中使用的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. |

## offVolumePercentageChange

```TypeScript
offVolumePercentageChange(callback?: Callback<VolumeEvent>): void
```

Unsubscribes from system volume percentage change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-offVolumePercentageChange(callback?: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-offVolumePercentageChange(callback?: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 否 | Callback used to return the system volume percentage change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
audioVolumeManager.offVolumePercentageChange();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let volumePercentageChangeCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Volume percentage: ${volumeEvent.percentage} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
};

audioVolumeManager.onVolumePercentageChange(volumePercentageChangeCallback);

audioVolumeManager.offVolumePercentageChange(volumePercentageChangeCallback);
```

## off_activeVolumeTypeChange

```TypeScript
off(type: 'activeVolumeTypeChange', callback?: Callback<AudioVolumeType>): void
```

取消订阅 活跃的音量类型 事件

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-AudioVolumeManager-off(type: 'activeVolumeTypeChange', callback?: Callback<AudioVolumeType>): void--><!--Device-AudioVolumeManager-off(type: 'activeVolumeTypeChange', callback?: Callback<AudioVolumeType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activeVolumeTypeChange' | 是 | Type of the event to unregister. Only the activeVolumeTypeChange event is supported. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)&gt; | 否 | Callback used to return the active volume type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
audioVolumeManager.off('activeVolumeTypeChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let activeVolumeTypeChangeCallback = (volumeType: audio.AudioVolumeType) => {
  console.info(`VolumeType of stream: ${volumeType} `);
};

audioVolumeManager.on('activeVolumeTypeChange', activeVolumeTypeChangeCallback);

audioVolumeManager.off('activeVolumeTypeChange', activeVolumeTypeChangeCallback);
```

## off_appVolumeChangeForUid

```TypeScript
off(type: 'appVolumeChangeForUid', callback?: Callback<VolumeEvent>): void
```

Unsubscribes to the app volume change events..

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeManager-off(type: 'appVolumeChangeForUid', callback?: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-off(type: 'appVolumeChangeForUid', callback?: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'appVolumeChangeForUid' | 是 | Type of the event to be unregistered. Only the appVolumeChangeForUid event is supported. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 否 | Callback used to obtain the invoking volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
audioVolumeManager.off('appVolumeChangeForUid');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let appVolumeChangeForUidCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
};

audioVolumeManager.on('appVolumeChangeForUid', appVolumeChangeForUidCallback);

audioVolumeManager.off('appVolumeChangeForUid', appVolumeChangeForUidCallback);
```

## off_systemVolumeChange

```TypeScript
off(type: 'systemVolumeChange', callback?: Callback<VolumeEvent>): void
```

Unsubscribes to the system volume change events.

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-AudioVolumeManager-off(type: 'systemVolumeChange', callback?: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-off(type: 'systemVolumeChange', callback?: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemVolumeChange' | 是 | Type of the event to be unregistered. Only the systemVolumeChange event is supported. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 否 | Callback used to obtain the invoking volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
audioVolumeManager.off('systemVolumeChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let systemVolumeChangeCallback = (volumeEvent: audio.VolumeEvent) => {
  console.info(`Succeeded in using on or off function, VolumeEvent: ${volumeEvent}.`);
};

audioVolumeManager.on('systemVolumeChange', systemVolumeChangeCallback);

audioVolumeManager.off('systemVolumeChange', systemVolumeChangeCallback);
```

## onActiveVolumeTypeChange

```TypeScript
onActiveVolumeTypeChange(callback: Callback<AudioVolumeType>): void
```

Subscribes to active volume type changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-onActiveVolumeTypeChange(callback: Callback<AudioVolumeType>): void--><!--Device-AudioVolumeManager-onActiveVolumeTypeChange(callback: Callback<AudioVolumeType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)&gt; | 是 | Callback used to return the active volume type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
audioVolumeManager.onActiveVolumeTypeChange((volumeType: audio.AudioVolumeType) => {
  console.info(`VolumeType of stream: ${volumeType} `);
});
```

## onAppVolumeChangeForUid

```TypeScript
onAppVolumeChangeForUid(uid: int, callback: Callback<VolumeEvent>): void
```

Listens for specified app volume change events. The app volume may changed by [setAppVolumePercentageForUid](#setAppVolumePercentageForUid).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeManager-onAppVolumeChangeForUid(uid: int, callback: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-onAppVolumeChangeForUid(uid: int, callback: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | The app's uid. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 是 | Callback used to get the app volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
let uid: int = 20010041; // 应用ID。

audioVolumeManager.onAppVolumeChangeForUid(uid, (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
});
```

## onSystemVolumeChange

```TypeScript
onSystemVolumeChange(callback: Callback<VolumeEvent>): void
```

Listens for system volume change events. This method uses a callback to get volume change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-onSystemVolumeChange(callback: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-onSystemVolumeChange(callback: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 是 | Callback used to get the system volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
audioVolumeManager.onSystemVolumeChange((volumeEvent: audio.VolumeEvent) => {
  console.info(`Succeeded in using on function, VolumeEvent: ${volumeEvent}.`);
});
```

## onSystemVolumeChangeByFilter

```TypeScript
onSystemVolumeChangeByFilter(filter: SystemVolumeFilter, callback: Callback<VolumeEvent>): void
```

订阅系统音量变化事件。当系统体积为目标时 系统卷过滤器更改，已注册的客户端将收到回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioVolumeManager-onSystemVolumeChangeByFilter(filter: SystemVolumeFilter, callback: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-onSystemVolumeChangeByFilter(filter: SystemVolumeFilter, callback: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [SystemVolumeFilter](arkts-audio-audio-systemvolumefilter-i-sys.md) | 是 | 系统音量变化的过滤器。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 是 | 回调用于接收系统音量的变化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not a system app. |

## onVolumePercentageChange

```TypeScript
onVolumePercentageChange(callback: Callback<VolumeEvent>): void
```

Subscribes to system volume percentage change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioVolumeManager-onVolumePercentageChange(callback: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-onVolumePercentageChange(callback: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 是 | Callback used to return the system volume percentage change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
audioVolumeManager.onVolumePercentageChange((volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Volume percentage: ${volumeEvent.percentage} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
});
```

## on_activeVolumeTypeChange

```TypeScript
on(type: 'activeVolumeTypeChange', callback: Callback<AudioVolumeType>): void
```

订阅 活跃的音量类型 变化事件

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-AudioVolumeManager-on(type: 'activeVolumeTypeChange', callback: Callback<AudioVolumeType>): void--><!--Device-AudioVolumeManager-on(type: 'activeVolumeTypeChange', callback: Callback<AudioVolumeType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activeVolumeTypeChange' | 是 | Type of the event to listen for. Only the activeVolumeTypeChange event is supported. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)&gt; | 是 | Callback used to return the active volume type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
audioVolumeManager.on('activeVolumeTypeChange', (volumeType: audio.AudioVolumeType) => {
  console.info(`VolumeType of stream: ${volumeType} `);
});
```

## on_appVolumeChangeForUid

```TypeScript
on(type: 'appVolumeChangeForUid', uid: int, callback: Callback<VolumeEvent>): void
```

Listens for specified app volume change events. The app volume may changed by [setAppVolumePercentageForUid](#setAppVolumePercentageForUid).

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeManager-on(type: 'appVolumeChangeForUid', uid: int, callback: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-on(type: 'appVolumeChangeForUid', uid: int, callback: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'appVolumeChangeForUid' | 是 | Type of the event to listen for. Only the appVolumeChangeForUid event is supported. |
| uid | int | 是 | The app's uid. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 是 | Callback used to get the app volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
let uid: number = 20010041; // 应用ID。

audioVolumeManager.on('appVolumeChangeForUid', uid, (volumeEvent: audio.VolumeEvent) => {
  console.info(`VolumeType of stream: ${volumeEvent.volumeType} `);
  console.info(`Volume level: ${volumeEvent.volume} `);
  console.info(`Whether to updateUI: ${volumeEvent.updateUi} `);
});
```

## on_systemVolumeChange

```TypeScript
on(type: 'systemVolumeChange', callback: Callback<VolumeEvent>): void
```

Listens for system volume change events. This method uses a callback to get volume change events.

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-AudioVolumeManager-on(type: 'systemVolumeChange', callback: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-on(type: 'systemVolumeChange', callback: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemVolumeChange' | 是 | Type of the event to listen for. Only the systemVolumeChange event is supported. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VolumeEvent](arkts-audio-audio-volumeevent-i.md)&gt; | 是 | Callback used to get the system volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
audioVolumeManager.on('systemVolumeChange', (volumeEvent: audio.VolumeEvent) => {
  console.info(`Succeeded in using on function, VolumeEvent: ${volumeEvent}.`);
});
```

## setAppVolumeMutedForUid

```TypeScript
setAppVolumeMutedForUid(uid: int, muted: boolean): Promise<void>
```

Change mute state of specified application volume. If there are multiple callers setting muted states, only when all callers cancel muted state the volume of this app will be truly unmuted.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeManager-setAppVolumeMutedForUid(uid: int, muted: boolean): Promise<void>--><!--Device-AudioVolumeManager-setAppVolumeMutedForUid(uid: int, muted: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | App's uid. |
| muted | boolean | 是 | Muted state to set. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Crash or blocking occurs in system process. |

## 示例

```TypeScript
let uid = 20010041; // 应用ID。

audioVolumeManager.setAppVolumeMutedForUid(uid, true).then(() => {
  console.info(`set app mute state success.`);
});
```

## setAppVolumePercentageForUid

```TypeScript
setAppVolumePercentageForUid(uid: int, volume: int): Promise<void>
```

Sets the volume for specified app with range from 0 to 100. Applications with same uid share the same volume.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeManager-setAppVolumePercentageForUid(uid: int, volume: int): Promise<void>--><!--Device-AudioVolumeManager-setAppVolumePercentageForUid(uid: int, volume: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | App's uid. |
| volume | int | 是 | Volume to set. The value range is from 0 to 100. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Crash or blocking occurs in system process. |

## 示例

```TypeScript
let uid = 20010041; // 应用ID。
let volume = 20;    // 要设置的音量值。

audioVolumeManager.setAppVolumePercentageForUid(uid, volume).then(() => {
  console.info(`set app volume success.`);
});
```

## setSystemVolumeByUid

```TypeScript
setSystemVolumeByUid(volumeType: AudioVolumeType, volume: int, callingUid: int): Promise<void>
```

Sets the volume for specific uid application. This method uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

<!--Device-AudioVolumeManager-setSystemVolumeByUid(volumeType: AudioVolumeType, volume: int, callingUid: int): Promise<void>--><!--Device-AudioVolumeManager-setSystemVolumeByUid(volumeType: AudioVolumeType, volume: int, callingUid: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type. |
| volume | int | 是 | Volume to set. The value range can be obtained by calling getMinVolume and getMaxVolume. |
| callingUid | int | 是 | Uid of the stream owner. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Crash or blocking occurs in system process. |

## setSystemVolumePercentage

```TypeScript
setSystemVolumePercentage(volumeType: AudioVolumeType, percentage: int): Promise<void>
```

Sets the system volume percentage, using an integer ranging from minimum system volume percentage to 100. The volume percentage corresponds to volume levels, with each level tied to a specific percentage. When the volume level changes, the volume percentage adjusts accordingly and is mapped within the range of volume levels. Zero volume is mapped to 0, and the maximum volume is mapped to 100%. Intermediate volume levels are evenly distributed between 1 and 99. When the volume percentage changes, the volume level changes accordingly.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_AUDIO_CONFIG

<!--Device-AudioVolumeManager-setSystemVolumePercentage(volumeType: AudioVolumeType, percentage: int): Promise<void>--><!--Device-AudioVolumeManager-setSystemVolumePercentage(volumeType: AudioVolumeType, percentage: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | Audio volume type to set. |
| percentage | int | 是 | Percentage to set. It must be an integer with the range from minimum value getted by [getMinSystemVolumePercentage](#getMinSystemVolumePercentage) to 100. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, including volumeType or percentage param being out of range. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Crash or blocking occurs in system process. |

## 示例

```TypeScript
audioVolumeManager.setSystemVolumePercentage(audio.AudioVolumeType.MEDIA, 10).then(() => {
  console.info('Promise returned to indicate a successful volume setting.');
});
```

