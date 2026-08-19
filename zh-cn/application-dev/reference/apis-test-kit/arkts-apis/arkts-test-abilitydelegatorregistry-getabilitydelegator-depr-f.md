# getAbilityDelegator

## 导入模块

```TypeScript
```

## getAbilityDelegator

```TypeScript
function getAbilityDelegator(): AbilityDelegator
```

获取应用程序的AbilityDelegator对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAbilityDelegator](arkts-test-abilitydelegatorregistry-getabilitydelegator-f.md)

<!--Device-abilityDelegatorRegistry-function getAbilityDelegator(): AbilityDelegator--><!--Device-abilityDelegatorRegistry-function getAbilityDelegator(): AbilityDelegator-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md) | [AbilityDelegator]{ |

**示例**

```TypeScript
import AbilityDelegatorRegistry from '@ohos.application.abilityDelegatorRegistry';

let abilityDelegator = AbilityDelegatorRegistry.getAbilityDelegator();
```

