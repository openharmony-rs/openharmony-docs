# LinkIntentInfo（系统接口）

LinkIntentInfo用于描述 @InsightIntentLink 装饰器支持的参数，例如应用间跳转需要的uri信息。

**起始版本：** 23

<!--Device-insightIntentDriver-interface LinkIntentInfo--><!--Device-insightIntentDriver-interface LinkIntentInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## uri

```TypeScript
readonly uri: string
```

表示意图的uri信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinkIntentInfo-readonly uri: string--><!--Device-LinkIntentInfo-readonly uri: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

