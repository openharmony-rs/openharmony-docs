# @ohos.bundle.skillManager

本模块提供技能（Skill）信息的查询能力，支持查询应用自身的技能信息、指定应用的技能信息以及所有应用的技能信息。AI代理框架在规划任务时，可通过本模块查询设备上所有应用可用的技能， 选择合适的技能来完成用户请求。通过技能信息查询，可以实现智能任务调度、能力匹配优化，提升AI代理的任务执行效率，降低开发者的技能集成复杂度。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-declare namespace skillManager--><!--Device-unnamed-declare namespace skillManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAllSkillInfos](arkts-ability-skillmanager-getallskillinfos-f.md#getallskillinfos) | 获取设备上安装应用的所有技能信息。使用Promise异步回调。 |
| [getSkillInfo](arkts-ability-skillmanager-getskillinfo-f.md#getskillinfo) | 获取指定应用中指定模块下指定名称的技能信息。使用Promise异步回调。 |
| [getSkillInfoForSelf](arkts-ability-skillmanager-getskillinfoforself-f.md#getskillinfoforself) | 获取本应用中指定模块下指定名称的技能信息。使用Promise异步回调。 |
| [getSkillInfos](arkts-ability-skillmanager-getskillinfos-f.md#getskillinfos) | 获取指定应用的所有技能信息。使用Promise异步回调。 |
| [getSkillInfosForSelf](arkts-ability-skillmanager-getskillinfosforself-f.md#getskillinfosforself) | 获取本应用的所有技能信息。使用Promise异步回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SkillInfoFlag](arkts-ability-skillmanager-skillinfoflag-e.md) | 技能信息标志，指示需要获取的技能信息的内容。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SkillInfo](arkts-ability-skillmanager-skillinfo-t.md) | 技能配置信息，用于定义AI代理的技能能力。 |
| [SkillType](arkts-ability-skillmanager-skilltype-t.md) | 技能类型的枚举。 |

