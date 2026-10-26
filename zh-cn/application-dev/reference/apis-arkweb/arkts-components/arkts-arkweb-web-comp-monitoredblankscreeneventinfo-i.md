# MonitoredBlankScreenEventInfo

```TypeScript
declare interface MonitoredBlankScreenEventInfo
```

提供监测到白屏并完成根因归因时的事件信息，包括页面URL、归因原因和附加详情。适用于需要监控页面白屏问题并分析根因的场景，提升白屏问题的定位效率和用户体验。

**起始版本：** 26.0.1

<!--Device-unnamed-declare interface MonitoredBlankScreenEventInfo--><!--Device-unnamed-declare interface MonitoredBlankScreenEventInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## extraMsg

```TypeScript
extraMsg: string
```

白屏归因原因的附加信息，JSON格式的字符串，包含根因归因报告的详细内容。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitoredBlankScreenEventInfo-extraMsg: string--><!--Device-MonitoredBlankScreenEventInfo-extraMsg: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: BlankScreenReason
```

本次白屏的归因原因。

**类型：** [BlankScreenReason](arkts-arkweb-web-comp-blankscreenreason-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitoredBlankScreenEventInfo-reason: BlankScreenReason--><!--Device-MonitoredBlankScreenEventInfo-reason: BlankScreenReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

监测到白屏时，页面的url。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitoredBlankScreenEventInfo-url: string--><!--Device-MonitoredBlankScreenEventInfo-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core
