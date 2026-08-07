# Class (VerifyPinHandler)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-07T04:48:50.825Z pushedAt=2026-08-07T08:12:36.231Z -->

VerifyPinHandler is a class in the Web component that handles PIN code verification requests. It is used to enhance app security in scenarios requiring identity authentication on web pages (such as secure payment, sensitive operation confirmation, etc.). When user PIN authentication is required, this handler is provided to the app through the onVerifyPin event callback, allowing the app to respond to the PIN verification result, effectively preventing unauthorized access and protecting user privacy. For sample code, see [onVerifyPin](./arkts-basic-components-web-events.md#onverifypin22).

> **NOTE**
>
> - This component is supported since API version 22. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 22.
>
> - The sample effect is subject to the actual device.

## constructor

constructor()

A constructor used to create a **VerifyPinHandler** instance.

**System capability**: SystemCapability.Web.Webview.Core

## confirm

confirm(result: PinVerifyResult): void

Notifies the Web component of the PIN authentication result. The app calls this method to return the PIN verification result to the Web component, which then continues the subsequent authentication process based on the result. If the verification is successful, the Web component allows access to protected content; if the verification fails, the Web component denies access and may prompt the user to retry.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type  | Mandatory  | Description   |
| ------- | ------ | ---- | ------- |
| result | [PinVerifyResult](./arkts-basic-components-web-e.md#pinverifyresult22) | Yes    | PIN authentication result. If successful, the Web component allows subsequent page operations; if failed, page navigation or content loading may be blocked. |