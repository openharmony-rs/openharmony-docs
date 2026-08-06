# OnBufferingUpdateHandler

```TypeScript
type OnBufferingUpdateHandler = (infoType: BufferingInfoType, value: int) => void
```

播放缓存事件回调方法。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-media-type OnBufferingUpdateHandler = (infoType: BufferingInfoType, value: int) => void--><!--Device-media-type OnBufferingUpdateHandler = (infoType: BufferingInfoType, value: int) => void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| infoType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 缓存时间类型。  |
| value | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 缓存时间类型的值。  |

