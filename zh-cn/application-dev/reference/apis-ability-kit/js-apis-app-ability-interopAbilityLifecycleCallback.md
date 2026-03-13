# @ohos.app.ability.InteropAbilityLifecycleCallback (UIAbility生命周期回调互操作监听器)

InteropAbilityLifecycleCallback模块提供应用中不同ArkTS环境下的[UIAbility](js-apis-app-ability-uiAbility.md)的生命周期发生变化时触发相应回调的能力。与[AbilityLifecycleCallback](js-apis-app-ability-abilityLifecycleCallback.md)不同的是，InteropAbilityLifecycleCallback只能用于在ArkTS-Dyn中监听ArkTS-Sta的UIAbility的生命周期，或者在ArkTS-Sta中监听ArkTS-Dyn的UIAbility的生命周期。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 23 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { InteropAbilityLifecycleCallback } from '@kit.AbilityKit';
```

## InteropAbilityLifecycleCallback

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称                 | 类型                                           | 只读 | 可选 | 说明                                                         |
| -------------------- | ---------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| onAbilityCreate      | [AbilityCallbackFn](AbilityCallbackFn)         | 否   | 否   | 注册监听应用中不同ArkTS环境下UIAbility生命周期后，在UIAbility创建时触发回调。 |
| onWindowStageCreate  | [WindowStageCallbackFn](WindowStageCallbackFn) | 否   | 否   | 注册监听应用中不同ArkTS环境下UIAbility生命周期后，在WindowStage创建时触发回调。 |
| onWindowStageDestroy | [WindowStageCallbackFn](WindowStageCallbackFn) | 否   | 否   | 注册监听应用中不同ArkTS环境下UIAbility生命周期后，在WindowStage创建时触发回调。 |
| onAbilityDestroy     | [AbilityCallbackFn](AbilityCallbackFn)         | 否   | 否   | 注册监听应用中不同ArkTS环境下UIAbility生命周期后，在UIAbility创建时触发回调。 |
| onAbilityForeground  | [AbilityCallbackFn](AbilityCallbackFn)         | 否   | 否   | 注册监听应用中不同ArkTS环境下UIAbility生命周期后，在UIAbility创建时触发回调。 |
| onAbilityBackground  | [AbilityCallbackFn](AbilityCallbackFn)         | 否   | 否   | 注册监听应用中不同ArkTS环境下UIAbility生命周期后，在UIAbility创建时触发回调。 |

## AbilityCallbackFn

ArkTS-Dyn: type AbilityCallbackFn = (ability: any) => void

ArkTS-Sta: type AbilityCallbackFn = (ability: Any) => void

注册监听应用中不同ArkTS环境下UIAbility生命周期后，在UIAbility创建时触发回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                              | 必填 | 说明                                                         |
| ------- | --------------------------------- | ---- | ------------------------------------------------------------ |
| ability | ArkTS-Dyn: any<br/>ArkTS-Sta: Any | 是   | 触发回调的UIAbility对象。<br>**说明：** 在ArkTS-Dyn环境中触发回调时，ability为监听的ArkTS-Sta的UIAbility对象。在ArkTS-Sta环境中触发回调时，ability为监听的ArkTS-Dyn的UIAbility对象。 |

**示例：**

参见[InteropAbilityLifecycleCallback使用](#interopabilitylifecyclecallback使用)。

## WindowStageCallbackFn

ArkTS-Dyn: type WindowStageCallbackFn = (ability: any, windowStage: window.WindowStage) => void

ArkTS-Sta: type WindowStageCallbackFn = (ability: Any, windowStage: window.WindowStage) => void

注册监听应用中不同ArkTS环境下UIAbility生命周期后，在WindowStage创建时触发回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | ArkTS-Dyn: any<br/>ArkTS-Sta: Any | 是 | 触发回调的UIAbility对象。<br>**说明：** 在ArkTS-Dyn环境中触发回调时，ability为监听的ArkTS-Sta的UIAbility对象。在ArkTS-Sta环境中触发回调时，ability为监听的ArkTS-Dyn的UIAbility对象。 |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 传入的WindowStage对象。 |

**示例：**

参见[InteropAbilityLifecycleCallback使用](#interopabilitylifecyclecallback使用)。

## InteropAbilityLifecycleCallback使用

**示例：**

ArkTS-Sta示例：

```ts
import { InteropAbilityLifecycleCallback, UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// 声明UIAbility生命周期回调，需配置所有回调后才可以在ApplicationContext注册
let interopAbilityLifecycleCallback: InteropAbilityLifecycleCallback = {
  onAbilityCreate: (ability: Any) => {
    let uiAblity: UIAbility = ability as UIAbility;
    let abilityName: string = uiAblity.context.abilityInfo.name;;
    console.info(`InteropAbilityLifecycleCallback ${abilityName} onAbilityCreate.`);
  },
  onWindowStageCreate: (ability: Any, windowStage: window.WindowStage) => {
    let uiAblity: UIAbility = ability as UIAbility;
    let abilityName: string = uiAblity.context.abilityInfo.name;;
    console.info(`InteropAbilityLifecycleCallback ${abilityName} onWindowStageCreate.`);
  },
  onWindowStageDestroy: (ability: Any, windowStage: window.WindowStage) => {
    let uiAblity: UIAbility = ability as UIAbility;
    let abilityName: string = uiAblity.context.abilityInfo.name;;
    console.info(`InteropAbilityLifecycleCallback ${abilityName} onWindowStageDestroy.`);
  },
  onAbilityDestroy: (ability: Any) => {
    let uiAblity: UIAbility = ability as UIAbility;
    let abilityName: string = uiAblity.context.abilityInfo.name;;
    console.info(`InteropAbilityLifecycleCallback ${abilityName} onAbilityDestroy.`);
  },
  onAbilityForeground: (ability: Any) => {
    let uiAblity: UIAbility = ability as UIAbility;
    let abilityName: string = uiAblity.context.abilityInfo.name;;
    console.info(`InteropAbilityLifecycleCallback ${abilityName} onAbilityForeground.`);
  },
  onAbilityBackground: (ability: Any) => {
    let uiAblity: UIAbility = ability as UIAbility;
    let abilityName: string = uiAblity.context.abilityInfo.name;;
    console.info(`InteropAbilityLifecycleCallback ${abilityName} onAbilityBackground.`);
  },
};

export default class MyFirstAbility extends UIAbility {
  onCreate() {
    console.info('MyFirstAbility onCreate');
    try {
      // 通过ApplicationContext注册监听应用内生命周期
      this.context.getApplicationContext().onInteropAbilityLifecycle(interopAbilityLifecycleCallback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }

  onDestroy() {
    try {
      // 通过ApplicationContext注销监听应用内生命周期
      this.context.getApplicationContext().offInteropAbilityLifecycle();
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    return undefined;
  }
}
```

