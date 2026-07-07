# 应用预加载
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
 

## 概述

从API version 20开始，提供应用预加载机制。该机制会根据用户的使用习惯，在系统资源充足时提前加载应用至特定阶段。当用户启动应用时，由于此前已完成了应用的部分加载，所需的启动时间会缩短，有助于提升用户体验和应用竞争力。

该机制尤其适用于因加载大量资源而启动耗时较长的应用，例如大型游戏应用和大型办公应用。

## 约束限制

- 当前仅支持2in1设备。

- 仅支持entry模块的AbilityStage和UIAbility预加载。无论预加载到哪种阶段，entry模块必须配置入口UIAbility，详见[开发步骤](#开发步骤)中步骤2。

- 应用配置预加载后，实际是否进行预加载以及具体的预加载时机，均由系统根据用户习惯等信息来综合决定。开发者无法对此进行干预。

## 运行机制

当系统资源充足时，系统将应用加载到特定阶段，提升启动速度。当前支持预加载到三种阶段。开发者可以根据应用冷启动各阶段耗时情况，选择其中的一种。

> **说明：** 
>
> 在应用预加载过程中不会显示任何界面，因此在预加载的任何阶段不应包含与界面显示、界面交互或依赖用户可见的相关操作，同时应确保用户正式启动应用后，所有功能正常运行且体验不受影响。

- processCreated：进程创建完成阶段。开发者配置此阶段后，预加载机制会创建空进程并初始化Application，但是不会触发任何生命周期回调。

- abilityStageCreated：[AbilityStage](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md)创建完成阶段。开发者配置此阶段后，预加载机制会创建空进程并初始化Application，随后触发entry模块[AbilityStage](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md)的[onCreate](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#oncreate)回调。

- windowStageCreated：[WindowStage](../reference/apis-arkui/arkts-apis-window-WindowStage.md)创建完成阶段。开发者配置此阶段后，预加载机制会创建空进程并初始化Application，随后触发entry模块[AbilityStage](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md)的[onCreate](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#oncreate)回调。接着会拉起entry模块的入口UIAbility，并触发其[onCreate](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate)回调和[onWindowStageCreate](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagecreate)回调。开发者可以在UIAbility的[onCreate](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate)回调中，通过[launchParam.launchReason](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchreason)的枚举值获取启动原因。枚举值为PRELOAD表示当前UIAbility是由预加载机制启动的。

![preload-application-procedure](figures/preload-application-procedure.png)

## 判断本次启动是否为预加载

应用被预加载后，开发者可以在[AbilityStage](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md)的[onCreate](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#oncreate)生命周期回调中，通过调用[application.getAppPreloadType()](../reference/apis-ability-kit/js-apis-app-ability-application.md#applicationgetapppreloadtype22)获取当前进程的预加载类型，从而判断本次启动是否为预加载，以及预加载到的具体阶段。

> **说明：**
>
> - 只有在进程首次执行[AbilityStage](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md)的[onCreate](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#oncreate)完成之前调用该接口，才可以返回真实的预加载类型。
> - AbilityStage创建完成后，应用的预加载数据将被清除，调用该接口将返回UNSPECIFIED，无法获取到真实的预加载类型。

[application.getAppPreloadType()](../reference/apis-ability-kit/js-apis-app-ability-application.md#applicationgetapppreloadtype22)的返回值[AppPreloadType](../reference/apis-ability-kit/js-apis-app-ability-application.md#apppreloadtype22)枚举值如下：

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| UNSPECIFIED | 0 | 未发生预加载或预加载数据已被清除。 |
| TYPE_CREATE_PROCESS | 1 | 进程最终预加载到进程创建完成阶段。 |
| TYPE_CREATE_ABILITY_STAGE | 2 | 进程最终预加载到[AbilityStage](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md)创建完成阶段。 |
| TYPE_CREATE_WINDOW_STAGE | 3 | 进程最终预加载到[WindowStage](../reference/apis-arkui/arkts-apis-window-WindowStage.md)创建完成阶段。 |

```ts
import { AbilityStage, application } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    let appPreloadType = application.getAppPreloadType();
    // 根据 appPreloadType 的值判断当前进程的预加载类型，取值见上表
  }
}
```

除了通过上述接口在AbilityStage中判断进程级别的预加载类型外，当应用配置预加载到windowStageCreated阶段时，开发者也可以在UIAbility的[onCreate](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate)回调中，通过[launchParam.launchReason](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchreason)是否等于PRELOAD来判断当前UIAbility实例是否由预加载机制启动，详见[开发步骤](#开发步骤)中步骤3。

## 开发步骤

1. 声明应用支持预加载到的阶段。

    以windowStageCreated阶段为例，在[app.json5配置文件](../quick-start/app-configuration-file.md)中配置[appPreloadPhase](../quick-start/app-configuration-file.md#配置文件标签)标签。

    ```json
    {
      "app": {
        "bundleName": "com.demo.preloadtest",
        "vendor": "example",
        "versionCode": 1000000,
        "versionName": "1.0.0",
        "icon": "$media:layered_image",
        "label": "$string:app_name",
        "appPreloadPhase": "windowStageCreated"
      }
    }
    ```

2. 配置入口UIAbility（新建工程默认已自动配置）。

    1. 以EntryAbility为例，在entry模块的[module.json5配置文件](../quick-start/module-configuration-file.md)中，设置mainElement为EntryAbility，且EntryAbility的skills标签下面的entities中添加"entity.system.home"、actions中添加"ohos.want.action.home"。

    2. 当[app.json5配置文件](../quick-start/app-configuration-file.md)中的[appPreloadPhase](../quick-start/app-configuration-file.md#配置文件标签)配置为windowStageCreated时，需要在entry模块的[module.json5配置文件](../quick-start/module-configuration-file.md)中配置EntryAbility的launchType标签为[singleton](uiability-launch-type.md#singleton启动模式)或[specified](uiability-launch-type.md#specified启动模式)。

    ```json5
    {
      "module": {
        "name": "entry",
        "type": "entry",
        "mainElement": "EntryAbility",
        // ...
        "abilities": [
          {
            "name": "EntryAbility",
            "srcEntry": "./ets/entryability/EntryAbility.ets",
            "launchType": "singleton",
            "skills": [
              {
                "entities": [
                  "entity.system.home"
                ],
                "actions": [
                  "ohos.want.action.home"
                ]
              }
            ]
            // ...
          }
        ]
      }
    }
    ```

3. （可选）获取UIAbility启动原因。

    仅当appPreloadPhase配置为windowStageCreated时，开发者可在UIAbility的[onCreate](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate)生命周期回调中通过[launchParam.launchReason](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchreason)的枚举值获取启动原因。枚举值为PRELOAD表示当前UIAbility是由预加载机制启动的。

    ```ts
    import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

    export default class EntryAbility extends UIAbility {
      onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        console.info(`EntryAbility onCreate, LaunchReason:${launchParam.launchReason}`);
        // 判断是否是预加载启动
        let isPreloadStart = launchParam.launchReason === AbilityConstant.LaunchReason.PRELOAD;
        // ...
      }
    }
    ```