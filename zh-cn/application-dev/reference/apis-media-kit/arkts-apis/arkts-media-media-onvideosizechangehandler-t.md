# OnVideoSizeChangeHandler

```TypeScript
type OnVideoSizeChangeHandler = (width: int, height: int) => void
```

视频播放宽高变化事件回调方法。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-media-type OnVideoSizeChangeHandler = (width: int, height: int) => void--><!--Device-media-type OnVideoSizeChangeHandler = (width: int, height: int) => void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 视频宽度，单位为像素（px）。  |
| height | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 视频高度，单位为像素（px）。  |

