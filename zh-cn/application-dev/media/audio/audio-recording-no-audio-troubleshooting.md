# 录音无声定位指导
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyy0412-->
<!--Designer: @weixin_41398971-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

开发者在实现音频录制功能时，可能会遇到录音启动失败、没有录音数据回调、录音文件无声等问题。本文面向应用开发者，介绍录音无声场景的常见现象、相关背景知识以及定位方法，并给出日志维测示例。

## 问题现象

应用录音时，常见的无声问题表现如下：

- 录音实例创建失败或启动失败。
- 录音实例创建和启动成功，但没有收到录音数据回调。
- 可以收到录音数据回调，但数据长度始终为0，或录音文件播放时全为静音。
- 前台录音正常，在通话、蓝牙切换、耳机插拔或其他特定场景下变为无声。

如果问题仅在应用切到后台后出现，或问题与锁屏、熄屏、长时任务、页面生命周期释放等后台录音场景相关，请优先参考[后台录音指导](audio-recording-background-guidelines.md)。

## 背景知识

- 录音必须在前台启动，启动成功后才可以退到后台继续录制。在后台直接启动录音会失败；后台录音的接入约束和定位方法可参考[后台录音指导](audio-recording-background-guidelines.md)。
- 录音无声不一定表示录音没有启动，也可能是录音已进入静音录制、输入设备路由发生变化、并发策略生效或应用写文件逻辑异常。
- `SourceType`会影响录音通路、算法处理、并发打断策略以及输入设备选择。错误的`SourceType`可能导致“有数据但近似无声”的现象，相关说明可参考[使用合适的音频流类型](using-right-streamusage-and-sourcetype.md)。
- 录音场景下，应用除了要关注`start`接口是否成功，还需要同时关注状态变化、读数据回调、输入设备信息以及录音流变化信息。

## 问题定位

- 确认是否已申请并实际获得`ohos.permission.MICROPHONE`权限，并确认录音是在前台启动。
- 确认录音实例是否真正进入`running`状态。对于`AudioCapturer`或`OHAudio Capturer`，不要只看`create`和`start`是否返回成功，还要确认是否收到了状态变化回调，以及停止、暂停、释放是否被其他业务提前调用。
- 如果没有收到录音数据回调，优先检查回调注册是否正确：
  - `AudioCapturer`是否正确注册`on('readData')`回调。
  - OHAudio是否通过`OH_AudioStreamBuilder_SetCapturerReadDataCallback`正确设置回调。
  - 回调是否注册在实例创建完成之后。
  - 是否存在重复注册、重复释放或对象提前销毁。
  - 回调线程内是否执行了耗时操作，导致读数据线程阻塞。
- 如果有录音数据回调，但录音结果无声，检查写文件逻辑是否正确：
  - 文件句柄是否创建成功。
  - 写入偏移是否累计正确。
  - 写入长度是否与回调数据长度一致。
  - 采样率、声道数、采样格式是否与后续播放器解析方式一致。
  - 如果应用需要在停止录音后再拼接、上传、转码或解析PCM数据，不要直接长期保存`readData`回调参数`ArrayBuffer`的引用；应在回调内立即拷贝出独立数据副本，再进行后续缓存或处理。
- 检查`SourceType`是否与业务场景匹配。常见误用包括普通录音场景误用`SOURCE_TYPE_VOICE_COMMUNICATION`、VoIP场景误用`SOURCE_TYPE_MIC`、直播场景未使用`SOURCE_TYPE_LIVE`、原始数据采集场景未使用`SOURCE_TYPE_UNPROCESSED`。
- 如果“回调持续触发，但录音内容全无声”，优先检查是否进入静音录制：
  - 应用是否调用了`setWillMuteWhenInterrupted`。
  - 应用是否配置了独立音频会话策略，并将行为设置为`MUTE_WHEN_INTERRUPTED`。
  - 录音过程中是否收到了中断事件。
  - 无声开始时间点是否与来电、VoIP、语音播报、其他录音任务启动等事件重合。
- 检查输入设备和录音路由是否符合预期：
  - 当前活跃输入设备是否为预期设备。
  - 录音开始前后是否发生输入设备切换。
  - 应用是否配置过输入设备相关策略，或显式切换过输入设备。
  - 是否存在蓝牙耳机、有线耳机、USB声卡等外设接入场景。

  相关能力可参考[查询和监听音频输入设备](audio-input-device-management.md)与[实现音频输入设备路由切换](audio-input-device-switcher.md)。

