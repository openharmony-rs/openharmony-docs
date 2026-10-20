# OnMonitorBlankScreenCallback

```TypeScript
type OnMonitorBlankScreenCallback = (event: MonitoredBlankScreenEventInfo) => void
```

Defines a callback triggered when the Web component monitors a blank screen and completes root cause attribution.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-type OnMonitorBlankScreenCallback = (event: MonitoredBlankScreenEventInfo) => void--><!--Device-unnamed-type OnMonitorBlankScreenCallback = (event: MonitoredBlankScreenEventInfo) => void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [MonitoredBlankScreenEventInfo](arkts-arkweb-web-comp-monitoredblankscreeneventinfo-i.md) | Yes | Event information for blank screen monitoring attribution. |
