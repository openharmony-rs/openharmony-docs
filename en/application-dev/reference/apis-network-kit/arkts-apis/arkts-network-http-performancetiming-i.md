# PerformanceTiming

```TypeScript
export interface PerformanceTiming
```

Defines the performance timing (unit: ms).

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

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) to DNS resolution completion. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-dnsTiming: double--><!--Device-PerformanceTiming-dnsTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## firstReceiveTiming

```TypeScript
firstReceiveTiming: number
```

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) to receiving the first byte. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-firstReceiveTiming: double--><!--Device-PerformanceTiming-firstReceiveTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## firstSendTiming

```TypeScript
firstSendTiming: number
```

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) to the start of sending the first byte. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-firstSendTiming: double--><!--Device-PerformanceTiming-firstSendTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## redirectTiming

```TypeScript
redirectTiming: number
```

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) to completion of all redirect steps. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-redirectTiming: double--><!--Device-PerformanceTiming-redirectTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## responseBodyTiming

```TypeScript
responseBodyTiming: number
```

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) to body parsing completion. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-responseBodyTiming: double--><!--Device-PerformanceTiming-responseBodyTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## responseHeaderTiming

```TypeScript
responseHeaderTiming: number
```

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) to header parsing completion. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-responseHeaderTiming: double--><!--Device-PerformanceTiming-responseHeaderTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## tcpTiming

```TypeScript
tcpTiming: number
```

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) to TCP connection completion. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-tcpTiming: double--><!--Device-PerformanceTiming-tcpTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## tlsTiming

```TypeScript
tlsTiming: number
```

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) to TLS connection completion. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-tlsTiming: double--><!--Device-PerformanceTiming-tlsTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## totalFinishTiming

```TypeScript
totalFinishTiming: number
```

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) to request completion. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-totalFinishTiming: double--><!--Device-PerformanceTiming-totalFinishTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack

## totalTiming

```TypeScript
totalTiming: number
```

Time elapsed from [request](arkts-network-http-httprequest-i.md#request-1) callback to the application. Unit: millisecond (ms).

**Type:** number

**Since:** 11

<!--Device-PerformanceTiming-totalTiming: double--><!--Device-PerformanceTiming-totalTiming: double-End-->

**System capability:** SystemCapability.Communication.NetStack
