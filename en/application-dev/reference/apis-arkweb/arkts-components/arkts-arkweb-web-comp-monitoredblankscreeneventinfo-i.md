# MonitoredBlankScreenEventInfo

```TypeScript
declare interface MonitoredBlankScreenEventInfo
```

Provides the event information for blank screen monitoring attribution, including the page URL, the attribution reason, and additional details.

**Since:** 26.0.1

<!--Device-unnamed-declare interface MonitoredBlankScreenEventInfo--><!--Device-unnamed-declare interface MonitoredBlankScreenEventInfo-End-->

**System capability:** SystemCapability.Web.Webview.Core

## extraMsg

```TypeScript
extraMsg: string
```

Extra message for blank screen reason.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-MonitoredBlankScreenEventInfo-extraMsg: string--><!--Device-MonitoredBlankScreenEventInfo-extraMsg: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: BlankScreenReason
```

Blank screen reason.

**Type:** [BlankScreenReason](arkts-arkweb-web-comp-blankscreenreason-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-MonitoredBlankScreenEventInfo-reason: BlankScreenReason--><!--Device-MonitoredBlankScreenEventInfo-reason: BlankScreenReason-End-->

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL of the page that is loading when the white screen is monitored.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-MonitoredBlankScreenEventInfo-url: string--><!--Device-MonitoredBlankScreenEventInfo-url: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
