# Interface (AudioCapturer)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--SE: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--TSE: @Filger-->

> **说明：**
>
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 8开始支持。

提供音频采集的相关接口。

在使用AudioCapturer的接口之前，需先通过[createAudioCapturer](arkts-apis-audio-f.md#audiocreateaudiocapturer8)获取AudioCapturer实例。

## 导入模块

```ts
import { audio } from '@kit.AudioKit';
```

## 属性

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

| 名称  | 类型                     | 只读 | 可选 | 说明             |
| :---- | :------------------------- | :--- | :--- | :--------------- |
| state<sup>8+</sup>  | [AudioState](arkts-apis-audio-e.md#audiostate8) | 是 | 否   | 音频采集器状态。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let state: audio.AudioState = audioCapturer.state;
```

## getCapturerInfo<sup>8+</sup>

getCapturerInfo(callback: AsyncCallback<AudioCapturerInfo\>): void

获取音频采集器信息。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                              | 必填 | 说明                                 |
| :------- | :-------------------------------- | :--- | :----------------------------------- |
| callback | AsyncCallback<[AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)\> | 是   | 回调函数。当获取音频采集器信息成功，err为undefined，data为获取到的音频采集器信息；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getCapturerInfo((err: BusinessError, capturerInfo: audio.AudioCapturerInfo) => {
  if (err) {
    console.error('Failed to get capture info');
  } else {
    console.info('Capturer getCapturerInfo:');
    console.info(`Capturer source: ${capturerInfo.source}`);
    console.info(`Capturer flags: ${capturerInfo.capturerFlags}`);
  }
});
```


## getCapturerInfo<sup>8+</sup>

getCapturerInfo(): Promise<AudioCapturerInfo\>

获取音频采集器信息。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型                                              | 说明                                |
| :------------------------------------------------ | :---------------------------------- |
| Promise<[AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)\> | Promise对象，返回音频采集器信息。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getCapturerInfo().then((audioParamsGet: audio.AudioCapturerInfo) => {
  if (audioParamsGet != undefined) {
    console.info('AudioFrameworkRecLog: Capturer CapturerInfo:');
    console.info(`AudioFrameworkRecLog: Capturer SourceType: ${audioParamsGet.source}`);
    console.info(`AudioFrameworkRecLog: Capturer capturerFlags: ${audioParamsGet.capturerFlags}`);
  } else {
    console.info(`AudioFrameworkRecLog: audioParamsGet is : ${audioParamsGet}`);
    console.info('AudioFrameworkRecLog: audioParams getCapturerInfo are incorrect');
  }
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRecLog: CapturerInfo :ERROR: ${err}`);
})
```

## getCapturerInfoSync<sup>10+</sup>

getCapturerInfoSync(): AudioCapturerInfo

获取音频采集器信息。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型                                              | 说明                                |
| :------------------------------------------------ | :---------------------------------- |
| [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8) | 返回音频采集器信息。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioParamsGet: audio.AudioCapturerInfo = audioCapturer.getCapturerInfoSync();
  console.info(`AudioFrameworkRecLog: Capturer SourceType: ${audioParamsGet.source}`);
  console.info(`AudioFrameworkRecLog: Capturer capturerFlags: ${audioParamsGet.capturerFlags}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`AudioFrameworkRecLog: CapturerInfo :ERROR: ${error}`);
}
```

## getStreamInfo<sup>8+</sup>

getStreamInfo(callback: AsyncCallback<AudioStreamInfo\>): void

获取音频采集器流信息。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                             |
| :------- | :--------------------------------------------------- | :--- | :------------------------------- |
| callback | AsyncCallback<[AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8)\> | 是   | 回调函数。当获取音频采集器流信息成功，err为undefined，data为获取到的音频采集器流信息；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getStreamInfo((err: BusinessError, streamInfo: audio.AudioStreamInfo) => {
  if (err) {
    console.error('Failed to get stream info');
  } else {
    console.info('Capturer GetStreamInfo:');
    console.info(`Capturer sampling rate: ${streamInfo.samplingRate}`);
    console.info(`Capturer channel: ${streamInfo.channels}`);
    console.info(`Capturer format: ${streamInfo.sampleFormat}`);
    console.info(`Capturer encoding type: ${streamInfo.encodingType}`);
  }
});
```

## getStreamInfo<sup>8+</sup>

getStreamInfo(): Promise<AudioStreamInfo\>

获取音频采集器流信息。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型                                           | 说明                            |
| :--------------------------------------------- | :------------------------------ |
| Promise<[AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8)\> | Promise对象，返回音频流信息。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getStreamInfo().then((audioParamsGet: audio.AudioStreamInfo) => {
  console.info('getStreamInfo:');
  console.info(`sampleFormat: ${audioParamsGet.sampleFormat}`);
  console.info(`samplingRate: ${audioParamsGet.samplingRate}`);
  console.info(`channels: ${audioParamsGet.channels}`);
  console.info(`encodingType: ${audioParamsGet.encodingType}`);
}).catch((err: BusinessError) => {
  console.error(`getStreamInfo :ERROR: ${err}`);
});
```

## getStreamInfoSync<sup>10+</sup>

getStreamInfoSync(): AudioStreamInfo

获取音频采集器流信息。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型                                           | 说明                            |
| :--------------------------------------------- | :------------------------------ |
| [AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8) | 返回音频流信息。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioParamsGet: audio.AudioStreamInfo = audioCapturer.getStreamInfoSync();
  console.info(`sampleFormat: ${audioParamsGet.sampleFormat}`);
  console.info(`samplingRate: ${audioParamsGet.samplingRate}`);
  console.info(`channels: ${audioParamsGet.channels}`);
  console.info(`encodingType: ${audioParamsGet.encodingType}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`getStreamInfo :ERROR: ${error}`);
}
```

## getAudioStreamId<sup>9+</sup>

getAudioStreamId(callback: AsyncCallback<number\>): void

获取音频流id。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                 |
| :------- | :--------------------------------------------------- | :--- | :------------------- |
| callback | AsyncCallback<number\> | 是   | 回调函数。当获取音频流id成功，err为undefined，data为获取到的音频流id；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioStreamId((err: BusinessError, streamId: number) => {
  console.info(`audioCapturer GetStreamId: ${streamId}`);
});
```

## getAudioStreamId<sup>9+</sup>

getAudioStreamId(): Promise<number\>

获取音频流id。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型             | 说明                   |
| :----------------| :--------------------- |
| Promise<number\> | Promise对象，返回音频流id。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioStreamId().then((streamId: number) => {
  console.info(`audioCapturer getAudioStreamId: ${streamId}`);
}).catch((err: BusinessError) => {
  console.error(`ERROR: ${err}`);
});
```

## getAudioStreamIdSync<sup>10+</sup>

getAudioStreamIdSync(): number

获取音频流id。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型             | 说明                   |
| :----------------| :--------------------- |
| number | 返回音频流id。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let streamId: number = audioCapturer.getAudioStreamIdSync();
  console.info(`audioCapturer getAudioStreamIdSync: ${streamId}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## start<sup>8+</sup>

start(callback: AsyncCallback<void\>): void

启动音频采集器，开始获取音频数据。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                 | 必填 | 说明                           |
| :------- | :------------------- | :--- | :----------------------------- |
| callback | AsyncCallback<void\> | 是   | 回调函数。当启动音频采集器成功，err为undefined，否则为错误对象。异常将返回error对象：<br>错误码6800301：表示包含状态检查异常、焦点抢占失败、系统处理异常（具体错误查看系统日志）。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.start((err: BusinessError) => {
  if (err) {
    console.error('Capturer start failed.');
  } else {
    console.info('Capturer start success.');
  }
});
```


## start<sup>8+</sup>

start(): Promise<void\>

启动音频采集器，开始获取音频数据。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型           | 说明                          |
| :------------- | :---------------------------- |
| Promise<void\> | Promise对象，成功表示启动音频采集器成功。异常将返回error对象：<br>错误码6800301：表示包含状态检查异常、焦点抢占失败、系统处理异常（具体错误查看系统日志）。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.start().then(() => {
  console.info('AudioFrameworkRecLog: ---------START---------');
  console.info('AudioFrameworkRecLog: Capturer started: SUCCESS');
  console.info(`AudioFrameworkRecLog: AudioCapturer: STATE: ${audioCapturer.state}`);
  console.info('AudioFrameworkRecLog: Capturer started: SUCCESS');
  if ((audioCapturer.state == audio.AudioState.STATE_RUNNING)) {
    console.info('AudioFrameworkRecLog: AudioCapturer is in Running State');
  }
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRecLog: Capturer start :ERROR : ${err}`);
});
```

## stop<sup>8+</sup>

stop(callback: AsyncCallback<void\>): void

停止音频采集器，停止输入音频流。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                 | 必填 | 说明                           |
| :------- | :------------------- | :--- | :----------------------------- |
| callback | AsyncCallback<void\> | 是   | 回调函数。当停止音频采集成功，err为undefined，否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.stop((err: BusinessError) => {
  if (err) {
    console.error('Capturer stop failed');
  } else {
    console.info('Capturer stopped.');
  }
});
```


## stop<sup>8+</sup>

stop(): Promise<void\>

停止音频采集器，停止输入音频流。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型           | 说明                          |
| :------------- | :---------------------------- |
| Promise<void\> | Promise对象。无返回结果的Promise对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.stop().then(() => {
  console.info('AudioFrameworkRecLog: ---------STOP RECORD---------');
  console.info('AudioFrameworkRecLog: Capturer stopped: SUCCESS');
  if ((audioCapturer.state == audio.AudioState.STATE_STOPPED)){
    console.info('AudioFrameworkRecLog: State is Stopped:');
  }
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRecLog: Capturer stop: ERROR: ${err}`);
});
```

## release<sup>8+</sup>

release(callback: AsyncCallback<void\>): void

释放音频采集器。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                |
| :------- | :------------------- | :--- | :---------------------------------- |
| callback | AsyncCallback<void\> | 是   | 回调函数。当释放音频采集器成功，err为undefined，否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.release((err: BusinessError) => {
  if (err) {
    console.error('capturer release failed');
  } else {
    console.info('capturer released.');
  }
});
```


## release<sup>8+</sup>

release(): Promise<void\>

释放音频采集器。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型           | 说明                          |
| :------------- | :---------------------------- |
| Promise<void\> | Promise对象。无返回结果的Promise对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.release().then(() => {
  console.info('AudioFrameworkRecLog: ---------RELEASE RECORD---------');
  console.info('AudioFrameworkRecLog: Capturer release : SUCCESS');
  console.info(`AudioFrameworkRecLog: AudioCapturer : STATE : ${audioCapturer.state}`);
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRecLog: Capturer stop: ERROR: ${err}`);
});
```


## getAudioTime<sup>8+</sup>

getAudioTime(callback: AsyncCallback<number\>): void

获取当前录制位置的时间戳（从1970年1月1日开始），单位为纳秒。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                   | 必填 | 说明                           |
| :------- | :--------------------- | :--- | :----------------------------- |
| callback | AsyncCallback<number\> | 是   | 回调函数。当获取时间戳成功，err为undefined，data为获取到的时间戳；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioTime((err: BusinessError, timestamp: number) => {
  console.info(`Current timestamp: ${timestamp}`);
});
```

## getAudioTime<sup>8+</sup>

getAudioTime(): Promise<number\>

获取当前录制位置的时间戳（从1970年1月1日开始），单位为纳秒。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型             | 说明                          |
| :--------------- | :---------------------------- |
| Promise<number\> | Promise对象，返回时间戳（从1970年1月1日开始），单位为纳秒。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioTime().then((audioTime: number) => {
  console.info(`AudioFrameworkRecLog: AudioCapturer getAudioTime : Success ${audioTime}`);
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRecLog: AudioCapturer Created : ERROR : ${err}`);
});
```

## getAudioTimeSync<sup>10+</sup>

getAudioTimeSync(): number

获取当前录制位置的时间戳（从1970年1月1日开始），单位为纳秒。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型             | 说明                          |
| :--------------- | :---------------------------- |
| number | 返回时间戳。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioTime: number = audioCapturer.getAudioTimeSync();
  console.info(`AudioFrameworkRecLog: AudioCapturer getAudioTimeSync : Success ${audioTime}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`AudioFrameworkRecLog: AudioCapturer getAudioTimeSync : ERROR : ${error}`);
}
```

## getAudioTimestampInfo<sup>19+</sup>

getAudioTimestampInfo(): Promise\<AudioTimestampInfo>

获取输入音频流时间戳和当前数据帧位置信息。

该接口可以获取到音频通道实际录制位置（framePosition）以及录制到该位置时候的时间戳（timestamp），时间戳单位为纳秒。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型                                                    | 描述                    |
|-------------------------------------------------------| ----------------------- |
| Promise\<[AudioTimestampInfo](arkts-apis-audio-i.md#audiotimestampinfo19)> | Promise对象，返回音频流时间戳和当前数据帧位置信息。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800103 | Operation not permit at current state. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioTimestampInfo().then((audioTimestampInfo: audio.AudioTimestampInfo) => {
  console.info(`Current timestamp: ${audioTimestampInfo.timestamp}`);
}).catch((err: BusinessError) => {
  console.error(`ERROR: ${err}`);
});
```

## getAudioTimestampInfoSync<sup>19+</sup>

getAudioTimestampInfoSync(): AudioTimestampInfo

获取音频流时间戳和当前数据帧位置信息。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型             | 描述                    |
| ---------------- | ----------------------- |
| [AudioTimestampInfo](arkts-apis-audio-i.md#audiotimestampinfo19) | 返回音频流时间戳和当前数据帧位置信息。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800103 | Operation not permit at current state. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioTimestampInfo: audio.AudioTimestampInfo = audioCapturer.getAudioTimestampInfoSync();
  console.info(`Current timestamp: ${audioTimestampInfo.timestamp}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## getBufferSize<sup>8+</sup>

getBufferSize(callback: AsyncCallback<number\>): void

获取采集器合理的最小缓冲区大小。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                 |
| :------- | :--------------------- | :--- | :----------------------------------- |
| callback | AsyncCallback<number\> | 是   | 回调函数。当获取采集器合理的最小缓冲区大小成功，err为undefined，data为获取到的采集器合理的最小缓冲区大小；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getBufferSize((err: BusinessError, bufferSize: number) => {
  if (!err) {
    console.info(`BufferSize : ${bufferSize}`);
    audioCapturer.read(bufferSize, true).then((buffer: ArrayBuffer) => {
      console.info(`Buffer read is ${buffer.byteLength}`);
    }).catch((err: BusinessError) => {
      console.error(`AudioFrameworkRecLog: AudioCapturer Created : ERROR : ${err}`);
    });
  }
});
```

## getBufferSize<sup>8+</sup>

getBufferSize(): Promise<number\>

获取采集器合理的最小缓冲区大小。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型             | 说明                                |
| :--------------- | :---------------------------------- |
| Promise<number\> | Promise对象，返回缓冲区大小。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bufferSize: number = 0;

audioCapturer.getBufferSize().then((data: number) => {
  console.info(`AudioFrameworkRecLog: getBufferSize :SUCCESS ${data}`);
  bufferSize = data;
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRecLog: getBufferSize :ERROR : ${err}`);
});
```

## getBufferSizeSync<sup>10+</sup>

getBufferSizeSync(): number

获取采集器合理的最小缓冲区大小。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型             | 说明                                |
| :--------------- | :---------------------------------- |
| number | 返回缓冲区大小。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bufferSize: number = 0;

try {
  bufferSize = audioCapturer.getBufferSizeSync();
  console.info(`AudioFrameworkRecLog: getBufferSizeSync :SUCCESS ${bufferSize}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`AudioFrameworkRecLog: getBufferSizeSync :ERROR : ${error}`);
}
```

## getCurrentInputDevices<sup>11+</sup>

getCurrentInputDevices(): AudioDeviceDescriptors

获取录音流输入设备信息。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型                   | 说明                                                   |
| ---------------------- | ------------------------------------------------------ |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)             | 同步接口，返回设备属性数组类型数据。 |

**示例：**

```ts
let deviceDescriptors: audio.AudioDeviceDescriptors = audioCapturer.getCurrentInputDevices();
console.info(`Device id: ${deviceDescriptors[0].id}`);
console.info(`Device type: ${deviceDescriptors[0].deviceType}`);
console.info(`Device role: ${deviceDescriptors[0].deviceRole}`);
console.info(`Device name: ${deviceDescriptors[0].name}`);
console.info(`Device address: ${deviceDescriptors[0].address}`);
console.info(`Device samplerates: ${deviceDescriptors[0].sampleRates[0]}`);
console.info(`Device channelcounts: ${deviceDescriptors[0].channelCounts[0]}`);
console.info(`Device channelmask: ${deviceDescriptors[0].channelMasks[0]}`);
if (deviceDescriptors[0].encodingTypes) {
  console.info(`Device encodingTypes: ${deviceDescriptors[0].encodingTypes[0]}`);
}
```

## getCurrentAudioCapturerChangeInfo<sup>11+</sup>

getCurrentAudioCapturerChangeInfo(): AudioCapturerChangeInfo

获取录音流配置。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型             | 说明                                |
| :--------------- | :---------------------------------- |
| [AudioCapturerChangeInfo](arkts-apis-audio-i.md#audiocapturerchangeinfo9) | 同步接口，返回描述音频采集器更改信息。 |

**示例：**

```ts
let info: audio.AudioCapturerChangeInfo = audioCapturer.getCurrentAudioCapturerChangeInfo();
console.info(`Info streamId: ${info.streamId}`);
console.info(`Info source: ${info.capturerInfo.source}`);
console.info(`Info capturerFlags: ${info.capturerInfo.capturerFlags}`);
console.info(`Info muted: ${info.muted}`);
console.info(`Info type: ${info.deviceDescriptors[0].deviceType}`);
console.info(`Info role: ${info.deviceDescriptors[0].deviceRole}`);
console.info(`Info name: ${info.deviceDescriptors[0].name}`);
console.info(`Info address: ${info.deviceDescriptors[0].address}`);
console.info(`Info samplerates: ${info.deviceDescriptors[0].sampleRates[0]}`);
console.info(`Info channelcounts: ${info.deviceDescriptors[0].channelCounts[0]}`);
console.info(`Info channelmask: ${info.deviceDescriptors[0].channelMasks[0]}`);
if (info.deviceDescriptors[0].encodingTypes) {
  console.info(`Device encodingTypes: ${info.deviceDescriptors[0].encodingTypes[0]}`);
}
```

## on('audioInterrupt')<sup>10+</sup>

on(type: 'audioInterrupt', callback: Callback\<InterruptEvent>): void

监听音频中断事件（当音频焦点发生变化时触发）。使用callback异步回调。

AudioCapturer对象在start事件时获取焦点，在pause、stop等事件时释放焦点，无需开发者主动申请。

调用此方法后，如果AudioCapturer对象获取焦点失败或发生中断事件（如被其他音频打断等），会收到[InterruptEvent](arkts-apis-audio-i.md#interruptevent9)。建议应用根据InterruptEvent的信息进行进一步处理。更多信息请参阅文档[音频焦点和音频会话介绍](../../media/audio/audio-playback-concurrency.md)。

**系统能力：** SystemCapability.Multimedia.Audio.Interrupt

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                                         |
| -------- | -------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                       | 是   | 事件回调类型，支持的事件为'audioInterrupt'，当音频焦点状态发生变化时，触发该事件。 |
| callback | Callback\<[InterruptEvent](arkts-apis-audio-i.md#interruptevent9)\> | 是   | 回调函数，返回中断事件信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let isCapturing: boolean = false; // 标识符，表示是否正在采集。

audioCapturer.on('audioInterrupt', (interruptEvent: audio.InterruptEvent) => {
  // 在发生音频打断事件时，audioCapturer收到interruptEvent回调，此处根据其内容做相应处理。
  // 1. 可选：读取interruptEvent.forceType的类型，判断系统是否已强制执行相应操作。
  // 注意：默认焦点策略下，INTERRUPT_HINT_RESUME为INTERRUPT_SHARE类型，其余hintType均为INTERRUPT_FORCE类型。因此对forceType可不做判断。
  // 2. 必选：读取interruptEvent.hintType的类型，做出相应的处理。
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // 音频焦点事件已由系统强制执行，应用需更新自身状态及显示内容等。
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // 音频流已被暂停，临时失去焦点，待可重获焦点时会收到resume对应的interruptEvent。
        console.info('Force paused. Update capturing status and stop reading');
        isCapturing = false; // 简化处理，代表应用切换至暂停状态的若干操作。
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // 音频流已被停止，永久失去焦点，若想恢复采集，需用户主动触发。
        console.info('Force stopped. Update capturing status and stop reading');
        isCapturing = false; // 简化处理，代表应用切换至暂停状态的若干操作。
        break;
      default:
        console.info('Invalid interruptEvent');
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // 音频焦点事件需由应用进行操作，应用可以自主选择如何处理该事件，建议应用遵从InterruptHint提示处理。
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // 建议应用继续采集（说明音频流此前被强制暂停，临时失去焦点，现在可以恢复采集）。
        // 由于INTERRUPT_HINT_RESUME操作需要应用主动执行，系统无法强制，故INTERRUPT_HINT_RESUME事件一定为INTERRUPT_SHARE类型。
        console.info('Resume force paused renderer or ignore');
        // 若选择继续采集，需在此处主动执行开始采集的若干操作。
        break;
      default:
        console.info('Invalid interruptEvent');
        break;
    }
  }
});
```

## off('audioInterrupt')<sup>10+</sup>

off(type: 'audioInterrupt'): void

取消监听音频中断事件。

**系统能力：** SystemCapability.Multimedia.Audio.Interrupt

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                                         |
| -------- | -------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                       | 是   | 事件回调类型，支持的事件为'audioInterrupt'，当取消监听音频中断事件时，触发该事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
audioCapturer.off('audioInterrupt');
```

## on('inputDeviceChange')<sup>11+</sup>

on(type: 'inputDeviceChange', callback: Callback\<AudioDeviceDescriptors>): void

监听音频输入设备变化事件（当音频输入设备发生变化时触发）。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                       | 必填 | 说明                                        |
| :------- | :------------------------- | :--- | :------------------------------------------ |
| type     | string                     | 是   | 事件回调类型，支持的事件为'inputDeviceChange'，当音频输入设备发生变化时，触发该事件。 |
| callback | Callback\<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) > | 是   | 回调函数，返回监听的音频输入设备变化(返回数据为切换后的设备信息)。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
audioCapturer.on('inputDeviceChange', (deviceChangeInfo: audio.AudioDeviceDescriptors) => {
  console.info(`inputDevice id: ${deviceChangeInfo[0].id}`);
  console.info(`inputDevice deviceRole: ${deviceChangeInfo[0].deviceRole}`);
  console.info(`inputDevice deviceType: ${deviceChangeInfo[0].deviceType}`);
});
```
## off('inputDeviceChange')<sup>11+</sup>

off(type: 'inputDeviceChange', callback?: Callback\<AudioDeviceDescriptors>): void

取消监听音频输入设备更改事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                       | 必填 | 说明                                       |
| :------- | :------------------------- | :--- |:-----------------------------------------|
| type     | string                     | 是   | 事件回调类型，支持的事件为'inputDeviceChange'，当取消监听音频输入设备更改事件时，触发该事件。 |
| callback | Callback\<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) > | 否   | 回调函数，返回监听的音频输入设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioCapturer.off('inputDeviceChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let inputDeviceChangeCallback = (deviceChangeInfo: audio.AudioDeviceDescriptors) => {
  console.info(`inputDevice id: ${deviceChangeInfo[0].id}`);
  console.info(`inputDevice deviceRole: ${deviceChangeInfo[0].deviceRole}`);
  console.info(`inputDevice deviceType: ${deviceChangeInfo[0].deviceType}`);
};

audioCapturer.on('inputDeviceChange', inputDeviceChangeCallback);

audioCapturer.off('inputDeviceChange', inputDeviceChangeCallback);
```

## on('audioCapturerChange')<sup>11+</sup>

on(type: 'audioCapturerChange', callback: Callback\<AudioCapturerChangeInfo>): void

监听录音流配置变化事件（当音频录制流状态变化、设备变化时触发）。使用callback异步回调。订阅内部是异步实现，是非精确回调，在录音流配置变化的同时注册回调，收到的返回结果存在变化可能性。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                       | 必填 | 说明                                        |
| :------- | :------------------------- | :--- | :------------------------------------------ |
| type     | string                     | 是   | 事件回调类型，支持的事件为'audioCapturerChange'，当音频录制流状态变化、设备变化时，触发该事件。 |
| callback | Callback\<[AudioCapturerChangeInfo](arkts-apis-audio-i.md#audiocapturerchangeinfo9)> | 是   | 回调函数，录音流配置或状态变化时返回监听的录音流当前配置和状态信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
audioCapturer.on('audioCapturerChange', (capturerChangeInfo: audio.AudioCapturerChangeInfo) => {
  console.info(`audioCapturerChange id: ${capturerChangeInfo[0].id}`);
  console.info(`audioCapturerChange deviceRole: ${capturerChangeInfo[0].deviceRole}`);
  console.info(`audioCapturerChange deviceType: ${capturerChangeInfo[0].deviceType}`);
});
```

## off('audioCapturerChange')<sup>11+</sup>

off(type: 'audioCapturerChange', callback?: Callback\<AudioCapturerChangeInfo>): void

取消监听录音流配置变化事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                       | 必填 | 说明                                        |
| :------- | :------------------------- | :--- | :------------------------------------------ |
| type     | string                     | 是   | 事件回调类型，支持的事件为'audioCapturerChange'，当取消监听录音流配置变化事件时，触发该事件。 |
| callback | Callback\<[AudioCapturerChangeInfo](arkts-apis-audio-i.md#audiocapturerchangeinfo9)> | 否   | 回调函数，返回取消监听的录音流配置或状态变化。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioCapturer.off('audioCapturerChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let audioCapturerChangeCallback = (capturerChangeInfo: audio.AudioCapturerChangeInfo) => {
  console.info(`audioCapturerChange id: ${capturerChangeInfo[0].id}`);
  console.info(`audioCapturerChange deviceRole: ${capturerChangeInfo[0].deviceRole}`);
  console.info(`audioCapturerChange deviceType: ${capturerChangeInfo[0].deviceType}`);
};

audioCapturer.on('audioCapturerChange', audioCapturerChangeCallback);

audioCapturer.off('audioCapturerChange', audioCapturerChangeCallback);
```

## on('markReach')<sup>8+</sup>

on(type: 'markReach', frame: number, callback: Callback&lt;number&gt;): void

监听标记到达事件（当采集的帧数达到frame参数的值时触发，仅调用一次）。使用callback异步回调。

如果将frame设置为100，当采集帧数到达第100帧时，系统将上报信息。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                       |
| :------- | :----------------------  | :--- | :----------------------------------------- |
| type     | string                   | 是   | 事件回调类型，支持的事件为'markReach'，当采集的帧数达到frame参数的值时，触发该事件。 |
| frame    | number                   | 是   | 触发事件的帧数。该值必须大于0。           |
| callback | Callback\<number>         | 是   | 回调函数，返回frame参数的值。 |

**示例：**

```ts
audioCapturer.on('markReach', 1000, (position: number) => {
  if (position == 1000) {
    console.info('ON Triggered successfully');
  }
});
```

## off('markReach')<sup>8+</sup>

off(type: 'markReach', callback?: Callback&lt;number&gt;): void

取消监听标记到达事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型   | 必填 | 说明                                              |
| :----- | :----- | :--- | :------------------------------------------------ |
| type   | string | 是   | 事件回调类型，支持的事件为'markReach'，当取消监听标记到达事件时，触发该事件。 |
| callback<sup>18+</sup> | Callback\<number>         | 否  | 回调函数，返回frame参数的值。 |

**示例：**

```ts
// 取消该事件的所有监听。
audioCapturer.off('markReach');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let markReachCallback = (position: number) => {
  if (position == 1000) {
    console.info('ON Triggered successfully');
  }
};

audioCapturer.on('markReach', 1000, markReachCallback);

audioCapturer.off('markReach', markReachCallback);
```

## on('periodReach')<sup>8+</sup>

on(type: 'periodReach', frame: number, callback: Callback&lt;number&gt;): void

监听标记到达事件（当采集的帧数达到frame参数的值时触发，即按周期上报信息）。使用callback异步回调。

如果将frame设置为10，每渲染10帧数据均会上报信息（例如：第10帧、第20帧、第30帧......）。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                        |
| :------- | :----------------------- | :--- | :------------------------------------------ |
| type     | string                   | 是   | 事件回调类型，支持的事件为'periodReach'，当采集的帧数达到frame参数的值时，触发该事件。 |
| frame    | number                   | 是   | 触发事件的帧数。该值必须大于0。            |
| callback | Callback\<number>         | 是   |回调函数，返回frame参数的值。    |

**示例：**

```ts
audioCapturer.on('periodReach', 1000, (position: number) => {
  if (position == 1000) {
    console.info('ON Triggered successfully');
  }
});
```

## off('periodReach')<sup>8+</sup>

off(type: 'periodReach', callback?: Callback&lt;number&gt;): void

取消监听标记到达事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                |
| :----- | :----- | :--- | :-------------------------------------------------- |
| type   | string | 是   | 事件回调类型，支持的事件为'periodReach'，当取消监听标记到达事件时，触发该事件。 |
| callback<sup>18+</sup> | Callback\<number>         | 否  | 回调函数，返回frame参数的值。 |

**示例：**

```ts
// 取消该事件的所有监听。
audioCapturer.off('periodReach');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let periodReachCallback = (position: number) => {
  if (position == 1000) {
    console.info('ON Triggered successfully');
  }
};

audioCapturer.on('periodReach', 1000, periodReachCallback);

audioCapturer.off('periodReach', periodReachCallback);
```

## on('stateChange')<sup>8+</sup>

on(type: 'stateChange', callback: Callback<AudioState\>): void

监听状态变化事件（当AudioCapturer状态发生变化时触发）。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                       | 必填 | 说明                                        |
| :------- | :------------------------- | :--- | :------------------------------------------ |
| type     | string                     | 是   | 事件回调类型，支持的事件为'stateChange'，当AudioCapturer状态发生变化时，触发该事件。 |
| callback | Callback\<[AudioState](arkts-apis-audio-e.md#audiostate8)> | 是   | 回调函数，返回当前音频的状态。 |

**示例：**

```ts
audioCapturer.on('stateChange', (state: audio.AudioState) => {
  if (state == 1) {
    console.info('audio capturer state is: STATE_PREPARED');
  }
  if (state == 2) {
    console.info('audio capturer state is: STATE_RUNNING');
  }
});
```

## off('stateChange')<sup>18+</sup>

off(type: 'stateChange', callback?: Callback&lt;AudioState&gt;): void

取消监听到达标记事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                |
| :----- | :----- | :--- | :-------------------------------------------------- |
| type   | string | 是   | 事件回调类型，支持的事件为'stateChange'，当取消监听到达标记事件时，触发该事件。 |
| callback | Callback\<[AudioState](arkts-apis-audio-e.md#audiostate8)> | 否 | 回调函数，返回当前音频的状态。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioCapturer.off('stateChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let stateChangeCallback = (state: audio.AudioState) => {
  if (state == 1) {
    console.info('audio renderer state is: STATE_PREPARED');
  }
  if (state == 2) {
    console.info('audio renderer state is: STATE_RUNNING');
  }
};

audioCapturer.on('stateChange', stateChangeCallback);

audioCapturer.off('stateChange', stateChangeCallback);
```

## on('readData')<sup>11+</sup>

on(type: 'readData', callback: Callback\<ArrayBuffer>): void

监听音频数据读取回调事件（当需要读取音频流数据时触发）。使用callback异步回调。

回调函数仅用来读取音频数据，请勿在回调函数中调用AudioCapturer相关接口。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                     | 必填 | 说明                        |
| :------- |:-----------------------| :--- |:--------------------------|
| type     | string                 | 是   | 事件回调类型，支持的事件为'readData'，当需要读取音频流数据时，触发该事件。 |
| callback | Callback\<ArrayBuffer> | 是   | 回调函数，返回读到的数据缓冲区。            |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

class Options {
  offset?: number;
  length?: number;
}

let bufferSize: number = 0;
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.cacheDir;
// 确保该沙箱路径下存在该资源。
let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
let file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
let readDataCallback = (buffer: ArrayBuffer) => {
  let options: Options = {
    offset: bufferSize,
    length: buffer.byteLength
  };
  fs.writeSync(file.fd, buffer, options);
  bufferSize += buffer.byteLength;
}

audioCapturer.on('readData', readDataCallback);

audioCapturer.start((err: BusinessError) => {
  if (err) {
    console.error('Capturer start failed.');
  } else {
    console.info('Capturer start success.');
  }
});
```

## off('readData')<sup>11+</sup>

off(type: 'readData', callback?: Callback\<ArrayBuffer>): void

取消监听音频数据读取回调事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                         |
| :------- |:-----------------------| :--- |:-------------------------------------------|
| type     | string                 | 是   | 事件回调类型，支持的事件为'readData'，当取消监听音频数据读取回调事件时，触发该事件。 |
| callback | Callback\<ArrayBuffer> | 否   | 回调函数，返回读到的数据缓冲区。                            |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioCapturer.off('readData');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let readDataCallback = (data: ArrayBuffer) => {
    console.info(`read data: ${data}`);
};

audioCapturer.on('readData', readDataCallback);

audioCapturer.off('readData', readDataCallback);
```

## getOverflowCount<sup>12+</sup>

getOverflowCount(): Promise&lt;number&gt;

获取当前录制音频流的过载音频帧数量。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型                | 说明                          |
| ------------------- | ----------------------------- |
| Promise&lt;number&gt;| Promise对象，返回音频流的过载音频帧数量。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getOverflowCount().then((value: number) => {
  console.info(`Get overflow count Success! ${value}`);
}).catch((err: BusinessError) => {
  console.error(`Get overflow count Fail: ${err}`);
});
```

## getOverflowCountSync<sup>12+</sup>

getOverflowCountSync(): number

获取当前录制音频流的过载音频帧数量。同步返回数据。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型                | 说明                          |
| ------------------- | ----------------------------- |
| number| 返回音频流的过载音频帧数量。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let value: number = audioCapturer.getOverflowCountSync();
  console.info(`Get overflow count Success! ${value}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Get overflow count Fail: ${error}`);
}
```

## setWillMuteWhenInterrupted<sup>20+</sup>

setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise&lt;void&gt;

设置当前录制音频流是否启用[静音打断模式](../../media/audio/using-audiocapturer-for-recording.md#设置静音打断模式)。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名     | 类型             | 必填   | 说明                                                      |
| ---------- |---------------- | ------ |---------------------------------------------------------|
| muteWhenInterrupted | boolean  | 是  | 设置当前录制音频流是否启用静音打断模式, true表示启用，false表示不启用，保持为默认打断模式。 |

**返回值：**

| 类型                | 说明                          |
| ------------------- | ----------------------------- |
| Promise&lt;void&gt;| Promise对象。无返回结果的Promise对象。|

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800103 | Operation not permit at current state. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.setWillMuteWhenInterrupted(true).then(() => {
  console.info('setWillMuteWhenInterrupted Success!');
}).catch((err: BusinessError) => {
  console.error(`setWillMuteWhenInterrupted Fail: ${err}`);
});
```

## read<sup>(deprecated)</sup>

read(size: number, isBlockingRead: boolean, callback: AsyncCallback<ArrayBuffer\>): void

读入缓冲区。使用callback异步回调。

> **说明：**
> 从API version 8开始支持，从API version 11开始废弃，建议使用[on('readData')](#onreaddata11)替代。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名         | 类型                        | 必填 | 说明                             |
| :------------- | :-------------------------- | :--- | :------------------------------- |
| size           | number                      | 是   | 读入的字节数。                   |
| isBlockingRead | boolean                     | 是   | 是否阻塞读操作。true表示阻塞，false表示不阻塞。                 |
| callback       | AsyncCallback<ArrayBuffer\> | 是   | 回调函数。当读入缓冲区成功，err为undefined，data为获取到的缓冲区；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getBufferSize().then((bufferSize: number) => {
  console.info('Succeeded in doing getBufferSize.');
  audioCapturer.read(bufferSize, true, (err: BusinessError, buffer: ArrayBuffer) => {
    if (err) {
      console.error(`Failed to read. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in doing read.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to getBufferSize. Code: ${err.code}, message: ${err.message}`);
});
```

## read<sup>(deprecated)</sup>

read(size: number, isBlockingRead: boolean): Promise<ArrayBuffer\>

读入缓冲区。使用Promise异步回调。

> **说明：**
> 从API version 8开始支持，从API version 11开始废弃，建议使用[on('readData')](#onreaddata11)替代。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名         | 类型    | 必填 | 说明             |
| :------------- | :------ | :--- | :--------------- |
| size           | number  | 是   | 读入的字节数。   |
| isBlockingRead | boolean | 是   | 是否阻塞读操作。true表示阻塞，false表示不阻塞。 |

**返回值：**

| 类型                  | 说明                                                   |
| :-------------------- | :----------------------------------------------------- |
| Promise<ArrayBuffer\> | Promise对象，返回读取的缓冲区数据。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getBufferSize().then((bufferSize: number) => {
  console.info('Succeeded in doing getBufferSize.');
  audioCapturer.read(bufferSize, true).then((buffer: ArrayBuffer) => {
    console.info('Succeeded in doing read.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to read. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to getBufferSize. Code: ${err.code}, message: ${err.message}`);
});
```
