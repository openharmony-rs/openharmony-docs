# @ohos.app.ability.AbilityConstant (Ability相关常量)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

AbilityConstant提供Ability相关的枚举，包括应用启动原因[LaunchReason](#launchreason)、上次退出原因[LastExitReason](#lastexitreason)、迁移结果[OnContinueResult](#oncontinueresult)等。

> **说明：**
> 
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { AbilityConstant } from '@kit.AbilityKit';
```

## 常量

**系统能力**：SystemCapability.Ability.AbilityBase

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

| 名称 | 类型 | 值 | 说明 |
| ---- | -----| ---- | ---------------------------------------------------------- |
| REASON_MESSAGE_DESKTOP_SHORTCUT<sup>20+</sup>  | string | "ReasonMessage_DesktopShortcut" | 通过桌面快捷方式启动。开发者如果从[LaunchParam](#launchparam)的launchReasonMessage属性中获取到该字符串，表示UIAbility是通过点击桌面快捷方式启动的。|

## LaunchParam

启动参数，主要包括Ability启动原因以及上次退出原因。Ability启动时由系统自动传入，开发者无需修改。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| launchReason | [LaunchReason](#launchreason)| 否 | 否 | 枚举类型，表示Ability启动原因（如故障恢复拉起、意图调用拉起、原子化服务分享拉起等），详见[LaunchReason](#launchreason)。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| launchReasonMessage<sup>18+</sup> | string | 否 | 是 | 表示Ability启动的详细原因。<br>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。 |
| lastExitReason | [LastExitReason](#lastexitreason) | 否 | 否 | 枚举类型，表示Ability上次退出原因。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| lastExitMessage<sup>12+</sup> | string | 否 | 否 | 表示Ability上次退出的详细原因。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。 |
| lastExitDetailInfo<sup>18+</sup> | [LastExitDetailInfo](#lastexitdetailinfo18) | 否 | 是 | 表示Ability上次退出时的关键运行信息（含进程ID、退出时间戳、RSS内存值等）。<br>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。 |

## LaunchReason

Ability启动原因，该类型为枚举，可配合UIAbility的[onCreate(want, launchParam)](js-apis-app-ability-uiAbility.md#oncreate)方法根据launchParam.launchReason的不同类型执行相应操作。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                          | 值   | 说明                                                         |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| UNKNOWN          | 0    | 未知原因。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| START_ABILITY          | 1    | 通过[startAbility](js-apis-inner-application-uiAbilityContext.md#startability)接口启动Ability。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| CALL | 2    | 通过[startAbilityByCall](js-apis-inner-application-uiAbilityContext.md#startabilitybycall)接口启动Ability。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| CONTINUATION           | 3    | 跨端迁移启动Ability。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| APP_RECOVERY           | 4    | 设置应用恢复后，应用故障时自动恢复启动Ability。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| SHARE<sup>10+</sup>           | 5    | 通过原子化服务分享启动Ability。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| AUTO_STARTUP<sup>11+</sup>           | 8    | 通过设置开机自启动来启动Ability。 |
| INSIGHT_INTENT<sup>11+</sup>           | 9    | 通过洞察意图来启动Ability。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| PREPARE_CONTINUATION<sup>12+</sup>           | 10    | 跨端迁移提前启动Ability。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。|
| PRELOAD<sup>20+</sup>           | 11    | 表明该UIAbility是通过预加载机制启动的。<br>**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。|

**示例：**

```ts
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    if (launchParam.launchReason === AbilityConstant.LaunchReason.START_ABILITY) {
      console.log('The ability has been started by the way of startAbility.');
    }
  }
}
```

## LastExitReason

Ability上次退出原因，该类型为枚举，可配合UIAbility的[onCreate()](js-apis-app-ability-uiAbility.md#oncreate)方法根据launchParam.lastExitReason的不同类型执行相应操作。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                          | 值   | 说明                                                         |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| UNKNOWN          | 0    | 未知原因。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| ABILITY_NOT_RESPONDING<sup>(deprecated)</sup> | 1    | Ability未响应。<br>**说明:** 从API version 9开始支持，从API version 10开始废弃，请使用APP_FREEZE替代。|
| NORMAL | 2    | 用户主动关闭，应用程序正常退出。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。<br>**说明**：当开发者直接调用[process.exit()](../apis-arkts/js-apis-process.md#processexitdeprecated)、内核kill命令等非Ability Kit提供的能力强制退出应用进程时，也会返回NORMAL。 |
| CPP_CRASH<sup>10+</sup>  | 3    | [进程崩溃](../../dfx/cppcrash-guidelines.md)导致的应用程序退出。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| JS_ERROR<sup>10+</sup>  | 4    | 当应用存在JS语法错误并未被开发者捕获时，触发JS_ERROR故障，导致应用程序退出。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| APP_FREEZE<sup>10+</sup>  | 5    | [应用冻屏](../../dfx/appfreeze-guidelines.md)导致的应用程序退出。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| PERFORMANCE_CONTROL<sup>10+</sup>  | 6    | 因系统性能问题（如设备内存不足）导致的应用程序退出。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。<br>**说明**：该接口即将废弃，建议使用RESOURCE_CONTROL替代。 |
| RESOURCE_CONTROL<sup>10+</sup>  | 7    | 系统资源使用不当导致的应用程序退出。具体错误原因可以通过[LaunchParam.lastExitMessage](#launchparam)获取，可能原因如下: <br> - CPU Highload，CPU高负载。<br> - CPU_EXT Highload，快速CPU负载检测。<br> - IO Manage Control，I/O管控。<br> - App Memory Deterioration，应用内存超限劣化。<br> - Temperature Control，温度管控。<br> - Memory Pressure，整机低内存触发按优先级由低到高查杀。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。|
| UPGRADE<sup>10+</sup>  | 8    | 应用升级导致的应用程序退出。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| USER_REQUEST<sup>18+</sup>  | 9    | 应用程序因多任务中心请求而退出。<br>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。 |
| SIGNAL<sup>18+</sup>  | 10    | 应用程序因收到系统kill指令信号而退出。<br>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。 |

**示例：**

```ts
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    if (launchParam.lastExitReason === AbilityConstant.LastExitReason.APP_FREEZE) {
      console.log('The ability has exit last because the ability was not responding.');
    }
    if (launchParam.lastExitReason === AbilityConstant.LastExitReason.RESOURCE_CONTROL) {
      console.log('The ability has exit last because the rss control，the lastExitReason is '+  launchParam.lastExitReason + ', the lastExitMessage is ' + launchParam.lastExitMessage);
    }
  }
}
```

## LastExitDetailInfo<sup>18+</sup>

记录Ability所在进程上次退出时的关键运行信息。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| pid | number | 否 | 否 | Ability上次退出所在进程的进程号。 <br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。|
| processName | string | 否 | 否 | Ability上次退出所在进程的名称。 <br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。|
| uid | number | 否 | 否 | Ability上次退出所在应用的UID。 <br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。|
| exitSubReason | number | 否 | 否 | Ability上次退出的子原因。 <br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。|
| exitMsg | string | 否 | 否 | Ability上次退出时所在进程被kill的描述信息。 <br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。|
| rss | number | 否 | 否 | Ability上次退出时所在进程实际占用内存大小，单位KB。 <br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。|
| pss | number | 否 | 否 | Ability上次退出时所在进程实际使用的物理内存大小，单位KB。 <br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。|
| timestamp | number | 否 | 否 | Ability上次退出时的时间戳。 <br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。|
| processState<sup>20+</sup> | [appManager.ProcessState](js-apis-app-ability-appManager.md#processstate10) | 否 | 是 | Ability上次退出时的进程状态。<br/>**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。 |

**示例**:

```ts
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    if (launchParam.lastExitDetailInfo) {
      console.log('pid: ' + launchParam.lastExitDetailInfo.pid +
        '\n processName: ' + launchParam.lastExitDetailInfo.processName +
        '\n uid: ' + launchParam.lastExitDetailInfo.uid +
        '\n exitSubReason: ' + launchParam.lastExitDetailInfo.exitSubReason +
        '\n exitMsg: ' + launchParam.lastExitDetailInfo.exitMsg +
        '\n rss: ' + launchParam.lastExitDetailInfo.rss +
        '\n pss: ' + launchParam.lastExitDetailInfo.pss +
        '\n timestamp: ' + launchParam.lastExitDetailInfo.timestamp +
        '\n processState: ' + launchParam.lastExitDetailInfo.processState
      );
    }
  }
}
```

## OnContinueResult 

Ability迁移结果，该类型为枚举，可配合UIAbility的[onContinue()](js-apis-app-ability-uiAbility.md#oncontinue)方法完成相应的返回。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                          | 值   | 说明                                                         |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| AGREE           | 0    | 表示同意。 |
| REJECT           | 1    | 表示拒绝：如应用在[onContinue](js-apis-app-ability-uiAbility.md#oncontinue)中异常会导致迁移以后数据恢复时显示异常，则可以返回REJECT。 |
| MISMATCH  | 2    | 表示版本不匹配：迁移发起端应用可以在[onContinue](js-apis-app-ability-uiAbility.md#oncontinue)中获取到迁移目标端应用的版本号，进行协商后，如果版本不匹配导致无法迁移，可以返回该结果。|

**示例：**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onContinue(wantParam: Record<string, Object>) {
    return AbilityConstant.OnContinueResult.AGREE;
  }
}
```

