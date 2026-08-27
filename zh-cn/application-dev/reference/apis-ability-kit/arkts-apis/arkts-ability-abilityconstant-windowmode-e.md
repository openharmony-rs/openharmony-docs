# WindowMode

启动UIAbility时窗口的创建模式，类型为枚举。可配合 [startAbility](arkts-ability-uiabilitycontext-c.md#startability) 方法使用。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_FULLSCREEN

```TypeScript
WINDOW_MODE_FULLSCREEN = 1
```

全屏模式。仅在2in1和Tablet设备上生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_SPLIT_PRIMARY

```TypeScript
WINDOW_MODE_SPLIT_PRIMARY = 100
```

支持应用内拉起Ability时设置为分屏，左侧分屏。仅在折叠屏和Tablet设备上生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_SPLIT_SECONDARY

```TypeScript
WINDOW_MODE_SPLIT_SECONDARY = 101
```

支持应用内拉起Ability时设置为分屏，右侧分屏。仅在折叠屏和Tablet设备上生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

```TypeScript
import { UIAbility, StartOptions, Want, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetWant: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility'
};
let option: StartOptions = {
  windowMode: AbilityConstant.WindowMode.WINDOW_MODE_SPLIT_PRIMARY
};

// 确保从上下文获取到context
export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    this.context.startAbility(targetWant, option).then(() => {
      console.info('Succeed to start ability.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to start ability with error: ${JSON.stringify(error)}`);
    });
  }
}
```

```TypeScript
import { UIAbility, StartOptions, Want, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility'
};
let option: StartOptions = {
  windowMode: AbilityConstant.WindowMode.WINDOW_MODE_FULLSCREEN
};

// 确保从上下文获取到context
export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    this.context.startAbility(want, option).then(() => {
      console.info('Succeed to start ability.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to start ability with error: ${JSON.stringify(error)}`);
    });
  }
}
```
