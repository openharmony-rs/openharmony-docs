# configEventPolicy

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## configEventPolicy

```TypeScript
function configEventPolicy(policy: EventPolicy): Promise<void>
```

Sets a system event configuration policy. This API uses a promise to return the result.

In the same lifecycle, you can set system event configuration by policy.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [EventPolicy](arkts-performanceanalysis-hiappevent-eventpolicy-i.md) | Yes | System event configuration policy. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. <br>For details about the event configuration policy, see [EventPolicy](arkts-performanceanalysis-hiappevent-eventpolicy-i.md). If the configuration policy is incorrect, the API returns a failure message. <br>- If the parameter type is incorrect, error code 401 is returned. <br>- If the parameter specifications are incorrect, the error information is output in HiLog logs. |

**Examples**

```TypeScript
The following example shows how to configure a policy for the MAIN_THREAD_JANK event:
```
