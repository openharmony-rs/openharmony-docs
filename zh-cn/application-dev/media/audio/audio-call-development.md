# 开发音频通话功能
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyy0412-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

在音频通话场景下，音频输出（播放对端声音）和音频输入（录制本端声音）会同时进行，应用可以通过使用AudioRenderer来实现音频输出，通过使用AudioCapturer来实现音频输入，同时使用AudioRenderer和AudioCapturer即可实现音频通话功能。

在音频通话开始和结束时，应用可以自行检查当前的[音频场景模式](audio-call-overview.md#音频场景模式)和[铃声模式](audio-call-overview.md#铃声模式)，以便采取合适的音频管理及提示策略。

以下代码示范了同时使用AudioRenderer和AudioCapturer实现音频通话功能的基本过程，其中未包含音频通话数据的传输过程，实际开发中，需要将网络传输来的对端通话数据解码播放，此处仅以读取音频文件的数据代替；同时需要将本端录制的通话数据编码打包，通过网络发送给对端，此处仅以将数据写入音频文件代替。

示例为片段代码，可通过点击示例代码右下方的链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/VoipCallSampleJS?_fb=blob)。

## 使用AudioRenderer播放对端的通话声音

该过程与[使用AudioRenderer开发音频播放功能(ArkTs)](using-audiorenderer-for-playback.md)过程相似，关键区别在于audioRendererInfo参数和音频数据来源。audioRendererInfo参数中，音频流使用类型usage需设置为VoIP通话：STREAM_USAGE_VOICE_COMMUNICATION。

ArkTS-Dyn示例：

<!-- @[all_VoIPDemoForAudioRenderer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/VoipCallSampleJS/entry/src/main/ets/pages/VoIpDemoForAudioRenderer.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit'; // 导入audio模块。
import { BusinessError } from '@kit.BasicServicesKit'; // 导入BusinessError。
import { fileIo as fs } from '@kit.CoreFileKit'; // 导入文件操作模块。
import { common } from '@kit.AbilityKit'; // 导入UIAbilityContext。

// 与使用AudioRenderer开发音频播放功能过程相似,关键区别在于audioRendererInfo参数和音频数据来源。
const TAG = 'VoIPDemoForAudioRenderer';

class Options {
  public offset?: number;
  public length?: number;
}

let bufferSize: number = 0;
let audioRenderer: audio.AudioRenderer | undefined = undefined;
let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // 采样率。
  channels: audio.AudioChannel.CHANNEL_2, // 通道。
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // 采样格式。
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // 编码格式。
};
let audioRendererInfo: audio.AudioRendererInfo = {
  // 需使用通话场景相应的参数。
  usage: audio.StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION, // 音频流使用类型:VoIP通话。
  rendererFlags: 0 // 音频渲染器标志:默认为0即可。
};
let audioRendererOptions: audio.AudioRendererOptions = {
  streamInfo: audioStreamInfo,
  rendererInfo: audioRendererInfo
};
let file: fs.File;
let writeDataCallback: audio.AudioRendererWriteDataCallback;
// ...
async function initArguments(context: common.UIAbilityContext) {
  let path = context.cacheDir;
  // 此处仅作示例,实际使用时需要将文件替换为应用要播放的PCM文件。
  let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
  file = fs.openSync(filePath, fs.OpenMode.READ_ONLY);
  writeDataCallback = (buffer: ArrayBuffer) => {
    let options: Options = {
      offset: bufferSize,
      length: buffer.byteLength
    };

    try {
      let bufferLength = fs.readSync(file.fd, buffer, options);
      bufferSize += buffer.byteLength;
      // 如果当前回调传入的数据不足一帧，空白区域需要使用静音数据填充，否则会导致播放出现杂音。
      if (bufferLength < buffer.byteLength) {
        let view = new DataView(buffer);
        for (let i = bufferLength; i < buffer.byteLength; i++) {
          // 空白区域填充静音数据。当使用音频采样格式为SAMPLE_FORMAT_U8时0x7F为静音数据，使用其他采样格式时0为静音数据。
          view.setUint8(i, 0);
        }
      }
      // API version 12之前不支持返回回调结果，API version 12及以后支持返回回调结果。
      // 如果开发者不希望播放某段buffer，返回audio.AudioDataCallbackResult.INVALID即可。
      return audio.AudioDataCallbackResult.VALID;
    } catch (error) {
      console.error('Error reading file:', error);

      if (globalLogUpdate) {
        globalLogUpdate(`Error reading file: ${error}`, true);
      }
      // API version 12之前不支持返回回调结果，API version 12及以后支持返回回调结果。
      return audio.AudioDataCallbackResult.INVALID;
    }
  };
}

