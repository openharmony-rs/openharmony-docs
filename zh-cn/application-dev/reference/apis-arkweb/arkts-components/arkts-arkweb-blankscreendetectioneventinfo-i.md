# BlankScreenDetectionEventInfo

提供检测到白屏时的事件信息，包括URL、原因和细节。适用于需要监控页面白屏问题的场景，提升白屏诊断的准确性和用户体验。

**起始版本：** 22

<!--Device-unnamed-declare interface BlankScreenDetectionEventInfo--><!--Device-unnamed-declare interface BlankScreenDetectionEventInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## blankScreenDetails

```TypeScript
blankScreenDetails?: BlankScreenDetails
```

本次检测白屏的结果的细节。当使用检测有内容的节点检测策略，且检测到的有内容节点数量未超过阈值时，此参数包含当前命中了多少有内容节点等详细信息；未使用该策略或节点数量超过阈值时，此参数为空。

**类型：** [BlankScreenDetails](arkts-arkweb-blankscreendetails-i.md)

**起始版本：** 22

<!--Device-BlankScreenDetectionEventInfo-blankScreenDetails?: BlankScreenDetails--><!--Device-BlankScreenDetectionEventInfo-blankScreenDetails?: BlankScreenDetails-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## blankScreenReason

```TypeScript
blankScreenReason: DetectedBlankScreenReason
```

本次检测到白屏时，具体原因与检测的方法相关。

**类型：** [DetectedBlankScreenReason](arkts-arkweb-detectedblankscreenreason-e.md)

**起始版本：** 22

<!--Device-BlankScreenDetectionEventInfo-blankScreenReason: DetectedBlankScreenReason--><!--Device-BlankScreenDetectionEventInfo-blankScreenReason: DetectedBlankScreenReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

检测到白屏时，页面的url。

**类型：** string

**起始版本：** 22

<!--Device-BlankScreenDetectionEventInfo-url: string--><!--Device-BlankScreenDetectionEventInfo-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

