# InsightIntentExecutionCallBack

```TypeScript
interface InsightIntentExecutionCallBack
```

意图执行回调。

**起始版本：** 26.1.0

<!--Device-insightIntentProvider-interface InsightIntentExecutionCallBack--><!--Device-insightIntentProvider-interface InsightIntentExecutionCallBack-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## onWillInsightIntentExecuteCallBack

```TypeScript
onWillInsightIntentExecuteCallBack?: OnWillInsightIntentExecuteCallBackFn
```

在意图执行前调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-InsightIntentExecutionCallBack-onWillInsightIntentExecuteCallBack?: OnWillInsightIntentExecuteCallBackFn--><!--Device-InsightIntentExecutionCallBack-onWillInsightIntentExecuteCallBack?: OnWillInsightIntentExecuteCallBackFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
