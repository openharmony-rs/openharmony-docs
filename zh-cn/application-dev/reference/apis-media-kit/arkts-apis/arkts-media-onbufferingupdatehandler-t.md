# OnBufferingUpdateHandler

```TypeScript
type OnBufferingUpdateHandler = (infoType: BufferingInfoType, value: number) => void
```

播放缓存事件回调方法。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| infoType | BufferingInfoType | 是 | 缓存时间类型。 |
| value | int | 是 | 缓存时间类型的值。 |

