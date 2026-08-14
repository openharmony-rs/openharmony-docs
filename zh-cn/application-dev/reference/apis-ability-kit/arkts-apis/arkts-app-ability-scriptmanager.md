# @ohos.app.ability.scriptManager

本模块提供管理和组织脚本信息的能力，支持应用的ArkTS脚本执行结果上报。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace scriptManager--><!--Device-unnamed-declare namespace scriptManager-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [completeArkTSScriptInApp](arkts-ability-scriptmanager-completearktsscriptinapp-f.md#completeArkTSScriptInApp) | 完成应用的ArkTS脚本执行，上报执行结果。使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArkTSScriptInfo](arkts-ability-scriptmanager-arktsscriptinfo-i.md) | 应用的ArkTS脚本入口函数的第一个参数，用于接收系统传递的脚本上下文信息。 |
| [ExecuteResult](arkts-ability-scriptmanager-executeresult-i.md) | ArkTS脚本执行结果。 |

