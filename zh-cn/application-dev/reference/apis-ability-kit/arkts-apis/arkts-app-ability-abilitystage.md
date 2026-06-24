# @ohos.app.ability.AbilityStage

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AbilityStage](arkts-ability-abilitystage-c.md) | AbilityStage是一个[Module](../../../../quick-start/application-package-overview.md#应用的多module设计机制)级别的组件管理器，用于进行Module级别的资源<br/>预加载、线程创建等初始化操作，以及维护Module下的应用状态。AbilityStage与Module一一对应，即一个Module拥有一个AbilityStage。<br/><br/>应用的[HAP](../../../../quick-start/hap-package.md)/[HSP](../../../../quick-start/in-app-hsp.md)在首次加载时会创建一个AbilityStage实例。当一<br/>个Module中存在AbilityStage和其他组件（UIAbility/ExtensionAbility组件），AbilityStage实例会早于其他组件实例创建。<br/><br/>AbilityStage拥有[onCreate()](arkts-ability-abilitystage-c.md#onCreate-1)、[onDestroy()](arkts-ability-abilitystage-c.md#onDestroy-1)生命周期回调和<br/>[onAcceptWant()](arkts-ability-abilitystage-c.md#onAcceptWant-1)、[onConfigurationUpdate()](arkts-ability-abilitystage-c.md#onConfigurationUpdate-1)<br/>、[onMemoryLevel()](arkts-ability-abilitystage-c.md#onMemoryLevel-1)事件回调等。<br/> |

