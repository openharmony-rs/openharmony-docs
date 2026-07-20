# @ohos.app.ability.UIExtensionAbility

## 导入模块

```TypeScript
import { UIExtensionAbility } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) | UIExtensionAbility组件是带界面的ExtensionAbility组件，继承自[ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)，提供了组件创建、销毁、前后台切换等基础生命周期。和UIAbility组件不同，UIExtensionAbility组件不会作为单独的任务在任务视图中体现。UIExtensionAbility组件被宿主窗口启动，该组件的前后台切换状态、以及是否可见均跟随宿主窗口。开发者不可以直接继承UIExtensionAbility组件，但可以根据实际业务场景选择使用继承自UIExtensionAbility组件的其他组件。例如，开发者处理其他应用分享的数据时，可以使用[ShareExtensionAbility组件](arkts-ability-app-ability-shareextensionability-shareextensionability-c.md)；开发者提供卡片编辑功能时，可以使用[FormEditExtensionAbility组件](./@ohos.app.form.FormEditExtensionAbility:FormEditExtensionAbility)。各类Ability组件的继承关系详见[继承关系说明](docroot://reference/apis-ability-kit/js-apis-app-ability-ability.md#ability的继承关系说明)。 |

