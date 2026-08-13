# @ohos.application.abilityDelegatorRegistry

AbilityDelegatorRegistry模块提供用于存储已注册的[AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md#AbilityDelegator)和 [AbilityDelegatorArgs](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegatorargs-abilitydelegatorargs-i.md#AbilityDelegatorArgs)对象的全局寄存器的能力，包括获取应用程序的 AbilityDelegator对象、获取单元测试参数AbilityDelegatorArgs对象。该模块中的接口只能用于测试框架中。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [abilityDelegatorRegistry](arkts-app-ability-abilitydelegatorregistry.md#@ohos.app.ability.abilityDelegatorRegistry)

<!--Device-unnamed-declare namespace abilityDelegatorRegistry--><!--Device-unnamed-declare namespace abilityDelegatorRegistry-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAbilityDelegator](arkts-test-abilitydelegatorregistry-getabilitydelegator-depr-f.md#getAbilityDelegator) | 获取应用程序的AbilityDelegator对象。 |
| [getArguments](arkts-test-abilitydelegatorregistry-getarguments-depr-f.md#getArguments) | 获取单元测试参数AbilityDelegatorArgs对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AbilityLifecycleState](arkts-test-abilitydelegatorregistry-abilitylifecyclestate-depr-e.md) | Ability生命周期状态。 |

