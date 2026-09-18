# registerTraceListener

## Modules to Import

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## registerTraceListener

```TypeScript
function registerTraceListener(callback: TraceEventListener): number
```

Registers a callback to notify whether the application trace capture is enabled. This API uses an asynchronous callback to return the result.

After the registration is successful, the callback is executed immediately. Subsequent callbacks are executed when the application trace capture status changes.

Callbacks are stored in the application process. A maximum of 10 callbacks can be registered in a process.

> **NOTE:** 
> 
> If the callback contains time-consuming operations, the registration or deregistration will be blocked (waiting
> for the callback execution to complete) when the callback is executed.
> 
> Therefore, you are advised not to register or deregister callbacks containing time-consuming operations in the
> main thread of the application to avoid application freeze.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [TraceEventListener](arkts-performanceanalysis-hitracemeter-traceeventlistener-t.md) | Yes | Registered callback. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Callback registration status. &gt;= 0: The registration is successful. The callback index for deregistration is returned. The index ranges from 0 to 9. **-1**: The maximum number of callbacks has been reached. **-2**: Invalid parameter. The parameter is not of the **TraceEventListener** type. |

**Examples**

```TypeScript
// Define the registered callback.
let callback: hiTraceMeter.TraceEventListener = (traceStatus: boolean) => {
  if (traceStatus) {
    // Trace capture is enabled for the current application.
    // ...
  } else {
    // Trace capture is disabled for the current application.
    // ...
  }
};

// Register a callback to notify whether the application trace capture is enabled.
let index = hiTraceMeter.registerTraceListener(callback);
if (index < 0) {
  // Handle exceptions.
}
```
