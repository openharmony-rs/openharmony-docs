# Class (SslErrorHandler)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:50:45.106Z pushedAt=2026-08-07T08:12:32.590Z -->

SslErrorHandler is a class in the Web component for handling SSL certificate verification errors. When an SSL certificate error (such as certificate expiration, hostname mismatch, or untrusted CA) is encountered while loading a secure page, the app can obtain an SslErrorHandler instance through the onSslErrorEvent callback and decide whether to continue loading or cancel navigation. For sample code, see the [onSslErrorEvent](./arkts-basic-components-web-events.md#onsslerrorevent12) event.

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
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
| abortLoading    | boolean  | Yes    | Whether to stop loading the page after canceling the request.<br>The value **true** indicates that the page stops loading, and **false** indicates that the page continues loading. |