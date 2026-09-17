# PerformanceTiming

Configures the timing for performance tracing, in ms.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## dnsTiming

```TypeScript
dnsTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the DNS resolution is complete.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## firstReceiveTiming

```TypeScript
firstReceiveTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the first byte is received.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## firstSendTiming

```TypeScript
firstSendTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the first byte is sent.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## redirectTiming

```TypeScript
redirectTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when all redirection steps are complete.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## responseBodyTiming

```TypeScript
responseBodyTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the body resolution is complete.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## responseHeaderTiming

```TypeScript
responseHeaderTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the header resolution is complete.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## tcpTiming

```TypeScript
tcpTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the TCP connection is complete.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## tlsTiming

```TypeScript
tlsTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the TLS connection is complete.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## totalFinishTiming

```TypeScript
totalFinishTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the request is complete.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## totalTiming

```TypeScript
totalTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when a callback is returned to the application.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack
