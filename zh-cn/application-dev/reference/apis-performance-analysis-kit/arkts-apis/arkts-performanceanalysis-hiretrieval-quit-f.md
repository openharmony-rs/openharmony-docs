# quit

## 导入模块

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## quit

```TypeScript
function quit(): void
```

设置此设备退出应用灰度活动，退出后此设备将无法在云端被圈选。

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-hiRetrieval-function quit(): void--><!--Device-hiRetrieval-function quit(): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 36000001 | Initialization error. Possibly caused by invoking this function before invoking init function. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';

try {
  // 初始化应用灰度模块
  hiRetrieval.init();
  // 设置设备退出应用灰度活动
  hiRetrieval.quit();
} catch (err) {
  // 捕获并打印错误信息
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```
