# TraceEventListener

```TypeScript
type TraceEventListener = (traceStatus: boolean) => void
```

Defines a callback to listen for whether the trace capture is enabled.

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-hiTraceMeter-type TraceEventListener = (traceStatus: boolean) => void--><!--Device-hiTraceMeter-type TraceEventListener = (traceStatus: boolean) => void-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| traceStatus | boolean | Yes | Whether the trace capture is enabled for the current application. The value **true** indicates that the trace capture is enabled, and **false** indicates the opposite. |
