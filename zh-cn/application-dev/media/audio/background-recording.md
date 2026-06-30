# 实现后台录音
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ZhengYong21-->
<!--Designer: @weixin_41398971-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

后台录音是指应用在前台启动录音任务后，退至后台仍持续采集音频的场景。典型场景包括会议记录、语音备忘、采访录音等需要长时间录制的业务。

后台录音涉及麦克风采集和后台运行，属于隐私敏感能力。应用需要同时满足麦克风权限、录音能力实现、后台长时任务声明和系统管控要求，不应在用户无感知或未授权的情况下启动录音。

## 管控考虑

后台录音涉及用户隐私和系统资源，应用设计时需要关注以下管控要求：

- 用户授权：录音前必须获得麦克风权限。用户撤销权限后，应用应立即停止录音并释放资源。
- 用户可感知：后台录音期间应保持明确的用户感知方式，例如展示正在录音的通知、状态提示或录音入口。
- 场景匹配：后台模式声明应与真实业务一致。应用申请录音类型长时任务后，需要实际执行录音业务。仅存在播放、播控或媒体会话控制诉求时，不应声明后台录音模式。
- 最小化采集：应用只在用户触发的录音任务期间采集音频，任务结束后及时停止，不应长期占用麦克风。
- 异常处理：系统可能因权限变化、设备占用、后台任务异常或资源管控等原因中断录音，应用需要监听并处理失败、暂停、停止等状态。
- 资源释放：应用进入后台、退出、崩溃恢复或录音完成后，需要确保录音器、文件句柄和后台任务状态一致，避免出现录音已停止但后台任务仍存在的情况。
- 隐私合规：录音文件的保存、上传、分享和删除应遵循用户授权和隐私政策要求，不应在后台自动上传用户未确认的录音内容。

## 实现方式

应用可以使用[AudioCapturer](using-audiocapturer-for-recording.md)、[OHAudio](using-ohaudio-for-recording.md)或[AVRecorder](../media/using-avrecorder-for-recording.md)实现录音。需要退至后台持续录音时，还需要申请录音类型的[长时任务](../../task-management/continuous-task.md)。

### 声明后台录音模式

在[module.json5配置文件](../../quick-start/module-configuration-file.md)中，为需要执行后台录音的UIAbility声明`audioRecording`后台模式。

```json
{
  "abilities": [
    {
      "name": "EntryAbility",
      "backgroundModes": [
        "audioRecording"
      ]
    }
  ]
}
```

### 启动录音任务

应用需要在前台启动录音任务，启动后可以退至后台继续录音。在后台直接启动录音会失败。

录音开始前，应用需要确认用户已经明确触发录音操作，并处理麦克风权限未授权、设备被占用、存储路径不可用等异常场景。录音开发方式请参考[音频录制开发概述](audio-recording-overview.md)。

针对应用在后台录音被其他音频流打断后无法恢复的场景，推荐使用以下解决方案：
1. 通话场景接入Call Service Kit在后台启动录音，开发方式请参考[Call Service Kit简介](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/call-introduction)
2. 应用录音在后台被打断，收到焦点恢复通知时出现start失败，可以弹窗提醒用户再次打开应用手动重新开始录音
3. 可以使用[OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/capi-native-audiostreambuilder-h#oh_audiostreambuilder_setcapturerwillmutewheninterrupted)将录音模式设置成静音打断模式

### 申请录音类型长时任务

当录音需要退至后台持续运行时，应用需要申请`AUDIO_RECORDING`类型长时任务，使系统识别该后台任务与录音业务匹配。

```ts
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

// 申请录音类型长时任务，wantAgentObj用于指定点击长时任务通知后跳转的界面。
await backgroundTaskManager.startBackgroundRunning(
  this.context,
  backgroundTaskManager.BackgroundMode.AUDIO_RECORDING,
  wantAgentObj
);
```

长时任务启动失败时，应用不应继续以后台录音方式运行，应停止录音或引导用户回到前台处理。长时任务的完整申请和取消流程请参考[长时任务](../../task-management/continuous-task.md)。

### 停止录音并释放资源

用户停止录音、录音异常中断或业务结束时，应用需要停止录音、释放音频采集资源，并同步取消录音类型长时任务。
