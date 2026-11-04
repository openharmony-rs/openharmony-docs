# Class (VerifyPinHandler)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:29:53.973Z pushedAt=2026-11-04T11:34:47.639Z nl=1 -->

VerifyPinHandler is a class in the Web component that handles PIN code verification requests. It is used to enhance app security in scenarios requiring identity authentication on web pages (such as secure payment, sensitive operation confirmation, etc.). When user PIN authentication is required, this handler is provided to the app through the onVerifyPin event callback, allowing the app to respond to the PIN verification result, effectively preventing unauthorized access and protecting user privacy. For sample code, see [onVerifyPin](./arkts-basic-components-web-events.md#onverifypin22).

> **NOTE**
>
> - This component is supported since API version 22. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This class is supported since API version 22.
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
| result | [PinVerifyResult](./arkts-basic-components-web-e.md#pinverifyresult22) | Yes    | PIN code verification result. Success indicates that the Web component will allow subsequent page operations; failure may cause page navigation or content loading to be blocked. |