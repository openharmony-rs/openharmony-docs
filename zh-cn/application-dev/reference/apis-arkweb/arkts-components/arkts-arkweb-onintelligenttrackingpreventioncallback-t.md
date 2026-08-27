# OnIntelligentTrackingPreventionCallback

```TypeScript
type OnIntelligentTrackingPreventionCallback = (details: IntelligentTrackingPreventionDetails) => void
```

当跟踪者cookie被拦截时触发的回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| details | [IntelligentTrackingPreventionDetails](arkts-arkweb-intelligenttrackingpreventiondetails-i.md) | 是 | 提供智能防跟踪拦截的详细信息。 |
