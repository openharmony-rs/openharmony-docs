# 开发音频通话功能
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyy0412-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

在音频通话场景下，应用需要同时进行音频输出（播放对端声音）和音频输入（录制本端声音）。应用可以使用AudioRenderer实现音频输出，使用AudioCapturer实现音频输入，并结合系统API version 8之后提供的3A算法（声学回声消除、噪声抑制、自动增益控制）提升通话质量。

## 3A算法介绍

系统面向通话场景，根据音频流类型自动启用3A算法，用于提升人声清晰度和通话听感。

3A通常包括以下音频处理能力：

- 声学回声消除（Acoustic Echo Cancellation，AEC）：抑制扬声器播放声音被麦克风再次采集形成的回声。
- 噪声抑制（Automatic Noise Suppression，ANS）：降低环境噪声对通话人声的影响。
- 自动增益控制（Automatic Gain Control，AGC）：动态调整采集音量，使人声保持在合适响度范围内。

### 生效方式

- 播放对端声音时，`AudioRendererInfo`中的`usage`需设置为[STREAM_USAGE_VOICE_COMMUNICATION](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)或者[STREAM_USAGE_VIDEO_COMMUNICATION](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)，用于标识VoIP语音通话播放流。该类型的播放流起播时，会触发开启3A算法。
- 录制本端声音时，`AudioCapturerInfo`中的`source`需设置为[SOURCE_TYPE_VOICE_COMMUNICATION](../../reference/apis-audio-kit/arkts-apis-audio-e.md#sourcetype8)，用于标识语音通话采集流。
- 播放和录制具体开发流程见下文[音频通话功能](audio-call-development.md#音频通话功能)。

### 注意事项

- 3A处理由系统根据设备能力和当前音频通路自动决策，不保证所有设备、所有路由下的处理效果完全一致。
- 通话场景下不建议叠加应用自定义降噪、回声消除或增益处理，避免与系统3A策略重复处理，造成声音失真、音量波动或人声异常。
- 如果通话中切换了输入或输出设备，系统可能重新选择音频通路，应用应关注设备变更并重新确认通话体验。
- 开发通话业务时，应同时按通话场景配置播放流和录音流。如果使用非STREAM_USAGE_VOICE_COMMUNICATION、STREAM_USAGE_VIDEO_COMMUNICATION播放类型或非SOURCE_TYPE_VOICE_COMMUNICATION录音类型，系统将无法识别为通话场景，导致回声消除、噪声抑制、自动增益控制等处理策略不生效或效果不符合预期。

## 音频通话功能

在音频通话开始和结束时，应用可以自行检查当前的[音频场景模式](audio-call-overview.md#音频场景模式)和[铃声模式](audio-call-overview.md#铃声模式)，以便采取合适的音频管理及提示策略。

以下代码示范了同时使用AudioRenderer和AudioCapturer实现音频通话功能的基本过程，其中未包含音频通话数据的传输过程，实际开发中，需要将网络传输来的对端通话数据解码播放，此处仅以读取音频文件的数据代替；同时需要将本端录制的通话数据编码打包，通过网络发送给对端，此处仅以将数据写入音频文件代替。

示例为片段代码，可通过点击示例代码右下方的链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/VoipCallSampleJS)。

### 使用AudioRenderer播放对端的通话声音

该过程与[使用AudioRenderer开发音频播放功能(ArkTS)](using-audiorenderer-for-playback.md)过程相似，关键区别在于audioRendererInfo参数和音频数据来源。audioRendererInfo参数中，音频流使用类型usage需设置为VoIP通话：STREAM_USAGE_VOICE_COMMUNICATION。

<!-- @[all_VoIPDemoForAudioRenderer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/VoipCallSampleJS/entry/src/main/ets/pages/VoIpDemoForAudioRenderer.ets) -->

### 使用AudioCapturer录制本端的通话声音

该过程与[使用AudioCapturer开发音频录制功能(ArkTs)](using-audiocapturer-for-recording.md)过程相似，关键区别在于audioCapturerInfo参数和音频数据流向。audioCapturerInfo参数中音源类型source需设置为语音通话：SOURCE_TYPE_VOICE_COMMUNICATION。

所有录制均需要申请麦克风权限：ohos.permission.MICROPHONE，申请方式请参考[向用户申请授权](../../security/AccessToken/request-user-authorization.md)。

<!-- @[all_VoIPDemoForAudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/VoipCallSampleJS/entry/src/main/ets/pages/VoIpDemoForAudioCapturer.ets) -->
