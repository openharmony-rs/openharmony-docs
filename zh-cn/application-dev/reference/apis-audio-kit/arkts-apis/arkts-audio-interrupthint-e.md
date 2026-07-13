# InterruptHint

表示中断提示的枚举。

当用户监听到音频中断事件（即收到[InterruptEvent](arkts-audio-interruptevent-i.md)事件）时，获取此信息。

此类型表示根据焦点策略，对音频流执行的具体操作（如暂停、调整音量等）。

可以结合InterruptEvent中的[InterruptForceType](arkts-audio-interruptforcetype-e.md)信息，判断该操作是否已由系统强制执行。详情请参阅文档
[音频焦点介绍](../../../../media/audio/audio-playback-concurrency.md)。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_NONE

```TypeScript
INTERRUPT_HINT_NONE = 0
```

无提示。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_RESUME

```TypeScript
INTERRUPT_HINT_RESUME = 1
```

提示音频恢复，应用可主动触发开始渲染或开始采集的相关操作。

此操作无法由系统强制执行，其对应的[InterruptForceType](arkts-audio-interruptforcetype-e.md)一定为INTERRUPT_SHARE类型。

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_PAUSE

```TypeScript
INTERRUPT_HINT_PAUSE = 2
```

提示音频暂停，暂时失去音频焦点。

待焦点可用时，会收到INTERRUPT_HINT_RESUME事件。

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_STOP

```TypeScript
INTERRUPT_HINT_STOP = 3
```

提示音频停止，彻底失去音频焦点。

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_DUCK

```TypeScript
INTERRUPT_HINT_DUCK = 4
```

提示音频躲避开始，降低音量播放。

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_UNDUCK

```TypeScript
INTERRUPT_HINT_UNDUCK = 5
```

提示音频躲避结束，恢复音量播放。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_MUTE

```TypeScript
INTERRUPT_HINT_MUTE = 6
```

提示音频静音。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_UNMUTE

```TypeScript
INTERRUPT_HINT_UNMUTE = 7
```

提示音频解除静音。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

