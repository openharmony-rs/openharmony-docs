# JsResult

定义 JS 返回结果。

**起始版本：** 8

<!--Device-unnamed-declare class JsResult--><!--Device-unnamed-declare class JsResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

JsResult的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsResult-constructor()--><!--Device-JsResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="handlecancel"></a>
## handleCancel

```TypeScript
handleCancel(): void
```

若取消弹窗，则处理用户的JavaScript执行结果。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsResult-handleCancel(): void--><!--Device-JsResult-handleCancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="handleconfirm"></a>
## handleConfirm

```TypeScript
handleConfirm(): void
```

确认弹窗后，处理用户的 JavaScript 执行结果。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsResult-handleConfirm(): void--><!--Device-JsResult-handleConfirm(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="handlepromptconfirm"></a>
## handlePromptConfirm

```TypeScript
handlePromptConfirm(result: string): void
```

确认提示框后，处理用户的 JavaScript 执行结果。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsResult-handlePromptConfirm(result: string): void--><!--Device-JsResult-handlePromptConfirm(result: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | string | 是 | The content of the dialog box entered by the user. |

