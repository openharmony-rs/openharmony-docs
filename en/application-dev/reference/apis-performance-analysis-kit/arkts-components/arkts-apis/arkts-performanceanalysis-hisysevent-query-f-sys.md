# query (System API)

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## query

```TypeScript
function query(queryArg: QueryArg, rules: QueryRule[], querier: Querier): void
```

Queries system events.

**Since:** 9

**Required permissions:** ohos.permission.READ_DFX_SYSEVENT

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| queryArg | [QueryArg](arkts-performanceanalysis-hisysevent-queryarg-i-sys.md) | Yes | Arguments for event query. |
| rules | [QueryRule](arkts-performanceanalysis-hisysevent-queryrule-i-sys.md)[] | Yes | Array of event query rules. |
| querier | [Querier](arkts-performanceanalysis-hisysevent-querier-i-sys.md) | Yes | Event query instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to read system event forbidden by permission: ohos.permission.READ_DFX_SYSEVENT. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [11200301](../errorcode-hisysevent-sys.md#11200301-number-of-query-rules-exceeding-the-limit) | The number of query rules exceeds the limit. |
| [11200302](../errorcode-hisysevent-sys.md#11200302-invalid-query-rule) | Invalid query rule. |
| [11200303](../errorcode-hisysevent-sys.md#11200303-number-of-concurrent-queries-exceeding-the-limit) | The number of concurrent queriers exceeds the limit. |
| [11200304](../errorcode-hisysevent-sys.md#11200304-query-frequency-exceeding-the-limit) | The query frequency exceeds the limit. |

**Examples**

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let customizedParams: Record<string, string | number> = {
    'PID': 487,
    'UID': 103,
    'PACKAGE_NAME': "com.ohos.hisysevent.test",
    'PROCESS_NAME': "syseventservice",
    'MSG': "no msg."
  };
  let eventInfo: hiSysEvent.SysEventInfo = {
    domain: "RELIABILITY",
    name: "STACK",
    eventType: hiSysEvent.EventType.FAULT,
    params: customizedParams
  };
  hiSysEvent.write(eventInfo, (err: BusinessError) => {
    // do something here.
  });

  let queryArg: hiSysEvent.QueryArg = {
    beginTime: -1,
    endTime: -1,
    maxEvents: 5,
  };
  let queryRules: hiSysEvent.QueryRule[] = [{
    domain: "RELIABILITY",
    names: ["STACK"],
    condition: '{"version":"V1","condition":{"and":[{"param":"PID","op":"=","value":487},{"param":"PROCESS_NAME","op":"=","value":"syseventservice"}]}}'
  } as hiSysEvent.QueryRule];
  let querier: hiSysEvent.Querier = {
    onQuery: (infos: hiSysEvent.SysEventInfo[]) => {
      // do something here.
    },
    onComplete: (reason: number, total: number) => {
      // do something here.
    }
  };
  hiSysEvent.query(queryArg, queryRules, querier);
} catch (err) {
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```
