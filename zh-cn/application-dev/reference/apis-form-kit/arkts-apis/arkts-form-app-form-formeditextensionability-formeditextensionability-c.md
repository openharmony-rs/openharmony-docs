# FormEditExtensionAbility

```TypeScript
declare class FormEditExtensionAbility extends UIExtensionAbility
```

提供卡片编辑功能，继承此类并实现生命周期方法后，可实现卡片编辑界面，用于在用户长按卡片等场景下触发卡片编辑。

**继承/实现关系：** FormEditExtensionAbility extends [UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)

**起始版本：** 18

<!--Device-unnamed-declare class FormEditExtensionAbility extends UIExtensionAbility--><!--Device-unnamed-declare class FormEditExtensionAbility extends UIExtensionAbility-End-->

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

<!--Device-FormEditExtensionAbility-context: FormEditExtensionContext--><!--Device-FormEditExtensionAbility-context: FormEditExtensionContext-End-->

**系统能力：** SystemCapability.Ability.Form
