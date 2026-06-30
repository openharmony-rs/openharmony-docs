# 使用ArkTS接口实现音频通话
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyy0412-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

音频通话场景需要同时完成音频采集、网络传输和音频播放。应用可基于ArkTS的[AudioCapturer](../../reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md)采集本端PCM数据，经过编码和网络发送给对端；同时基于[AudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md)播放从网络接收并解码后的对端PCM数据。

本文介绍使用ArkTS接口实现VoIP通话的基本思路和注意事项。蜂窝通话能力仅对系统应用开放，普通应用不支持通过ArkTS接口实现蜂窝通话。

## 基本流程

1. 申请麦克风权限`ohos.permission.MICROPHONE`，申请方式参考[向用户申请授权](../../security/AccessToken/request-user-authorization.md)。
2. 创建AudioCapturer实例，音源类型设置为语音通话：`SOURCE_TYPE_VOICE_COMMUNICATION`。
3. 创建AudioRenderer实例，音频流使用类型设置为VoIP通话：`STREAM_USAGE_VOICE_COMMUNICATION`。
4. 订阅AudioCapturer的`readData`回调，读取本端PCM数据，完成编码、回声控制策略适配和网络发送。
5. 订阅AudioRenderer的`writeData`回调，将对端网络数据解码后的PCM数据写入系统提供的buffer。
6. 通话结束时停止采集和播放，并调用`release()`释放音频流资源。

## 关键参数配置

通话场景下，采集端和播放端应使用匹配的采样率、声道数、采样格式和编码类型，避免额外重采样或格式转换导致时延增加。

```ts
import { audio } from '@kit.AudioKit';

let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000,
  channels: audio.AudioChannel.CHANNEL_1,
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE,
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW
};

let audioRendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION,
  rendererFlags: 0
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_VOICE_COMMUNICATION,
  capturerFlags: 0
};
```

## ArkTS接口使用约束

- ArkTS的AudioRenderer和AudioCapturer适合实现业务逻辑清晰、时延要求中等的VoIP通话。对极低时延、长时间稳定实时处理或复杂音频算法要求较高的场景，建议评估使用OHAudio等C/C++接口。
- AudioRenderer输入和AudioCapturer输出均为PCM数据。编解码、网络传输、丢包补偿、抖动缓冲、音量策略等能力需要应用自行实现。
- 通话流应使用通话相关的[StreamUsage](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/arkts-apis-audio-e#streamusage)和[SourceType](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/arkts-apis-audio-e#sourcetype8)，否则系统无法按通话场景应用合适的音频策略。
- AudioCapturer录音时必须完成权限申请，并处理用户拒绝授权、录音并发限制等异常情况。
- 音频流处于非released状态时会占用系统音频资源，通话结束或异常退出时必须释放资源。如不释放资源，通话流会占用音频焦点产生媒体音频从听筒出声、音量键默认调节通话音量、部分录音流（语音消息录制、语音识别录制）无法启动的问题

## 避免主线程阻塞

音频通话的数据回调线程会调用应用起流时设置的回调接口`OnReadData`、`OnWriteData`，如果在主线程中执行音频数据读写、编解码、网络收发或文件读写等耗时任务，会和其他任务竞争主线程资源导致音频数据无法及时读取和填充，阻塞客户端的应用回调线程从而导致音频丢帧，具体表现为通话卡顿、断续、杂音或录音数据丢失。

建议将音频数据处理放到独立任务或线程中，并在回调中只完成轻量的数据拷贝和状态检查。`readData`回调中应尽快取走采集数据，`writeData`回调中应及时填充播放buffer；当网络数据不足时，需要填充静音数据，避免播放残留数据或杂音。

## 相关文档

- [音频通话开发概述](audio-call-overview.md)
- [开发音频通话功能](audio-call-development.md)
- [使用AudioRenderer开发音频播放功能(ArkTs)](using-audiorenderer-for-playback.md)
- [使用AudioCapturer开发音频录制功能(ArkTS)](using-audiocapturer-for-recording.md)
