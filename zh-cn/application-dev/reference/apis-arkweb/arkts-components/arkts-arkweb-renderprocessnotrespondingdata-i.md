# RenderProcessNotRespondingData

提供渲染进程无响应的详细信息。适用于需要诊断渲染进程异常的场景，提升故障排查的准确性和效率。

**起始版本：** 12

<!--Device-unnamed-declare interface RenderProcessNotRespondingData--><!--Device-unnamed-declare interface RenderProcessNotRespondingData-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## jsStack

```TypeScript
jsStack: string
```

网页的JavaScript调用栈信息。

**类型：** string

**起始版本：** 12

<!--Device-RenderProcessNotRespondingData-jsStack: string--><!--Device-RenderProcessNotRespondingData-jsStack: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## pid

```TypeScript
pid: number
```

网页的进程id。

**类型：** number

**起始版本：** 12

<!--Device-RenderProcessNotRespondingData-pid: number--><!--Device-RenderProcessNotRespondingData-pid: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: RenderProcessNotRespondingReason
```

触发渲染进程无响应回调的原因。

**类型：** [RenderProcessNotRespondingReason](arkts-arkweb-renderprocessnotrespondingreason-e.md)

**起始版本：** 12

<!--Device-RenderProcessNotRespondingData-reason: RenderProcessNotRespondingReason--><!--Device-RenderProcessNotRespondingData-reason: RenderProcessNotRespondingReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

