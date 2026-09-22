# HttpProtocol

```TypeScript
export enum HttpProtocol
```

Enumerates HTTP protocol versions.

**Since:** 9

**System capability:** SystemCapability.Communication.NetStack

## HTTP1_1

```TypeScript
HTTP1_1 = 0
```

HTTP1.1.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## HTTP2

```TypeScript
HTTP2 = 1
```

HTTP2.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## HTTP3

```TypeScript
HTTP3 = 2
```

HTTP3. If the system or server does not support HTTP3, the HTTP protocol of an earlier version is used.

**Note:**  This parameter takes effect only for HTTPS URLs. If this parameter is set to HTTP, the request will fail.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack
