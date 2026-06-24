# @ohos.app.ability.AbilityConstant

AbilityConstant提供Ability相关的枚举，包括应用启动原因[LaunchReason](arkts-ability-abilityconstant-launchreason-e.md#LaunchReason)、上次退出原因
[LastExitReason](arkts-ability-abilityconstant-lastexitreason-e.md#LastExitReason)、迁移结果[OnContinueResult](arkts-ability-abilityconstant-oncontinueresult-e.md#OnContinueResult)
等。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [LastExitDetailInfo](arkts-ability-abilityconstant-lastexitdetailinfo-i.md) | 记录Ability所在进程上次退出时的关键运行信息。<br/> |
| [LaunchParam](arkts-ability-abilityconstant-launchparam-i.md) | 启动参数，主要包括Ability启动原因以及上次退出原因。Ability启动时由系统自动传入，开发者无需修改。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CollaborateResult](arkts-ability-abilityconstant-collaborateresult-e.md) | 应用协同状态，该类型为枚举。用于多设备场景下，调用方应用拉起协同方应用时，协同方应用是否接受协同。需要配合UIAbility的<br/>[onCollaborate()](@ohos.app.ability.UIAbility:UIAbility.onCollaborate(wantParam: Record&lt;string, Object&gt;))方法进行<br/>设置。<br/> |
| [ContinueState](arkts-ability-abilityconstant-continuestate-e.md) | 流转状态枚举值。用于表示当前应用任务流转的状态。可配合[UIAbilityContext](arkts-ability-uiabilitycontext-c.md#UIAbilityContext)的<br/>[setMissionContinueState](./application/UIAbilityContext:UIAbilityContext.setMissionContinueState(state: AbilityConstant.ContinueState, callback: AsyncCallback&lt;void&gt;))<br/>方法进行设置。<br/> |
| [LastExitReason](arkts-ability-abilityconstant-lastexitreason-e.md) | Ability上次退出原因，该类型为枚举，可配合UIAbility的[onCreate()](arkts-ability-uiability-c.md#onCreate-1)方法根据<br/>launchParam.lastExitReason的不同类型执行相应操作。<br/> |
| [LaunchReason](arkts-ability-abilityconstant-launchreason-e.md) | Ability启动原因，该类型为枚举，可配合UIAbility的[onCreate(want, launchParam)](arkts-ability-uiability-c.md#onCreate-1)<br/>方法根据launchParam.launchReason的不同类型执行相应操作。<br/> |
| [MemoryLevel](arkts-ability-abilityconstant-memorylevel-e.md) | 整机可用内存级别，该类型为枚举，可配合UIAbility的[onMemoryLevel()](arkts-ability-ability-c.md#onMemoryLevel-1)方法根据level执行不同内<br/>存级别的相应操作。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 不同产品的触发条件可能存在差异。以12G内存的标准设备为例：<br/>&gt; - 当整机可用内存下降至1700MB~1800MB时，会触发取值为0的onMemoryLevel回调，表示当前整机可用内存适中。<br/>&gt; - 当整机可用内存下降至1600MB~1700MB时，会触发取值为1的onMemoryLevel回调，表示当前整机可用内存偏低。<br/>&gt; - 当整机可用内存下降至1600MB以下时，会触发取值为2的onMemoryLevel回调，表示当前整机可用内存很低。<br/>&gt;<br/>&gt; - LRU：表示按应用最近使用顺序排序的链表。通常将最近使用的应用放在链表头部（位置靠前），将最不常用的应用放在链表尾部（位置靠后）。当内存不足时，位置靠后的应用将优先被清理。<br/>&gt;<br/>&gt; - 当LRU发生变化时，后台应用会根据处于应用使用排序链表（LRU）的位置，触发对应MemoryLevel级别(MEMORY_LEVEL_BACKGROUND_MODERATE、<br/>&gt; MEMORY_LEVEL_BACKGROUND_LOW、MEMORY_LEVEL_BACKGROUND_CRITICAL)的onMemoryLevel回调。如果应用被冻结，则会在应用唤醒时收到对应的onMemoryLevel回<br/>&gt; 调，因此不建议在此回调接口中做耗时操作。<br/> |
| [OnContinueResult](arkts-ability-abilityconstant-oncontinueresult-e.md) | Ability迁移结果，该类型为枚举，可配合UIAbility的[onContinue()](arkts-ability-uiability-c.md#onContinue-1)方法完成相应的返回。<br/> |
| [OnSaveResult](arkts-ability-abilityconstant-onsaveresult-e.md) | 保存应用数据的结果，该类型为枚举。配合UIAbility的<br/>[onSaveState()](@ohos.app.ability.UIAbility:UIAbility.onSaveState(reason: AbilityConstant.StateType, wantParam: Record&lt;string, Object&gt;))<br/>方法使用，可以实现[UIAbility备份恢复](../../../../application-models/ability-recover-guideline.md)。<br/> |
| [PrepareTermination](arkts-ability-abilityconstant-preparetermination-e.md) | 应用准备关闭时返回的动作，该类型为枚举。需要配合[AbilityStage](arkts-ability-abilitystage-c.md#AbilityStage)的<br/>[onPrepareTermination](arkts-ability-abilitystage-c.md#onPrepareTermination-1)或者<br/>[onPrepareTerminationAsync](arkts-ability-abilitystage-c.md#onPrepareTerminationAsync-1)方法使用。<br/> |
| [StateType](arkts-ability-abilityconstant-statetype-e.md) | 保存应用数据场景原因，该类型为枚举。配合UIAbility的<br/>[onSaveState()](@ohos.app.ability.UIAbility:UIAbility.onSaveState(reason: AbilityConstant.StateType, wantParam: Record&lt;string, Object&gt;))<br/>方法使用，可以实现[UIAbility备份恢复](../../../../application-models/ability-recover-guideline.md)。<br/> |
| [WindowMode](arkts-ability-abilityconstant-windowmode-e.md) | 启动UIAbility时窗口的创建模式，类型为枚举。可配合<br/>[startAbility](arkts-ability-uiabilitycontext-c.md#startAbility-3)<br/>方法使用。<br/> |
| <!--DelRow-->[WindowMode](arkts-ability-abilityconstant-windowmode-e-sys.md) | 启动UIAbility时窗口的创建模式，类型为枚举。可配合<br/>[startAbility](arkts-ability-uiabilitycontext-c.md#startAbility-3)<br/>方法使用。<br/> |

### 常量

| 名称 | 说明 |
| --- | --- |
| [REASON_MESSAGE_DESKTOP_SHORTCUT](arkts-ability-abilityconstant-con.md#REASON_MESSAGE_DESKTOP_SHORTCUT) | 通过桌面快捷方式启动。开发者如果从[LaunchParam](arkts-ability-abilityconstant-launchparam-i.md#LaunchParam)的launchReasonMessage属性中获取到该字符串，表示UIAbility是通过点击桌面快<br/>捷方式启动的。<br/> |

