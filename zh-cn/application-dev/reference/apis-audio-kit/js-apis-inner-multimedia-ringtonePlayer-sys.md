# ringtonePlayer (铃声播放器)(系统接口)

铃声播放器提供了系统铃声的播放、配置、获取信息等功能。

ringtonePlayer需要和[@ohos.multimedia.systemSoundManager](js-apis-systemSoundManager-sys.md)配合使用，才能完成管理系统铃声的功能。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口为系统接口。

## 导入模块

```ts
import { systemSoundManager } from '@kit.AudioKit';
```

## RingtoneOptions<sup>10+</sup>

铃声参数选项。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

| 名称      | 类型            |必填   | 说明                              |
| --------- | -------------- | ---- | --------------------------------- |
| volume    | ArkTS-Dyn: number<br>ArkTS-Sta: double         | 是   | 指定的相对音量大小，取值范围为[0.00, 1.00]，1表示最大音量，即100%。 |
| loop      | boolean        | 是   | 是否开启循环播放，true表示开启循环播放，false表示不开启循环播放。 |

## RingtonePlayer<sup>10+</sup>

系统铃声播放器，提供系统铃声的参数设置、参数获取、播放、停止等功能。在调用RingtonePlayer的接口前，需要先通过[getRingtonePlayer](./js-apis-systemSoundManager-sys.md#getringtoneplayer11)创建实例。

### 属性

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

| 名称  | 类型                        | 只读 | 可选 | 说明               |
| ----- | -------------------------- | ---- | ---- | ------------------ |
| state | [media.AVPlayerState](../apis-media-kit/arkts-apis-media-t.md#avplayerstate9) | 是   | 否   | 音频渲染器的状态。 |

**示例：**

```ts
import { media } from '@kit.MediaKit';
let state: media.AVPlayerState = systemRingtonePlayer.state;
```

### getTitle<sup>10+</sup>

getTitle(callback: AsyncCallback&lt;string&gt;): void

获取铃声标题。使用callback异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | -----------------------------------------| ---- | ------------------------- |
| callback | AsyncCallback&lt;string&gt;              | 是   | 回调函数。<br>ArkTS-Dyn：当获取铃声标题成功，err为undefined，data为获取到的铃声标题；否则为错误对象。<br>ArkTS-Sta：当获取铃声标题成功，err为null，data为获取到的铃声标题；否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.getTitle((err: BusinessError, value: string) => {
  if (err) {
    console.error(`Failed to get system ringtone title. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate the value of the system ringtone title is obtained ${value}.`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.getTitle((err: BusinessError<void> | null, value: string | undefined) => {
  if (err) {
    console.error(`Failed to get system ringtone title. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate the value of the system ringtone title is obtained ${value}.`);
});
```

### getTitle<sup>10+</sup>

getTitle(): Promise&lt;string&gt;

获取铃声标题。使用Promise异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                  | 说明                              |
| --------------------- | -------------------------------- |
| Promise&lt;string&gt; | Promise对象，返回获取的系统铃声标题。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.getTitle().then((value: string) => {
  console.info(`Promise returned to indicate that the value of the system ringtone title is obtained ${value}.`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to get the system ringtone title ${err}`);
});
```

ArkTS-Sta示例：

```ts
systemRingtonePlayer.getTitle().then((value: string) => {
  console.info(`Promise returned to indicate that the value of the system ringtone title is obtained ${value}.`);
}).catch (async (err: BusinessError) => {
  console.error(`Failed to get the system ringtone title ${err}`);
});
```

### getAudioRendererInfo<sup>10+</sup>

getAudioRendererInfo(callback: AsyncCallback&lt;audio.AudioRendererInfo&gt;): void

获取铃声使用的AudioRendererInfo。使用callback异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | -----------------------------------------| ---- | ------------------------- |
| callback | AsyncCallback&lt;[audio.AudioRendererInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiorendererinfo8)&gt; | 是 | 回调函数。<br>ArkTS-Dyn：当获取音频渲染器信息成功，err为undefined，data为获取到的音频渲染器信息；否则为错误对象。<br>ArkTS-Sta：当获取音频渲染器信息成功，err为null，data为获取到的音频渲染器信息；否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioRendererInfo: audio.AudioRendererInfo | undefined = undefined;

systemRingtonePlayer.getAudioRendererInfo((err: BusinessError, value: audio.AudioRendererInfo) => {
  if (err) {
    console.error(`Failed to get ringtone AudioRendererInfo. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate the value of the ringtone AudioRendererInfo is obtained.`);
  audioRendererInfo = value;
});
```

ArkTS-Sta示例：

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioRendererInfo: audio.AudioRendererInfo | undefined = undefined;

systemRingtonePlayer.getAudioRendererInfo((err: BusinessError<void> | null, value: audio.AudioRendererInfo | undefined) => {
  if (err) {
    console.error(`Failed to get ringtone AudioRendererInfo. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate the value of the ringtone AudioRendererInfo is obtained.`);
  audioRendererInfo = value;
});
```

### getAudioRendererInfo<sup>10+</sup>

getAudioRendererInfo(): Promise&lt;audio.AudioRendererInfo&gt;

获取铃声使用的AudioRendererInfo。使用Promise异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                | 说明                            |
| ------------------- | ------------------------------- |
| Promise&lt;[audio.AudioRendererInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiorendererinfo8)&gt; | Promise对象，返回获取的音频渲染器信息。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioRendererInfo: audio.AudioRendererInfo | undefined = undefined;

systemRingtonePlayer.getAudioRendererInfo().then((value: audio.AudioRendererInfo) => {
  console.info(`Promise returned to indicate that the value of the ringtone AudioRendererInfo is obtained ${value}.`);
  audioRendererInfo = value;
}).catch ((err: BusinessError) => {
  console.error(`Failed to get the ringtone AudioRendererInfo ${err}`);
});
```

ArkTS-Sta示例：

```ts
import { audio } from '@kit.AudioKit';

let audioRendererInfo: audio.AudioRendererInfo | undefined = undefined;

systemRingtonePlayer.getAudioRendererInfo().then((value: audio.AudioRendererInfo) => {
  console.info(`Promise returned to indicate that the value of the ringtone AudioRendererInfo is obtained ${value}.`);
  audioRendererInfo = value;
}).catch (async (err: BusinessError) => {
  console.error(`Failed to get the ringtone AudioRendererInfo ${err}`);
});
```

### configure<sup>10+</sup>

configure(options: RingtoneOptions, callback: AsyncCallback&lt;void&gt;): void

配置铃声播放参数。使用callback异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | -----------------------------------------| ---- | ------------------------- |
| options  | [RingtoneOptions](#ringtoneoptions)      | 是   | 指定铃声参数。             |
| callback | AsyncCallback&lt;void&gt;                | 是   | 回调函数。<br>ArkTS-Dyn：当配置铃声播放参数成功，err为undefined，否则为错误对象。<br>ArkTS-Sta：当配置铃声播放参数成功，err为null，否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class RingtoneOptions {
  volume: number = 0;
  loop: boolean = false;
}
let ringtoneOptions: RingtoneOptions = {volume: 0.5, loop: true};

systemRingtonePlayer.configure(ringtoneOptions, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to configure ringtone options. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful setting of ringtone options.`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { RingtoneOptions } from 'multimedia.ringtonePlayer';

let ringtoneOptions: RingtoneOptions = {volume: 0.5, loop: true};

systemRingtonePlayer.configure(ringtoneOptions, (err: BusinessError<void> | null) => {
  if (err) {
    console.error(`Failed to configure ringtone options. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful setting of ringtone options.`);
});
```

### configure<sup>10+</sup>

configure(options: RingtoneOptions): Promise&lt;void&gt;

配置铃声播放参数。使用Promise异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | -----------------------------------------| ---- | ------------------------- |
| options  | [RingtoneOptions](#ringtoneoptions)      | 是   | 指定铃声参数。              |

**返回值：**

| 类型                | 说明                            |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class RingtoneOptions {
  volume: number = 0;
  loop: boolean = false;
}
let ringtoneOptions: RingtoneOptions = {volume: 0.5, loop: true};

systemRingtonePlayer.configure(ringtoneOptions).then(() => {
  console.info(`Promise returned to indicate a successful setting of ringtone options.`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to configure ringtone options. ${err}`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { RingtoneOptions } from 'multimedia.ringtonePlayer';

let ringtoneOptions: RingtoneOptions = {volume: 0.5, loop: true};

systemRingtonePlayer.configure(ringtoneOptions).then(() => {
  console.info(`Promise returned to indicate a successful setting of ringtone options.`);
}).catch (async (err: BusinessError) => {
  console.error(`Failed to configure ringtone options. ${err}`);
});
```

### start<sup>10+</sup>

start(callback: AsyncCallback&lt;void&gt;): void

开始播放铃声。使用callback异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | -----------------------------------------| ---- | ------------------------- |
| callback | AsyncCallback&lt;void&gt;                | 是   | 回调函数。<br>ArkTS-Dyn：当开始播放铃声成功，err为undefined，否则为错误对象。<br>ArkTS-Sta：当开始播放铃声成功，err为null，否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.start((err: BusinessError) => {
  if (err) {
    console.error(`Failed to start playing ringtone. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful starting of ringtone.`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.start((err: BusinessError<void> | null) => {
  if (err) {
    console.error(`Failed to start playing ringtone. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful starting of ringtone.`);
});
```

### start<sup>10+</sup>

start(): Promise&lt;void&gt;

开始播放铃声。使用Promise异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                | 说明                              |
| ------------------- | -------------------------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.start().then(() => {
  console.info(`Promise returned to indicate a successful starting of ringtone.`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to start playing ringtone. ${err}`);
});
```

ArkTS-Sta示例：

```ts
systemRingtonePlayer.start().then(() => {
  console.info(`Promise returned to indicate a successful starting of ringtone.`);
}).catch (async (err: BusinessError) => {
  console.error(`Failed to start playing ringtone. ${err}`);
});
```

### stop<sup>10+</sup>

stop(callback: AsyncCallback&lt;void&gt;): void

停止播放铃声。使用callback异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | -----------------------------------------| ---- | ------------------------- |
| callback | AsyncCallback&lt;void&gt;                | 是   | 回调函数。<br>ArkTS-Dyn：当停止播放铃声成功，err为undefined，否则为错误对象。<br>ArkTS-Sta：当停止播放铃声成功，err为null，否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.stop((err: BusinessError) => {
  if (err) {
    console.error(`Failed to stop playing ringtone. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful stopping of ringtone.`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.stop((err: BusinessError<void> | null) => {
  if (err) {
    console.error(`Failed to stop playing ringtone. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful stopping of ringtone.`);
});
```

### stop<sup>10+</sup>

stop(): Promise&lt;void&gt;

停止播放铃声。使用Promise异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                | 说明                              |
| ------------------- | -------------------------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.stop().then(() => {
  console.info(`Promise returned to indicate a successful stopping of ringtone.`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to stop playing ringtone. ${err}`);
});
```

ArkTS-Sta示例：

```ts
systemRingtonePlayer.stop().then(() => {
  console.info(`Promise returned to indicate a successful stopping of ringtone.`);
}).catch (async (err: BusinessError) => {
  console.error(`Failed to stop playing ringtone. ${err}`);
});
```

### release<sup>10+</sup>

release(callback: AsyncCallback&lt;void&gt;): void

释放铃声播放器。使用callback异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                       |
| -------- | -----------------------------------------| ---- | ------------------------- |
| callback | AsyncCallback&lt;void&gt;                | 是   | 回调函数。<br>ArkTS-Dyn：当释放铃声播放器成功，err为undefined，否则为错误对象。<br>ArkTS-Sta：当释放铃声播放器成功，err为null，否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.release((err: BusinessError) => {
  if (err) {
    console.error(`Failed to release ringtone player. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful releasing of ringtone player.`);
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.release((err: BusinessError<void> | null) => {
  if (err) {
    console.error(`Failed to release ringtone player. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful releasing of ringtone player.`);
});
```

### release<sup>10+</sup>

release(): Promise&lt;void&gt;

释放铃声播放器。使用Promise异步回调。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                | 说明                            |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemRingtonePlayer.release().then(() => {
  console.info(`Promise returned to indicate a successful releasing of ringtone player.`);
}).catch ((err: BusinessError) => {
  console.error(`Failed to release ringtone player. ${err}`);
});
```

ArkTS-Sta示例：

```ts
systemRingtonePlayer.release().then(() => {
  console.info(`Promise returned to indicate a successful releasing of ringtone player.`);
}).catch (async (err: BusinessError) => {
  console.error(`Failed to release ringtone player. ${err}`);
});
```

### on('audioInterrupt')<sup>10+</sup>

on(type: 'audioInterrupt', callback: Callback&lt;audio.InterruptEvent&gt;): void

监听音频中断事件（当音频焦点发生变化时触发）。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onAudioInterrupt](#onAudioInterrupt22)。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                                       |
| -------- | ----------------------- | ---- | -------------------------------------------------------------------------- |
| type     | string                  | 是   | 事件回调类型，支持的事件为'audioInterrupt'，当音频焦点状态发生变化时，触发该事件。 |
| callback | Callback&lt;[audio.InterruptEvent](../apis-audio-kit/arkts-apis-audio-i.md#interruptevent9)&gt; | 是   | 回调函数，返回中断事件信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let isPlaying: boolean; // 标识符，表示是否正在渲染。
let isDucked: boolean; // 标识符，表示是否被降低音量。

systemRingtonePlayer.on('audioInterrupt', async(interruptEvent: audio.InterruptEvent) => {
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // 由系统进行操作，强制打断音频渲染，应用需更新自身状态及显示内容等。
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
        console.info('Force ducked. Update volume status');
        isDucked = false; // 简化处理，代表应用更新音量状态的若干操作。
        break;
      default:
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // 由应用进行操作，应用可以自主选择响应操作或忽略该事件。
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // 建议应用继续渲染（说明音频流此前被强制暂停，临时失去焦点，现在可以恢复渲染）。
        console.info('Resume force paused renderer or ignore');
        // 若选择继续渲染，需在此处主动执行开始渲染的若干操作。
        break;
      default:
        break;
    }
  }
});
```

### onAudioInterrupt<sup>22+</sup>

onAudioInterrupt(callback: Callback&lt;audio.InterruptEvent&gt;): void

监听音频中断事件（当音频焦点发生变化时触发）。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('audioInterrupt')](#onaudioInterrupt10)。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                                       |
| -------- | ----------------------- | ---- | -------------------------------------------------------------------------- |
| callback | Callback&lt;[audio.InterruptEvent](../apis-audio-kit/arkts-apis-audio-i.md#interruptevent9)&gt; | 是   | 回调函数，返回中断事件信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202     | Not system application. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let isPlaying: boolean; // 标识符，表示是否正在渲染。
let isDucked: boolean; // 标识符，表示是否被降低音量。

systemRingtonePlayer.onAudioInterrupt((interruptEvent: audio.InterruptEvent) => {
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // 由系统进行操作，强制打断音频渲染，应用需更新自身状态及显示内容等。
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
        console.info('Force ducked. Update volume status');
        isDucked = false; // 简化处理，代表应用更新音量状态的若干操作。
        break;
      default:
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // 由应用进行操作，应用可以自主选择响应操作或忽略该事件。
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // 建议应用继续渲染（说明音频流此前被强制暂停，临时失去焦点，现在可以恢复渲染）。
        console.info('Resume force paused renderer or ignore');
        // 若选择继续渲染，需在此处主动执行开始渲染的若干操作。
        break;
      default:
        break;
    }
  }
});
```

### off('audioInterrupt')<sup>10+<sup>

off(type: 'audioInterrupt'): void

取消监听音频中断事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offAudioInterrupt](#offAudioInterrupt22)。

**系统接口：** 该接口为系统接口

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名 | 类型   | 必填 | 说明                                              |
| :----- | :----- | :--- | :------------------------------------------------ |
| type   | string | 是   | 事件回调类型，支持的事件为'audioInterrupt'，当取消监听音频中断事件时，触发该事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
systemRingtonePlayer.off('audioInterrupt');
```

### offAudioInterrupt<sup>22+</sup>

offAudioInterrupt(): void

取消监听音频中断事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('audioInterrupt')](#offaudioInterrupt10)。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Sta起始版本：** 22

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202     | Not system application. |

**示例：**

```ts
systemRingtonePlayer.offAudioInterrupt();
```
