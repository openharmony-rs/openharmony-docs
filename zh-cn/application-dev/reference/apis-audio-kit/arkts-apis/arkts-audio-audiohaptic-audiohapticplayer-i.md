# AudioHapticPlayer

音振播放器，提供音振协同播放功能。在调用AudioHapticPlayer的接口前，需要先通过[createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer-1)创建实例。

**起始版本：** 11

<!--Device-audioHaptic-interface AudioHapticPlayer--><!--Device-audioHaptic-interface AudioHapticPlayer-End-->

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

<!--Device-AudioHapticPlayer-isMuted(type: AudioHapticType): boolean--><!--Device-AudioHapticPlayer-isMuted(type: AudioHapticType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AudioHapticType](arkts-audio-audiohaptic-audiohaptictype-e.md) | 是 | 音振类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 表示查询的音振类型是否被静音。true表示静音，false表示非静音。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Parameter verification failed. |

**示例：**

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

<!--Device-AudioHapticPlayer-off(type: 'endOfStream', callback?: Callback<void>): void--><!--Device-AudioHapticPlayer-off(type: 'endOfStream', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 事件回调类型，支持的事件为'endOfStream'，当取消监听流结束事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<void> | 否 | 回调函数，无返回结果。 |

**示例：**

```TypeScript
// 取消该事件的所有监听。
audioHapticPlayerInstance.off('endOfStream');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let endOfStreamCallback = () => {
  console.info('Succeeded in using on or off function.');
};

audioHapticPlayerInstance.on('endOfStream', endOfStreamCallback);

audioHapticPlayerInstance.off('endOfStream', endOfStreamCallback);

```

## off('audioInterrupt')

```TypeScript
off(type: 'audioInterrupt', callback?: Callback<audio.InterruptEvent>): void
```

取消监听音频中断事件。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioHapticPlayer-off(type: 'audioInterrupt', callback?: Callback<audio.InterruptEvent>): void--><!--Device-AudioHapticPlayer-off(type: 'audioInterrupt', callback?: Callback<audio.InterruptEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 事件回调类型，支持的事件为'audioInterrupt'，当取消监听音频中断事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<audio.InterruptEvent> | 否 | 回调函数，返回中断事件信息。 |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';

// 取消该事件的所有监听。
audioHapticPlayerInstance.off('audioInterrupt');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let isPlaying: boolean; // 标识符，表示是否正在渲染。
let isDucked: boolean; // 标识符，表示是否被降低音量。
let audioInterruptCallback = (interruptEvent: audio.InterruptEvent) => {
  // 在发生音频打断事件时，audioHapticPlayerInstance收到interruptEvent回调，此处根据其内容做相应处理。
  // 1. 可选：读取interruptEvent.forceType的类型，判断系统是否已强制执行相应操作。
  // 注意：默认焦点策略下，INTERRUPT_HINT_RESUME为INTERRUPT_SHARE类型，其余hintType均为INTERRUPT_FORCE类型。因此对forceType可不做判断。
  // 2. 必选：读取interruptEvent.hintType的类型，做出相应的处理。
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // 音频焦点事件已由系统强制执行，应用需更新自身状态及显示内容等。
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // 音频流已被暂停，临时失去焦点，待可重获焦点时会收到resume对应的interruptEvent。
        console.info('Force paused. Update playing status and stop writing');
        isPlaying = false; // 简化处理，代表应用切换至暂停状态的若干操作。
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // 音频流已被停止，永久失去焦点，若想恢复渲染，需用户主动触发。
        console.info('Force stopped. Update playing status and stop writing');
        isPlaying = false; // 简化处理，代表应用切换至暂停状态的若干操作。
        break;
      case audio.InterruptHint.INTERRUPT_HINT_DUCK:
        // 音频流已被降低音量渲染。
        console.info('Force ducked. Update volume status');
        isDucked = true; // 简化处理，代表应用更新音量状态的若干操作。
        break;
      case audio.InterruptHint.INTERRUPT_HINT_UNDUCK:
        // 音频流已被恢复正常音量渲染。
        console.info('Force unducked. Update volume status');
        isDucked = false; // 简化处理，代表应用更新音量状态的若干操作。
        break;
      default:
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // 音频焦点事件需由应用进行操作，应用可以自主选择如何处理该事件，建议应用遵从InterruptHint提示处理。
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // 建议应用继续渲染（说明音频流此前被强制暂停，临时失去焦点，现在可以恢复渲染）。
        // 由于INTERRUPT_HINT_RESUME操作需要应用主动执行，系统无法强制，故INTERRUPT_HINT_RESUME事件一定为INTERRUPT_SHARE类型。
        console.info('Resume force paused renderer or ignore');
        // 若选择继续渲染，需在此处主动执行开始渲染的若干操作。
        break;
      default:
        break;
    }
  }
};

audioHapticPlayerInstance.on('audioInterrupt', audioInterruptCallback);

