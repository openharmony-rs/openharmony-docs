# @ohos.InputMethodExtensionAbility

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [InputMethodExtensionAbility](arkts-ime-inputmethodextensionability-c.md) | **@ohos.InputMethodExtensionAbility**模块提供输入法ExtensionAbility的基础类定义，是开发输入法应用的入口和生命周期管理框架。本模块是输入法ExtensionAbility的核心类模块，定义了`InputMethodExtensionAbility`类，作为输入法应用的Extension基类。开发者需继承该类并实现`onCreate`和`onDestroy`生命周期回调，系统在拉起和销毁输入法Extension时自动调用这些回调。本模块提供两大核心能力：1）通过`onCreate(want)`回调实现输入法应用的初始化——系统拉起输入法Extension时调用，开发者在此完成资源加载、面板创建等初始化工作；2）通过`onDestroy()`回调实现输入法应用的资源清理——系统销毁输入法Extension时调用，开发者在此释放资源。此外，通过`context`属性提供`InputMethodExtensionContext`上下文对象，供开发者在生命周期内执行销毁自身、拉起其他应用等上下文级操作。当开发输入法应用时必须使用本模块。开发者通过继承`InputMethodExtensionAbility` → 在module.json5中配置ExtensionAbility信息 → 系统拉起时触发`onCreate`（初始化） →系统销毁或开发者主动调用`context.destroy()`时触发`onDestroy`（清理）。 |

