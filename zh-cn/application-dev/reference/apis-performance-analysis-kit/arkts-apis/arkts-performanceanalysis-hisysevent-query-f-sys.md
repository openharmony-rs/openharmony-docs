# query（系统接口）

## query

```TypeScript
function query(queryArg: QueryArg, rules: QueryRule[], querier: Querier): void
```

查询系统事件。

**起始版本：** 9

**需要权限：** ohos.permission.READ_DFX_SYSEVENT

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryArg | QueryArg | 是 | 查询需要配置的查询参数。 |
| rules | QueryRule[] | 是 | 查询规则数组，每次查询可配置多个查询规则。 |
| querier | Querier | 是 | 查询者对象，包含查询结果及结束的相关回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. An attempt was made to read system event forbidden by permission:<br/>ohos.permission.READ_DFX_SYSEVENT. |
| [202](../../errorcode-universal.md#202-System) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [11200301](../../errorcode-universal.md#11200301-The) | The number of query rules exceeds the limit. |
| [11200302](../../errorcode-universal.md#11200302-Invalid) | Invalid query rule. |
| [11200303](../../errorcode-universal.md#11200303-The) | The number of concurrent queriers exceeds the limit. |
| [11200304](../../errorcode-universal.md#11200304-The) | The query frequency exceeds the limit. |

**示例：**

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

