# InteractionInfo（系统接口）

定义当前意图执行完成后返回的交互信息，包括下一个要触发的意图和要显示的交互界面。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## interactionUI

```TypeScript
interactionUI?: InteractionUI
```

当前意图执行完成后需要展示的交互界面信息。

**类型：** [InteractionUI](arkts-ability-insightintent-interactionui-i-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
