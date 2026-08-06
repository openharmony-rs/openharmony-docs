# @ohos.app.ability.abilityDelegatorRegistry

AbilityDelegatorRegistry是自动化测试框架使用指南模块，该模块用于获取[AbilityDelegator]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 和[AbilityDelegatorArgs]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_对象，其中 [AbilityDelegator]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_对象提供添加用于监视指定ability的生命周期状态更改的 [AbilityMonitor]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_对象的能力， [AbilityDelegatorArgs]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_对象提供获取当前测试参数的能力。 > **说明：** > > 本模块接口仅可在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中使用。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace abilityDelegatorRegistry--><!--Device-unnamed-declare namespace abilityDelegatorRegistry-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAbilityDelegator](arkts-test-abilitydelegatorregistry-getabilitydelegator-f.md#getabilitydelegator) | 获取应用程序的[AbilityDelegator]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_对象，该对象能够使用调度测试框架的相关功能。 |
| [getArguments](arkts-test-abilitydelegatorregistry-getarguments-f.md#getarguments) | 获取单元测试参数[AbilityDelegatorArgs]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AbilityLifecycleState](arkts-test-abilitydelegatorregistry-abilitylifecyclestate-e.md) | Ability生命周期状态，该类型为枚举，可配合[AbilityDelegator]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的 [getAbilityState(ability)]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法返回不同ability生命周期。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityDelegator](arkts-test-abilitydelegatorregistry-abilitydelegator-t.md) | AbilityDelegator模块。 |
| [AbilityDelegatorArgs](arkts-test-abilitydelegatorregistry-abilitydelegatorargs-t.md) | AbilityDelegatorArgs模块。 |
| [AbilityMonitor](arkts-test-abilitydelegatorregistry-abilitymonitor-t.md) | AbilityMonitor模块。 |
| [AbilityStageMonitor](arkts-test-abilitydelegatorregistry-abilitystagemonitor-t.md) | AbilityStageMonitor模块。 |
| [InteropAbilityMonitor](arkts-test-abilitydelegatorregistry-interopabilitymonitor-t.md) | 提供匹配满足指定条件的监控对象的方法。 最近匹配的Ability对象将保存在InteropAbilityMonitor对象中。 |
| [ShellCmdResult](arkts-test-abilitydelegatorregistry-shellcmdresult-t.md) | ShellCmdResult模块。 |

