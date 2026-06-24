# OnFrameFetched

```TypeScript
type OnFrameFetched = (frameInfo: FrameInfo, err?: BusinessError<void>) => void
```

批量获取缩略图回调函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| frameInfo | FrameInfo | 是 | 返回的缩略图信息。 |
| err | BusinessError&lt;void&gt; | 否 | 获取缩略图时发生错误，默认值为null。 |

