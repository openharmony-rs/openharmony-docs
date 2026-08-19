# JsResult

JsResult是Web组件在处理JavaScript弹窗事件时返回的结果处理对象，适用于开发者拦截并自定义处理`window.alert`、`window.confirm`、`window.prompt`等弹窗场景。开发者可在 [onAlert](arkts-arkweb-web-attribute.md#onalert)、[onConfirm](arkts-arkweb-web-attribute.md#onconfirm)或 [onPrompt](arkts-arkweb-web-attribute.md#onprompt)等事件回调中，通过该对象向Web组件反馈用户的确认、取消或输入内容等操作结果，从而控制弹窗的后续行为。

**起始版本：** 8

<!--Device-unnamed-declare class JsResult--><!--Device-unnamed-declare class JsResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

JsResult的构造函数。用于处理JavaScript弹窗事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsResult-constructor()--><!--Device-JsResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(): void
```

通知Web组件用户取消弹窗操作。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsResult-handleCancel(): void--><!--Device-JsResult-handleCancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleConfirm

```TypeScript
handleConfirm(): void
```

通知Web组件用户确认弹窗操作。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsResult-handleConfirm(): void--><!--Device-JsResult-handleConfirm(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handlePromptConfirm

```TypeScript
handlePromptConfirm(result: string): void
```

通知Web组件用户确认弹窗操作并传递对话框内容。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsResult-handlePromptConfirm(result: string): void--><!--Device-JsResult-handlePromptConfirm(result: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | string | 是 | 用户输入的对话框内容。 |

