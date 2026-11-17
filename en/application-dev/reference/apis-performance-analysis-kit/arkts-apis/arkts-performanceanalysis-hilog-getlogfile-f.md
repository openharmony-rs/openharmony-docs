# getLogFile

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## getLogFile

```TypeScript
function getLogFile(latestSeconds: number): Array<string>
```

Returns hilog sandbox log files that have been modified within the specified number of seconds.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-hilog-function getLogFile(latestSeconds: int): Array<string>--><!--Device-hilog-function getLogFile(latestSeconds: int): Array<string>-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| latestSeconds | number | Yes | The time interval from now, in seconds. <br>If the value is less than 0, it is invalid and the return value is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of sandbox files that have been written within the specified time period. |

**Examples**

Obtain the files that have been modified within 5 minutes.

```TypeScript
hilog.info(0x0001, "testTag", 'sandbox log to share sandbox with console');
hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_WITH_CONSOLE);
let timeInterval = 300
let logs = hilog.getLogFile(timeInterval);
hilog.info(0x0001, "testTag", 'sandbox log files:%{public}s', logs.toString());
hilog.flush();
```

Log result:

Sandbox log output.

```TypeScript
05-15 16:57:04.238 40518 40518 I A00001/testTag: sandbox log files:hiapplog.40518.001.20260515-165602.log
```