## MemoryLevel

整机可用内存级别，该类型为枚举，可配合UIAbility的[onMemoryLevel()](js-apis-app-ability-ability.md#abilityonmemorylevel)方法根据level执行不同内存级别的相应操作。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                         | 值 | 说明                |
| ---                         | --- | ---           |
| MEMORY_LEVEL_MODERATE       | 0   | 整机可用内存适中。 |
| MEMORY_LEVEL_LOW            | 1   | 整机可用内存低。   |
| MEMORY_LEVEL_CRITICAL       | 2   | 整机可用内存极低。   |

> **说明：**
> 
> 不同产品的触发条件可能存在差异。以12G内存的标准设备为例：
> - 当整机可用内存下降至1700M~1800M时，会触发取值为0的onMemoryLevel回调，表示当前整机可用内存适中。
> - 当整机可用内存下降至1600M~1700M时，会触发取值为1的onMemoryLevel回调，表示当前整机可用内存偏低。
> - 当整机可用内存下降至1600M以下时，会触发取值为2的onMemoryLevel回调，表示当前整机可用内存很低。

**示例：**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    if (level === AbilityConstant.MemoryLevel.MEMORY_LEVEL_CRITICAL) {
      console.log('The memory of device is critical, please release some memory.');
    }
  }
}
```

## WindowMode<sup>12+</sup>

启动UIAbility时窗口的创建模式，类型为枚举。可配合[startAbility](js-apis-inner-application-uiAbilityContext.md#startability)方法使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                        | 值 | 说明                 |
| ---                         | --- | ---                  |
| WINDOW_MODE_FULLSCREEN      | 1   | 全屏模式。仅在2in1和Tablet设备上生效。  |
| WINDOW_MODE_SPLIT_PRIMARY   | 100 | 支持应用内拉起Ability时设置为分屏，左侧分屏。仅在折叠屏和Tablet设备上生效。   |
| WINDOW_MODE_SPLIT_SECONDARY | 101 | 支持应用内拉起Ability时设置为分屏，右侧分屏。仅在折叠屏和Tablet设备上生效。   |

**示例：**

```ts
import { UIAbility, StartOptions, Want, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility'
};
let option: StartOptions = {
  windowMode: AbilityConstant.WindowMode.WINDOW_MODE_SPLIT_PRIMARY
};

