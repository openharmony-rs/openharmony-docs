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

**Model restriction:** This API can be used in both the stage model and FA model.

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

Log result:

Console output.

```TypeScript
05-15 16:57:04.238  40518-40518  A00001/testTag  com.example.hilogDemo  I  last output type:4
```
