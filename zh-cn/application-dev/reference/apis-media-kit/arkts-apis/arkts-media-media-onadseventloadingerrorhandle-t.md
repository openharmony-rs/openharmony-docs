# OnAdsEventLoadingErrorHandle

```TypeScript
type OnAdsEventLoadingErrorHandle = (adsId: string, reason: BusinessError) => void
```

广告媒体资源加载失败事件回调方法。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adsId | string | 是 | 加载失败的广告资源ID。 |
| reason | [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md) | 是 | 加载失败的原因。 |
