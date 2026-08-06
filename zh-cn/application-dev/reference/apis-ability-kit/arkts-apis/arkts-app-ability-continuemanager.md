# @ohos.app.ability.continueManager

continueManager提供了应用跨端迁移的管理能力，如获取应用跨端迁移过程中快速拉起目标应用的结果。 > 本模块接口仅可在Stage模型下使用。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace continueManager--><!--Device-unnamed-declare namespace continueManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off](arkts-ability-continuemanager-off-f.md#off) | 在应用快速拉起时，注销回调函数，不再获取快速拉起结果。使用callback异步回调。 |
| [offPrepareContinue](arkts-ability-continuemanager-offpreparecontinue-f.md#offpreparecontinue) | Unregister prepareContinue event. |
| [on](arkts-ability-continuemanager-on-f.md#on) | 在应用快速拉起时，注册回调函数以获取快速拉起结果。使用callback异步回调。 |
| [onPrepareContinue](arkts-ability-continuemanager-onpreparecontinue-f.md#onpreparecontinue) | prepareContinue 事件，当在 continueType 中配置了“ContinueQuickStart”功能时，即可获取 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ContinueResultInfo](arkts-ability-continuemanager-continueresultinfo-i.md) | 注册或注销回调函数返回的快速拉起的结果。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ContinueStateCode](arkts-ability-continuemanager-continuestatecode-e.md) | 快速拉起的结果状态码的枚举值。 |

