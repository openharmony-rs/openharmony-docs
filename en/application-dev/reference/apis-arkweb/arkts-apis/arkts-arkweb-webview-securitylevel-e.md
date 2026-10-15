# SecurityLevel

```TypeScript
enum SecurityLevel
```

Enumerates the security levels of the web page.

**Since:** 11

<!--Device-webview-enum SecurityLevel--><!--Device-webview-enum SecurityLevel-End-->

**System capability:** SystemCapability.Web.Webview.Core

## DANGEROUS

```TypeScript
DANGEROUS = 3
```

The web page is dangerous. This means that the page may have attempted to load HTTPS scripts to no avail, have failed authentication, or contain insecure active content in HTTPS, malware, phishing, or any other sources of major threats.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SecurityLevel-DANGEROUS = 3--><!--Device-SecurityLevel-DANGEROUS = 3-End-->

**System capability:** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

The web page is neither absolutely secure nor insecure, that is, neutral. A typical example is a web page whose URL scheme is not HTTP or HTTPS.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SecurityLevel-NONE = 0--><!--Device-SecurityLevel-NONE = 0-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SECURE

```TypeScript
SECURE = 1
```

The web page is secure, using the HTTPS protocol and a trusted certificate.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SecurityLevel-SECURE = 1--><!--Device-SecurityLevel-SECURE = 1-End-->

**System capability:** SystemCapability.Web.Webview.Core

## WARNING

```TypeScript
WARNING = 2
```

The web page is insecure. A typical example is a web page that uses the HTTP or HTTPS protocol but an outdated TLS version.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SecurityLevel-WARNING = 2--><!--Device-SecurityLevel-WARNING = 2-End-->

**System capability:** SystemCapability.Web.Webview.Core
