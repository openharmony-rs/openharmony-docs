# IntentDecoratorInfo（系统接口）

```TypeScript
declare interface IntentDecoratorInfo
```

意图装饰器的通用属性，用于定义意图的基本信息（包括意图名称、意图版本号）。适用于本模块的所有装饰器。

> **说明：** 
> 
> 如果根据schema与intentVersion字段，在标准意图列表存在匹配的标准意图，系统会将intentName、domain、llmDescription、keywords、parameters、result字段均设置为标准
> 意图的相应字段值。

**起始版本：** 20

<!--Device-unnamed-declare interface IntentDecoratorInfo--><!--Device-unnamed-declare interface IntentDecoratorInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## exported

```TypeScript
exported?: boolean
```

表示该意图是否可被三方应用调用。取值为true表示该意图可被三方应用调用，取值为false表示该意图不可被三方应用调用。默认值：false。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IntentDecoratorInfo-exported?: boolean--><!--Device-IntentDecoratorInfo-exported?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
