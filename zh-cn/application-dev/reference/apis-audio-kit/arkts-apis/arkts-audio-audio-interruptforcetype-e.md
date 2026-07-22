# InterruptForceType

表示音频打断类型的枚举。

当用户监听到音频中断（即收到[InterruptEvent](arkts-audio-audio-interruptevent-i.md)事件）时，获取此信息。

此类型表示音频打断是否已由系统强制执行，具体操作信息（如音频暂停、停止等）可通过[InterruptHint](arkts-audio-audio-interrupthint-e.md)获取。关于音频打断策略的详细说明可参考文档[音频焦点介绍](../../../media/audio/audio-playback-concurrency.md)。

**起始版本：** 9

<!--Device-audio-enum InterruptForceType--><!--Device-audio-enum InterruptForceType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_FORCE

```TypeScript
INTERRUPT_FORCE = 0
```

强制打断类型，即具体操作已由系统强制执行。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterruptForceType-INTERRUPT_FORCE = 0--><!--Device-InterruptForceType-INTERRUPT_FORCE = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_SHARE

```TypeScript
INTERRUPT_SHARE = 1
```

共享打断类型，即系统不执行具体操作，通过[InterruptHint](arkts-audio-audio-interrupthint-e.md)建议并提示应用操作，应用可自行决策下一步处理方式。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterruptForceType-INTERRUPT_SHARE = 1--><!--Device-InterruptForceType-INTERRUPT_SHARE = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