// 初始化,创建实例,设置监听事件。
async function init() {
  audio.createAudioRenderer(audioRendererOptions, (err, renderer) => { // 创建AudioRenderer实例。
    if (!err) {
      console.info(`${TAG}: creating AudioRenderer success`);
      // ...
      audioRenderer = renderer;
      if (audioRenderer !== undefined) {
        audioRenderer.on('writeData', writeDataCallback);
      }
    } else {
      console.info(`${TAG}: creating AudioRenderer failed, error: ${err.message}`);
      // ...
    }
  });
}

// 开始一次音频渲染。
async function start() {
  if (audioRenderer !== undefined) {
    let stateGroup = [audio.AudioState.STATE_PREPARED, audio.AudioState.STATE_PAUSED, audio.AudioState.STATE_STOPPED];
    if (stateGroup.indexOf(audioRenderer.state.valueOf()) === -1) { // 当且仅当状态为prepared、paused和stopped之一时才能启动渲染。
      console.error(TAG + 'start failed');
      // ...
      return;
    }
    // 启动渲染。
    audioRenderer.start((err: BusinessError) => {
      if (err) {
        console.error('Renderer start failed.');
        // ...
      } else {
        console.info('Renderer start success.');
        // ...
      }
    });
  }
}

// 暂停渲染。
async function pause() {
  if (audioRenderer !== undefined) {
    // 只有渲染器状态为running的时候才能暂停。
    if (audioRenderer.state.valueOf() !== audio.AudioState.STATE_RUNNING) {
      console.info('Renderer is not running');
      // ...
      return;
    }
    // 暂停渲染。
    audioRenderer.pause((err: BusinessError) => {
      if (err) {
        console.error('Renderer pause failed.');
        // ...
      } else {
        console.info('Renderer pause success.');
        // ...
      }
    });
  }
}

// 停止渲染。
async function stop() {
  if (audioRenderer !== undefined) {
    // 只有渲染器状态为running或paused的时候才可以停止。
    if (audioRenderer.state.valueOf() !== audio.AudioState.STATE_RUNNING &&
      audioRenderer.state.valueOf() !== audio.AudioState.STATE_PAUSED) {
      console.info('Renderer is not running or paused.');
      // ...
      return;
    }
    // 停止渲染。
    audioRenderer.stop((err: BusinessError) => {
      if (err) {
        console.error('Renderer stop failed.');
        // ...
      } else {
        fs.close(file);
        console.info('Renderer stop success.');
        // ...
      }
    });
  }
}

