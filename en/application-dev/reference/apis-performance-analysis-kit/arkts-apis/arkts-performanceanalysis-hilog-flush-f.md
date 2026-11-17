# flush

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## flush

```TypeScript
function flush(): void
```

Flushes hilog logs in the sandbox to ensure logs are persisted to disk.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-hilog-function flush(): void--><!--Device-hilog-function flush(): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

**Examples**

```TypeScript
hilog.flush();
```
