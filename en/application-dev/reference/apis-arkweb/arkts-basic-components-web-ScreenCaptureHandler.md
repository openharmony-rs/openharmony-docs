# Class (ScreenCaptureHandler)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @qq_42700029-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=15a7b43c23e3cb1ccde062079f37bedc40d4c072 translatedAt=2026-10-21T03:06:15.892Z pushedAt=2026-10-21T10:25:56.315Z -->

**ScreenCaptureHandler** is the screen capture permission handling class provided by the **Web** component, used to respond to screen capture requests initiated by web pages. This class is applicable to application scenarios that require access to the user's screen content, such as online education, remote meetings, and screen sharing. It allows developers to control whether to grant screen capture permission to a web page through the **grant** or **deny** method, and to obtain the request origin information through the **getOrigin** method. This helps developers flexibly handle web page screen capture access requirements while protecting user privacy, thereby improving application security and user experience. For details about the sample code, see the [onScreenCaptureRequest](./arkts-basic-components-web-events.md#onscreencapturerequest10) event.

> **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This class is supported since API version 10.
>
> - The sample effect is subject to the actual running on a real device.
>
> - The [grant](./arkts-basic-components-web-ScreenCaptureHandler.md#grant10)() and [deny](./arkts-basic-components-web-ScreenCaptureHandler.md#deny10)() methods are mutually exclusive. For the same request on the same **ScreenCaptureHandler** instance, only one of them can be called.
>
> - After calling one method, do not call the other method for the same request.

## constructor<sup>10+</sup>

constructor()

Constructs a **ScreenCaptureHandler** object.

**System capability**: SystemCapability.Web.Webview.Core

## deny<sup>10+</sup>

deny(): void

Denies the screen capture operation initiated by a web page. This method is called when the user chooses not to allow screen capture, or when screen capture needs to be blocked for security reasons. After being called, the current screen capture request is terminated, and the system notifies the web page that the screen capture permission has been denied. The denial does not affect subsequent new screen capture requests.

**System capability**: SystemCapability.Web.Webview.Core

## getOrigin<sup>10+</sup>

getOrigin(): string

Obtains the web page origin. Used to validate the origin of the web page initiating the request, allowing developers to control which web pages are permitted to initiate screen capture requests via an origin allowlist.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description          |
| ------ | ------------ |
| string | Origin of the web page that currently initiates the screen capture request. |

## grant<sup>10+</sup>

grant(config: ScreenCaptureConfig): void

Grants permission for the screen capture operation accessed by a web page. This method grants screen capture permission based on the provided configuration parameters. After the permission is granted, the web page can perform screen capture according to the configured parameters. The configuration parameters are validated to ensure compliance with system security requirements. This method is called after the user agrees to the screen capture request from a web page, or when automatically granting permission to trusted web pages based on business policies.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type                                    | Mandatory  | Description   |
| ------ | ---------------------------------------- | ---- | ------- |
| config | [ScreenCaptureConfig](./arkts-basic-components-web-i.md#screencaptureconfig10) | Yes | Screen capture configuration, used to set the related parameters for screen capture. |