// 销毁实例,释放资源。
async function release() {
  if (audioRenderer !== undefined) {
    // 渲染器状态不是released状态,才能release。
    if (audioRenderer.state.valueOf() === audio.AudioState.STATE_RELEASED) {
      console.info('Renderer already released');
      // ...
      return;
    }
    // 释放资源。
    audioRenderer.release((err: BusinessError) => {
      if (err) {
        console.error('Renderer release failed.');
        // ...
      } else {
        console.info('Renderer release success.');
        // ...
      }
    });
  }
}
```

ArkTS-Sta示例：

<!-- @[all_VoIPDemoForAudioRenderer](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Audio/VoipCallSampleJS-Sta/entry/src/main/ets/pages/VoIpDemoForAudioRenderer.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit'; // 导入audio模块。
import { fileIo as fs, ReadOptions } from '@kit.CoreFileKit'; // 导入文件操作模块。
import { common } from '@kit.AbilityKit'; // 导入UIAbilityContext。
import {
  Color,
  ClickEvent,
  Column,
  Component,
  Entry,
  FlexAlign,
  HorizontalAlign,
  Row,
  Scroll,
  Text
} from '@kit.ArkUI';
import { State } from '@kit.ArkUI';

// 与使用AudioRenderer开发音频播放功能过程相似，关键区别在于audioRendererInfo参数和音频数据来源。
const TAG = 'VoIPDemoForAudioRenderer';
const SAMPLE_RATE_48000: int = 48000;

let bufferSize: long = 0;
let audioRenderer: audio.AudioRenderer | undefined = undefined;
let file: fs.File | undefined = undefined;
let writeDataCallback: audio.AudioRendererWriteDataCallback = (_buffer: ArrayBuffer): audio.AudioDataCallbackResult => {
  return audio.AudioDataCallbackResult.INVALID;
};

class RendererAudioStreamInfo implements audio.AudioStreamInfo {
  samplingRate: audio.AudioSamplingRate | int = SAMPLE_RATE_48000;
  channels: audio.AudioChannel = audio.AudioChannel.CHANNEL_2;
  sampleFormat: audio.AudioSampleFormat = audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE;
  encodingType: audio.AudioEncodingType = audio.AudioEncodingType.ENCODING_TYPE_RAW;
}

class VoipAudioRendererInfo implements audio.AudioRendererInfo {
  // 需使用通话场景相应的参数。
  usage: audio.StreamUsage = audio.StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION;
  rendererFlags: int = 0;
}

class VoipAudioRendererOptions implements audio.AudioRendererOptions {
  streamInfo: audio.AudioStreamInfo = new RendererAudioStreamInfo();
  rendererInfo: audio.AudioRendererInfo = new VoipAudioRendererInfo();
}

function createAudioRendererOptions(): audio.AudioRendererOptions {
  return new VoipAudioRendererOptions();
}
// ...
async function initArguments(context: common.UIAbilityContext) {
  let path = context.cacheDir;
  // 此处仅作示例，实际使用时需要将文件替换为应用要播放的PCM文件。
  let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
  file = fs.openSync(filePath, fs.OpenMode.READ_ONLY);
  bufferSize = 0;
  writeDataCallback = (buffer: ArrayBuffer) => {
    const openedFile = file;
    if (openedFile === undefined) {
      return audio.AudioDataCallbackResult.INVALID;
    }
    let options: ReadOptions = {
      offset: bufferSize,
      length: buffer.byteLength.toLong()
    };

    try {
      let bufferLength = fs.readSync(openedFile.fd, buffer, options);
      bufferSize += buffer.byteLength.toLong();
      // 如果当前回调传入的数据不足一帧，空白区域需要使用静音数据填充，否则会导致播放出现杂音。
      if (bufferLength < buffer.byteLength.toLong()) {
        let view = new DataView(buffer);
        let startIndex = bufferLength.toInt();
        let endIndex = buffer.byteLength.toInt();
        for (let i: int = startIndex; i < endIndex; i++) {
          // 空白区域填充静音数据。当使用音频采样格式为SAMPLE_FORMAT_U8时，0x7F为静音数据；使用其他采样格式时，0为静音数据。
          view.setUint8(i, 0);
        }
      }
      // API version 12之前不支持返回回调结果，API version 12及以后支持返回回调结果。
      // 如果开发者不希望播放某段buffer，返回audio.AudioDataCallbackResult.INVALID即可。
      return audio.AudioDataCallbackResult.VALID;
    } catch (error) {
      console.error('Error reading file:', error);

      if (globalLogUpdate) {
        globalLogUpdate(`Error reading file: ${error}`, true);
      }
      // API version 12之前不支持返回回调结果，API version 12及以后支持返回回调结果。
      return audio.AudioDataCallbackResult.INVALID;
    }
  };
}

// 初始化，创建实例，设置监听事件。
async function init() {
  try {
    let renderer = await audio.createAudioRenderer(createAudioRendererOptions()); // 创建AudioRenderer实例。
    if (renderer === null) {
      const errorMsg = `${TAG}: creating AudioRenderer failed, renderer is null`;
      console.info(errorMsg);
      if (globalLogUpdate) {
        globalLogUpdate(errorMsg, true);
      }
      return;
    }
    console.info(`${TAG}: creating AudioRenderer success`);
    // ...
    audioRenderer = renderer;
    renderer.onWriteData(writeDataCallback);
  } catch (error) {
    console.info(`${TAG}: creating AudioRenderer failed, error: ${error}`);
    // ...
  }
}

// 开始一次音频渲染。
async function start() {
  const renderer = audioRenderer;
  if (renderer === undefined) {
    return;
  }
  const state = renderer.state;
  if (state !== audio.AudioState.STATE_PREPARED &&
    state !== audio.AudioState.STATE_PAUSED &&
    state !== audio.AudioState.STATE_STOPPED) { // 当且仅当状态为prepared、paused和stopped之一时才能启动渲染。
    console.error(TAG + 'start failed');
    // ...
    return;
  }
  try {
    // 启动渲染。
    await renderer.start();
    console.info('Renderer start success.');
    // ...
  } catch (error) {
    console.error(`Renderer start failed: ${error}`);
    // ...
  }
}

// 暂停渲染。
async function pause() {
  const renderer = audioRenderer;
  if (renderer === undefined) {
    return;
  }
  // 只有渲染器状态为running的时候才能暂停。
  if (renderer.state !== audio.AudioState.STATE_RUNNING) {
    console.info('Renderer is not running');
    // ...
    return;
  }
  try {
    // 暂停渲染。
    await renderer.pause();
    console.info('Renderer pause success.');
    // ...
  } catch (error) {
    console.error(`Renderer pause failed: ${error}`);
    // ...
  }
}

// 停止渲染。
async function stop() {
  const renderer = audioRenderer;
  if (renderer === undefined) {
    return;
  }
  const state = renderer.state;
  // 只有渲染器状态为running或paused的时候才可以停止。
  if (state !== audio.AudioState.STATE_RUNNING &&
    state !== audio.AudioState.STATE_PAUSED) {
    console.info('Renderer is not running or paused.');
    // ...
    return;
  }
  try {
    // 停止渲染。
    await renderer.stop();
    const openedFile = file;
    if (openedFile !== undefined) {
      fs.closeSync(openedFile);
      file = undefined;
    }
    console.info('Renderer stop success.');
    // ...
  } catch (error) {
    console.error(`Renderer stop failed: ${error}`);
    // ...
  }
}

// 销毁实例，释放资源。
async function release() {
  const renderer = audioRenderer;
  if (renderer === undefined) {
    return;
  }
  // 渲染器状态不是released状态，才能release。
  if (renderer.state === audio.AudioState.STATE_RELEASED) {
    console.info('Renderer already released');
    // ...
    return;
  }
  try {
    // 释放资源。
    await renderer.release();
    audioRenderer = undefined;
    console.info('Renderer release success.');
    // ...
  } catch (error) {
    console.error(`Renderer release failed: ${error}`);
    // ...
  }
}
```

