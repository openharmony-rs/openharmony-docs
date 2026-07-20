# @ohos.app.ability.AbilityStage

## 导入模块

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md) | AbilityStage是一个[Module](docroot://quick-start/application-package-overview.md#应用的多module设计机制)级别的组件管理器，用于进行Module级别的资源预加载、线程创建等初始化操作，以及维护Module下的应用状态。AbilityStage与Module一一对应，即一个Module拥有一个AbilityStage。  应用的[HAP](docroot://quick-start/hap-package.md)/[HSP](docroot://quick-start/in-app-hsp.md)在首次加载时会创建一个AbilityStage实例。当一个Module中存在AbilityStage和其他组件（UIAbility/ExtensionAbility组件），AbilityStage实例会早于其他组件实例创建。  AbilityStage拥有[onCreate()](arkts-ability-app-ability-abilitystage-abilitystage-c.md#oncreate-1)、[onDestroy()](arkts-ability-app-ability-abilitystage-abilitystage-c.md#ondestroy-1)生命周期回调和[onAcceptWant()](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onacceptwant-1)、[onConfigurationUpdate()](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onconfigurationupdate-1)、[onMemoryLevel()](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onmemorylevel-1)事件回调等。 |

