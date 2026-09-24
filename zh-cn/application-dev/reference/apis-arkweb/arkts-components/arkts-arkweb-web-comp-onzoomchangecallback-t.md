# OnZoomChangeCallback

```TypeScript
type OnZoomChangeCallback = (zoomChangeInfo: OnZoomChangeEvent) => void
```

浏览器级缩放倍率变化时触发的回调类型。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| zoomChangeInfo | [OnZoomChangeEvent](arkts-arkweb-web-comp-onzoomchangeevent-i.md) | 是 | 浏览器级缩放倍率变化信息。 |
