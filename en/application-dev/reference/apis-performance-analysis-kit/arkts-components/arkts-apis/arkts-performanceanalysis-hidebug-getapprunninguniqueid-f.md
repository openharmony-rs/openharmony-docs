# getAppRunningUniqueId

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getAppRunningUniqueId

```TypeScript
function getAppRunningUniqueId(): string
```

Obtains the running unique identifier of the application.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the running unique ID string. Returns an empty string on failure. |
