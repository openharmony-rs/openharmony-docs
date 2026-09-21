# ExternalLogWrapper

```TypeScript
class ExternalLogWrapper
```

The wrapper of external log, providing various information.

**Since:** 26.0.1

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## getFilePath

```TypeScript
getFilePath(): string
```

Get the file path

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Return value:**

| Type | Description |
| --- | --- |
| string | The file path |

## getGenerationTime

```TypeScript
getGenerationTime(): number
```

Get the generation time point (ms) of the file

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Return value:**

| Type | Description |
| --- | --- |
| number | The generation time |

## getSizeInKb

```TypeScript
getSizeInKb(): number
```

Get the file size in kb

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Return value:**

| Type | Description |
| --- | --- |
| number | The file size in kb |

## getSysEvent

```TypeScript
getSysEvent(): string
```

Get the system event of the file

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Return value:**

| Type | Description |
| --- | --- |
| string | The string form of system event |
