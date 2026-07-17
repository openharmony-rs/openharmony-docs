# query（系统接口）

## 导入模块

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## query

```TypeScript
function query(queryArg: QueryArg, rules: QueryRule[], querier: Querier): void
```

查询系统事件。

**起始版本：** 9

**需要权限：** ohos.permission.READ_DFX_SYSEVENT

<!--Device-hiSysEvent-function query(queryArg: QueryArg, rules: QueryRule[], querier: Querier): void--><!--Device-hiSysEvent-function query(queryArg: QueryArg, rules: QueryRule[], querier: Querier): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryArg | [QueryArg](arkts-performanceanalysis-hisysevent-queryarg-i-sys.md) | 是 | 查询需要配置的查询参数。 |
| rules | [QueryRule](arkts-performanceanalysis-hisysevent-queryrule-i-sys.md)[] | 是 | 查询规则数组，每次查询可配置多个查询规则。 |
| querier | [Querier](arkts-performanceanalysis-hisysevent-querier-i-sys.md) | 是 | 查询者对象，包含查询结果及结束的相关回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to read system event forbidden by permission:ohos.permission.READ_DFX_SYSEVENT. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [11200301](../errorcode-hisysevent-sys.md#11200301-查询规则的数量超过限制) | The number of query rules exceeds the limit. |
| [11200302](../errorcode-hisysevent-sys.md#11200302-非法的查询规则) | Invalid query rule. |
| [11200303](../errorcode-hisysevent-sys.md#11200303-并发查询的数量超过限制) | The number of concurrent queriers exceeds the limit. |
| [11200304](../errorcode-hisysevent-sys.md#11200304-查询频率超过限制) | The query frequency exceeds the limit. |

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
    // 处理事件写入成功后的操作
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
      // 处理查询到的系统事件infos
    },
    onComplete: (reason: number, total: number) => {
      // 处理结束查询
    }
  };
  hiSysEvent.query(queryArg, queryRules, querier);
} catch (err) {
  // 捕获并打印错误信息
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}

```