audioHapticPlayerInstance.off('audioInterrupt', audioInterruptCallback);

```

## on('endOfStream')

```TypeScript
on(type: 'endOfStream', callback: Callback<void>): void
```

监听流结束事件（音频流播放结束时触发）。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioHapticPlayer-on(type: 'endOfStream', callback: Callback<void>): void--><!--Device-AudioHapticPlayer-on(type: 'endOfStream', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 事件回调类型，支持的事件为'endOfStream'，当音频流播放结束时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<void> | 是 | 回调函数，无返回结果。 |

**示例：**

```TypeScript
audioHapticPlayerInstance.on('endOfStream', () => {
  console.info('Succeeded in using on function.');
});

```

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void
```

监听音频中断事件（当音频焦点发生变化时触发）。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioHapticPlayer-on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void--><!--Device-AudioHapticPlayer-on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 事件回调类型，支持的事件为'audioInterrupt'，当音频焦点状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<audio.InterruptEvent> | 是 | 回调函数，返回中断事件信息。 |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';

let isPlaying: boolean; // 标识符，表示是否正在渲染。
let isDucked: boolean; // 标识符，表示是否被降低音量。

audioHapticPlayerInstance.on('audioInterrupt', (interruptEvent: audio.InterruptEvent) => {
  // 在发生音频打断事件时，audioHapticPlayerInstance收到interruptEvent回调，此处根据其内容做相应处理。
  // 1. 可选：读取interruptEvent.forceType的类型，判断系统是否已强制执行相应操作。
  // 注意：默认焦点策略下，INTERRUPT_HINT_RESUME为INTERRUPT_SHARE类型，其余hintType均为INTERRUPT_FORCE类型。因此对forceType可不做判断。
  // 2. 必选：读取interruptEvent.hintType的类型，做出相应的处理。
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // 音频焦点事件已由系统强制执行，应用需更新自身状态及显示内容等。
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // 音频流已被暂停，临时失去焦点，待可重获焦点时会收到resume对应的interruptEvent。
        console.info('Force paused. Update playing status and stop writing');
        isPlaying = false; // 简化处理，代表应用切换至暂停状态的若干操作。
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // 音频流已被停止，永久失去焦点，若想恢复渲染，需用户主动触发。
        console.info('Force stopped. Update playing status and stop writing');
        isPlaying = false; // 简化处理，代表应用切换至暂停状态的若干操作。
        break;
      case audio.InterruptHint.INTERRUPT_HINT_DUCK:
        // 音频流已被降低音量渲染。
        console.info('Force ducked. Update volume status');
        isDucked = true; // 简化处理，代表应用更新音量状态的若干操作。
        break;
      case audio.InterruptHint.INTERRUPT_HINT_UNDUCK:
        // 音频流已被恢复正常音量渲染。
        console.info('Force unducked. Update volume status');
        isDucked = false; // 简化处理，代表应用更新音量状态的若干操作。
        break;
      default:
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // 音频焦点事件需由应用进行操作，应用可以自主选择如何处理该事件，建议应用遵从InterruptHint提示处理。
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // 建议应用继续渲染（说明音频流此前被强制暂停，临时失去焦点，现在可以恢复渲染）。
        // 由于INTERRUPT_HINT_RESUME操作需要应用主动执行，系统无法强制，故INTERRUPT_HINT_RESUME事件一定为INTERRUPT_SHARE类型。
        console.info('Resume force paused renderer or ignore');
        // 若选择继续渲染，需在此处主动执行开始渲染的若干操作。
        break;
      default:
        break;
    }
  }
});

```

## release

```TypeScript
release(): Promise<void>
```

释放音振播放器。使用Promise异步回调。

**起始版本：** 11

<!--Device-AudioHapticPlayer-release(): Promise<void>--><!--Device-AudioHapticPlayer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |

**示例：**

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

<!--Device-AudioHapticPlayer-setLoop(loop: boolean): Promise<void>--><!--Device-AudioHapticPlayer-setLoop(loop: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loop | boolean | 是 | 是否循环播放。true表示循环播放，false表示不循环播放。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit in current state. |

**示例：**

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

<!--Device-AudioHapticPlayer-setVolume(volume: double): Promise<void>--><!--Device-AudioHapticPlayer-setVolume(volume: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 取值范围为[0.00, 1.00]，其中1.00表示最大音量（100%）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit in current state. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-参数超过取值范围) | Parameter out of range. |

**示例：**

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

<!--Device-AudioHapticPlayer-start(): Promise<void>--><!--Device-AudioHapticPlayer-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | IO error. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |

**示例：**

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

<!--Device-AudioHapticPlayer-stop(): Promise<void>--><!--Device-AudioHapticPlayer-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.stop().then(() => {
  console.info('Succeeded in stopping.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop Code: ${err.code}, message: ${err.message}`);
});

```

