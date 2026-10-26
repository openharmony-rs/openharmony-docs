# PlaybackCommand

```TypeScript
enum PlaybackCommand
```

可执行的播控指令枚举定义，用于应用在Prepare()完成后，查询该片源是否可以执行对应的播放控制操作；

**起始版本：** 26.1.0

<!--Device-media-enum PlaybackCommand--><!--Device-media-enum PlaybackCommand-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## PLAYBACK_COMMAND_RATE

```TypeScript
PLAYBACK_COMMAND_RATE = 1
```

调整播放速率的操作值

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PlaybackCommand-PLAYBACK_COMMAND_RATE = 1--><!--Device-PlaybackCommand-PLAYBACK_COMMAND_RATE = 1-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## PLAYBACK_COMMAND_SEEK

```TypeScript
PLAYBACK_COMMAND_SEEK = 0
```

SEEK操作枚举值定义

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PlaybackCommand-PLAYBACK_COMMAND_SEEK = 0--><!--Device-PlaybackCommand-PLAYBACK_COMMAND_SEEK = 0-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer
