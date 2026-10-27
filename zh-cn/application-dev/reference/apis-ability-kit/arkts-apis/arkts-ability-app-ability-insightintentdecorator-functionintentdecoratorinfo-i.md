# FunctionIntentDecoratorInfo

```TypeScript
declare interface FunctionIntentDecoratorInfo extends IntentDecoratorInfo
```

[@InsightIntentFunctionMethod](arkts-ability-app-ability-insightintentdecorator-insightintentfunctionmethod-d.md#insightintentfunctionmethod)装饰器的参数类型，当前全部属性均继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)。

**继承/实现关系：** FunctionIntentDecoratorInfo extends [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)

**起始版本：** 20

<!--Device-unnamed-declare interface FunctionIntentDecoratorInfo extends IntentDecoratorInfo--><!--Device-unnamed-declare interface FunctionIntentDecoratorInfo extends IntentDecoratorInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## permissions

```TypeScript
permissions?: string[]
```

调用该意图所需的权限列表，为可选字段。该字段仅用于调用方查询或参考。系统不会自动校验这些权限。权限校验必须由意图提供方（服务端）实现。

**类型：** string[]

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-FunctionIntentDecoratorInfo-permissions?: string[]--><!--Device-FunctionIntentDecoratorInfo-permissions?: string[]-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