## 使用AudioCapturer录制本端的通话声音

该过程与[使用AudioCapturer开发音频录制功能(ArkTs)](using-audiocapturer-for-recording.md)过程相似，关键区别在于audioCapturerInfo参数和音频数据流向。audioCapturerInfo参数中音源类型source需设置为语音通话：SOURCE_TYPE_VOICE_COMMUNICATION。

所有录制均需要申请麦克风权限：ohos.permission.MICROPHONE，申请方式请参考[向用户申请授权](../../security/AccessToken/request-user-authorization.md)。

ArkTS-Dyn示例：

<!-- @[all_VoIPDemoForAudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/VoipCallSampleJS/entry/src/main/ets/pages/VoIpDemoForAudioCapturer.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit'; // 导入audio模块。
import { BusinessError } from '@kit.BasicServicesKit'; // 导入BusinessError。
import { fileIo as fs } from '@kit.CoreFileKit'; // 导入文件操作模块。
import { common, abilityAccessCtrl, PermissionRequestResult } from '@kit.AbilityKit'; // 导入UIAbilityContext。
// 与使用AudioCapturer开发音频录制功能过程相似,关键区别在于audioCapturerInfo参数和音频数据流向。
const TAG = 'VoIPDemoForAudioCapturer';

class Options {
  public offset?: number;
  public length?: number;
}

let bufferSize: number = 0;
let audioCapturer: audio.AudioCapturer | undefined = undefined;
let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // 采样率。
  channels: audio.AudioChannel.CHANNEL_2, // 通道。
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // 采样格式。
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // 编码格式。
};
let audioCapturerInfo: audio.AudioCapturerInfo = {
  // 需使用通话场景相应的参数。
  source: audio.SourceType.SOURCE_TYPE_VOICE_COMMUNICATION, // 音源类型:语音通话。
  capturerFlags: 0 // 音频采集器标志:默认为0即可。
};
let audioCapturerOptions: audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo
};
let file: fs.File;
let readDataCallback: Callback<ArrayBuffer>;

// ...

