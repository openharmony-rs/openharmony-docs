# AudioSessionBehaviorFlags

表示音频会话行为的枚举。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-audio-enum AudioSessionBehaviorFlags--><!--Device-audio-enum AudioSessionBehaviorFlags-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## DEFAULT_BEHAVIOR

```TypeScript
DEFAULT_BEHAVIOR = 0x00000000
```

默认行为，用于清空音频会话行为设置。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSessionBehaviorFlags-DEFAULT_BEHAVIOR = 0x00000000--><!--Device-AudioSessionBehaviorFlags-DEFAULT_BEHAVIOR = 0x00000000-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## MUTE_WHEN_INTERRUPTED

```TypeScript
MUTE_WHEN_INTERRUPTED = 0x00000002
```

当系统需要停止或暂停音频流时，执行强制静音替代。 调用[setAudioSessionBehavior]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口配置该行为时，必须同步调用 [setAudioSessionScene]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口，否则配置将无法生效。 在音频会话场景下，当音频流静音或恢复时，应用将分别收到[AudioSessionStateChangeHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_. AUDIO\_SESSION\_STATE\_CHANGE\_HINT\_MUTE与[AudioSessionStateChangeHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_. AUDIO\_SESSION\_STATE\_CHANGE\_HINT\_UNMUTE的通知。 在AudioRenderer和AudioCapturer场景下，当音频流静音或恢复时，应用将分别收到[InterruptHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_.INTERRUPT\_HINT\_MUTE与 [InterruptHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_.INTERRUPT\_HINT\_UNMUTE的通知。 **注意：** 该标志不能与PAUSE\_WHEN\_INTERRUPTED共存，若同时设置，仅PAUSE\_WHEN\_INTERRUPTED生效。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSessionBehaviorFlags-MUTE_WHEN_INTERRUPTED = 0x00000002--><!--Device-AudioSessionBehaviorFlags-MUTE_WHEN_INTERRUPTED = 0x00000002-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## PAUSE_WHEN_INTERRUPTED

```TypeScript
PAUSE_WHEN_INTERRUPTED = 0x00000004
```

当系统需要停止音频流时，执行暂停替代。 调用[setAudioSessionBehavior]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口配置该行为时，必须同步调用 [setAudioSessionScene]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口，否则配置将无法生效。 在音频会话场景下，当音频流暂停或恢复时，应用将分别收到[AudioSessionStateChangeHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_. AUDIO\_SESSION\_STATE\_CHANGE\_HINT\_PAUSE与[AudioSessionStateChangeHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_. AUDIO\_SESSION\_STATE\_CHANGE\_HINT\_RESUME的通知。 在AudioRenderer和AudioCapturer场景下，当音频流暂停或恢复时，应用将分别收到[InterruptHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_.INTERRUPT\_HINT\_PAUSE 与[InterruptHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_.INTERRUPT\_HINT\_RESUME的通知。 **注意：** 该标志不能与MUTE\_WHEN\_INTERRUPTED共存，若同时设置，仅该标志生效。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSessionBehaviorFlags-PAUSE_WHEN_INTERRUPTED = 0x00000004--><!--Device-AudioSessionBehaviorFlags-PAUSE_WHEN_INTERRUPTED = 0x00000004-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

