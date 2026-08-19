# OnDataResubmittedEvent

定义网页表单可以重新提交时触发的回调信息，包括提交句柄。适用于需要处理表单重试提交的场景，提升表单交互的可靠性和用户体验。

**起始版本：** 12

<!--Device-unnamed-declare interface OnDataResubmittedEvent--><!--Device-unnamed-declare interface OnDataResubmittedEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## handler

```TypeScript
handler: DataResubmissionHandler
```

表单数据重新提交句柄。

**类型：** [DataResubmissionHandler](arkts-arkweb-dataresubmissionhandler-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnDataResubmittedEvent-handler: DataResubmissionHandler--><!--Device-OnDataResubmittedEvent-handler: DataResubmissionHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

