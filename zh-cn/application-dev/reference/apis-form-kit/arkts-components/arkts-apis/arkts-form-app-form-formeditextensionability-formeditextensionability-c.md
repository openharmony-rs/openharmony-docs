# FormEditExtensionAbility

FormEditExtensionAbility模块提供卡片编辑功能，支持用户在卡片提供方应用内编辑卡片内容，适用于需要动态更新卡片展示信息、实现卡片个性化配置的场景。继承自[UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。

**继承/实现关系：** FormEditExtensionAbility extends [UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)

**起始版本：** 18

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { FormEditExtensionAbility } from '@kit.FormKit';
```

## context

```TypeScript
context: FormEditExtensionContext
```

FormEditExtensionAbility的上下文环境，FormEditExtensionContext继承自UIExtensionContext。提供拉起编辑页面的能力。

**类型：** [FormEditExtensionContext](arkts-form-formeditextensioncontext-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form
