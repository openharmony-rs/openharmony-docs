# UIAbility

表示包含UI界面的应用组件，提供组件创建、销毁、前后台切换等生命周期回调，同时也具备后台通信能力。

**继承/实现关系：** UIAbility extends [Ability](arkts-ability-app-ability-ability-ability-c.md)

**起始版本：** 9

<!--Device-unnamed-declare class UIAbility extends Ability--><!--Device-unnamed-declare class UIAbility extends Ability-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
import { Callee, Caller, OnReleaseCallback, OnRemoteStateChangeCallback, CalleeCallback } from '@kit.AbilityKit';
```

## onBackPressed

```TypeScript
onBackPressed(): boolean
```

UIAbility生命周期回调，当UIAbility侧滑返回时触发，根据返回值决定是否销毁UIAbility。

- 当targetSdkVersion&lt;12时，默认返回值为false，会销毁UIAbility。  
- 当targetSdkVersion&gt;=12时，默认返回值为true，会将UIAbility移动到后台不销毁。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onBackPressed(): boolean--><!--Device-UIAbility-onBackPressed(): boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | The value <code>true</code> means that the UIAbility instance will be moved to the background and will not be destroyed, and <code>false</code> means that the UIAbility instance will be destroyed. |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onBackPressed() {
    return true;
  }
}

```

## onBackground

```TypeScript
onBackground(): void
```

当应用从前台转入到后台时，系统触发该回调。开发者可在该回调中实现UI不可见时的资源释放操作，如停止定位功能等。

同步接口，不支持异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onBackground(): void--><!--Device-UIAbility-onBackground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class MyUIAbility extends UIAbility {
  onBackground() {
    // UIAbility回到后台
    hilog.info(0x0000, 'testTag', `onBackground`);
  }
}

```

## onCollaborate

```TypeScript
onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult
```

UIAbility生命周期回调，在多设备协同场景下，协同方应用在被拉起的过程中返回是否接受协同。
> **说明：**  
>  
> - 该生命周期回调不支持[specified启动模式](../../../application-models/uiability-launch-type.md#specified启动模式)。  
>  
> - 通过  
> [startAbility](arkts-ability-uiabilitycontext-c.md#startability)  
> 等方法拉起协同方应用时，需要在Want对象中设置协同标记[Flags](arkts-ability-wantconstant-flags-e.md)为  
> FLAG_ABILITY_ON_COLLABORATE。  
>  
> - [冷启动](../../../application-models/uiability-intra-device-interaction.md#目标uiability冷启动)时，该回调在  
> [onForeground](arkts-ability-app-ability-uiability-uiability-c.md#onforeground)前或[onBackground](arkts-ability-app-ability-uiability-uiability-c.md#onbackground)后调用；  
> [热启动](../../../application-models/uiability-intra-device-interaction.md#目标uiability热启动)时，该回调在  
> [onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant)前调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbility-onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult--><!--Device-UIAbility-onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantParam | Record&lt;string, Object&gt; | 是 | want相关参数，仅支持key值取"ohos.extra.param.key.supportCollaborateIndex"。通过该key值可以获取到调用方传输的数据并进行相应的处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AbilityConstant.CollaborateResult | 协同方是否接受协同的结果。 |

**示例：**

```TypeScript
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onCollaborate(wantParam: Record<string, Object>) {
    return AbilityConstant.CollaborateResult.ACCEPT;
  }
}

```

## onContinue

```TypeScript
onContinue(wantParam: Record<string, Object>):
    AbilityConstant.OnContinueResult | Promise<AbilityConstant.OnContinueResult>
