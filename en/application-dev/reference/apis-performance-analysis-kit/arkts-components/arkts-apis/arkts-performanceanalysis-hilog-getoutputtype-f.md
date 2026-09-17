# getOutputType

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## getOutputType

```TypeScript
function getOutputType(): OutputType
```

Returns the current output type of hilog.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog

**Return value:**

| Type | Description |
| --- | --- |
| [OutputType](arkts-performanceanalysis-hilog-outputtype-e.md) | current output type for hilog. |

**Examples**

```TypeScript
hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_WITH_CONSOLE);
let last = hilog.getOutputType();
hilog.info(0x0001, "testTag", 'last output type:%{public}d', last);
```

```TypeScript
Log result:

Console output.
```
