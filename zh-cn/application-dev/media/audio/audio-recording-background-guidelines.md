# 后台录音指导
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyy0412-->
<!--Designer: @weixin_41398971-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

开发者在实现后台录音能力时，需要重点关注前台启动约束、长时任务接入、页面生命周期管理以及并发场景适配。本文面向应用开发者，介绍后台录音的接入前提、开发要点以及适配建议。

## 后台录音开发须知

- 调用麦克风录音前，需要先向用户申请`ohos.permission.MICROPHONE`权限。相关说明可参考[音频录制开发概述](audio-recording-overview.md)。
- 录制必须在前台启动，启动成功后才可以退到后台继续录制。在后台直接启动录音会失败，相关约束可参考[音频录制开发概述](audio-recording-overview.md)。
- 需要在[module.json5配置文件](../../quick-start/module-configuration-file.md)中为对应的UIAbility声明`audioRecording`后台模式。
- 如果业务需要持续录制或后台录制，必须接入长时任务，避免应用进入挂起（Suspend）后业务线程停止。长时任务的申请方式可参考[长时任务(ArkTS)](../../task-management/continuous-task.md)。
- 应用录制音频时需要使用合适的录制流类型，请参考[使用合适的音频流类型](using-right-streamusage-and-sourcetype.md)。
- 建议将录音核心对象、读数据回调以及写文件逻辑从页面生命周期中解耦，避免页面退后台后对象被释放。
- 建议在后台录音场景下同步关注录音状态、中断事件、录音流变化和输入设备变化，避免仅根据`start`是否成功判断业务正常。
- 后台录音比前台录音更容易受到通话、VoIP、其他录音任务、蓝牙设备切换和系统中断策略的影响。

## 开发指导

后台录音开发通常涉及录音实例创建、长时任务申请、录音启动、前后台切换期间的状态维护，以及录音停止后的资源释放。建议搭配[使用AudioCapturer开发音频录制功能(ArkTS)](using-audiocapturer-for-recording.md)和[长时任务(ArkTS)](../../task-management/continuous-task.md)说明阅读。

### 开发步骤及注意事项

1. 在[module.json5配置文件](../../quick-start/module-configuration-file.md)中为对应的UIAbility声明`audioRecording`后台模式。

   ```json5
   "module": {
     // ...
     "abilities": [
       {
         // ...
         "backgroundModes": [
           "audioRecording"
         ]
       }
     ]
   }
   ```

2. 在前台页面完成录音参数配置并创建录音实例。

   > **说明：**
   >
   > 录音必须在前台启动，不能在应用已经进入后台后再直接创建并启动录音。

3. 按照[使用AudioCapturer开发音频录制功能(ArkTS)](using-audiocapturer-for-recording.md)中的方式，创建`AudioCapturer`实例、注册`readData`回调，并完成音频数据写文件或业务处理逻辑。

4. 在启动录音前，按业务场景申请对应的长时任务，并确保长时任务在录音期间持续有效。

5. 调用`start`启动录音。录音启动成功后，应用可以退到后台继续录制。

6. 将录音对象、读数据回调和文件写入逻辑与页面生命周期解耦，避免页面`onDisappear`或`aboutToDisappear`时误释放录音资源。

7. 录音结束后，停止录音、释放录音实例，并取消长时任务。

以下示例为片段代码，演示后台录音场景下的关键接入点。完整录音创建、读数据回调和写文件方式，可参考[使用AudioCapturer开发音频录制功能(ArkTS)](using-audiocapturer-for-recording.md)中的示例；长时任务申请和取消方式，可参考[长时任务(ArkTS)](../../task-management/continuous-task.md)中的`audioRecording`类型示例。

```ts
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function startContinuousTask(context: Context) {
  let wantAgentInfo: wantAgent.WantAgentInfo = {
    wants: [
      {
        bundleName: 'com.example.myapplication',
        abilityName: 'MainAbility'
      }
    ],
    actionType: wantAgent.OperationType.START_ABILITY,
    requestCode: 0,
    actionFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
  };

  wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
    backgroundTaskManager.startBackgroundRunning(context, ['audioRecording'], wantAgentObj).then(() => {
      console.info('Succeeded in operationing startBackgroundRunning.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to operation startBackgroundRunning. Code is ${err.code}, message is ${err.message}`);
    });
  });
}

function stopContinuousTask(context: Context) {
  backgroundTaskManager.stopBackgroundRunning(context).then(() => {
    console.info('Succeeded in operationing stopBackgroundRunning.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to operation stopBackgroundRunning. Code is ${err.code}, message is ${err.message}`);
  });
}
```

> **注意：**
>
> - 后台录音期间，如果需要对`readData`中的音频数据做缓存、上传、转码或停止后再处理，请在回调内立即拷贝数据，不要只保存`ArrayBuffer`引用。相关说明可参考[录音无声定位指导](audio-recording-no-audio-troubleshooting.md)。
> - 页面退后台不应直接等价于录音结束。若业务需要持续录音，应避免在页面隐藏时直接调用`stop`或`release`。
> - 如果业务存在通话、VoIP、直播、录屏带麦克风等并发场景，建议提前验证对应录音流类型和音频会话策略是否符合预期。
> - 如果业务存在蓝牙耳机、有线耳机、USB声卡等设备接入场景，建议同步验证后台期间输入设备路由是否符合业务预期。

## 相关说明

- 后台无声、切后台后无回调、锁屏后录音异常等问题，本质上仍属于录音无声问题的一部分。相关定位思路可参考[录音无声定位指导](audio-recording-no-audio-troubleshooting.md)。
- 后台录音涉及的并发策略、录音流类型和其他录音流监听能力，可进一步参考[录音并发策略说明](audio-recording-concurrency.md)、[查询和监听其他应用录制状态](audio-recording-stream-management.md)和[音频焦点和音频会话开发概述](audio-playback-concurrency-audio-session-overview.md)。
