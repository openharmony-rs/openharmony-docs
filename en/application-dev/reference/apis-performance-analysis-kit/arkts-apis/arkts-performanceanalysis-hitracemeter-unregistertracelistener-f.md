# unregisterTraceListener

## Modules to Import

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## unregisterTraceListener

```TypeScript
function unregisterTraceListener(index: number): number
```

Unregisters the callback function used to notify whether the trace capture is enabled, which is registered using **registerTraceListener()**.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the registered callback function, that is, the return value when [registerTraceListener()](arkts-performanceanalysis-hitracemeter-registertracelistener-f.md) is successfully called. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Callback deregistration status. **0**: Deregistration succeeded. **-1**: The callback corresponding to the index is not registered. **-2**: Invalid index. The index value is not within the range of 0 to 9. |

**Examples**

```TypeScript
// Deregister the callback used to notify whether the application trace capture is enabled. index is the callback index returned by hiTraceMeter.registerTraceListener.
let ret = hiTraceMeter.unregisterTraceListener(index);
if (ret < 0) {
  // Handle exceptions.
}
```
