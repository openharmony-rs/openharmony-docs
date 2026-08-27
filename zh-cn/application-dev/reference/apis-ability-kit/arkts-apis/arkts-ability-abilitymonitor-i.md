# AbilityMonitor

本模块提供监听指定[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)生命周期状态变化的能力。开发者可以将AbilityMonitor作为 [abilityDelegator.addAbilityMonitor](arkts-ability-abilitydelegator-i.md#addabilitymonitor) 的入参来注册监听。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityBackground

```TypeScript
onAbilityBackground?: (ability: UIAbility) => void
```

UIAbility对象状态变成后台时，触发该回调函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | 是 |  |

## onAbilityCreate

```TypeScript
onAbilityCreate?: (ability: UIAbility) => void
```

UIAbility对象被创建时，触发该回调函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | 是 |  |

## onAbilityDestroy

```TypeScript
onAbilityDestroy?: (ability: UIAbility) => void
```

UIAbility对象被销毁前，触发该回调函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | 是 |  |

## onAbilityForeground

```TypeScript
onAbilityForeground?: (ability: UIAbility) => void
```

UIAbility对象状态变成前台时，触发该回调函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | 是 |  |

## onWindowStageCreate

```TypeScript
onWindowStageCreate?: (ability: UIAbility) => void
```

当WindowStage实例被创建时，触发该回调函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | 是 |  |

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy?: (ability: UIAbility) => void
```

当WindowStage被销毁前，触发该回调函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | 是 |  |

## onWindowStageRestore

```TypeScript
onWindowStageRestore?: (ability: UIAbility) => void
```

当UIAbility跨端迁移时，目标端UIAbility恢复页面栈时，触发该回调函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | 是 |  |

## abilityName

```TypeScript
abilityName: string
```

被监听的UIAbility对象名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName?: string
```

被监听的UIAbility对象所属模块名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

```TypeScript
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function onAbilityCreateCallback(data: UIAbility) {
  console.info(`onAbilityCreateCallback, data: ${JSON.stringify(data)}`);
}

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityname',
  moduleName: 'moduleName',
  onAbilityCreate: onAbilityCreateCallback
}

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.addAbilityMonitor(monitor, (error: BusinessError) => {
  if (error) {
    console.error(`Failed to add ability monitor. Code: ${error.code}, message: ${error.message}`);
  }
});
```
