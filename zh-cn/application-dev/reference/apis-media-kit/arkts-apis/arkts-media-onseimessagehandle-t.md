# OnSeiMessageHandle

```TypeScript
type OnSeiMessageHandle = (messages: Array<SeiMessage>, playbackPosition?: number) => void
```

获取SEI信息，使用场景：订阅SEI信息事件，回调返回SEI详细信息。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messages | Array&lt;SeiMessage&gt; | 是 | SEI信息。 |
| playbackPosition | int | 否 | 获取当前播放位置（单位：毫秒）。 |

