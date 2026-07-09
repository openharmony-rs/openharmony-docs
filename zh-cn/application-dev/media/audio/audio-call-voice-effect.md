# 音频通话算法选择
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ZhengYong21-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

系统面向通话场景主动提供音频算法处理能力，主要用于提升人声清晰度和通话听感。系统会根据音频流类型和音频场景识别通话业务，并自动启用相应的3A处理策略。

3A通常包括以下音频处理能力：

- 声学回声消除（Acoustic Echo Cancellation，AEC）：抑制扬声器播放声音被麦克风再次采集形成的回声。
- 噪声抑制（Noise Suppression，NS）：降低环境噪声对通话人声的影响。
- 自动增益控制（Automatic Gain Control，AGC）：动态调整采集音量，使人声保持在合适响度范围内。

## 生效方式

1. 应用无需单独创建3A音效节点。开发VoIP通话时，系统会依据播放流和录音流的通话类型自动选择通话音频通路，并在支持的设备上启用3A处理。
2. 当应用需要进行语音通话等注重增强人声、抑制环境噪声、回声消除的音频场景，建议使用通话类型创建音频流；当应用更关注录制环境声音如录像场景，不推荐使用通话类型录制。

关键配置如下：

- 播放对端声音时，`AudioRendererInfo`中的`usage`需设置为[STREAM_USAGE_VOICE_COMMUNICATION](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)或者[STREAM_USAGE_VIDEO_COMMUNICATION](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)，用于标识VoIP语音通话播放流。该类型的播放流起播时，会触发开启3A算法。
- 录制本端声音时，`AudioCapturerInfo`中的`source`需设置为[SOURCE_TYPE_VOICE_COMMUNICATION](../../reference/apis-audio-kit/arkts-apis-audio-e.md#sourcetype8)，用于标识语音通话采集流。单独启动该录音流不会开启3A，需要同时存在通话类型的播放流起播。

## 开发建议

通话的播放和录音开发流程可参考[开发音频通话功能](audio-call-development.md)。通话场景、铃声模式和设备切换说明可参考[音频通话开发概述](audio-call-overview.md)。

## 注意事项

- 3A处理由系统根据设备能力和当前音频通路自动决策，不保证所有设备、所有路由下的处理效果完全一致。
- 通话场景下不建议叠加应用自定义降噪、回声消除或增益处理，避免与系统3A策略重复处理，造成声音失真、音量波动或人声异常。
- 如果通话中切换了输入或输出设备，系统可能重新选择音频通路，应用应关注设备变更并重新确认通话体验。
- 开发通话业务时，应同时按通话场景配置播放流和录音流。若使用普通媒体播放类型或普通麦克风录音类型，系统可能无法识别为通话场景，导致回声消除、噪声抑制、自动增益控制等处理策略不生效或效果不符合预期。
