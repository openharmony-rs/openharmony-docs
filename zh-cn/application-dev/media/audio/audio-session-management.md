# 音频会话管理
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

对于涉及多个音频流并发的场景，系统已预设了默认的[音频焦点策略](audio-playback-concurrency.md#音频焦点策略)，该策略将对所有音频流（包括播放和录制）实施统一的焦点管理。

当系统提供的默认焦点策略不能满足应用需求时，应用可利用音频会话管理提供的接口，管理应用内音频流的焦点，自定义音频流的焦点策略，调整音频流释放焦点的时机，以满足特定需求。该篇文章的示例代码均为ArkTS，如果需要使用OHAudio开发请参考[使用OHAudio开发音频会话功能(C/C++)](using-ohaudio-for-session.md)。

使用音频会话相关接口，可以实现以下功能：

- 系统默认焦点策略不能满足应用当前需求，应用可[使用音频会话修改焦点策略](#使用音频会话修改焦点策略)来适配适合自己的焦点策略。

  典型场景：应用播放短视频时，会打断后台音乐，应用希望自身的音频流停止后，后台的音乐可以自动恢复（该场景需要应用在音频流启动前激活音频会话，音频流停止后停用音频会话）。

- 当应用在某个业务流程中需要启动多个音频流，且要保证整个流程的完整性时，应用可[使用音频会话申请焦点策略](#使用音频会话申请焦点策略)来适配适合自己业务场景的焦点策略。

  典型场景：应用连续播放多个音频时，在多个音频衔接的间隙，不希望后台被影响的其他音频自动恢复，希望整个播放过程保持音频焦点的连贯性（该场景需要应用在整个播放过程开始前激活音频会话，整个播放过程结束后停用音频会话）。

> **注意：**
>
> - 音频并发策略优先级为：STOP > PAUSE > DUCK > PLAYBOTH。当指定的音频会话策略优先级高于默认并发策略时，指定的音频会话策略不会生效。
> - 应用在开始音频播放或录制之前需要确保音频会话已经处于激活状态，否则音频会话的自定义焦点策略不会生效。若应用使用了异步接口，则需要格外注意异步操作执行的时序。

## 获取音频会话管理器

在使用AudioSessionManager的API前，需要先通过[getSessionManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioManager.md#getsessionmanager12)获取一个单例AudioSessionManager对象。

使用OHAudio开发请参考：[获取音频会话管理器](using-ohaudio-for-session.md#获取音频会话管理器)。

<!-- @[get_sessionmanager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
```

## 音频会话策略

应用在激活AudioSession时，需先指定[音频会话策略（AudioSessionStrategy）](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessionstrategy12)。可通过设置[音频并发模式（AudioConcurrencyMode）](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audioconcurrencymode12)来指定不同的音频会话策略。

使用OHAudio开发请参考：[音频会话策略（OH_AudioSession_Strategy）](../../reference/apis-audio-kit/capi-ohaudio-oh-audiosession-strategy.md)

系统预设的音频并发模式如下所示：

- 默认模式（CONCURRENCY_DEFAULT）：即系统默认的[音频焦点策略](audio-playback-concurrency.md#音频焦点策略)。

- 并发模式（CONCURRENCY_MIX_WITH_OTHERS）：和其他音频流并发。

    **典型场景：**
    - 应用播放音乐时，会被后起的音乐或视频打断，应用希望自身的音频流和后起的音乐或视频并发（该场景需要应用在音频流启动前激活AudioSession）。

    - 应用录音时，会打断后台正在播放的音乐或视频，应用希望自身的音频流和后台正在播放的音乐或视频并发（该场景需要应用在音频流启动前激活AudioSession）。

- 降低音量模式（CONCURRENCY_DUCK_OTHERS）：和其他音频流并发，并且降低其他音频流的音量。

    **典型场景：** 应用播放游戏音效时，会和后台正在播放的音乐并发，应用希望自身的音频流和后台正在播放的音乐并发时压低后台音乐音量（该场景需要应用在音频流启动前激活AudioSession）。

- 暂停模式（CONCURRENCY_PAUSE_OTHERS）：暂停其他音频流，待释放焦点后通知其他音频流恢复。

    **典型场景：** 应用播放短视频时，会打断后台正在播放的音乐，应用希望自身的音频流停止后，后台的音乐可以自动恢复（该场景需要应用在音频流启动前激活AudioSession，音频流停止后停用AudioSession）。

> **注意：**
>
> - 当应用通过AudioSession使用上述各种模式时，系统将尽量满足其焦点策略，但可能无法保证在所有场景下完全满足。
> - 并发模式（CONCURRENCY_MIX_WITH_OTHERS）在本应用申请焦点和后续其他应用申请焦点时均会生效；降低音量模式（CONCURRENCY_DUCK_OTHERS）和暂停模式（CONCURRENCY_PAUSE_OTHERS）仅在本应用申请焦点时生效，后续其他应用申请焦点时，优先遵循其他应用的并发模式。

## 使用音频会话修改焦点策略

系统默认焦点策略不能满足应用当前需求时，应用可通过指定[音频会话策略](#音频会话策略)后激活AudioSession来完成焦点策略修改。

AudioSession激活成功后，应用新起的音频流将会按照修改后的焦点策略起流。

使用AudioSession修改焦点策略时，AudioSession不会持有焦点，焦点仍由各个音频流持有。

使用OHAudio开发请参考：[使用OHAudio开发音频会话功能(C/C++)](using-ohaudio-for-session.md)。

> **注意：**
> 
> 当AudioSession因超时而停用时，被其压低音量（Duck）的音频会触发恢复音量（Unduck）操作，被其暂停（Pause）的音频流会触发停止（Stop）操作。

### AudioSession停用事件

应用在使用AudioSession的过程中，推荐应用监听音频会话停用事件（AudioSessionDeactivatedEvent）。当AudioSession被停用（非主动停用）时，应用会收到此事件通知。应用可根据自身业务需求，做相应的处理，例如释放相应资源、重新激活AudioSession等。

音频会话停用事件（AudioSessionDeactivatedEvent）包含参数音频会话停用原因（AudioSessionDeactivatedReason），该参数表示AudioSession被停用的原因，主要有两种：

1. 应用焦点被抢占（DEACTIVATED_LOWER_PRIORITY）：该应用所有的音频流持有的焦点全部被其他应用抢占时，AudioSession被同时停用。

2. 超时（DEACTIVATED_TIMEOUT）：若AudioSession处于激活状态，但该应用没有音频流在运行状态，则AudioSession会在规定时间后被超时停用。

### 开发步骤

1. 指定音频会话策略（AudioSessionStrategy）并激活音频会话。

   应用可以通过[activateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#activateaudiosession12)接口激活当前应用的音频会话。

   应用在激活AudioSession时，需指定[音频会话策略](#音频会话策略)。策略中包含参数concurrencyMode，其类型为[AudioConcurrencyMode](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audioconcurrencymode12)，用于声明音频并发策略。

   ```ts
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   let strategy: audio.AudioSessionStrategy = {
     concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
   };
   
   audioSessionManager.activateAudioSession(strategy).then(() => {
     console.info('Succeeded in activating audio session.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to activate audio session. Code: ${err.code}, message: ${err.message}`);
   });
   ```

2. 查询音频会话是否已激活（可选）。

   应用可以通过[isAudioSessionActivated](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#isaudiosessionactivated12)接口检查当前应用的音频会话是否已激活。

   ```ts
   let isActivated = audioSessionManager.isAudioSessionActivated();
   ```

3. 监听音频会话停用事件（可选）。

   应用可以通过[on('audioSessionDeactivated')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#onaudiosessiondeactivated12)接口监听[音频会话停用事件（AudioSessionDeactivatedEvent）](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessiondeactivatedevent12)。

   当AudioSession被停用（非主动停用）时，应用会收到[音频会话停用事件（AudioSessionDeactivatedEvent）](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessiondeactivatedevent12)，其中包含[音频会话停用原因（AudioSessionDeactivatedReason）](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audiosessiondeactivatedreason12)。

   在收到AudioSessionDeactivatedEvent时，应用可根据自身业务需求，做相应的处理，例如释放相应资源、重新激活AudioSession等。

   应用可以通过[off('audioSessionDeactivated')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#offaudiosessiondeactivated12)接口取消监听音频会话停用事件。

   ```ts
   import { audio } from '@kit.AudioKit';

   audioSessionManager.on('audioSessionDeactivated', (audioSessionDeactivatedEvent: audio.AudioSessionDeactivatedEvent) => {
     console.info(`Succeeded in using on function. AudioSessionDeactivatedEvent: ${JSON.stringify(audioSessionDeactivatedEvent)}`);
   });
   ```

4. 停用音频会话。

   应用可以通过[deactivateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#deactivateaudiosession12)接口停用当前应用的音频会话。

   > **说明：**
   >
   > AudioSession停用后，应用新起的音频流将会按照默认焦点策略起流。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';

   audioSessionManager.deactivateAudioSession().then(() => {
     console.info('Succeeded in deactivating audio session.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to deactivate audio session. Code: ${err.code}, message: ${err.message}`);
   });
   ```

### 完整示例

下面展示了使用AudioSession修改焦点策略的示例代码。

<!-- @[all_sessionprocess](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
// ...
  let strategy: audio.AudioSessionStrategy = {
    concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
  };

  // 激活AudioSession，即抢占焦点
  audioSessionManager.activateAudioSession(strategy).then(() => {
    console.info('Succeeded in doing activateAudioSession.');
    if (globalLogUpdate) {
      globalLogUpdate('Succeeded in doing activateAudioSession.', false);
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to activateAudioSession. Code: ${err.code}, message: ${err.message}`);
    if (globalLogUpdate) {
      globalLogUpdate(`Failed to activateAudioSession. Code: ${err.code}, message: ${err.message}`, true);
    }
  });
  let isActivated = audioSessionManager.isAudioSessionActivated();
  // ...
  audioSessionManager.on('audioSessionDeactivated', (audioSessionDeactivatedEvent: audio
  .AudioSessionDeactivatedEvent) => {
    console.info(`reason of audioSessionDeactivated: ${audioSessionDeactivatedEvent.reason} `);
    if (globalCallbackUpdate) {
      globalCallbackUpdate(`reason of audioSessionDeactivated: ${audioSessionDeactivatedEvent.reason}`);
    }
  });
  // ...
  // 结束AudioSession，即释放焦点
  audioSessionManager.deactivateAudioSession().then(() => {
    console.info('Succeeded in doing deactivateAudioSession.');
    if (globalLogUpdate) {
      globalLogUpdate('Succeeded in doing deactivateAudioSession.', false);
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to deactivateAudioSession. Code: ${err.code}, message: ${err.message}`);
    if (globalLogUpdate) {
      globalLogUpdate(`Failed to deactivateAudioSession. Code: ${err.code}, message: ${err.message}`, true);
    }
  });
  // ...
  audioSessionManager.off('audioSessionDeactivated');
```
## 使用音频会话申请焦点策略

当应用需要启动多个音频流并保证流程连续性时，可通过AudioSession申请焦点，确保多音频流播放的连续性。

激活AudioSession时系统会根据应用选择的[音频会话场景](#音频会话场景)申请对应的音频焦点并由AudioSession持有该焦点，后续应用通过AudioRenderer启动的播放流将不再申请音频焦点。

使用OHAudio开发请参考：[使用OHAudio开发音频会话功能(C/C++)](using-ohaudio-for-session.md)。

典型使用场景如下：
- 在多个小视频滑动播放时，多个音频流频繁申请和释放焦点可能导致漏音。使用AudioSession申请一次焦点，可以避免中间多个音频流播放时频繁申请和释放焦点，从而防止漏音。
- 在VoIP通话场景下，可能需要启动铃声流、录音流和播放流，这些音频流的焦点优先级不同，部分音频流可能被其他应用的音频流中断。为了保持业务体验的连续性，可以使用AudioSession申请焦点，避免音频流被中断。
- 应用使用播放器的SDK播放音频流，不持有AudioRenderer对象，但希望监听焦点变化。

> **注意：**
>
> - AudioSession申请的焦点是应用级别的，如果应用内部包含不同的模块，各个模块间要做好协调处理，避免其中一个模块使用AudioSession申请了焦点，另一个模块的音频流被AudioSession的焦点管控而产生非预期的效果。
> - 通过AudioSession申请焦点，仅对播放流有效，对录音流及部分播放音频流（如STREAM_USAGE_ALARM、STREAM_USAGE_NOTIFICATION、STREAM_USAGE_ACCESSIBILITY等）无效。
> - 在AudioSession激活过程中，如果动态修改AudioSessionScene，需要重新调用activateAudioSession才能生效。
> - 通过AudioSession申请焦点后，焦点由AudioSession持有。应用当前播放场景结束后，需要主动停用AudioSession才会释放焦点。避免出现播放流停止后，焦点未释放导致的焦点异常持有。

### 音频会话场景

使用AudioSession申请焦点策略时，系统提供了三种音频会话场景。激活AudioSession前需要先通过[setAudioSessionScene](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setaudiosessionscene20)设置对应的音频会话场景，后续AudioSession激活时系统会根据应用选择的音频会话场景申请对应的音频焦点。

| 名称                   | 值 | 说明      |
| :--------------------- |:--|:--------|
| AUDIO_SESSION_SCENE_MEDIA | 0 | 媒体音频会话场景。     |
| AUDIO_SESSION_SCENE_GAME | 1 | 游戏音频会话场景。     |
| AUDIO_SESSION_SCENE_VOICE_COMMUNICATION  | 2 | VoIP语音通话音频会话场景。 |

### 监听AudioSession焦点和状态变化事件

AudioSession申请的焦点和AudioRenderer申请的焦点是同等地位。

应用可以通过[on('audioSessionStateChanged')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#onaudiosessionstatechanged20)来监听AudioSession的焦点和状态变化。为了维持应用和系统的状态一致性，确保良好的用户体验，应用应监听AudioSession焦点状态事件，并在焦点变化时做出必要响应。

[on('audioSessionStateChanged')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#onaudiosessionstatechanged20)包含了[AudioSession停用事件](#audiosession停用事件)的信息，当[使用音频会话申请焦点策略](#使用音频会话申请焦点策略)时无需再额外监听音频会话停用事件（AudioSessionDeactivatedEvent）。

> **说明：**
>
> 如果应用同时注册了AudioRenderer的焦点事件监听，需要注意以下两点：
> 1. 应用会收到AudioSession焦点状态变化和AudioRenderer焦点变化的回调（[InterruptEvent](../../reference/apis-audio-kit/arkts-apis-audio-i.md#interruptevent9)），根据需要处理这些回调即可。
> 2. 如果AudioSession的焦点被暂停，恢复暂停状态时，只会给AudioSession发送焦点恢复事件，不会再给AudioRenderer发送焦点恢复事件。

### 开发步骤

1. 指定音频会话场景（AudioSessionScene）和策略（AudioSessionStrategy）并激活音频会话。

   应用通过AudioSession申请焦点。首先要调用接口[setAudioSessionScene](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setaudiosessionscene20)设置场景参数，然后调用[activateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#activateaudiosession12)接口激活AudioSession。激活AudioSession时系统会根据应用选择的音频会话场景申请对应的音频焦点。

   > **说明：**
   >
   > - 激活AudioSession时系统会根据应用选择的音频会话场景申请对应的音频焦点，后续应用通过AudioRenderer启动的播放流不再申请音频焦点。
   > - 如果激活AudioSession时应用已存在启动的音频播放流，系统会释放该音频播放流持有的焦点，并由AudioSession统一管理。

   ```ts
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   audioSessionManager.setAudioSessionScene(audio.AudioSessionScene.AUDIO_SESSION_SCENE_MEDIA);

   let strategy: audio.AudioSessionStrategy = {
     concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
   };

   audioSessionManager.activateAudioSession(strategy).then(() => {
     console.info('Succeeded in activating audio session.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to activate audio session. Code: ${err.code}, message: ${err.message}`);
   });
   ```

2. 查询音频会话是否已激活（可选）。

   应用可以通过[isAudioSessionActivated](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#isaudiosessionactivated12)接口检查当前应用的音频会话是否已激活。

   ```ts
   let isActivated = audioSessionManager.isAudioSessionActivated();
   ```

3. 监听AudioSession焦点状态变化事件。

   应用可以通过[on('audioSessionStateChanged')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#onaudiosessionstatechanged20)来监听AudioSession的焦点和状态变化。

   ```ts
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   let audioSessionStateChangedCallback = (audioSessionStateChangedEvent: audio.AudioSessionStateChangedEvent) => {
     console.info(`hint of audioSessionStateChanged: ${audioSessionStateChangedEvent.stateChangeHint} `);

     switch (audioSessionStateChangedEvent.stateChangeHint) {
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE:
         // 此分支表示系统已将音频流暂停，应用需切换至音频暂停状态。
         // 临时失去焦点：其他音频流释放音频焦点后，本音频流会收到resume事件，可继续播放。
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_RESUME:
         // 此分支表示系统解除AudioSession焦点的暂停操作。
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_STOP:
         // 此分支表示系统已将音频流停止（永久失去焦点），为保持状态一致，应用需切换至音频暂停状态。
         // 永久失去焦点：后续不会再收到音频焦点事件，恢复播放需用户主动触发。
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP:
         // 此分支表示由于长时间无音频流播放，系统已将AudioSession停止（永久失去焦点），应用需切换至音频暂停状态。
         // 永久失去焦点：后续不会再收到音频焦点事件，恢复播放需用户主动触发。
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_DUCK:
         // 此分支表示系统已将音频音量降低（默认降到正常音量的20%）。
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK:
         // 此分支表示系统已将音频音量恢复正常。
         break;
       default:
         break;
     }
   };

   audioSessionManager.on('audioSessionStateChanged', audioSessionStateChangedCallback);
   ```

3. 停用音频会话。

   应用可以通过[deactivateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#deactivateaudiosession12)接口停用当前应用的音频会话。

   > **说明：**
   >
   > - 停用AudioSession时系统会释放AudioSession申请的焦点，并停用该应用正在播放的所有音频流。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';

   audioSessionManager.deactivateAudioSession().then(() => {
     console.info('Succeeded in doing deactivateAudioSession.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to deactivateAudioSession. Code: ${err.code}, message: ${err.message}`);
   });
   ```

### 完整示例

下面展示了使用AudioSession申请焦点策略的示例代码。

<!-- @[all_focusprocess](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';  // 导入audio模块。
import { BusinessError } from '@kit.BasicServicesKit'; // 导入BusinessError。

// ...

let audioSessionStateChangedCallback = (audioSessionStateChangedEvent: audio.AudioSessionStateChangedEvent) => {
  console.info(`hint of audioSessionStateChanged: ${audioSessionStateChangedEvent.stateChangeHint} `);

  // ...

  switch (audioSessionStateChangedEvent.stateChangeHint) {
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE:
      // 此分支表示系统已将音频流暂停，应用需切换至音频暂停状态。
      // 临时失去焦点：其他音频流释放音频焦点后，本音频流会收到resume事件，可继续播放。
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_RESUME:
      // 此分支表示系统解除AudioSession焦点的暂停操作。
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_STOP:
      // 此分支表示系统已将音频流停止（永久失去焦点），为保持状态一致，应用需切换至音频暂停状态。
      // 永久失去焦点：后续不会再收到音频焦点事件，恢复播放需用户主动触发。
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP:
      // 此分支表示由于长时间无音频流播放，系统已将AudioSession停止（永久失去焦点），应用需切换至音频暂停状态。
      // 永久失去焦点：后续不会再收到音频焦点事件，恢复播放需用户主动触发。
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_DUCK:
      // 此分支表示系统已将音频音量降低（默认降到正常音量的20%）。
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK:
      // 此分支表示系统已将音频音量恢复正常。
      break;
    default:
      break;
  }
};

let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
// ...
  audioSessionManager.setAudioSessionScene(audio.AudioSessionScene.AUDIO_SESSION_SCENE_MEDIA);
  // ...
  // 激活AudioSession，即抢占焦点
  audioSessionManager.activateAudioSession(strategy).then(() => {
    console.info('Succeeded in doing activateAudioSession.');
    if (globalLogUpdate) {
      globalLogUpdate('Succeeded in doing activateAudioSession.', false);
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to activateAudioSession. Code: ${err.code}, message: ${err.message}`);
    if (globalLogUpdate) {
      globalLogUpdate(`Failed to activateAudioSession. Code: ${err.code}, message: ${err.message}`, true);
    }
  });
  let isActivated = audioSessionManager.isAudioSessionActivated();
  if (!isActivated) {
    console.error(`session is not activated.`);
  } else {
    console.info('session is activated.');
  }

  audioSessionManager.on('audioSessionStateChanged', audioSessionStateChangedCallback);
  audioSessionManager.on('audioSessionDeactivated', (audioSessionDeactivatedEvent: audio
  .AudioSessionDeactivatedEvent) => {
    console.info(`reason of audioSessionDeactivated: ${audioSessionDeactivatedEvent.reason} `);
    if (globalCallbackUpdate) {
      globalCallbackUpdate(`reason of audioSessionDeactivated: ${audioSessionDeactivatedEvent.reason}`);
    }
  });
}
// 根据实际业务，可以启动多个AudioRenderer等音频播放。
// ...
  // 结束AudioSession，即释放焦点
  audioSessionManager.deactivateAudioSession().then(() => {
    console.info('Succeeded in doing deactivateAudioSession.');
    // ...
  }).catch((err: BusinessError) => {
    console.error(`Failed to deactivateAudioSession. Code: ${err.code}, message: ${err.message}`);
    // ...
  });
  // ...
  audioSessionManager.off('audioSessionStateChanged', audioSessionStateChangedCallback);
```