- 检查并发场景是否触发了录音策略：
  - 当前设备上是否已有其他应用正在录音。
  - 当前业务是否与VoIP通话、系统来电、语音识别、转写、耳返、直播等场景并发。
  - 应用是否监听了其他录音流状态。

  相关说明可参考[录音并发策略说明](audio-recording-concurrency.md)和[查询和监听其他应用录制状态](audio-recording-stream-management.md)。

### 日志维测示例

开发者可以在关键路径增加日志，帮助判断问题发生在录音实例创建、录音启动、数据回调、设备切换还是静音录制阶段。应用侧日志打印能力可参考[使用HiLog打印日志（ArkTS）](../../dfx/hilog-guidelines-arkts.md)。

例如，录音实例创建阶段可能会看到如下日志：

```txt
17:02:44.042   55177-55177   C02B8B/com.example.audiodemo  com.example.audiodemo  E
    [CreateAudioCapturerNativeObject]Capturer Create failed
17:02:44.042   55177-55177   C02B8B/com.example.audiodemo  com.example.audiodemo  E
    [Construct]failed to CreateAudioCapturerNativeObject
17:02:44.042   55177-55177   C01320/com.example.audiodemo  com.example.audiodemo  W
    [source_map145]the stack without line info
17:02:44.043   55177-55177   A03D00/com.example.audiodemo  com.example.audiodemo  E
    Invoke createAudioCapturer failed, code is 6800301, message is system error
```

这类日志说明问题出现在**录音实例创建阶段**，应用还没有进入读数据、写文件或静音录制阶段。开发者应优先排查权限、前台启动时机、录音参数配置、并发场景以及是否重复创建录音对象。

以下示例为片段代码，开发者可按需放入录音关键路径中。示例仅展示已确认的公共接口字段，避免引入与具体业务无关的上下文依赖：

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x3200;
const TAG = 'AudioRecordDFX';

let readCallbackCount = 0;
let totalBytes = 0;

function printCurrentCapturerInfo(audioCapturer: audio.AudioCapturer): void {
  try {
    let capturerInfo = audioCapturer.getCapturerInfoSync();
    let streamInfo = audioCapturer.getStreamInfoSync();
    let streamId = audioCapturer.getAudioStreamIdSync();
    hilog.info(DOMAIN, TAG,
      'capturer info streamId=%{public}d source=%{public}d flags=%{public}d',
      streamId, capturerInfo.source, capturerInfo.capturerFlags);
    hilog.info(DOMAIN, TAG,
      'stream info sampleFormat=%{public}d samplingRate=%{public}d channels=%{public}d encodingType=%{public}d',
      streamInfo.sampleFormat, streamInfo.samplingRate, streamInfo.channels, streamInfo.encodingType);
  } catch (err) {
    let error = err as BusinessError;
    hilog.error(DOMAIN, TAG,
      'printCurrentCapturerInfo failed, code=%{public}d message=%{public}s',
      error.code, error.message);
  }
}

function printCapturerSnapshot(audioStreamManager: audio.AudioStreamManager): void {
  try {
    let infos = audioStreamManager.getCurrentAudioCapturerInfoArraySync();
    hilog.info(DOMAIN, TAG, 'capturer snapshot size=%{public}d', infos.length);
    for (let i = 0; i < infos.length; i++) {
      let info = infos[i];
      hilog.info(DOMAIN, TAG,
        'snapshot[%{public}d]: streamId=%{public}d source=%{public}d muted=%{public}s',
        i, info.streamId, info.capturerInfo.source, String(info.muted));
      if (info.deviceDescriptors.length > 0) {
        hilog.info(DOMAIN, TAG,
          'snapshot[%{public}d]: deviceType=%{public}d deviceRole=%{public}d name=%{public}s address=%{public}s',
          i,
          info.deviceDescriptors[0].deviceType,
          info.deviceDescriptors[0].deviceRole,
          info.deviceDescriptors[0].name,
          info.deviceDescriptors[0].address);
      }
    }
  } catch (err) {
    let error = err as BusinessError;
    hilog.error(DOMAIN, TAG,
      'getCurrentAudioCapturerInfoArraySync failed, code=%{public}d message=%{public}s',
      error.code, error.message);
  }
}

