# AVSessionType

```TypeScript
type AVSessionType = 'audio' | 'video' | 'voice_call' | 'video_call' | 'photo'
```

当前会话支持的会话类型。

该类型可取的值为下表字符串。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-avSession-type AVSessionType = 'audio' | 'video' | 'voice_call' | 'video_call' | 'photo'--><!--Device-avSession-type AVSessionType = 'audio' | 'video' | 'voice_call' | 'video_call' | 'photo'-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

| 类型 | 说明 |
| --- | --- |
| 'audio' | 音频 |
| 'video' | 视频 |
| 'voice_call' | 音频通话。 [since 11] |
| 'video_call' | 视频通话。 [since 12] |
| 'photo' | 图片。 [since 22] |

