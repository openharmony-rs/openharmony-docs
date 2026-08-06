# OnPlaybackRateDone

```TypeScript
type OnPlaybackRateDone = (rate: double) => void
```

播放速率设置完成事件回调方法。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-media-type OnPlaybackRateDone = (rate: double) => void--><!--Device-media-type OnPlaybackRateDone = (rate: double) => void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 播放速率。  |

