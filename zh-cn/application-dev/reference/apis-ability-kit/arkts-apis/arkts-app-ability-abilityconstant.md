# @ohos.app.ability.AbilityConstant

AbilityConstant提供Ability相关的枚举，包括应用启动原因[LaunchReason](arkts-ability-abilityconstant-launchreason-e.md)、上次退出原因[LastExitReason](arkts-ability-abilityconstant-lastexitreason-e.md)、迁移结果[OnContinueResult](arkts-ability-abilityconstant-oncontinueresult-e.md)等。

**起始版本：** 9

<!--Device-unnamed-declare namespace AbilityConstant--><!--Device-unnamed-declare namespace AbilityConstant-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { AbilityConstant } from '@kit.AbilityKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [LastExitDetailInfo](arkts-ability-abilityconstant-lastexitdetailinfo-i.md) | 记录Ability所在进程上次退出时的关键运行信息。 |
| [LaunchParam](arkts-ability-abilityconstant-launchparam-i.md) | 启动参数，主要包括Ability启动原因以及上次退出原因。Ability启动时由系统自动传入，开发者无需修改。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CollaborateResult](arkts-ability-abilityconstant-collaborateresult-e.md) | 应用协同状态，该类型为枚举。用于多设备场景下，调用方应用拉起协同方应用时，协同方应用是否接受协同。需要配合UIAbility的[onCollaborate()](arkts-ability-app-ability-uiability-uiability-c.md#oncollaborate-1)方法进行设置。 |
| [ContinueState](arkts-ability-abilityconstant-continuestate-e.md) | 流转状态枚举值。用于表示当前应用任务流转的状态。可配合[UIAbilityContext](arkts-ability-uiabilitycontext-c.md)的[setMissionContinueState](arkts-ability-uiabilitycontext-c.md#setmissioncontinuestate-1)方法进行设置。 |
| [LastExitReason](arkts-ability-abilityconstant-lastexitreason-e.md) | Ability上次退出原因，该类型为枚举，可配合UIAbility的[onCreate()](arkts-ability-app-ability-uiability-uiability-c.md#oncreate-1)方法根据launchParam.lastExitReason的不同类型执行相应操作。 |
| [LaunchReason](arkts-ability-abilityconstant-launchreason-e.md) | Ability启动原因，该类型为枚举，可配合UIAbility的[onCreate(want, launchParam)](arkts-ability-app-ability-uiability-uiability-c.md#oncreate-1)方法根据launchParam.launchReason的不同类型执行相应操作。 |
| [MemoryLevel](arkts-ability-abilityconstant-memorylevel-e.md) | 整机可用内存级别，该类型为枚举，可配合UIAbility的[onMemoryLevel()](arkts-ability-app-ability-ability-ability-c.md#onmemorylevel-1)方法根据level执行不同内存级别的相应操作。 |
| [OnContinueResult](arkts-ability-abilityconstant-oncontinueresult-e.md) | Ability迁移结果，该类型为枚举，可配合UIAbility的[onContinue()](arkts-ability-app-ability-uiability-uiability-c.md#oncontinue-1)方法完成相应的返回。 |
| [OnSaveResult](arkts-ability-abilityconstant-onsaveresult-e.md) | 保存应用数据的结果，该类型为枚举。配合UIAbility的[onSaveState()](arkts-ability-app-ability-uiability-uiability-c.md#onsavestate-1)方法使用，可以实现[UIAbility备份恢复](../../../../application-models/ability-recover-guideline.md)。 |
| [PrepareTermination](arkts-ability-abilityconstant-preparetermination-e.md) | 应用准备关闭时返回的动作，该类型为枚举。需要配合[AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md)的[onPrepareTermination](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onpreparetermination-1)或者[onPrepareTerminationAsync](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onprepareterminationasync-1)方法使用。 |
| [StateType](arkts-ability-abilityconstant-statetype-e.md) | 保存应用数据场景原因，该类型为枚举。配合UIAbility的[onSaveState()](arkts-ability-app-ability-uiability-uiability-c.md#onsavestate-1)方法使用，可以实现[UIAbility备份恢复](../../../../application-models/ability-recover-guideline.md)。 |
| [WindowMode](arkts-ability-abilityconstant-windowmode-e.md) | 启动UIAbility时窗口的创建模式，类型为枚举。可配合[startAbility](arkts-ability-uiabilitycontext-c.md#startability-3)方法使用。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [WindowMode](arkts-ability-abilityconstant-windowmode-e-sys.md) | 启动UIAbility时窗口的创建模式，类型为枚举。可配合[startAbility](arkts-ability-uiabilitycontext-c.md#startability-3)方法使用。 |
<!--DelEnd-->

### 常量

| 名称 | 说明 |
| --- | --- |
| [REASON_MESSAGE_DESKTOP_SHORTCUT](arkts-ability-abilityconstant-con.md#reason_message_desktop_shortcut) | 通过桌面快捷方式启动。开发者如果从[LaunchParam](arkts-ability-abilityconstant-launchparam-i.md)的launchReasonMessage属性中获取到该字符串，表示UIAbility是通过点击桌面快捷方式启动的。 |

