# AudioHapticPlayer

音振播放器，提供音振协同播放功能。在调用AudioHapticPlayer的接口前，需要先通过[createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer)创建实例。

@typedef AudioHapticPlayer

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## 导入模块

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## isMuted

```TypeScript
isMuted(type: AudioHapticType): boolean
```

查询该音振类型是否被静音。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AudioHapticType](arkts-audio-audiohaptic-audiohaptictype-e.md) | 是 | 音振类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示查询的音振类型是否被静音。true表示静音，false表示非静音。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Parameter verification failed. |

**示例**

```TypeScript
let audioHapticType: audioHaptic.AudioHapticType = audioHaptic.AudioHapticType.AUDIO_HAPTIC_TYPE_AUDIO;

let result: boolean = audioHapticPlayerInstance.isMuted(audioHapticType);
```

## off('endOfStream')

```TypeScript
off(type: 'endOfStream', callback?: Callback<void>): void
```

取消监听流结束事件。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 事件回调类型，支持的事件为'endOfStream'，当取消监听流结束事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数，无返回结果。 |

## off('audioInterrupt')

```TypeScript
off(type: 'audioInterrupt', callback?: Callback<audio.InterruptEvent>): void
```

取消监听音频中断事件。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 事件回调类型，支持的事件为'audioInterrupt'，当取消监听音频中断事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.InterruptEvent](arkts-audio-audio-interruptevent-i.md)&gt; | 否 | 回调函数，返回中断事件信息。 |

## on('endOfStream')

```TypeScript
on(type: 'endOfStream', callback: Callback<void>): void
```

监听流结束事件（音频流播放结束时触发）。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 事件回调类型，支持的事件为'endOfStream'，当音频流播放结束时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，无返回结果。 |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void
```

监听音频中断事件（当音频焦点发生变化时触发）。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 事件回调类型，支持的事件为'audioInterrupt'，当音频焦点状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.InterruptEvent](arkts-audio-audio-interruptevent-i.md)&gt; | 是 | 回调函数，返回中断事件信息。 |

## release

```TypeScript
release(): Promise<void>
```

释放音振播放器。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.release().then(() => {
  console.info('Succeeded in releasing.');
}).catch((err: BusinessError) => {
  console.error(`Failed to release. Code: ${err.code}, message: ${err.message}`);
});
```

## setLoop

```TypeScript
setLoop(loop: boolean): Promise<void>
```

设置音振播放器循环播放。使用Promise异步回调。

> **注意：**
> 
> 该方法需在音振播放器销毁前调用。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loop | boolean | 是 | 是否循环播放。true表示循环播放，false表示不循环播放。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit in current state. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.setLoop(true).then(() => {
  console.info('Succeeded in setting loop.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set loop. Code: ${err.code}, message: ${err.message}`);
});
```

## setVolume

```TypeScript
setVolume(volume: number): Promise<void>
```

设置音振播放器的音量。使用Promise异步回调。

> **注意：**
> 
> 该方法需在音振播放器释放前调用。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 取值范围为[0.00, 1.00]，其中1.00表示最大音量（100%）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit in current state. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-参数超过取值范围) | Parameter out of range. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.setVolume(0.5).then(() => {
  console.info('Succeeded in setting volume.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set volume. Code: ${err.code}, message: ${err.message}`);
});
```

## start

```TypeScript
start(): Promise<void>
```

开始播放。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | IO error. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.start().then(() => {
  console.info('Succeeded in starting.');
}).catch((err: BusinessError) => {
  console.error(`Failed to start. Code: ${err.code}, message: ${err.message}`);
});
```

## stop

```TypeScript
stop(): Promise<void>
```

停止播放。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.stop().then(() => {
  console.info('Succeeded in stopping.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop. Code: ${err.code}, message: ${err.message}`);
});
```
