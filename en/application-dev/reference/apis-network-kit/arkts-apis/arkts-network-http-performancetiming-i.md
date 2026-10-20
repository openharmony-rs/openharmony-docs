# PerformanceTiming

```TypeScript
export interface PerformanceTiming
```

Configures the timing for performance tracing, in ms.

**Since:** 11

<!--Device-http-export interface PerformanceTiming--><!--Device-http-export interface PerformanceTiming-End-->

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

<!--Device-PerformanceTiming-dnsTiming: double--><!--Device-PerformanceTiming-dnsTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## firstReceiveTiming

```TypeScript
firstReceiveTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the first byte is received.

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-firstReceiveTiming: double--><!--Device-PerformanceTiming-firstReceiveTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## firstSendTiming

```TypeScript
firstSendTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the first byte is sent.

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-firstSendTiming: double--><!--Device-PerformanceTiming-firstSendTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## redirectTiming

```TypeScript
redirectTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when all redirection steps are complete.

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-redirectTiming: double--><!--Device-PerformanceTiming-redirectTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## responseBodyTiming

```TypeScript
responseBodyTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the body resolution is complete.

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-responseBodyTiming: double--><!--Device-PerformanceTiming-responseBodyTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## responseHeaderTiming

```TypeScript
responseHeaderTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the header resolution is complete.

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-responseHeaderTiming: double--><!--Device-PerformanceTiming-responseHeaderTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## tcpTiming

```TypeScript
tcpTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the TCP connection is complete.

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-tcpTiming: double--><!--Device-PerformanceTiming-tcpTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## tlsTiming

```TypeScript
tlsTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the TLS connection is complete.

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-tlsTiming: double--><!--Device-PerformanceTiming-tlsTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## totalFinishTiming

```TypeScript
totalFinishTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when the request is complete.

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-totalFinishTiming: double--><!--Device-PerformanceTiming-totalFinishTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## totalTiming

```TypeScript
totalTiming: number
```

Duration from the time when the [request](arkts-network-http-httprequest-i.md#request) is sent to the time when a callback is returned to the application.

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-totalTiming: double--><!--Device-PerformanceTiming-totalTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack
