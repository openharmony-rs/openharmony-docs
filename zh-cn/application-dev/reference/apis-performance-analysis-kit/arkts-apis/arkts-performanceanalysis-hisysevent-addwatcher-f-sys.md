# addWatcher（系统接口）

## addWatcher

```TypeScript
function addWatcher(watcher: Watcher): void
```

订阅系统事件，接收[Watcher](arkts-performanceanalysis-hisysevent-watcher-i-sys.md#Watcher)类型的对象作为事件参数。

**起始版本：** 9

**需要权限：** ohos.permission.READ_DFX_SYSEVENT

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watcher | Watcher | 是 | 系统事件订阅者对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. An attempt was made to read system event forbidden by permission:<br/>ohos.permission.READ_DFX_SYSEVENT. |
| [202](../../errorcode-universal.md#202-System) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [11200101](../../errorcode-universal.md#11200101-The) | The number of watchers exceeds the limit. |
| [11200102](../../errorcode-universal.md#11200102-The) | The number of watch rules exceeds the limit. |

**示例：**

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

