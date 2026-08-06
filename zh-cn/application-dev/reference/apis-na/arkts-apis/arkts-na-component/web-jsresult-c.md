# JsResult

Defines the js result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class JsResult--><!--Device-unnamed-export declare class JsResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-JsResult-constructor()--><!--Device-JsResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(): void
```

Handle the user's JavaScript result if cancel the dialog.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-JsResult-handleCancel(): void--><!--Device-JsResult-handleCancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleConfirm

```TypeScript
handleConfirm(): void
```

Handle the user's JavaScript result if confirm the dialog.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-JsResult-handleConfirm(): void--><!--Device-JsResult-handleConfirm(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handlePromptConfirm

```TypeScript
handlePromptConfirm(result: string): void
```

Handle the user's JavaScript result if confirm the prompt dialog.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-JsResult-handlePromptConfirm(result: string): void--><!--Device-JsResult-handlePromptConfirm(result: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | string | 是 | The content of the dialog box entered by the user. |

