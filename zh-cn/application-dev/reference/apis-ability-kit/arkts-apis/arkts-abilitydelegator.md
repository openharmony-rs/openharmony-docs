# AbilityDelegator

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AbilityDelegator](arkts-ability-abilitydelegator-i.md) | AbilityDelegator模块可以通过[AbilityMonitor](arkts-ability-abilitymonitor-i.md#AbilityMonitor)实例来监听和管理<br/>[UIAbility](arkts-app-ability-uiability.md)生命周期的变化。例如获取UIAbility当前状态（如是否已创建/是否在前台等）、查询当前获焦的UIAbility、等待UIAbility进入<br/>某个生命周期节点（如等待UIAbility进入onForeground）、启动指定UIAbility、设置超时机制等功能。<br/>AbilityDelegator可以通过<br/>[getAbilityDelegator](../../apis-test-kit/arkts-apis/arkts-test-abilitydelegatorregistry-getabilitydelegator-f.md#getAbilityDelegator-1)方<br/>法获取。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 本模块接口仅可在[单元测试框架](../../../../application-test/unittest-guidelines.md)中使用。<br/> |

