# @ohos.InputMethodExtensionContext

## 导入模块

```TypeScript
import { InputMethodExtensionContext } from '@kit.IMEKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [InputMethodExtensionContext](arkts-ime-inputmethodextensioncontext-c.md) | **@ohos.InputMethodExtensionContext**模块是InputMethodExtensionAbility的上下文环境，继承于ExtensionContext，为输入法扩展能力提供上下文级别的操作接口。本模块是输入法ExtensionAbility的上下文类，继承自`ExtensionContext`，作为`InputMethodExtensionAbility`实例的`context`属性提供。它承载了输入法扩展应用在其生命周期内可使用的上下文能力，包括销毁自身和拉起其他应用。本模块提供两大核心能力：1）通过`destroy()`销毁输入法ExtensionAbility自身，实现输入法应用的生命周期终止；2）通过`startAbility()`拉起目标应用，使输入法应用能够启动其他Ability进行交互，拓展输入法功能的灵活性和可扩展性。当开发输入法ExtensionAbility并需要在其生命周期内执行上下文级操作时使用本模块。典型场景包括：输入法应用在`onDestroy`回调中主动销毁自身、输入法应用需要拉起设置页面或其他辅助应用等。模块内的核心API按功能分为两类：1. **生命周期管理**：`destroy()`用于销毁输入法ExtensionAbility自身，终止输入法应用运行。2. **Ability交互**：`startAbility()`用于从输入法应用拉起目标Ability（如设置页面等），拓展输入法应用与其他应用的交互能力。典型使用流程：在`InputMethodExtensionAbility`的`onCreate`回调中获取`this.context` → 在需要终止输入法时调用`context.destroy()` → 在需要拉起其他应用时调用`context.startAbility(want)`。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InputMethodExtensionContext](arkts-ime-inputmethodextensioncontext-c-sys.md) | **@ohos.InputMethodExtensionContext**模块是InputMethodExtensionAbility的上下文环境，继承于ExtensionContext，为输入法扩展能力提供上下文级别的操作接口。本模块是输入法ExtensionAbility的上下文类，继承自`ExtensionContext`，作为`InputMethodExtensionAbility`实例的`context`属性提供。它承载了输入法扩展应用在其生命周期内可使用的上下文能力，包括销毁自身和拉起其他应用。本模块提供两大核心能力：1）通过`destroy()`销毁输入法ExtensionAbility自身，实现输入法应用的生命周期终止；2）通过`startAbility()`拉起目标应用，使输入法应用能够启动其他Ability进行交互，拓展输入法功能的灵活性和可扩展性。当开发输入法ExtensionAbility并需要在其生命周期内执行上下文级操作时使用本模块。典型场景包括：输入法应用在`onDestroy`回调中主动销毁自身、输入法应用需要拉起设置页面或其他辅助应用等。模块内的核心API按功能分为两类：1. **生命周期管理**：`destroy()`用于销毁输入法ExtensionAbility自身，终止输入法应用运行。2. **Ability交互**：`startAbility()`用于从输入法应用拉起目标Ability（如设置页面等），拓展输入法应用与其他应用的交互能力。典型使用流程：在`InputMethodExtensionAbility`的`onCreate`回调中获取`this.context` → 在需要终止输入法时调用`context.destroy()` → 在需要拉起其他应用时调用`context.startAbility(want)`。 |
<!--DelEnd-->