async function initArguments(context: common.UIAbilityContext) {
  let path = context.cacheDir;
  let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
  file = fs.openSync(filePath, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  console.info(`File opened: ${filePath}`);

  readDataCallback = (buffer: ArrayBuffer) => {
    let options: Options = {
      offset: bufferSize,
      length: buffer.byteLength
    }
    fs.writeSync(file.fd, buffer, options);
    bufferSize += buffer.byteLength;
  }
}

// 初始化,创建实例,设置监听事件。
async function init() {
  audio.createAudioCapturer(audioCapturerOptions, (err, capturer) => { // 创建AudioCapturer实例。
    if (err) {
      console.error(`Invoke createAudioCapturer failed, code is ${err.code}, message is ${err.message}`);
      // ...
      return;
    }
    console.info(`${TAG}: create AudioCapturer success`);
    // ...
    audioCapturer = capturer;
    if (audioCapturer !== undefined) {
      audioCapturer.on('readData', readDataCallback);
    }
  });
}

// 开始一次音频采集。
async function start() {
  if (audioCapturer !== undefined) {
    let stateGroup = [audio.AudioState.STATE_PREPARED, audio.AudioState.STATE_PAUSED, audio.AudioState.STATE_STOPPED];
    if (stateGroup.indexOf(audioCapturer.state.valueOf()) === -1) {
      // 当且仅当状态为STATE_PREPARED、STATE_PAUSED和STATE_STOPPED之一时才能启动采集。
      console.error(`${TAG}: start failed`);
      // ...
      return;
    }

    // 启动采集。
    audioCapturer.start((err: BusinessError) => {
      if (err) {
        console.error('Capturer start failed.');
        // ...
      } else {
        console.info('Capturer start success.');
        // ...
      }
    });
  }
}

// 停止采集。
async function stop() {
  if (audioCapturer !== undefined) {
    // 只有采集器状态为STATE_RUNNING或STATE_PAUSED的时候才可以停止。
    if (audioCapturer.state.valueOf() !== audio.AudioState.STATE_RUNNING &&
      audioCapturer.state.valueOf() !== audio.AudioState.STATE_PAUSED) {
      console.info('Capturer is not running or paused');
      // ...
      return;
    }

    // 停止采集。
    audioCapturer.stop((err: BusinessError) => {
      if (err) {
        console.error('Capturer stop failed.');
        // ...
      } else {
        fs.close(file);
        console.info('Capturer stop success.');
        // ...
      }
    });
  }
}

// 销毁实例,释放资源。
async function release() {
  if (audioCapturer !== undefined) {
    // 采集器状态不是STATE_RELEASED或STATE_NEW状态,才能release。
    if (audioCapturer.state.valueOf() === audio.AudioState.STATE_RELEASED ||
      audioCapturer.state.valueOf() === audio.AudioState.STATE_NEW) {
      console.info('Capturer already released');
      // ...
      return;
    }

    // 释放资源。
    audioCapturer.release((err: BusinessError) => {
      if (err) {
        console.error('Capturer release failed.');
        // ...
      } else {
        console.info('Capturer release success.');
        // ...
      }
    });
  }
}
```

ArkTS-Sta示例：

<!-- @[all_VoIPDemoForAudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Audio/VoipCallSampleJS-Sta/entry/src/main/ets/pages/VoIpDemoForAudioCapturer.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit'; // 导入audio模块。
import { Callback } from '@kit.BasicServicesKit';
import { fileIo as fs, WriteOptions } from '@kit.CoreFileKit'; // 导入文件操作模块。
import { common, abilityAccessCtrl, PermissionRequestResult } from '@kit.AbilityKit'; // 导入UIAbilityContext。
import {
  Color,
  ClickEvent,
  Column,
  Component,
  Entry,
  FlexAlign,
  HorizontalAlign,
  Row,
  Scroll,
  Text
} from '@kit.ArkUI';
import { State } from '@kit.ArkUI';
// 与使用AudioCapturer开发音频录制功能过程相似，关键区别在于audioCapturerInfo参数和音频数据流向。
const TAG = 'VoIPDemoForAudioCapturer';
const SAMPLE_RATE_48000: int = 48000;

let bufferSize: long = 0;
let audioCapturer: audio.AudioCapturer | undefined = undefined;
let file: fs.File | undefined = undefined;
let readDataCallback: Callback<ArrayBuffer> = (_buffer: ArrayBuffer): void => {};

class CapturerAudioStreamInfo implements audio.AudioStreamInfo {
  samplingRate: audio.AudioSamplingRate | int = SAMPLE_RATE_48000;
  channels: audio.AudioChannel = audio.AudioChannel.CHANNEL_2;
  sampleFormat: audio.AudioSampleFormat = audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE;
  encodingType: audio.AudioEncodingType = audio.AudioEncodingType.ENCODING_TYPE_RAW;
}

class VoipAudioCapturerInfo implements audio.AudioCapturerInfo {
  // 需使用通话场景相应的参数。
  source: audio.SourceType = audio.SourceType.SOURCE_TYPE_VOICE_COMMUNICATION;
  capturerFlags: int = 0;
}

class VoipAudioCapturerOptions implements audio.AudioCapturerOptions {
  streamInfo: audio.AudioStreamInfo = new CapturerAudioStreamInfo();
  capturerInfo: audio.AudioCapturerInfo = new VoipAudioCapturerInfo();
}

function createAudioCapturerOptions(): audio.AudioCapturerOptions {
  return new VoipAudioCapturerOptions();
}

// ...

async function initArguments(context: common.UIAbilityContext) {
  let path = context.cacheDir;
  let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
  file = fs.openSync(filePath, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  bufferSize = 0;
  console.info(`File opened: ${filePath}`);

  readDataCallback = (buffer: ArrayBuffer) => {
    const openedFile = file;
    if (openedFile === undefined) {
      return;
    }
    let options: WriteOptions = {
      offset: bufferSize,
      length: buffer.byteLength.toLong()
    }
    fs.writeSync(openedFile.fd, buffer, options);
    bufferSize += buffer.byteLength.toLong();
  }
}

// 初始化，创建实例，设置监听事件。
async function init() {
  try {
    let capturer = await audio.createAudioCapturer(createAudioCapturerOptions()); // 创建AudioCapturer实例。
    if (capturer === null) {
      const errorMsg = 'Invoke createAudioCapturer failed, capturer is null';
      console.error(errorMsg);
      if (globalLogUpdate) {
        globalLogUpdate(errorMsg, true);
      }
      return;
    }
    console.info(`${TAG}: create AudioCapturer success`);
    // ...
    audioCapturer = capturer;
    capturer.onReadData(readDataCallback);
  } catch (error) {
    console.error(`Invoke createAudioCapturer failed: ${error}`);
    // ...
  }
}

// 开始一次音频采集。
async function start() {
  const capturer = audioCapturer;
  if (capturer === undefined) {
    return;
  }
  const state = capturer.state;
  if (state !== audio.AudioState.STATE_PREPARED &&
    state !== audio.AudioState.STATE_PAUSED &&
    state !== audio.AudioState.STATE_STOPPED) {
    // 当且仅当状态为STATE_PREPARED、STATE_PAUSED和STATE_STOPPED之一时才能启动采集。
    console.error(`${TAG}: start failed`);
    // ...
    return;
  }

  try {
    // 启动采集。
    await capturer.start();
    console.info('Capturer start success.');
    // ...
  } catch (error) {
    console.error(`Capturer start failed: ${error}`);
    // ...
  }
}

// 停止采集。
async function stop() {
  const capturer = audioCapturer;
  if (capturer === undefined) {
    return;
  }
  const state = capturer.state;
  // 只有采集器状态为STATE_RUNNING或STATE_PAUSED时才可以停止。
  if (state !== audio.AudioState.STATE_RUNNING &&
    state !== audio.AudioState.STATE_PAUSED) {
    console.info('Capturer is not running or paused');
    // ...
    return;
  }

  try {
    // 停止采集。
    await capturer.stop();
    const openedFile = file;
    if (openedFile !== undefined) {
      fs.closeSync(openedFile);
      file = undefined;
    }
    console.info('Capturer stop success.');
    // ...
  } catch (error) {
    console.error(`Capturer stop failed: ${error}`);
    // ...
  }
}

// 销毁实例，释放资源。
async function release() {
  const capturer = audioCapturer;
  if (capturer === undefined) {
    return;
  }
  const state = capturer.state;
  // 采集器状态不是STATE_RELEASED或STATE_NEW状态，才能release。
  if (state === audio.AudioState.STATE_RELEASED ||
    state === audio.AudioState.STATE_NEW) {
    console.info('Capturer already released');
    // ...
    return;
  }

  try {
    // 释放资源。
    await capturer.release();
    audioCapturer = undefined;
    console.info('Capturer release success.');
    // ...
  } catch (error) {
    console.error(`Capturer release failed: ${error}`);
    // ...
  }
}
```
