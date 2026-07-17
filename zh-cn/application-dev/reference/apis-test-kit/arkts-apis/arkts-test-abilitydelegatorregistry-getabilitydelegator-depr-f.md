# getAbilityDelegator

## getAbilityDelegator

```TypeScript
function getAbilityDelegator(): AbilityDelegator
```

获取应用程序的AbilityDelegator对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAbilityDelegator](arkts-test-abilitydelegatorregistry-getabilitydelegator-f.md#getabilitydelegator-1)

<!--Device-abilityDelegatorRegistry-function getAbilityDelegator(): AbilityDelegator--><!--Device-abilityDelegatorRegistry-function getAbilityDelegator(): AbilityDelegator-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbilityDelegator](arkts-test-abilitydelegatorregistry-abilitydelegator-t.md) | [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md)对象。可以用来调度测试框架相关功能。 |

**示例：**

```TypeScript
import AbilityDelegatorRegistry from '@ohos.application.abilityDelegatorRegistry';

let abilityDelegator = AbilityDelegatorRegistry.getAbilityDelegator();

```

