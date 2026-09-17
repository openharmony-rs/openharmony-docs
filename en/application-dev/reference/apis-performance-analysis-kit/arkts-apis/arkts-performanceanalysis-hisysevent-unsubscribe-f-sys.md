# unsubscribe (System API)

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## unsubscribe

```TypeScript
function unsubscribe(): void
```

Unsubscribes from system events.

**Since:** 10

**Required permissions:** ohos.permission.READ_DFX_SYSEVENT

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to read system event forbidden by permission: ohos.permission.READ_DFX_SYSEVENT. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [11200305](../errorcode-hisysevent-sys.md#11200305-unsubscription-failed) | Unsubscription failed. |

**Examples**

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let rules: hiSysEvent.QueryRule[] = [{
    domain: "RELIABILITY",
    names: ["STACK"],
  } as hiSysEvent.QueryRule,
  {
    domain: "BUNDLE_MANAGER",
    names: ["BUNDLE_UNINSTALL"],
  } as hiSysEvent.QueryRule];
  hiSysEvent.subscribe(rules);
  hiSysEvent.unsubscribe();
} catch (err) {
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```