```

当UIAbility准备跨端迁移时触发，可以保存待迁移的业务数据。
> **说明：**  
>  
> 对于API version 18（不含18） 之前版本仅支持同步调用，从API version 18及后续版本可支持异步调用。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onContinue(wantParam: Record<string, Object>):    AbilityConstant.OnContinueResult | Promise<AbilityConstant.OnContinueResult>--><!--Device-UIAbility-onContinue(wantParam: Record<string, Object>):    AbilityConstant.OnContinueResult | Promise<AbilityConstant.OnContinueResult>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantParam | Record&lt;string, Object&gt; | 是 | 开发者通过该参数保存待迁移的数据。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AbilityConstant.OnContinueResult | Return the result of onContinue.<br>**适用版本：** 9 - 11 |
| AbilityConstant.OnContinueResult \| Promise&lt;AbilityConstant.OnContinueResult&gt; | 表示是否同意迁移的结果：<br>- AGREE：表示同意。<br>- REJECT：表示拒绝，如应用在onContinue中异常可以返回REJECT。<br>- MISMATCH：表示版本不匹配，接续源端应用可以在onContinue中获取到迁移对端应用的版本号，进行协商后，如果版本不匹配导致无法迁移，可以返回该结果。<br> 该回调与onWindowStageRestore成对出现。在接续场景下，源端的UIAbility触发onContinue保存自定义数据，在目标端UIAbility触发onWindowStageRestore恢复自定义数据。<br>**适用版本：** 12+ |

**示例：**

应用迁移时使用同步接口进行数据保存，示例如下：

```TypeScript
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyUIAbility extends UIAbility {
  onContinue(wantParam: Record<string, Object>) {
    console.info('onContinue');
    wantParam['myData'] = 'my1234567'; // 保存待迁移的业务数据
    return AbilityConstant.OnContinueResult.AGREE;
  }
}

```

应用迁移时使用异步接口进行数据保存，示例如下：

```TypeScript
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyUIAbility extends UIAbility {
  async setWant(wantParams: Record<string, Object>) {
    console.info('setWant start');
    for (let time = 0; time < 1000; ++time) {
      wantParams[time] = time;
    }
    console.info('setWant end');
  }

  async onContinue(wantParams: Record<string, Object>) {
    console.info('onContinue');
    // 异步保存待迁移数据
    return this.setWant(wantParams).then(() => {
      return AbilityConstant.OnContinueResult.AGREE;
    });
  }
}

```

## onCreate

```TypeScript
onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void
```

当UIAbility实例创建完成时，系统会触发该回调，开发者可在该回调中执行初始化逻辑（如定义变量、加载资源等）。该回调仅会在UIAbility [冷启动](../../../application-models/uiability-intra-device-interaction.md#目标uiability冷启动)时触发。

同步接口，不支持异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void--><!--Device-UIAbility-onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 调用方拉起该UIAbility时传递的数据。 |
| launchParam | AbilityConstant.LaunchParam | 是 | 应用启动参数，包含应用启动原因、应用上次退出原因等。 |

**示例：**

```TypeScript
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class MyUIAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    // 执行异步任务
    hilog.info(0x0000, 'testTag',
      `onCreate, want: ${want.abilityName}, the launchReason is ${launchParam.launchReason}, the lastExitReason is ${launchParam.lastExitReason}`);
  }
}

```

## onDestroy

```TypeScript
onDestroy(): void | Promise<void>
```

当UIAbility被销毁（例如使用[terminateSelf](arkts-ability-uiabilitycontext-c.md#terminateself)接口停止UIAbility）时，系统触发该回调。开发者可以在该生命周期中执行资源清理、数据保存等相关操作。

使用同步回调或Promise异步回调。
> **说明：**  
>  
> - 在执行完onDestroy生命周期回调后，应用可能会退出，从而导致其中的异步函数（比如异步写入数据库）未能正确执行。在此情况下，推荐使用Promise异步回调。  
>  
> - 该回调仅在UIAbility正常退出时触发，当UIAbility异常退出（例如低内存终止进程）时，该回调将不被触发。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onDestroy(): void | Promise<void>--><!--Device-UIAbility-onDestroy(): void | Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

同步回调示例如下：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class MyUIAbility extends UIAbility {
  onDestroy() {
    hilog.info(0x0000, 'testTag', `onDestroy`);
    // 调用同步函数...
  }
}

```

Promise异步回调示例如下：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class MyUIAbility extends UIAbility {
  async onDestroy() {
    hilog.info(0x0000, 'testTag', `onDestroy`);
    // 调用异步函数...
  }
}

