# SslErrorHandler

```TypeScript
declare class SslErrorHandler
```

SslErrorHandler is a class in the Web component for handling SSL certificate verification errors. When an SSL certificate error (such as certificate expiration, hostname mismatch, or untrusted CA) is encountered while loading a secure page, the app can obtain an SslErrorHandler instance through the onSslErrorEvent callback and decide whether to continue loading or cancel navigation. For sample code, see the [onSslErrorEvent](arkts-arkweb-web-comp-attribute.md#onsslerrorevent) event.

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **SslErrorHandler** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(): void
```

Notifies the Web component to cancel this request and stops the current SSL certificate verification process.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

<a id="handlecancel-1"></a>

## handleCancel

```TypeScript
handleCancel(abortLoading: boolean): void
```

Cancels this request and determines whether to stop loading based on the **abortLoading** parameter.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abortLoading | boolean | Yes | Whether to stop loading the page after canceling the request.<br>The value **true** indicates that the page stops loading, and **false** indicates that the page continues loading. |

## handleConfirm

```TypeScript
handleConfirm(): void
```

Ignores the SSL certificate verification error and continues loading the page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
