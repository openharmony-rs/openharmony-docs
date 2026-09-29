# SecureDnsMode

```TypeScript
enum SecureDnsMode
```

Enumerates the modes in which the **Web** component uses HTTPDNS.

**Since:** 10

<!--Device-webview-enum SecureDnsMode--><!--Device-webview-enum SecureDnsMode-End-->

**System capability:** SystemCapability.Web.Webview.Core

## OFF

```TypeScript
OFF = 0
```

HTTPDNS is not used. It can be used to revoke the previously used HTTPDNS configuration.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SecureDnsMode-OFF = 0--><!--Device-SecureDnsMode-OFF = 0-End-->

**System capability:** SystemCapability.Web.Webview.Core

## AUTO

```TypeScript
AUTO = 1
```

HTTPDNS is used in automatic mode. If the specified HTTPDNS server is unavailable for resolution, the component falls back to the system DNS server.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SecureDnsMode-AUTO = 1--><!--Device-SecureDnsMode-AUTO = 1-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SECURE_ONLY

```TypeScript
SECURE_ONLY = 2
```

The specified HTTPDNS server is forcibly used for DNS resolution.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SecureDnsMode-SECURE_ONLY = 2--><!--Device-SecureDnsMode-SECURE_ONLY = 2-End-->

**System capability:** SystemCapability.Web.Webview.Core
