# InvokeMode (System API)

```TypeScript
export enum InvokeMode
```

Enumerates the API invoking mode. Indicates how an API call is executed and how its result is delivered.

**Since:** 26.1.0

<!--Device-power-export enum InvokeMode--><!--Device-power-export enum InvokeMode-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

## ASYNC

```TypeScript
ASYNC = 1
```

Asynchronous invocation. The caller returns immediately; the result is delivered via a Promise.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InvokeMode-ASYNC = 1--><!--Device-InvokeMode-ASYNC = 1-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

## SYNC

```TypeScript
SYNC = 0
```

Synchronous invocation. The caller blocks until the API returns the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InvokeMode-SYNC = 0--><!--Device-InvokeMode-SYNC = 0-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.
