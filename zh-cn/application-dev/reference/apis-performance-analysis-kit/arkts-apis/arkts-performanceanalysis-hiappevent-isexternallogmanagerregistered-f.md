# isExternalLogManagerRegistered

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## isExternalLogManagerRegistered

```TypeScript
function isExternalLogManagerRegistered(): boolean
```

查询外部日志管理者是否已注册

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-hiAppEvent-function isExternalLogManagerRegistered(): boolean--><!--Device-hiAppEvent-function isExternalLogManagerRegistered(): boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果已经注册，则返回true，否则返回false。 |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

// 检查是否已注册
let registered: boolean = hiAppEvent.isExternalLogManagerRegistered();
hilog.info(0x0000, 'hiAppEvent', `[App] 已注册: ${registered}`);
```
