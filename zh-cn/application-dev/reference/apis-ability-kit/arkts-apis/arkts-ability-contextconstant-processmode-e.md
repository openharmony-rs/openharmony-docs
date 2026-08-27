# ProcessMode

UIAbility启动后的进程模式。 ProcessMode作为[StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md)的一个属性，仅在 [UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability) 中生效，用来指定目标UIAbility的进程模式。 该功能仅在2in1和Tablet设备上生效，在其他设备中返回801错误码。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## NEW_PROCESS_ATTACH_TO_PARENT

```TypeScript
NEW_PROCESS_ATTACH_TO_PARENT = 1
```

创建一个新进程，并在该进程上启动UIAbility。该进程会跟随父进程退出。  
**约束：**使用此模式时，要求目标UIAbility跟调用方是在同一个应用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM

```TypeScript
NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM = 2
```

创建一个新进程，在该进程上启动UIAbility，并绑定该进程到状态栏图标上。  
**约束：**使用此模式时，要求目标UIAbility跟调用方是在同一个应用，并且应用要在状态栏中有图标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ATTACH_TO_STATUS_BAR_ITEM

```TypeScript
ATTACH_TO_STATUS_BAR_ITEM = 3
```

启动UIAbility，并绑定该UIAbility所在进程到状态栏图标上。  
**约束：**使用此模式时，要求目标UIAbility跟调用方是在同一个应用，并且应用要在状态栏中有图标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

```TypeScript
import { UIAbility, Want, StartOptions, contextConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // 构造Want对象，指定目标UIAbility信息
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'MainAbility2'
    };
  // 创建启动选项，设置进程模式和启动可见性
  let options: StartOptions = {
        processMode: contextConstant.ProcessMode.NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM,
        startupVisibility: contextConstant.StartupVisibility.STARTUP_HIDE
      };

    try {
      // 启动目标UIAbility
      this.context.startAbility(want, options, (err: BusinessError) => {
        if (err.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```
