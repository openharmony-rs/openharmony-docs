# JsResult

```TypeScript
declare class JsResult
```

JsResult is a result handling object returned by the Web component when processing JavaScript dialog box events. It is used in scenarios where developers intercept and customize the handling of dialog boxes such as `window.alert`, `window.confirm`, and `window.prompt`. In event callbacks such as [onAlert](arkts-arkweb-web-comp-attribute.md#onalert), [onConfirm](arkts-arkweb-web-comp-attribute.md#onconfirm), or [onPrompt](arkts-arkweb-web-comp-attribute.md#onprompt), developers can use this object to feed back the user's operation results, such as confirmation, cancellation, or input content, to the Web component, thereby controlling the subsequent behavior of the dialog box.

**Since:** 8

<!--Device-unnamed-declare class JsResult--><!--Device-unnamed-declare class JsResult-End-->

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor of JsResult. Used to handle JavaScript dialog box events.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-JsResult-constructor()--><!--Device-JsResult-constructor()-End-->

**System capability:** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(): void
```

Notifies the **Web** component of the user's cancel operation in the dialog box.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-JsResult-handleCancel(): void--><!--Device-JsResult-handleCancel(): void-End-->

**System capability:** SystemCapability.Web.Webview.Core

## handleConfirm

```TypeScript
handleConfirm(): void
```

Notifies the **Web** component of the user's confirm operation in the dialog box.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-JsResult-handleConfirm(): void--><!--Device-JsResult-handleConfirm(): void-End-->

**System capability:** SystemCapability.Web.Webview.Core

## handlePromptConfirm

```TypeScript
handlePromptConfirm(result: string): void
```

Notifies the Web component that the user has confirmed the dialog box operation and passes the dialog box content.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-JsResult-handlePromptConfirm(result: string): void--><!--Device-JsResult-handlePromptConfirm(result: string): void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | string | Yes | User input in the dialog box. |
