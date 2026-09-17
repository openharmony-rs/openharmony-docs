# getLogFile

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## getLogFile

```TypeScript
function getLogFile(latestSeconds: number): Array<string>
```

Returns the list of hilog log file paths in the sandbox for the specified recent time period.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| latestSeconds | number | Yes | the specified time period from a given number of seconds in the past to the present. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | list of hilog log file paths in the sandbox for the specified rencent time period, with newer files appearing first in the list. |

**Examples**

```TypeScript
Obtain the files that have been modified within 5 minutes.
```

```TypeScript
Log result:

Sandbox log output.
```
