# BlankScreenDetectionEventInfo

定义检测到白屏时的事件信息。

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## blankScreenDetails

```TypeScript
blankScreenDetails?: BlankScreenDetails
```

本次检测白屏的结果的细节。

如当发现近似白屏的现象产生，这个细节就包含具体命中了多少点。否则没有该属性。

**类型：** BlankScreenDetails

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## blankScreenReason

```TypeScript
blankScreenReason: DetectedBlankScreenReason
```

本次检测到白屏时，具体原因与检测的方法相关。

**类型：** DetectedBlankScreenReason

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

检测到白屏时，页面的url。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

