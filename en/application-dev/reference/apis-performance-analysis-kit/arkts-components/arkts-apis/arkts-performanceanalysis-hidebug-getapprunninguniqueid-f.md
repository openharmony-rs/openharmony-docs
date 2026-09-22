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

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the running unique ID string. Returns an empty string on failure. |
