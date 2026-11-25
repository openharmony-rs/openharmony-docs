# Class (SslErrorHandler)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:21:12.138Z pushedAt=2026-11-04T11:34:29.789Z nl=1 -->

SslErrorHandler is a class in the Web component for handling SSL certificate verification errors. When an SSL certificate error (such as certificate expiration, hostname mismatch, or untrusted CA) is encountered while loading a secure page, the app can obtain an SslErrorHandler instance through the onSslErrorEvent callback and decide whether to continue loading or cancel navigation. For sample code, see the [onSslErrorEvent](./arkts-basic-components-web-events.md#onsslerrorevent12) event.

> **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This class is supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs a **SslErrorHandler** object.

**System capability**: SystemCapability.Web.Webview.Core

## handleCancel<sup>9+</sup>

handleCancel(): void

Notifies the Web component to cancel this request and stops the current SSL certificate verification process.

**System capability**: SystemCapability.Web.Webview.Core

## handleConfirm<sup>9+</sup>

handleConfirm(): void

Ignores the SSL certificate verification error and continues loading the page.

**System capability**: SystemCapability.Web.Webview.Core

## handleCancel<sup>20+</sup>

handleCancel(abortLoading: boolean): void

Cancels this request and determines whether to stop loading based on the **abortLoading** parameter.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type| Mandatory | Description            |
| --------------- | -------- | ----  |------- |
| abortLoading    | boolean  | Yes    | In the SSL error page scenario, whether to stop page loading after rejecting the invalid certificate; when abortLoading is false, loading is not stopped, and when it is true, loading is stopped. |