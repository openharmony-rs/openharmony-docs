# PageIntentDecoratorInfo

PageIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)，用于描述@InsightIntentPage装饰器支持的参数，例如目标页面的NavDestination名称。

**继承/实现关系：** PageIntentDecoratorInfo extends [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)

**起始版本：** 20

<!--Device-unnamed-declare interface PageIntentDecoratorInfo extends IntentDecoratorInfo--><!--Device-unnamed-declare interface PageIntentDecoratorInfo extends IntentDecoratorInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentFunction, InsightIntentForm, InsightIntentLink, InsightIntentEntity, LinkParamCategory, InsightIntentPage, InsightIntentEntry, InsightIntentFunctionMethod } from '@kit.AbilityKit';
```

## navDestinationName

```TypeScript
navDestinationName?: string
```

表示与意图绑定NavDestination组件的名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PageIntentDecoratorInfo-navDestinationName?: string--><!--Device-PageIntentDecoratorInfo-navDestinationName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## navigationId

```TypeScript
navigationId?: string
```

表示与意图绑定的Navigation组件的id属性。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PageIntentDecoratorInfo-navigationId?: string--><!--Device-PageIntentDecoratorInfo-navigationId?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pagePath

```TypeScript
pagePath: string
```

表示与意图绑定的页面路径，该页面需要是一个实际存在的文件。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PageIntentDecoratorInfo-pagePath: string--><!--Device-PageIntentDecoratorInfo-pagePath: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uiAbility

```TypeScript
uiAbility?: string
```

表示与意图绑定的UIAbility名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PageIntentDecoratorInfo-uiAbility?: string--><!--Device-PageIntentDecoratorInfo-uiAbility?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