function registerDfxLogs(audioCapturer: audio.AudioCapturer, audioStreamManager: audio.AudioStreamManager): void {
  audioCapturer.on('stateChange', (state) => {
    hilog.info(DOMAIN, TAG, 'stateChange state=%{public}d', state);
  });

  audioCapturer.on('audioInterrupt', (event) => {
    hilog.info(DOMAIN, TAG,
      'audioInterrupt eventType=%{public}d forceType=%{public}d hintType=%{public}d',
      event.eventType, event.forceType, event.hintType);
  });

  audioCapturer.on('audioCapturerChange', (changeInfo) => {
    hilog.info(DOMAIN, TAG,
      'audioCapturerChange streamId=%{public}d source=%{public}d muted=%{public}s',
      changeInfo.streamId, changeInfo.capturerInfo.source, String(changeInfo.muted));
    if (changeInfo.deviceDescriptors.length > 0) {
      hilog.info(DOMAIN, TAG,
        'audioCapturerChange deviceType=%{public}d deviceRole=%{public}d name=%{public}s address=%{public}s',
        changeInfo.deviceDescriptors[0].deviceType,
        changeInfo.deviceDescriptors[0].deviceRole,
        changeInfo.deviceDescriptors[0].name,
        changeInfo.deviceDescriptors[0].address);
    }
  });

  audioCapturer.on('inputDeviceChange', (devices) => {
    hilog.info(DOMAIN, TAG, 'inputDeviceChange size=%{public}d', devices.length);
    if (devices.length > 0) {
      hilog.info(DOMAIN, TAG,
        'inputDeviceChange deviceType=%{public}d deviceRole=%{public}d name=%{public}s address=%{public}s',
        devices[0].deviceType, devices[0].deviceRole, devices[0].name, devices[0].address);
    }
  });

  audioStreamManager.on('audioCapturerChange', (infos) => {
    hilog.info(DOMAIN, TAG, 'streamManager audioCapturerChange size=%{public}d', infos.length);
  });

  audioCapturer.on('readData', (buffer: ArrayBuffer) => {
    readCallbackCount++;
    totalBytes += buffer.byteLength;
    if (readCallbackCount <= 5 || readCallbackCount % 50 === 0) {
      hilog.info(DOMAIN, TAG,
        'readData count=%{public}d bytes=%{public}d totalBytes=%{public}d',
        readCallbackCount, buffer.byteLength, totalBytes);
    }
  });
}
```

- 建议至少打印以下信息：
  - `SourceType`
  - 采样率、声道数、采样格式
  - `start/stop/release`调用结果
  - `stateChange`状态值
  - `audioInterrupt`中的`eventType`、`forceType`、`hintType`
  - `audioCapturerChange`中的`streamId`、`muted`
  - 输入设备的`deviceType`、`deviceRole`、`name`、`address`
  - `readData`回调次数、单次字节数、累计字节数

- 建议在`start`成功后立即打印一次当前录音流配置和录音流快照，例如：

```ts
audioCapturer.start().then(() => {
  hilog.info(DOMAIN, TAG, 'start success');
  printCurrentCapturerInfo(audioCapturer);
  printCapturerSnapshot(audioStreamManager);
}).catch((err: BusinessError) => {
  hilog.error(DOMAIN, TAG, 'start failed, code=%{public}d message=%{public}s', err.code, err.message);
});
```

- 如果录音对象已创建成功，但最终录音无声，建议重点观察如下几类官方日志组合：

```txt
17:15:02.101   55177-55177   0x3200/AudioRecordDFX  com.example.audiodemo  I
    start success
17:15:02.103   55177-55177   0x3200/AudioRecordDFX  com.example.audiodemo  I
    capturer info streamId=73 source=1 flags=0
17:15:02.104   55177-55177   0x3200/AudioRecordDFX  com.example.audiodemo  I
    stream info sampleFormat=0 samplingRate=48000 channels=2 encodingType=0
17:15:02.108   55177-55177   0x3200/AudioRecordDFX  com.example.audiodemo  I
    stateChange state=2
17:15:02.121   55177-55231   0x3200/AudioRecordDFX  com.example.audiodemo  I
    readData count=1 bytes=4096 totalBytes=4096
17:15:05.442   55177-55177   0x3200/AudioRecordDFX  com.example.audiodemo  I
    audioInterrupt eventType=1 forceType=0 hintType=6
17:15:05.443   55177-55177   0x3200/AudioRecordDFX  com.example.audiodemo  I
    audioCapturerChange streamId=73 source=1 muted=true
17:15:05.460   55177-55231   0x3200/AudioRecordDFX  com.example.audiodemo  I
    readData count=80 bytes=4096 totalBytes=327680
17:15:11.207   55177-55177   0x3200/AudioRecordDFX  com.example.audiodemo  I
    inputDeviceChange size=1
17:15:11.207   55177-55177   0x3200/AudioRecordDFX  com.example.audiodemo  I
    inputDeviceChange deviceType=7 deviceRole=1 name=Bluetooth device address=XX:XX:XX:XX:XX:XX
