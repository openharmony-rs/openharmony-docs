# Class (JsResult)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=ff3cdc7904576f258fd8d07326a4708bead0b2a0 translatedAt=2026-08-07T04:37:28.887Z pushedAt=2026-08-07T08:12:27.603Z -->

JsResult is a result handling object returned by the Web component when processing JavaScript dialog box events. It is used in scenarios where developers intercept and customize the handling of dialog boxes such as `window.alert`, `window.confirm`, and `window.prompt`. In event callbacks such as [onAlert](./arkts-basic-components-web-events.md#onalert), [onConfirm](./arkts-basic-components-web-events.md#onconfirm), or [onPrompt](./arkts-basic-components-web-events.md#onprompt9), developers can use this object to feed back the user's operation results, such as confirmation, cancellation, or input content, to the Web component, thereby controlling the subsequent behavior of the dialog box.

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 8.
>
> - The sample effect is subject to the actual device.

## constructor

constructor()

Constructor of JsResult. Used to handle JavaScript dialog box events.

**System capability**: SystemCapability.Web.Webview.Core

## handleCancel

handleCancel(): void

Notifies the **Web** component of the user's cancel operation in the dialog box.

**System capability**: SystemCapability.Web.Webview.Core

## handleConfirm

handleConfirm(): void

Notifies the **Web** component of the user's confirm operation in the dialog box.

**System capability**: SystemCapability.Web.Webview.Core

## handlePromptConfirm<sup>9+</sup>

handlePromptConfirm(result: string): void

Notifies the Web component that the user has confirmed the dialog box operation and passes the dialog box content.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description       |
| ------ | ------ | ---- | ----------- |
| result | string | Yes   | User input in the dialog box.|