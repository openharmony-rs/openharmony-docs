# AudioHapticManager

管理音振协同功能。在调用AudioHapticManager的接口前，需要先通过[getAudioHapticManager](arkts-audio-audiohaptic-getaudiohapticmanager-f.md)创建实例。

**起始版本：** 23

<!--Device-audioHaptic-interface AudioHapticManager--><!--Device-audioHaptic-interface AudioHapticManager-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## 导入模块

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## createPlayer

```TypeScript
createPlayer(id: number, options?: AudioHapticPlayerOptions): Promise<AudioHapticPlayer>
```

创建音振播放器。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.VIBRATE

<!--Device-AudioHapticManager-createPlayer(id: number, options?: AudioHapticPlayerOptions): Promise<AudioHapticPlayer>--><!--Device-AudioHapticManager-createPlayer(id: number, options?: AudioHapticPlayerOptions): Promise<AudioHapticPlayer>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 已注册资源的source id。 |
| options | [AudioHapticPlayerOptions](arkts-audio-audiohaptic-audiohapticplayeroptions-i.md) | 否 | 音振播放器选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioHapticPlayer](arkts-audio-audiohaptic-audiohapticplayer-i.md)&gt; | Promise对象，返回创建的音振播放器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400106](../../apis-media-kit/errorcode-media.md#5400106-不支持的规格) | Unsupport format. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // 需要通过registerSource或registerSourceFromFd方法获取。

let options: audioHaptic.AudioHapticPlayerOptions = {muteAudio: false, muteHaptics: false};
let audioHapticPlayerInstance;

audioHapticManagerInstance.createPlayer(id, options).then((value: audioHaptic.AudioHapticPlayer) => {
  audioHapticPlayerInstance = value;
  console.info('Succeeded in creating the player.');
}).catch((err: BusinessError) => {
  console.error(`Failed to create the player. Code: ${err.code}, message: ${err.message}`);
});
```

## createPlayer

```TypeScript
createPlayer(id: int, options?: AudioHapticPlayerOptions): Promise<AudioHapticPlayer | null>
```

Create an audio haptic player. This method uses a promise to return the result. If haptics is needed, caller should have the permission of ohos.permission.VIBRATE.

**起始版本：** 23

**需要权限：** ohos.permission.VIBRATE

<!--Device-AudioHapticManager-createPlayer(id: int, options?: AudioHapticPlayerOptions): Promise<AudioHapticPlayer | null>--><!--Device-AudioHapticManager-createPlayer(id: int, options?: AudioHapticPlayerOptions): Promise<AudioHapticPlayer | null>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | int | 是 | Source id. |
| options | [AudioHapticPlayerOptions](arkts-audio-audiohaptic-audiohapticplayeroptions-i.md) | 否 | Options when creating audio haptic player. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioHapticPlayer](arkts-audio-audiohaptic-audiohapticplayer-i.md) \| null&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400106](../../apis-media-kit/errorcode-media.md#5400106-不支持的规格) | Unsupport format. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## registerSource

```TypeScript
registerSource(audioUri: string, hapticUri: string): Promise<int>
```

通过Uri注册音频和振动资源。使用Promise异步回调。 > **注意：** > > 单个应用最多支持同时注册128个资源，超过之后将会注册失败（返回注册的资源ID为负数）。推荐应用合理控制注册资源数量，对于不再需要使用的资源，建议及时取消注册。

**起始版本：** 23

<!--Device-AudioHapticManager-registerSource(audioUri: string, hapticUri: string): Promise<int>--><!--Device-AudioHapticManager-registerSource(audioUri: string, hapticUri: string): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| audioUri | string | 是 | 音频资源的Uri。 <br>- 对普通时延模式，音频资源格式和路径格式的支持可参考[AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)。 <br>- 对低时延模式，音频资源格式支持可参考[SoundPool](../../apis-media-kit/arkts-apis/arkts-media-soundpool-soundpool-i.md)，路径格式需满足 [fileIo.open](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-open-f.md)的要求。 <br>- 对两种时延模式，均建议传入文件的绝对路径。 |
| hapticUri | string | 是 | 振动资源的Uri。 <br>振动资源格式支持可参考[HapticFileDescriptor](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-vibrator-hapticfiledescriptor-i.md)，路径格式需满足 [fileIo.open](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-open-f.md)的要求。 <br>建议传入文件的绝对路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回注册的资源ID。 <br>正常情况下返回注册的资源ID为非负数。若返回注册的资源ID为负数，则表示注册失败，需检查注册资源数量是否超过上限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 音频资源的URI，传递给registerSource用于注册。
let audioUri = 'data/audioTest.wav'; // 需更改为目标音频资源的URI。
// 振动资源的URI，传递给registerSource用于注册。
let hapticUri = 'data/hapticTest.json'; // 需更改为目标振动资源的URI。
let id = 0;
// 单个应用最多支持同时注册128个资源，超过之后将会注册失败（返回注册的资源ID为负数）。推荐应用合理控制注册资源数量，对于不再需要使用的资源，建议及时取消注册。
audioHapticManagerInstance.registerSource(audioUri, hapticUri).then((value) => {
  id = value;
  console.info(`Succeeded in registering the source, sourceId: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to register the source. Code: ${err.code}, message: ${err.message}`);
});
```

## registerSourceFromFd

```TypeScript
registerSourceFromFd(audioFd: AudioHapticFileDescriptor, hapticFd: AudioHapticFileDescriptor): Promise<int>
```

通过文件描述符注册音频和振动资源。使用Promise异步回调。 > **注意：** > > 单个应用最多支持同时注册128个资源，超过之后将会注册失败（返回注册的资源ID为负数）。推荐应用合理控制注册资源数量，对于不再需要使用的资源，建议及时取消注册。

**起始版本：** 23

<!--Device-AudioHapticManager-registerSourceFromFd(audioFd: AudioHapticFileDescriptor, hapticFd: AudioHapticFileDescriptor): Promise<int>--><!--Device-AudioHapticManager-registerSourceFromFd(audioFd: AudioHapticFileDescriptor, hapticFd: AudioHapticFileDescriptor): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| audioFd | [AudioHapticFileDescriptor](arkts-audio-audiohaptic-audiohapticfiledescriptor-i.md) | 是 | 已打开的有效文件描述符对象，用于描述音频文件。配套的offset和length需符合实际文件长度。 |
| hapticFd | [AudioHapticFileDescriptor](arkts-audio-audiohaptic-audiohapticfiledescriptor-i.md) | 是 | 已打开的有效文件描述符对象，用于描述振动文件。配套的offset和length必须符合实际文件长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回注册的资源ID。 <br>正常情况下返回注册的资源ID为非负数。若返回注册的资源ID为负数，则表示注册失败，需检查注册资源数量是否超过上限。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let audioFile = context.resourceManager.getRawFdSync('audioTest.ogg'); // 需要改成rawfile目录下的对应文件。
let audioFd: audioHaptic.AudioHapticFileDescriptor = {
  fd: audioFile.fd,
  offset: audioFile.offset,
  length: audioFile.length,
};

let hapticFile = context.resourceManager.getRawFdSync('hapticTest.json'); // 需要改成rawfile目录下的对应文件。
let hapticFd: audioHaptic.AudioHapticFileDescriptor = {
  fd: hapticFile.fd,
  offset: hapticFile.offset,
  length: hapticFile.length,
};
let id = 0;
// 单个应用最多支持同时注册128个资源，超过之后将会注册失败（返回注册的资源ID为负数）。推荐应用合理控制注册资源数量，对于不再需要使用的资源，建议及时取消注册。
audioHapticManagerInstance.registerSourceFromFd(audioFd, hapticFd).then((value) => {
  id = value;
  console.info(`Succeeded in registering the source from fd, sourceId: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to register the source from fd. Code: ${err.code}, message: ${err.message}`);
});
```

## setAudioLatencyMode

```TypeScript
setAudioLatencyMode(id:int, latencyMode: AudioLatencyMode): void
```

设置音频时延模式。

**起始版本：** 23

<!--Device-AudioHapticManager-setAudioLatencyMode(id:int, latencyMode: AudioLatencyMode): void--><!--Device-AudioHapticManager-setAudioLatencyMode(id:int, latencyMode: AudioLatencyMode): void-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | int | 是 | 已注册资源的source id。 |
| latencyMode | [AudioLatencyMode](arkts-audio-audiohaptic-audiolatencymode-e.md) | 是 | 音频时延模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // 需要通过registerSource或registerSourceFromFd方法获取。

let latencyMode: audioHaptic.AudioLatencyMode = audioHaptic.AudioLatencyMode.AUDIO_LATENCY_MODE_FAST;

audioHapticManagerInstance.setAudioLatencyMode(id, latencyMode);
```

## setStreamUsage

```TypeScript
setStreamUsage(id: int, usage: audio.StreamUsage): void
```

设置音频流使用类型。

**起始版本：** 23

<!--Device-AudioHapticManager-setStreamUsage(id: int, usage: audio.StreamUsage): void--><!--Device-AudioHapticManager-setStreamUsage(id: int, usage: audio.StreamUsage): void-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | int | 是 | 已注册资源的source id。 |
| usage | audio.StreamUsage | 是 | 音频流使用类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // 需要通过registerSource或registerSourceFromFd方法获取。

let usage: audio.StreamUsage = audio.StreamUsage.STREAM_USAGE_NOTIFICATION;

audioHapticManagerInstance.setStreamUsage(id, usage);
```

## unregisterSource

```TypeScript
unregisterSource(id: int): Promise<void>
```

取消注册音频和振动资源。使用Promise异步回调。 > **注意：** > > 对于不再需要使用的资源，建议应用及时取消注册，避免出现资源泄漏或资源数量超上限等问题。

**起始版本：** 23

<!--Device-AudioHapticManager-unregisterSource(id: int): Promise<void>--><!--Device-AudioHapticManager-unregisterSource(id: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | int | 是 | 已注册资源的source id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let id = 0; // 需要通过registerSource或registerSourceFromFd方法获取。

audioHapticManagerInstance.unregisterSource(id).then(() => {
  console.info('Succeeded in unregistering the source.');
}).catch((err: BusinessError) => {
  console.error(`Failed to unregister the source. Code: ${err.code}, message: ${err.message}`);
});
```

