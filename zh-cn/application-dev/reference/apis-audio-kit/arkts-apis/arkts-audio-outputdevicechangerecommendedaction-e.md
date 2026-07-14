# OutputDeviceChangeRecommendedAction

表示输出设备变更后推荐操作的枚举。

常见场景示例：耳机设备和外放设备之间进行切换。当佩戴耳机时，从外放设备切换到耳机设备，系统会推荐继续播放，提示应用无需停止当前播放。当摘下耳机设备切换到外放设备时，系统会推荐停止播放。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Core

## DEVICE_CHANGE_RECOMMEND_TO_CONTINUE

```TypeScript
DEVICE_CHANGE_RECOMMEND_TO_CONTINUE = 0
```

推荐继续播放（该事件作为播放维持提示，作用是告知应用本次设备变动音频无需停止播放，但‌不可将其作为启动音频播放的判断依据）。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Core

## DEVICE_CHANGE_RECOMMEND_TO_STOP

```TypeScript
DEVICE_CHANGE_RECOMMEND_TO_STOP = 1
```

推荐停止播放。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Core

