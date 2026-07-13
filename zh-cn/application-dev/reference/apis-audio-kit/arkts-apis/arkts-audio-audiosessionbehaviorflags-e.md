# AudioSessionBehaviorFlags

表示音频会话行为的枚举。

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Audio.Core

## DEFAULT_BEHAVIOR

```TypeScript
DEFAULT_BEHAVIOR = 0x00000000
```

默认行为，用于清空音频会话行为设置。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## MUTE_WHEN_INTERRUPTED

```TypeScript
MUTE_WHEN_INTERRUPTED = 0x00000002
```

当系统需要停止或暂停音频流时，执行强制静音替代。

调用[setAudioSessionBehavior](arkts-audio-audiosessionmanager-i.md#setaudiosessionbehavior-1)接口配置该行为时，必须同步调用
[setAudioSessionScene](arkts-audio-audiosessionmanager-i.md#setaudiosessionscene-1)接口，否则配置将无法生效。

在音频会话场景下，当音频流静音或恢复时，应用将分别收到[AudioSessionStateChangeHint](arkts-audio-audiosessionstatechangehint-e.md).
AUDIO_SESSION_STATE_CHANGE_HINT_MUTE与[AudioSessionStateChangeHint](arkts-audio-audiosessionstatechangehint-e.md).
AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE的通知。

在AudioRenderer和AudioCapturer场景下，当音频流静音或恢复时，应用将分别收到[InterruptHint](arkts-audio-interrupthint-e.md).INTERRUPT_HINT_MUTE与
[InterruptHint](arkts-audio-interrupthint-e.md).INTERRUPT_HINT_UNMUTE的通知。

**注意：** 该标志不能与PAUSE_WHEN_INTERRUPTED共存，若同时设置，仅PAUSE_WHEN_INTERRUPTED生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## PAUSE_WHEN_INTERRUPTED

```TypeScript
PAUSE_WHEN_INTERRUPTED = 0x00000004
```

当系统需要停止音频流时，执行暂停替代。

调用[setAudioSessionBehavior](arkts-audio-audiosessionmanager-i.md#setaudiosessionbehavior-1)接口配置该行为时，必须同步调用
[setAudioSessionScene](arkts-audio-audiosessionmanager-i.md#setaudiosessionscene-1)接口，否则配置将无法生效。

在音频会话场景下，当音频流暂停或恢复时，应用将分别收到[AudioSessionStateChangeHint](arkts-audio-audiosessionstatechangehint-e.md).
AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE与[AudioSessionStateChangeHint](arkts-audio-audiosessionstatechangehint-e.md).
AUDIO_SESSION_STATE_CHANGE_HINT_RESUME的通知。

在AudioRenderer和AudioCapturer场景下，当音频流暂停或恢复时，应用将分别收到[InterruptHint](arkts-audio-interrupthint-e.md).INTERRUPT_HINT_PAUSE
与[InterruptHint](arkts-audio-interrupthint-e.md).INTERRUPT_HINT_RESUME的通知。

**注意：** 该标志不能与MUTE_WHEN_INTERRUPTED共存，若同时设置，仅该标志生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

