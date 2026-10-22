# MonitoredBlankScreenEventInfo

```TypeScript
declare interface MonitoredBlankScreenEventInfo
```

提供监测到白屏并完成根因归因时的事件信息，包括页面URL、归因原因和附加详情。

**起始版本：** 26.0.1

<!--Device-unnamed-declare interface MonitoredBlankScreenEventInfo--><!--Device-unnamed-declare interface MonitoredBlankScreenEventInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## extraMsg

```TypeScript
extraMsg: string
```

白屏归因原因的附加信息。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitoredBlankScreenEventInfo-extraMsg: string--><!--Device-MonitoredBlankScreenEventInfo-extraMsg: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: BlankScreenReason
```

白屏归因原因。

**类型：** [BlankScreenReason](arkts-arkweb-web-comp-blankscreenreason-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitoredBlankScreenEventInfo-reason: BlankScreenReason--><!--Device-MonitoredBlankScreenEventInfo-reason: BlankScreenReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

监测到白屏时，正在加载页面的URL。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitoredBlankScreenEventInfo-url: string--><!--Device-MonitoredBlankScreenEventInfo-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core
