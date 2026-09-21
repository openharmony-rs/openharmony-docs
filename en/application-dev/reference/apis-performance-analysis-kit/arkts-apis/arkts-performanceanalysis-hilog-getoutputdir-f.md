# getOutputDir

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## getOutputDir

```TypeScript
function getOutputDir(): string
```

Returns the directory path of hilog logs in the sandbox. If the output type of hilog is DEFAULT, an empty string is returned.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog

**Return value:**

| Type | Description |
| --- | --- |
| string | the directory path of hilog logs in the sandbox. |

**Examples**

```TypeScript
hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_WITH_CONSOLE);
let dir = hilog.getOutputDir();
hilog.info(0x0001, "testTag", 'sandbox output dir:%{public}s', dir);
```

Log result:

Console output.

```TypeScript
05-15 16:57:04.238  40518-40518  A00001/testTag  com.example.hilogDemo  I  sandbox output dir:/data/storage/el2/log/hiapplog/
```
