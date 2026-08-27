# OnAdsEventAdsStartedHandle

```TypeScript
type OnAdsEventAdsStartedHandle = (adsId: string, duration: number) => void
```

广告内容播放开始事件回调方法。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adsId | string | 是 | 正在播放的广告资源ID。 |
| duration | number | 是 | 广告的播放时长，单位为毫秒。  取值限定为整数。 |
