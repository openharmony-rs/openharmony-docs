# init

## 导入模块

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## init

```TypeScript
function init(): void
```

初始化应用灰度模块。

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-hiRetrieval-function init(): void--><!--Device-hiRetrieval-function init(): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';

try {
  // 初始化应用灰度模块
  hiRetrieval.init();
} catch (err) {
  // 捕获并打印错误信息
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
// 后续可以完成其他的灰度接口调用
```
