# Class (VerifyPinHandler)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

Defines the PIN verification handler object returned by the **Web** component. For details about the sample code, see [onVerifyPin](./arkts-basic-components-web-events.md#onverifypin22).

> **NOTE**
>
> - This component is supported since API version 22. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 22.
>
> - The sample effect is subject to the actual device.

## constructor<sup>22+</sup>

constructor()

A constructor used to create a **VerifyPinHandler** instance.

**System capability**: SystemCapability.Web.Webview.Core

## confirm<sup>22+</sup>

confirm(result: PinVerifyResult): void

Notifies the **Web** component of the PIN verification result.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type  | Mandatory  | Description   |
| ------- | ------ | ---- | ------- |
| result | [PinVerifyResult](./arkts-basic-components-web-e.md#pinverifyresult22) | Yes   | PIN verification result.|