```

## onDidBackground

```TypeScript
onDidBackground(): void
```

UIAbility生命周期回调，当应用从前台转到后台后触发，在[onBackground](arkts-ability-app-ability-uiability-uiability-c.md#onbackground)之后被调用。可在该回调中实现应用进入后台之后的资源释放操作，如进入后台后停止音频播放等。

同步接口，不支持异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onDidBackground(): void--><!--Device-UIAbility-onDidBackground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { audio } from '@kit.AudioKit';

export default class MyUIAbility extends UIAbility {
  static audioRenderer: audio.AudioRenderer;

  // ...
  onForeground(): void {
    let audioStreamInfo: audio.AudioStreamInfo = {
      samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // 采样率，单位：Hz。
      channels: audio.AudioChannel.CHANNEL_2, // 通道。
      sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // 采样格式。
      encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // 编码格式。
    };

    let audioRendererInfo: audio.AudioRendererInfo = {
      usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // 音频流使用类型：音乐。根据业务场景配置，参考StreamUsage。
      rendererFlags: 0 // 音频渲染器标志。
    };

    let audioRendererOptions: audio.AudioRendererOptions = {
      streamInfo: audioStreamInfo,
      rendererInfo: audioRendererInfo
    };

    // 在前台时申请audioRenderer，用于播放PCM（Pulse Code Modulation）音频数据
    audio.createAudioRenderer(audioRendererOptions).then((data) => {
      MyUIAbility.audioRenderer = data;
      hilog.info(0x0000, 'testTag', `AudioRenderer Created : Success : Stream Type: SUCCESS.`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `AudioRenderer Created : F : ${JSON.stringify(err)}.`);
    });
  }

  onDidBackground() {
    // 转到后台后，释放audioRenderer资源
    MyUIAbility.audioRenderer.release((err: BusinessError) => {
      if (err) {
        hilog.error(0x0000, 'testTag', `AudioRenderer release failed, error: ${JSON.stringify(err)}.`);
      } else {
        hilog.info(0x0000, 'testTag', `AudioRenderer released.`);
      }
    });
  }
}

```

## onDidForeground

```TypeScript
onDidForeground(): void
```

