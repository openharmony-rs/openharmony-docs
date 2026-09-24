# setOutputType

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## setOutputType

```TypeScript
function setOutputType(type: OutputType): OutputType
```

Sets the output type of hilog.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [OutputType](arkts-performanceanalysis-hilog-outputtype-e.md) | Yes | output type of hilog. |

**Return value:**

| Type | Description |
| --- | --- |
| [OutputType](arkts-performanceanalysis-hilog-outputtype-e.md) | previous output type of hilog. |

**Examples**

```TypeScript
hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_ONLY);
hilog.info(0x0001, "testTag", 'sandbox log to share sandbox only');
hilog.flush();
```

Log result:

Sandbox log output.

```TypeScript
05-15 16:57:04.238 40518 40518 I A00001/testTag: sandbox log to share sandbox only
```
