# 使用AudioCapturer采集内录音频(ArkTS)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyy0412-->
<!--Designer: @weixin_41398971-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

内录是指以系统内部播放音频作为采集源，常用于会议共享、直播、音频录制等需要采集设备内部声音的场景。从API version 26.0.0开始，AudioCapturer提供内录启动接口，应用可通过AudioCapturer采集内部播放音频的PCM数据。

> **说明：**
>
> - 本文介绍Audio Kit侧采集内录音频数据的开发方式，适用于仅需要音频PCM数据，或需要将音频数据交给自定义处理链路的场景。
> - 如果需要同时采集屏幕画面、内录音频和麦克风音频，并直接完成录屏写文件或录屏取码流，建议使用Media Kit的[AVScreenCapture录屏基础流程](../media/avscreencapture-c-basic-process.md)。
> - [SourceType.SOURCE_TYPE_PLAYBACK_CAPTURE](../../reference/apis-audio-kit/arkts-apis-audio-e.md#sourcetype8)已废弃，不建议再通过该音源类型创建内录流。

## 开发流程

使用AudioCapturer采集内录音频的基本流程如下：

1. 创建AudioCapturer实例，配置音频流参数和内录模式。
2. 订阅`readData`回调，接收采集到的PCM数据。
3. 调用`requestPlaybackCaptureStart()`请求启动内录。
4. 根据启动结果处理采集业务。
5. 停止采集并释放AudioCapturer资源。

## 开发步骤

### 导入模块

```ts
import { audio } from '@kit.AudioKit';
import { fileIo as fs } from '@kit.CoreFileKit';
```

### 创建AudioCapturer实例

创建AudioCapturer时，通过[AudioCapturerOptions](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiocaptureroptions8)中的`playbackCaptureMode`配置内录模式。该字段支持[AudioPlaybackCaptureMode](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audioplaybackcapturemode)枚举值或按位或组合。

`capturerInfo.source`可按普通音频采集器配置为`SOURCE_TYPE_MIC`。是否启动内录由`playbackCaptureMode`和后续`requestPlaybackCaptureStart()`决定，不需要将`source`配置为已废弃的`SOURCE_TYPE_PLAYBACK_CAPTURE`。

```ts
let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_2,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC,
  capturerFlags: 0
};

let audioCapturerOptions: audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo,
  playbackCaptureMode: audio.AudioPlaybackCaptureMode.MODE_MEDIA |
    audio.AudioPlaybackCaptureMode.MODE_EXCLUDING_SELF
};

let audioCapturer: audio.AudioCapturer = await audio.createAudioCapturer(audioCapturerOptions);
```

内录模式说明如下：

| 内录模式 | 说明 |
| -------- | ---- |
| `MODE_DEFAULT` | 默认模式，录制大部分音频流，不包括提示音流和隐私流。 |
| `MODE_MEDIA` | 媒体模式，录制媒体、语音消息和未知流等。 |
| `MODE_EXCLUDING_SELF` | 排除自身模式，录制除应用自身播放音频以外的流。 |
| `MODE_MEDIA \| MODE_EXCLUDING_SELF` | 录制媒体类音频，同时排除应用自身播放音频。 |

### 读取内录PCM数据

调用[on('readData')](../../reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md#onreaddata11)订阅音频数据回调。回调返回的数据为PCM数据，应用可根据业务写入文件、送入编码器或交给自定义音频处理模块。

```ts
let filePath: string = getContext().cacheDir + '/playback_capture.pcm';
let file = fs.openSync(filePath, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE | fs.OpenMode.TRUNC);
let writeOffset: number = 0;

let readDataCallback = (buffer: ArrayBuffer) => {
  fs.writeSync(file.fd, buffer, {
    offset: writeOffset,
    length: buffer.byteLength
  });
  writeOffset += buffer.byteLength;
};

audioCapturer.on('readData', readDataCallback);
```

> **注意：**
>
> `readData`回调中不建议执行耗时任务。若需要编码、网络发送或复杂算法处理，建议将PCM数据转交给独立任务处理，避免数据回调阻塞导致丢帧、卡顿或杂音。

### 请求启动内录

内录流需要通过[requestPlaybackCaptureStart()](../../reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md#requestplaybackcapturestart)启动。该接口为非阻塞接口，系统会继续处理用户授权检查和内录流启动，最终结果通过[PlaybackCaptureStartState](../../reference/apis-audio-kit/arkts-apis-audio-e.md#playbackcapturestartstate)返回。

```ts
audioCapturer.requestPlaybackCaptureStart((state: audio.PlaybackCaptureStartState) => {
  if (state === audio.PlaybackCaptureStartState.STATE_SUCCESS) {
    console.info('Succeeded in starting playback capture.');
    return;
  }

  if (state === audio.PlaybackCaptureStartState.STATE_NOT_AUTHORIZED) {
    console.error('Failed to start playback capture because user authorization is not granted.');
    return;
  }

  console.error(`Failed to start playback capture. State: ${state}.`);
});
```

启动结果说明如下：

| 启动结果 | 说明 |
| -------- | ---- |
| `STATE_SUCCESS` | 内录启动成功，应用可通过`readData`回调接收PCM数据。 |
| `STATE_FAILED` | 内录启动失败，可能是焦点请求被拒绝或系统内部处理失败。 |
| `STATE_NOT_AUTHORIZED` | 用户未授权，内录启动失败。 |

### 停止采集并释放资源

应用结束内录后，需要停止AudioCapturer并释放资源。释放前应取消`readData`监听，避免对象释放后仍处理回调。

```ts
async function stopPlaybackCapture(): Promise<void> {
  audioCapturer.off('readData', readDataCallback);

  if (audioCapturer.state === audio.AudioState.STATE_RUNNING) {
    await audioCapturer.stop();
  }

  await audioCapturer.release();
  fs.closeSync(file);
}
```

## 完整示例

```ts
import { audio } from '@kit.AudioKit';
import { fileIo as fs } from '@kit.CoreFileKit';

let audioCapturer: audio.AudioCapturer;
let file: fs.File;
let writeOffset: number = 0;

let readDataCallback = (buffer: ArrayBuffer) => {
  fs.writeSync(file.fd, buffer, {
    offset: writeOffset,
    length: buffer.byteLength
  });
  writeOffset += buffer.byteLength;
};

async function startPlaybackCapture(): Promise<void> {
  let audioStreamInfo: audio.AudioStreamInfo = {
    samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
    channels: audio.AudioChannel.CHANNEL_2,
    sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
    encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW
  };

  let audioCapturerInfo: audio.AudioCapturerInfo = {
    source: audio.SourceType.SOURCE_TYPE_MIC,
    capturerFlags: 0
  };

  let audioCapturerOptions: audio.AudioCapturerOptions = {
    streamInfo: audioStreamInfo,
    capturerInfo: audioCapturerInfo,
    playbackCaptureMode: audio.AudioPlaybackCaptureMode.MODE_MEDIA |
      audio.AudioPlaybackCaptureMode.MODE_EXCLUDING_SELF
  };

  audioCapturer = await audio.createAudioCapturer(audioCapturerOptions);
  file = fs.openSync(getContext().cacheDir + '/playback_capture.pcm',
    fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE | fs.OpenMode.TRUNC);
  audioCapturer.on('readData', readDataCallback);

  audioCapturer.requestPlaybackCaptureStart((state: audio.PlaybackCaptureStartState) => {
    if (state === audio.PlaybackCaptureStartState.STATE_SUCCESS) {
      console.info('Succeeded in starting playback capture.');
    } else {
      console.error(`Failed to start playback capture. State: ${state}.`);
    }
  });
}

async function stopPlaybackCapture(): Promise<void> {
  audioCapturer.off('readData', readDataCallback);

  if (audioCapturer.state === audio.AudioState.STATE_RUNNING) {
    await audioCapturer.stop();
  }

  await audioCapturer.release();
  fs.closeSync(file);
}
```

## 相关实例

AudioCapturer基础录制流程可参考[AudioCapturer示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS)。如果需要同时采集屏幕画面和音频，可参考[ScreenCapture示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample)。
