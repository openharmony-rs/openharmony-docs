# addWatcher (System API)

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## addWatcher

```TypeScript
function addWatcher(watcher: Watcher): void
```

Adds a watcher for event subscription.

**Since:** 9

**Required permissions:** ohos.permission.READ_DFX_SYSEVENT

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| watcher | [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md) | Yes | Watcher for event subscription. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to read system event forbidden by permission: ohos.permission.READ_DFX_SYSEVENT. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [11200101](../errorcode-hisysevent-sys.md#11200101-number-of-event-watchers-exceeding-the-limit) | The number of watchers exceeds the limit. |
| [11200102](../errorcode-hisysevent-sys.md#11200102-number-of-event-watcher-rules-exceeding-the-limit) | The number of watch rules exceeds the limit. |

**Examples**

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let watchRules: hiSysEvent.WatchRule[] = [{
    domain: "RELIABILITY",
    name: "STACK",
    tag: "STABILITY",
    ruleType: hiSysEvent.RuleType.WHOLE_WORD,
  } as hiSysEvent.WatchRule];
let watcher: hiSysEvent.Watcher = {
  rules: watchRules,
  onEvent: (info: hiSysEvent.SysEventInfo) => {
    // do something here.
  },
  onServiceDied: () => {
    // do something here.
  }
};
try {
  hiSysEvent.addWatcher(watcher);
} catch (err) {
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```
