# clearData

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## clearData

```TypeScript
function clearData(): void
```

应用事件打点数据清理方法，将当前应用存储在本地的打点数据进行清除。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-hiAppEvent-function clearData(): void--><!--Device-hiAppEvent-function clearData(): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**示例：**

```TypeScript
hiAppEvent.clearData();

```

