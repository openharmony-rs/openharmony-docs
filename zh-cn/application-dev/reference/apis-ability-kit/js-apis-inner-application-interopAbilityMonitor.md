# InteropAbilityMonitor

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

本模块提供监听指定[UIAbility](js-apis-app-ability-uiAbility.md)生命周期状态变化的能力。开发者可以将InteropAbilityMonitor作为abilityDelegator.[addInteropAbilityMonitorSync](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#addinteropabilitymonitorsync)的入参来注册监听。

**起始版本**：26.0.0

> **说明：**
> 
> 本模块同时支持ArkTS-Dyn，ArkTS-Sta。

## 导入模块

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## 使用说明

可以作为abilityDelegator中的[addInteropAbilityMonitorSync](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#addinteropabilitymonitorsync)的入参来监听指定UIAbility的生命周期变化。

## InteropAbilityMonitor

**原子化服务API(仅ArkTS-Dyn)**：从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

| 名称                                                         | 类型     | 只读 | 可选 | 说明                                                         |
| ------------------------------------------------------------ | -------- | ---- | ---- | ------------------------------------------------------------ |
| abilityName                                                  | string   | 否   | 否   |  被监听的UIAbility对象名称。 |
| moduleName                                                  | string   | 否   | 是   | 被监听的UIAbility对象所属模块名称。 |
| onAbilityCreate | ArkTS-Dyn:(ability: object) => void<br>ArkTS-Sta:(ability: Any) => void | 否   | 是   | UIAbility对象被创建时，触发该回调函数。 |
| onAbilityForeground | ArkTS-Dyn:(ability: object) => void<br>ArkTS-Sta:(ability: Any) => void | 否   | 是   | UIAbility对象状态变成前台时，触发该回调函数。 |
| onAbilityBackground | ArkTS-Dyn:(ability: object) => void<br>ArkTS-Sta:(ability: Any) => void | 否   | 是   | UIAbility对象状态变成后台时，触发该回调函数。 |
| onAbilityDestroy | ArkTS-Dyn:(ability: object) => void<br>ArkTS-Sta:(ability: Any) => void | 否   | 是   | UIAbility对象被销毁前，触发该回调函数。 |
| onWindowStageCreate | ArkTS-Dyn:(ability: object) => void<br>ArkTS-Sta:(ability: Any) => void | 否   | 是   | 当WindowStage实例被创建时，触发该回调函数。 |
| onWindowStageRestore | ArkTS-Dyn:(ability: object) => void<br>ArkTS-Sta:(ability: Any) => void | 否   | 是   | 当UIAbility跨端迁移时，目标端UIAbility恢复页面栈时，触发该回调函数。 |
| onWindowStageDestroy | ArkTS-Dyn:(ability: object) => void<br>ArkTS-Sta:(ability: Any) => void | 否   | 是   | 当WindowStage被销毁前，触发该回调函数。 |

**示例：**

> **说明：**
>
> 需要先启动[单元测试框架](../../application-test/unittest-guidelines.md)。

**ArkTS-Dyn：**
```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

function onAbilityCreateCallback(data: object) {
  console.info(`onAbilityCreateCallback success`);
}

let monitor: abilityDelegatorRegistry.InteropAbilityMonitor = {
  abilityName: 'abilityname',
  onAbilityCreate: onAbilityCreateCallback
};

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.addInteropAbilityMonitorSync(monitor);
```

**ArkTS-Sta：**
```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

function onAbilityCreateCallback(data: Any) {
  console.info(`onAbilityCreateCallback success`);
}

let monitor: abilityDelegatorRegistry.InteropAbilityMonitor = {
  abilityName: 'abilityname',
  onAbilityCreate: onAbilityCreateCallback
};

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.addInteropAbilityMonitorSync(monitor);
```