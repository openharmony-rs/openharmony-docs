# getAbilityDelegator

## 导入模块

```TypeScript
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## getAbilityDelegator

```TypeScript
function getAbilityDelegator(): AbilityDelegator
```

获取应用程序的[AbilityDelegator](application/AbilityDelegator:AbilityDelegator)对象，该对象能够使用调度测试框架的相关功能。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-abilityDelegatorRegistry-function getAbilityDelegator(): AbilityDelegator--><!--Device-abilityDelegatorRegistry-function getAbilityDelegator(): AbilityDelegator-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbilityDelegator](arkts-test-abilitydelegatorregistry-abilitydelegator-t.md) | [AbilityDelegator](application/AbilityDelegator:AbilityDelegator)对象。可以用来调度测试框架相关功能。 |

**示例：**

```TypeScript
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { Want } from '@kit.AbilityKit';

// 获取应用程序的AbilityDelegator对象
let abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
// 构造Want参数，指定目标Ability
let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility'
};

// 启动指定Ability
abilityDelegator.startAbility(want, (err) => {
  if (err) {
    console.error(`Failed start ability, error: ${JSON.stringify(err)}`);
  } else {
    console.info('Success start ability.');
  }
});

```