```

  这些日志可按如下方式理解：

  - `stateChange state=2`表示录音流已经进入`STATE_RUNNING`状态。
  - `readData`持续打印说明录音回调仍在触发，录音链路没有停在“未启动”阶段。
  - `audioInterrupt eventType=1 forceType=0 hintType=6`表示发生了音频中断开始事件，系统执行了强制静音提示。对应枚举分别是`INTERRUPT_TYPE_BEGIN`、`INTERRUPT_FORCE`和`INTERRUPT_HINT_MUTE`。
  - `audioCapturerChange ... muted=true`说明当前录音流已经处于静音状态。
  - `inputDeviceChange`日志可以用于判断无声前后是否发生了输入设备切换。

- 问题复现时，开发者可通过以下命令按`tag`过滤应用日志：

```txt
hdc shell hilog -T AudioRecordDFX
```

  如果应用日志中已经出现系统接口报错，也建议同时结合接口关键字一起看，例如`CreateAudioCapturerNativeObject`、`Construct`、`createAudioCapturer`、`readData`、`audioCapturerChange`等，按时间顺序判断问题是发生在创建、启动、回调还是设备切换阶段。

  如果需要查看录音状态，建议结合`stateChange`事件或`audioCapturer.state`属性判断，不要把`audioCapturerChange`中的信息当成录音状态字段使用。

  如果需要查看当前录音流的输入设备，也可以结合`audioCapturer.getCurrentInputDevices()`或`audioCapturer.getCurrentAudioCapturerChangeInfo()`进一步确认当前设备信息。

  如果录音实例已经创建成功并进入`running`状态，框架侧可直接确认的信息主要包括：是否持续收到`readData`回调、`readData`返回的缓冲区大小、`audioCapturerChange`中的`muted`是否为`true`、以及当前输入设备信息。当前接口不会直接给出“静音帧”这样的统一判定字段。

  需要注意，[on('readData')](../../reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md#onreaddata11)回调返回的是`ArrayBuffer`。如果开发者希望进一步分析PCM数据内容，只能基于本应用实际使用的采样格式、采样位宽、声道数和编码方式自行解析缓冲区；这属于应用侧自定义调试逻辑，不是框架统一提供的日志字段，因此不同业务的判定方法和阈值可能不同。

  对于需要延后处理的数据，还应特别关注缓冲区的使用方式。常见错误写法是仅在`readData`回调中保存`ArrayBuffer`引用，等停止录音后再统一拼接和解析。这样做可能导致后续读到的内容与回调触发当时的PCM数据不一致，表现为最终文件接近静音、只有底噪，或回调内观察到的峰值与停止后重新解析的峰值明显不一致。

  建议在`readData`回调内立即拷贝当前数据，再保存到应用自己的缓存队列中。例如：

```ts
audioCapturer.on('readData', (buffer: ArrayBuffer) => {
  const source = new Uint8Array(buffer);
  const chunk = new Uint8Array(source.length);
  chunk.set(source);
  this.audioChunks.push(chunk);
});
```

  其中，`new Uint8Array(buffer)`只是基于当前`ArrayBuffer`创建视图，不等于完成数据复制；真正的独立副本是在重新分配`Uint8Array`并执行`chunk.set(source)`后得到的。

  因此，如果应用侧现象是“`readData`回调持续有数据，但停止录音后再拼接出的PCM幅值很小、接近底噪”，除了检查采样率、采样格式和大小端解析方式外，也要优先检查是否把`readData`中的`ArrayBuffer`直接保存引用并延后读取。

  此外，API参考中明确说明，为了消除麦克风硬件设计带来的上电杂音，录音启动后的前100ms数据通常会进行静音处理。因此，即使启动成功后最开始几次`readData`回调拿到的数据接近静音，也不能直接据此判断录音异常。

- 如果日志停留在`CreateAudioCapturerNativeObject failed`、`Invoke createAudioCapturer failed`等阶段，问题通常发生在录音实例创建阶段，应优先排查权限、前台启动时机、参数配置和并发场景。
- 如果录音实例已进入`running`状态，但没有`readData`日志，问题通常集中在回调注册、对象生命周期或线程阻塞。
- 如果`readData`持续打印，但`audioCapturerChange`中出现`muted=true`，问题通常与静音录制、中断策略或音频会话策略相关。
- 如果无声前后输入设备信息发生变化，问题通常与输入设备路由切换相关。

  通过录音流信息查询接口获取设备名称或地址时，如果应用未声明`ohos.permission.USE_BLUETOOTH`权限，蓝牙设备相关名称和地址字段可能为空。

开发者反馈问题时，建议同时提供录音接口类型、`SourceType`取值、启动方式、是否申请长时任务、是否发生前后台切换、是否有蓝牙/USB等外设、是否与通话或其他录音任务并发、是否收到中断或设备切换事件、读数据回调是否持续触发等信息。
