# @ohos.app.ability.abilityDelegatorRegistry

AbilityDelegatorRegistry是自动化测试框架使用指南模块，该模块用于获取[AbilityDelegator](application/AbilityDelegator:AbilityDelegator)
和[AbilityDelegatorArgs](application/abilityDelegatorArgs:AbilityDelegatorArgs)对象，其中
[AbilityDelegator](application/AbilityDelegator:AbilityDelegator)对象提供添加用于监视指定ability的生命周期状态更改的
[AbilityMonitor](application/AbilityMonitor:AbilityMonitor)对象的能力，
[AbilityDelegatorArgs](application/abilityDelegatorArgs:AbilityDelegatorArgs)对象提供获取当前测试参数的能力。

> **说明：**
>
> 本模块接口仅可在[单元测试框架](../../../../application-test/unittest-guidelines.md)中使用。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAbilityDelegator](arkts-test-abilitydelegatorregistry-getabilitydelegator-f.md#getAbilityDelegator-1) | 获取应用程序的[AbilityDelegator](application/AbilityDelegator:AbilityDelegator)对象，该对象能够使用调度测试框架的相关功能。<br/> |
| [getArguments](arkts-test-abilitydelegatorregistry-getarguments-f.md#getArguments-1) | 获取单元测试参数[AbilityDelegatorArgs](application/abilityDelegatorArgs:AbilityDelegatorArgs)对象。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AbilityLifecycleState](arkts-test-abilitydelegatorregistry-abilitylifecyclestate-e.md) | Ability生命周期状态，该类型为枚举，可配合[AbilityDelegator](application/AbilityDelegator:AbilityDelegator)的<br/>[getAbilityState(ability)](application/AbilityDelegator:AbilityDelegator.getAbilityState)方法返回不同ability生命周期。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityDelegator](arkts-test-abilitydelegatorregistry-abilitydelegator-t.md) | AbilityDelegator模块。<br/> |
| [AbilityDelegatorArgs](arkts-test-abilitydelegatorregistry-abilitydelegatorargs-t.md) | AbilityDelegatorArgs模块。<br/> |
| [AbilityMonitor](arkts-test-abilitydelegatorregistry-abilitymonitor-t.md) | AbilityMonitor模块。<br/> |
| [AbilityStageMonitor](arkts-test-abilitydelegatorregistry-abilitystagemonitor-t.md) | AbilityStageMonitor模块。<br/> |
| [InteropAbilityMonitor](arkts-test-abilitydelegatorregistry-interopabilitymonitor-t.md) | 提供匹配满足指定条件的监控对象的方法。<br/>最近匹配的Ability对象将保存在InteropAbilityMonitor对象中。<br/> |
| [ShellCmdResult](arkts-test-abilitydelegatorregistry-shellcmdresult-t.md) | ShellCmdResult模块。<br/> |

