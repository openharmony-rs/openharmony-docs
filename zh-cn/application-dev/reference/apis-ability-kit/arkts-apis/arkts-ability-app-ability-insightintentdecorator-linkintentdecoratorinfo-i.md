# LinkIntentDecoratorInfo

LinkIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)，用于描述[@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)装饰器支持的参数，例如应用间跳转需要的uri信息。

**继承/实现关系：** LinkIntentDecoratorInfo extends [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)

**起始版本：** 20

<!--Device-unnamed-declare interface LinkIntentDecoratorInfo extends IntentDecoratorInfo--><!--Device-unnamed-declare interface LinkIntentDecoratorInfo extends IntentDecoratorInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentFunction, InsightIntentForm, InsightIntentLink, InsightIntentEntity, LinkParamCategory, InsightIntentPage, InsightIntentEntry, InsightIntentFunctionMethod } from '@kit.AbilityKit';
```

## paramMappings

```TypeScript
paramMappings?: LinkIntentParamMapping[]
```

意图参数和uri信息的映射。

**类型：** LinkIntentParamMapping[]

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LinkIntentDecoratorInfo-paramMappings?: LinkIntentParamMapping[]--><!--Device-LinkIntentDecoratorInfo-paramMappings?: LinkIntentParamMapping[]-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uri

```TypeScript
uri: string
```

表示意图的uri信息。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LinkIntentDecoratorInfo-uri: string--><!--Device-LinkIntentDecoratorInfo-uri: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

