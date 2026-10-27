# OnMonitorBlankScreenCallback

```TypeScript
type OnMonitorBlankScreenCallback = (event: MonitoredBlankScreenEventInfo) => void
```

监测到白屏并完成根因归因时触发此回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type OnMonitorBlankScreenCallback = (event: MonitoredBlankScreenEventInfo) => void--><!--Device-unnamed-type OnMonitorBlankScreenCallback = (event: MonitoredBlankScreenEventInfo) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [MonitoredBlankScreenEventInfo](arkts-arkweb-web-comp-monitoredblankscreeneventinfo-i.md) | 是 | 监测到白屏并完成归因时的详细信息。 |
