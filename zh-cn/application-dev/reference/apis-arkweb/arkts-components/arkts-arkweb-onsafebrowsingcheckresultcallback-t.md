# OnSafeBrowsingCheckResultCallback

```TypeScript
type OnSafeBrowsingCheckResultCallback = (threatType: ThreatType) => void
```

网站安全风险检查触发的回调。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| threatType | [ThreatType](arkts-arkweb-threattype-e.md) | 是 | 定义网站threat类型。 |
