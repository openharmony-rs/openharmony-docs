# FormIntentInfo（系统接口）

FormIntentInfo用于描述[@InsightIntentForm](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)装饰器支持的参数，例如卡片名称。同时，该接口也可用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的卡片信息。

**起始版本：** 20

<!--Device-insightIntentDriver-interface FormIntentInfo--><!--Device-insightIntentDriver-interface FormIntentInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## abilityName

```TypeScript
readonly abilityName: string
```

Ability名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormIntentInfo-readonly abilityName: string--><!--Device-FormIntentInfo-readonly abilityName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## formName

```TypeScript
readonly formName: string
```

表示[FormExtensionAbility](@ohos.app.form.FormExtensionAbility)绑定的卡片名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormIntentInfo-readonly formName: string--><!--Device-FormIntentInfo-readonly formName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

