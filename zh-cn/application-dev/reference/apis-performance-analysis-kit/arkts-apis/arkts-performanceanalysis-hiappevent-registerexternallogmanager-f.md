# registerExternalLogManager

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## registerExternalLogManager

```TypeScript
function registerExternalLogManager(logMngr: ExternalLogManager): void
```

注册外部日志管理者

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-hiAppEvent-function registerExternalLogManager(logMngr: ExternalLogManager): void--><!--Device-hiAppEvent-function registerExternalLogManager(logMngr: ExternalLogManager): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| logMngr | [ExternalLogManager](arkts-performanceanalysis-hiappevent-externallogmanager-c.md) | 是 | 外部日志管理者。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11106001](../errorcode-hiappevent.md#11106001-注册external_log日志管理者失败) | State error. Possible causes: 1. Log manager already registered; |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

// 定义ExternalLogManager实现
let myLogManager: hiAppEvent.ExternalLogManager = {
  onCapacityReached(container: hiAppEvent.ExternalLogContainer): void {
  }
};

// 注册管理者，当external_log目录达到阈值时，回调onCapacityReached
try {
  hiAppEvent.registerExternalLogManager(myLogManager);
  hilog.info(0x0000, 'hiAppEvent', '[App] ExternalLogManager 注册成功');
} catch (e) {
  hilog.info(0x0000, 'hiAppEvent', `[App] 注册失败: ${e.code}, ${e.message}`);
}
```
