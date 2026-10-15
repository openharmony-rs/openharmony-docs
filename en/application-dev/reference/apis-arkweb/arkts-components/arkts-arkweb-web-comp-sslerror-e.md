# SslError

```TypeScript
declare enum SslError
```

Enumerates the error codes returned by **onSslErrorEventReceive** API.

**Since:** 9

<!--Device-unnamed-declare enum SslError--><!--Device-unnamed-declare enum SslError-End-->

**System capability:** SystemCapability.Web.Webview.Core

## DateInvalid

```TypeScript
DateInvalid = 2
```

The certificate has an invalid date.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SslError-DateInvalid = 2--><!--Device-SslError-DateInvalid = 2-End-->

**System capability:** SystemCapability.Web.Webview.Core

## HostMismatch

```TypeScript
HostMismatch = 1
```

The host name does not match.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SslError-HostMismatch = 1--><!--Device-SslError-HostMismatch = 1-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Invalid

```TypeScript
Invalid = 0
```

Minor error.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SslError-Invalid = 0--><!--Device-SslError-Invalid = 0-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Untrusted

```TypeScript
Untrusted = 3
```

The certificate issuer is not trusted.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SslError-Untrusted = 3--><!--Device-SslError-Untrusted = 3-End-->

**System capability:** SystemCapability.Web.Webview.Core
