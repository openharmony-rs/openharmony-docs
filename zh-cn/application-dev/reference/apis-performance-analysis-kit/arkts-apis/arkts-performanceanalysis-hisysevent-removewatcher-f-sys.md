# removeWatcher（系统接口）

## 导入模块

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## removeWatcher

```TypeScript
function removeWatcher(watcher: Watcher): void
```

取消订阅系统事件，接收[Watcher](arkts-performanceanalysis-hisysevent-watcher-i-sys.md)类型的对象作为事件参数。

**起始版本：** 9

**需要权限：** ohos.permission.READ_DFX_SYSEVENT

<!--Device-hiSysEvent-function removeWatcher(watcher: Watcher): void--><!--Device-hiSysEvent-function removeWatcher(watcher: Watcher): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watcher | [Watcher](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-watcher-i.md) | 是 | 系统事件订阅者对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to read system event forbidden by permission:ohos.permission.READ_DFX_SYSEVENT. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [11200201](../errorcode-hisysevent-sys.md#11200201-事件监听者不存在) | The watcher does not exist. |

**示例：**

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let watchRules: hiSysEvent.WatchRule[] = [{
    domain: "RELIABILITY",
    name: "STACK",
    tag: "STABILITY",
    ruleType: hiSysEvent.RuleType.WHOLE_WORD,
  } as hiSysEvent.WatchRule ];
let watcher: hiSysEvent.Watcher = {
  rules: watchRules,
  onEvent: (info: hiSysEvent.SysEventInfo) => {
    // 处理订阅到的系统事件
  },
  onServiceDied: () => {
    // 处理系统事件服务异常
  }
};
try {
  hiSysEvent.addWatcher(watcher);
  hiSysEvent.removeWatcher(watcher);
} catch (err) {
  // 捕获并打印错误信息
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}

```

