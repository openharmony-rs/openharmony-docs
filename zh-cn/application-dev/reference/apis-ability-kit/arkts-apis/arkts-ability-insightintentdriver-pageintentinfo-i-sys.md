# PageIntentInfo（系统接口）

```TypeScript
interface PageIntentInfo
```

PageIntentInfo用于描述[@InsightIntentPage](arkts-ability-app-ability-insightintentdecorator-insightintentpage-d.md#insightintentpage)装饰器支持的参数，例如目标页面的[NavDestination](../../apis-arkui/arkts-components/arkts-arkui-navdestination-comp.md)名称。

**起始版本：** 20

<!--Device-insightIntentDriver-interface PageIntentInfo--><!--Device-insightIntentDriver-interface PageIntentInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## navDestinationName

```TypeScript
readonly navDestinationName: string
```

表示与意图绑定[NavDestination组件](../../apis-arkui/arkts-components/arkts-arkui-navdestination-comp.md)的名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageIntentInfo-readonly navDestinationName: string--><!--Device-PageIntentInfo-readonly navDestinationName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## navigationId

```TypeScript
readonly navigationId: string
```

表示与意图绑定Navigation的id。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageIntentInfo-readonly navigationId: string--><!--Device-PageIntentInfo-readonly navigationId: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## pagePath

```TypeScript
readonly pagePath: string
```

页面名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageIntentInfo-readonly pagePath: string--><!--Device-PageIntentInfo-readonly pagePath: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## uiAbility

```TypeScript
readonly uiAbility: string
```

UIAbility组件名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageIntentInfo-readonly uiAbility: string--><!--Device-PageIntentInfo-readonly uiAbility: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
