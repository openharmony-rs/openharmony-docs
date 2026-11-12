# run

## 导入模块

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## run

```TypeScript
function run(): void
```

若此设备正在参与应用灰度活动（即已调用participate接口且未调用quit接口），则应用灰度模块开始工作，否则调用该接口不会产生任何效果。

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-hiRetrieval-function run(): void--><!--Device-hiRetrieval-function run(): void-End-->

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
  // 开始运行应用灰度模块
  hiRetrieval.run();
} catch (err) {
  // 捕获并打印错误信息
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```
