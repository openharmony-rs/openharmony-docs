# HttpProtocol

```TypeScript
export enum HttpProtocol
```

Enumerates HTTP protocol versions.

**Since:** 9

<!--Device-http-export enum HttpProtocol--><!--Device-http-export enum HttpProtocol-End-->

**System capability:** SystemCapability.Communication.NetStack

## HTTP1_1

```TypeScript
HTTP1_1 = 0
```

HTTP1.1.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HttpProtocol-HTTP1_1 = 0--><!--Device-HttpProtocol-HTTP1_1 = 0-End-->

**System capability:** SystemCapability.Communication.NetStack

## HTTP2

```TypeScript
HTTP2 = 1
```

HTTP2.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HttpProtocol-HTTP2 = 1--><!--Device-HttpProtocol-HTTP2 = 1-End-->

**System capability:** SystemCapability.Communication.NetStack

## HTTP3

```TypeScript
HTTP3 = 2
```

HTTP3. If the system or server does not support HTTP3, the HTTP protocol of an earlier version is used.

**Note:**  This parameter takes effect only for HTTPS URLs. If this parameter is set to HTTP, the request will fail.

**Since:** 11

<!--Device-HttpProtocol-HTTP3 = 2--><!--Device-HttpProtocol-HTTP3 = 2-End-->

**System capability:** SystemCapability.Communication.NetStack