UIAbility生命周期回调，应用转到前台后触发，在[onForeground](arkts-ability-app-ability-uiability-uiability-c.md#onforeground)后被调用，可在该回调中实现应用切换到前台后的时间打点。如果与[onWillForeground](arkts-ability-app-ability-uiability-uiability-c.md#onwillforeground)配合使用，还可以统计出从应用开始进入前台到切换至前台状态的耗时。

同步接口，不支持异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onDidForeground(): void--><!--Device-UIAbility-onDidForeground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

参考[onWillForeground](#onwillforeground20)。

## onDump

```TypeScript
onDump(params: Array<string>): Array<string>
```

应用调测场景下，通过命令行dump UIAbility数据时，系统会触发该回调。开发者可以在该回调中返回UIAbility要转储的非敏感信息。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onDump(params: Array<string>): Array<string>--><!--Device-UIAbility-onDump(params: Array<string>): Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Array&lt;string&gt; | 是 | 表示dump命令参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回的dump信息。 |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyUIAbility extends UIAbility {
  onDump(params: Array<string>) {
    console.info(`dump, params: ${JSON.stringify(params)}`);
    return ['params'];
  }
}

```

## onForeground

```TypeScript
onForeground(): void
```

当应用首次启动到前台或者从后台转入到前台时，系统触发该回调。开发者可在该回调中实现系统所需资源的申请，如应用转到前台时申请定位服务等。

同步接口，不支持异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onForeground(): void--><!--Device-UIAbility-onForeground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class MyUIAbility extends UIAbility {
  onForeground() {
    hilog.info(0x0000, 'testTag', `onForeground`);
  }
}

```

## onNewWant

```TypeScript
onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam): void
```

当已经启动的UIAbility实例再次被拉起时，系统会触发该回调。若在特定场景下（参见[Scenarios](arkts-ability-contextconstant-scenarios-e.md)），不需要触发该生命周期回调，可以使用[setOnNewWantSkipScenarios](arkts-ability-uiabilitycontext-c.md#setonnewwantskipscenarios)接口设置。

同步接口，不支持异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam): void--><!--Device-UIAbility-onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 调用方再次拉起该UIAbility时传递的数据。 |
| launchParam | AbilityConstant.LaunchParam | 是 | UIAbility启动参数，包含启动原因等。 |

**示例：**

```TypeScript
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';

export default class MyUIAbility extends UIAbility {
  onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info(`onNewWant, want: ${want.abilityName}`);
    console.info(`onNewWant, launchParam: ${JSON.stringify(launchParam)}`);
  }
}

```

## onPrepareToTerminate

```TypeScript
onPrepareToTerminate(): boolean
```

在UIAbility即将关闭前（例如用户通过点击应用窗口右上角的关闭按钮、或者通过Dock栏/托盘右键退出应用时），系统会触发该回调，用于在UIAbility正式关闭前执行其他操作。开发者可以在该回调中返回true阻拦此次关闭，然后在合适时机主动调用[terminateSelf](arkts-ability-uiabilitycontext-c.md#terminateself)接口关闭。例如，询问用户是否确认关闭UIAbility，再主动销毁UIAbility。该接口仅在2in1和Tablet设备中可正常执行回调，在其他设备上不执行回调。
> **说明：**  
>  
> - 从API version 15开始，当[UIAbility.onPrepareToTerminateAsync](arkts-ability-app-ability-uiability-uiability-c.md#onpreparetoterminateasync)实现时，本回调函数将不执  
> 行。当  
> [AbilityStage.onPrepareTerminationAsync](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onprepareterminationasync)  
> 或[AbilityStage.onPrepareTermination](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onpreparetermination)实现时，在  
> dock栏或系统托盘处右键点击关闭，本回调函数将不执行。  
>  
> - 如果应用本身或者所使用的三方框架注册了  
> [window.WindowStage.on('windowStageClose')](../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#onwindowstageclose14)  
> 监听，本回调函数将不执行。

**起始版本：** 10

**需要权限：** ohos.permission.PREPARE_APP_TERMINATE

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onPrepareToTerminate(): boolean--><!--Device-UIAbility-onPrepareToTerminate(): boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether to terminate the UIAbility.<br>The value <code>true</code> means that the termination process is canceled.<br>The value <code>false</code> means to continue terminating the UIAbility. |

**示例：**

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onPrepareToTerminate() {
    // 开发者定义预关闭动作
    // 例如拉起另一个ability，根据ability处理结果执行异步关闭
    let want: Want = {
      bundleName: "com.example.myapplication",
      moduleName: "entry",
      abilityName: "SecondAbility"
    }
    this.context.startAbilityForResult(want)
      .then((result) => {
        // 获取ability处理结果，当返回结果的resultCode为0关闭当前UIAbility
        console.info('startAbilityForResult success, resultCode is ' + result.resultCode);
        if (result && result.resultCode === 0) {
          this.context.terminateSelf(); // 关闭当前UIAbility
        }
      }).catch((err: BusinessError) => {
      // 异常处理
      console.error('startAbilityForResult failed, err:' + JSON.stringify(err));
      this.context.terminateSelf();
    })

    return true; // 已定义预关闭操作后，返回true表示UIAbility取消关闭
  }
}

```

## onPrepareToTerminateAsync

```TypeScript
onPrepareToTerminateAsync(): Promise<boolean>
```

在UIAbility关闭前（例如用户通过点击应用窗口右上角的关闭按钮、或者通过Dock栏/托盘右键退出应用时），系统会触发该回调，用于在UIAbility正式关闭前执行其他操作。

开发者可以在该回调中返回true阻拦此次关闭，然后在合适时机主动调用[terminateSelf](arkts-ability-uiabilitycontext-c.md#terminateself)接口关闭。例如，询问用户是否确认关闭UIAbility，再主动销毁UIAbility。从API version 15开始，该接口仅在2in1设备中可正常执行回调，在其他设备上不执行回调。从API version 19开始，该接口在2in1和Tablet设备中可正常执行回调，在其他设备上不执行回调。
> **说明：**  
>  
> - 当  
> [AbilityStage.onPrepareTerminationAsync](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onprepareterminationasync)  
> 或[AbilityStage.onPrepareTermination](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onpreparetermination)实现时，在  
> dock栏或系统托盘处右键点击关闭，本回调函数将不执行。  
>  
> - 如果应用本身或者所使用的三方框架注册了  
> [window.WindowStage.on('windowStageClose')](../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#onwindowstageclose14)  
> 监听，本回调函数将不执行。  
>  
> - 若异步回调内发生crash，按超时处理，执行等待超过10秒未响应，UIAbility将被强制关闭。

**起始版本：** 15

**需要权限：** ohos.permission.PREPARE_APP_TERMINATE

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onPrepareToTerminateAsync(): Promise<boolean>--><!--Device-UIAbility-onPrepareToTerminateAsync(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result.<br>The value <code>true</code> means that the termination process is canceled.<br>The value <code>false</code> means to continue terminating the UIAbility. |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  async onPrepareToTerminateAsync(): Promise<boolean> {
    await new Promise<boolean>((res, rej) => {
      setTimeout(res, 2000); // 延时2秒
    });
    return true; // 已定义预关闭操作后，返回true表示UIAbility取消关闭
  }
}

```

## onSaveState

```TypeScript
onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>): AbilityConstant.OnSaveResult
```

该接口需要与[appRecovery](arkts-app-ability-apprecovery.md)配合使用。如果应用已使能故障恢复功能（即[enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md#enableapprecovery)接口中的saveOccasion参数设置为SAVE_WHEN_ERROR），当应用出现故障时，系统将触发该回调来保存UIAbility的数据。
> **说明：**  
>  
> 从API version 20开始，当  
> [onSaveStateAsync](arkts-ability-app-ability-uiability-uiability-c.md#onsavestateasync)  
> 实现时，本回调函数将不执行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>): AbilityConstant.OnSaveResult--><!--Device-UIAbility-onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>): AbilityConstant.OnSaveResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | AbilityConstant.StateType | 是 | 触发应用保存状态的原因，当前仅支持APP_RECOVERY（即应用故障恢复场景）。 |
| wantParam | Record&lt;string, Object&gt; | 是 | 用户自定义的应用状态数据，应用再启动时被保存在[onCreate](arkts-ability-app-ability-uiability-uiability-c.md#oncreate)的Want.parameters中。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AbilityConstant.OnSaveResult | 返回一个数据保存策略的对象（如全部拒绝、全部允许、只允许故障恢复场景等）。 |

**示例：**

```TypeScript
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyUIAbility extends UIAbility {
  onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>) {
    console.info('onSaveState');
    wantParam['myData'] = 'my1234567'; // 保存UIAbility的状态数据，用于故障恢复
    return AbilityConstant.OnSaveResult.RECOVERY_AGREE;
  }
}

```

## onSaveStateAsync

```TypeScript
onSaveStateAsync(stateType: AbilityConstant.StateType, wantParam: Record<string, Object>): Promise<AbilityConstant.OnSaveResult>
```

该接口需要与[appRecovery](arkts-app-ability-apprecovery.md)配合使用。如果应用已使能故障恢复功能（即[enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md#enableapprecovery)接口中的saveOccasion参数设置为SAVE_WHEN_ERROR），当应用出现故障时，将触发该回调来保存UIAbility的数据。使用Promise异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onSaveStateAsync(stateType: AbilityConstant.StateType, wantParam: Record<string, Object>): Promise<AbilityConstant.OnSaveResult>--><!--Device-UIAbility-onSaveStateAsync(stateType: AbilityConstant.StateType, wantParam: Record<string, Object>): Promise<AbilityConstant.OnSaveResult>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stateType | AbilityConstant.StateType | 是 | 触发应用保存状态的原因，当前仅支持`APP_RECOVERY`（即应用故障恢复场景）。 |
| wantParam | Record&lt;string, Object&gt; | 是 | 用户自定义的应用状态数据，应用再启动时被保存在[onCreate](arkts-ability-app-ability-uiability-uiability-c.md#oncreate)的Want.parameters中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityConstant.OnSaveResult&gt; | Promise对象。返回一个数据保存策略的对象（如全部拒绝、全部允许、只允许故障恢复场景等）。 |

**示例：**

```TypeScript
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

class MyUIAbility extends UIAbility {
  async onSaveStateAsync(stateType: AbilityConstant.StateType,
    wantParam: Record<string, Object>): Promise<AbilityConstant.OnSaveResult> {
    await new Promise<string>((res, rej) => {
      setTimeout(res, 1000); // 延时1秒后执行
    });
    return AbilityConstant.OnSaveResult.RECOVERY_AGREE;
  }
}

```

## onShare

```TypeScript
onShare(wantParam: Record<string, Object>): void
```

当跨端分享原子化服务时，系统触发该回调。开发者可以在该回调中设置待分享原子化服务的标题、摘要和URL等数据。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onShare(wantParam: Record<string, Object>): void--><!--Device-UIAbility-onShare(wantParam: Record<string, Object>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantParam | Record&lt;string, Object&gt; | 是 | 待分享的数据。<br>**起始版本：** 11 |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyUIAbility extends UIAbility {
  onShare(wantParams: Record<string, Object>) {
    console.info('onShare');
    wantParams['ohos.extra.param.key.shareUrl'] = 'example.com';
  }
}

```

## onWillBackground

```TypeScript
onWillBackground(): void
```

UIAbility生命周期回调，当应用从前台转到后台前触发，在[onBackground](arkts-ability-app-ability-uiability-uiability-c.md#onbackground)前被调用。可在该回调中实现数据打点，例如，打点应用运行过程中发生的故障信息、统计信息、安全信息、用户行为信息等。

同步接口，不支持异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onWillBackground(): void--><!--Device-UIAbility-onWillBackground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyUIAbility extends UIAbility {
  onWillBackground(): void {
    let eventParams: Record<string, number | string> = {
      "int_data": 100,
      "str_data": "strValue",
    };
    // 写入打点应用故障信息
    hiAppEvent.write({
      domain: "test_domain",
      name: "test_event",
      eventType: hiAppEvent.EventType.FAULT,
      params: eventParams,
    }, (err: BusinessError) => {
      if (err) {
        hilog.error(0x0000, 'testTag', `hiAppEvent code: ${err.code}, message: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', `hiAppEvent success to write event`);
    });
  }
}

```

## onWillForeground

```TypeScript
onWillForeground(): void
```

UIAbility生命周期回调，应用转到前台前触发，在[onForeground](arkts-ability-app-ability-uiability-uiability-c.md#onforeground)前被调用。可在该回调中实现采集应用开始进入前台的时间。如果与[onDidForeground](arkts-ability-app-ability-uiability-uiability-c.md#ondidforeground)配合使用，还可以统计出从应用开始进入前台到切换至前台状态的耗时。

同步接口，不支持异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onWillForeground(): void--><!--Device-UIAbility-onWillForeground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWillForeground(): void {
    // 应用开始进入前台事件打点
    let eventParams: Record<string, number> = { 'xxxx': 100 };
    let eventInfo: hiAppEvent.AppEventInfo = {
      // 事件领域定义
      domain: "lifecycle",
      // 事件名称定义
      name: "onwillforeground",
      // 事件类型定义
      eventType: hiAppEvent.EventType.BEHAVIOR,
      // 事件参数定义
      params: eventParams,
    };
    hiAppEvent.write(eventInfo).then(() => {
      hilog.info(0x0000, 'testTag', `HiAppEvent success to write event`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `HiAppEvent err.code: ${err.code}, err.message: ${err.message}`);
    });
  }

  // ...

  onDidForeground(): void {
    // 应用进入前台后事件打点
    let eventParams: Record<string, number> = { 'xxxx': 100 };
    let eventInfo: hiAppEvent.AppEventInfo = {
      // 事件领域定义
      domain: "lifecycle",
      // 事件名称定义
      name: "ondidforeground",
      // 事件类型定义
      eventType: hiAppEvent.EventType.BEHAVIOR,
      // 事件参数定义
      params: eventParams,
    };
    hiAppEvent.write(eventInfo).then(() => {
      hilog.info(0x0000, 'testTag', `HiAppEvent success to write event`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `HiAppEvent err.code: ${err.code}, err.message: ${err.message}`);
    });
  }
}

```

## onWindowStageCreate

```TypeScript
onWindowStageCreate(windowStage: window.WindowStage): void
```

当[WindowStage](../../apis-arkui/arkts-apis/arkts-window.md)实例创建完成后，系统会触发该回调。开发者可以在该回调中通过WindowStage加载页面。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onWindowStageCreate(windowStage: window.WindowStage): void--><!--Device-UIAbility-onWindowStageCreate(windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowStage | window.WindowStage | 是 | WindowStage实例对象。 |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

export default class MyUIAbility extends UIAbility {
  // 主窗口已创建，为该UIAbility设置主页面
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause: ${JSON.stringify(err)}`);
        return;
      }
      hilog.info(0x0000, 'testTag', `Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}

```

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy(): void
```

当WindowStage销毁后，系统触发该回调。该回调用于通知开发者WindowStage对象已被销毁，不能再继续使用。

仅当UIAbility正常退出时会触发该回调，异常退出场景（例如低内存终止进程）不会触发该回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onWindowStageDestroy(): void--><!--Device-UIAbility-onWindowStageDestroy(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class MyUIAbility extends UIAbility {
  onWindowStageDestroy() {
    // 主窗口已销毁，释放UI相关资源
    hilog.info(0x0000, 'testTag', `onWindowStageDestroy`);
  }
}

```

## onWindowStageRestore

```TypeScript
onWindowStageRestore(windowStage: window.WindowStage): void
```

当UIAbility跨端迁移时，目标端UIAbility恢复页面栈时回调。
> **说明：**  
>  
> 在应用迁移启动时，无论是[冷启动](../../../application-models/uiability-intra-device-interaction.md#目标uiability冷启动)还是  
> [热启动](../../../application-models/uiability-intra-device-interaction.md#目标uiability热启动)，都会在执行完  
> [onCreate()](arkts-ability-app-ability-uiability-uiability-c.md#oncreate)/[onNewWant()](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant)后，触发onWindowStageRestore()生命周期函数，不  
> 执行onWindowStageCreate()生命周期函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onWindowStageRestore(windowStage: window.WindowStage): void--><!--Device-UIAbility-onWindowStageRestore(windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowStage | window.WindowStage | 是 | WindowStage实例对象。 |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

export default class MyUIAbility extends UIAbility {
  onWindowStageRestore(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', `onWindowStageRestore`);
  }
}

```

## onWindowStageWillDestroy

```TypeScript
onWindowStageWillDestroy(windowStage: window.WindowStage): void
```

当WindowStage即将销毁时，系统触发该回调。开发者可以在该生命周期中取消windowStage事件的监听。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-onWindowStageWillDestroy(windowStage: window.WindowStage): void--><!--Device-UIAbility-onWindowStageWillDestroy(windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowStage | window.WindowStage | 是 | WindowStage实例对象。 |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

export default class MyUIAbility extends UIAbility {
  onWindowStageWillDestroy(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', `onWindowStageWillDestroy`);
  }
}

```

## callee

```TypeScript
callee: Callee
```

系统为UIAbility创建的后台通信对象，Callee UIAbility（被调用方）可以通过Callee对象接收Caller对象发送的数据。

**类型：** Callee

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbility-callee: Callee--><!--Device-UIAbility-callee: Callee-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## context

```TypeScript
context: UIAbilityContext
```

UIAbility的上下文。

**类型：** UIAbilityContext

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-context: UIAbilityContext--><!--Device-UIAbility-context: UIAbilityContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## lastRequestWant

```TypeScript
lastRequestWant: Want
```

最近一次拉起UIAbility请求的Want参数。

- 首次拉起UIAbility时，取值为[onCreate](arkts-ability-app-ability-uiability-uiability-c.md#oncreate)接收到的Want参数。  
- 重复拉起UIAbility时，取值为[onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant)最近一次接收到的Want参数。

**类型：** Want

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-lastRequestWant: Want--><!--Device-UIAbility-lastRequestWant: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## launchWant

```TypeScript
launchWant: Want
```

UIAbility[冷启动](../../../application-models/uiability-intra-device-interaction.md#目标uiability冷启动)时接收到的Want参数，取值为[onCreate](arkts-ability-app-ability-uiability-uiability-c.md#oncreate)接收到的Want参数。

**类型：** Want

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbility-launchWant: Want--><!--Device-UIAbility-launchWant: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## specifiedId

```TypeScript
specifiedId?: string
```

仅当UIAbility启动模式为[specified](../../../application-models/uiability-launch-type.md#specified启动模式)时存在，取值为开发者自定义的UIAbility标识。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbility-specifiedId?: string--><!--Device-UIAbility-specifiedId?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

