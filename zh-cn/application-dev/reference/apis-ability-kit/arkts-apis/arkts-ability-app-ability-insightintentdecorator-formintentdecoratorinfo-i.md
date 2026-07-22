# FormIntentDecoratorInfo

FormIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)，用于描述[@InsightIntentForm](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)装饰器支持的参数。

**继承/实现关系：** FormIntentDecoratorInfo extends [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)

**起始版本：** 20

<!--Device-unnamed-declare interface FormIntentDecoratorInfo extends IntentDecoratorInfo--><!--Device-unnamed-declare interface FormIntentDecoratorInfo extends IntentDecoratorInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentFunction, InsightIntentForm, InsightIntentLink, InsightIntentEntity, LinkParamCategory, InsightIntentPage, InsightIntentEntry, InsightIntentFunctionMethod } from '@kit.AbilityKit';
```

## formName

```TypeScript
formName: string
```

表示FormExtensionAbility绑定的卡片名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FormIntentDecoratorInfo-formName: string--><!--Device-FormIntentDecoratorInfo-formName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