// 确保从上下文获取到context
export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    this.context.startAbility(want, option).then(() => {
      console.log('Succeed to start ability.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to start ability with error: ${JSON.stringify(error)}`);
    });
  }
}
```

## OnSaveResult

保存应用数据的结果，该类型为枚举。配合UIAbility的[onSaveState()](js-apis-app-ability-uiAbility.md#onsavestate)方法使用，可以实现[UIAbility备份恢复](../../application-models/ability-recover-guideline.md)。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                          | 值   | 说明                                                         |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| ALL_AGREE           | 0    | 总是同意保存状态。 |
| CONTINUATION_REJECT           | 1    | 拒绝迁移保存状态。 |
| CONTINUATION_MISMATCH  | 2    | 迁移不匹配。|
| RECOVERY_AGREE           | 3    | 同意恢复保存状态。 |
| RECOVERY_REJECT  | 4    | 拒绝恢复保存状态。|
| ALL_REJECT  | 5    | 总是拒绝保存状态。|

**示例：**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>) {
    return AbilityConstant.OnSaveResult.ALL_AGREE;
  }
}
```

## StateType

保存应用数据场景原因，该类型为枚举。配合UIAbility的[onSaveState()](js-apis-app-ability-uiAbility.md#onsavestate)方法使用，可以实现[UIAbility备份恢复](../../application-models/ability-recover-guideline.md)。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                          | 值   | 说明                                                         |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| CONTINUATION           | 0    | 应用迁移场景。 |
| APP_RECOVERY           | 1    | 应用故障恢复场景。 |

**示例：**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>) {
    if (reason === AbilityConstant.StateType.CONTINUATION) {
      console.log('Save the ability data when the ability continuation.');
    }
    return AbilityConstant.OnSaveResult.ALL_AGREE;
  }
}
```

## ContinueState<sup>10+</sup>

流转状态枚举值。用于表示当前应用任务流转的状态。可配合[UIAbilityContext](js-apis-inner-application-uiAbilityContext.md)的[setMissionContinueState](js-apis-inner-application-uiAbilityContext.md#setmissioncontinuestate10)方法进行设置。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称           | 值       | 说明                                                         |
| ------------- | --------- | ------------------------------------------------------------ |
| ACTIVE        | 0         | 指示当前应用任务流转处于激活状态。                              |
| INACTIVE      | 1         | 指示当前应用任务流转处于未激活状态。                            |

**示例：**

```ts
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    this.context.setMissionContinueState(AbilityConstant.ContinueState.INACTIVE, (result: BusinessError) => {
      console.info(`setMissionContinueState: ${JSON.stringify(result)}`);
    });
  }
}
```

## CollaborateResult<sup>18+</sup>

应用协同状态，该类型为枚举。用于多设备场景下，调用方应用拉起协同方应用时，协同方应用是否接受协同。需要配合UIAbility的[onCollaborate()](js-apis-app-ability-uiAbility.md#oncollaborate18)方法进行设置。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称     | 值   | 说明       |
| -------- | ---- | ---------- |
| ACCEPT   | 0    | 接受协同。 |
| REJECT   | 1    | 拒绝协同。 |

**示例：**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onCollaborate(wantParam: Record<string, Object>) {
    return AbilityConstant.CollaborateResult.ACCEPT;
  }
}
```

## PrepareTermination<sup>15+</sup>

应用准备关闭时返回的动作，该类型为枚举。需要配合[AbilityStage](js-apis-app-ability-abilityStage.md)的[onPrepareTermination](js-apis-app-ability-abilityStage.md#onpreparetermination15)或者[onPrepareTerminationAsync](js-apis-app-ability-abilityStage.md#onprepareterminationasync15)方法使用。

**原子化服务API**：从API version 15开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 值 | 说明 |
| ------------- | --------- | ----------- |
| TERMINATE_IMMEDIATELY | 0 | 表示立即执行结束动作，默认值。|
| CANCEL | 1 | 表示取消结束动作。|

**示例：**

```ts
import { AbilityConstant, AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onPrepareTermination(): AbilityConstant.PrepareTermination {
    console.info('MyAbilityStage.onPrepareTermination is called');
    return AbilityConstant.PrepareTermination.CANCEL;
  }
}
```