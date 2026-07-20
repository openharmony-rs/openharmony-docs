# InsightIntentEntryExecutor

本模块提供[@InsightIntentEntry](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententry)装饰器的意图执行基类，必须与@InsightIntentEntry装饰器联合使用。开发者需要在继承该基类的子类中，实现[onExecute()](InsightIntentEntryExecutor.InsightIntentEntryExecutor#onExecute)意图执行回调，并使用@InsightIntentEntry装饰器来装饰子类。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export default class InsightIntentEntryExecutor<T>--><!--Device-unnamed-export default class InsightIntentEntryExecutor<T>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentEntryExecutor } from '@kit.AbilityKit';
```

