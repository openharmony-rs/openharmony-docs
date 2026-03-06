# 使用AudioSession管理应用音频焦点(ArkTS)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

对于涉及多个音频流并发播放的场景，系统已预设了默认的[音频焦点策略](audio-playback-concurrency.md#音频焦点策略)，该策略将对所有音频流（包括播放和录制）实施统一的焦点管理。

应用可利用音频会话管理（AudioSessionManager）提供的接口，通过AudioSession主动管理应用内音频流的焦点，自定义本应用音频流的焦点策略，调整本应用音频流释放音频焦点的时机，从而贴合应用特定的使用需求。

本文档主要介绍AudioSession相关ArkTS API的使用方法和注意事项，更多音频焦点及音频会话的信息，可参考：[音频焦点和音频会话介绍](audio-playback-concurrency.md)。

以下各步骤示例为片段代码，可通过示例代码右下方链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS)。

## 获取音频会话管理器

创建AudioSessionManager实例。在使用AudioSessionManager的API前，需要先通过[getSessionManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioManager.md#getsessionmanager12)创建实例。

<!-- @[get_sessionmanager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
```

## 激活音频会话

应用可以通过[AudioSessionManager.activateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#activateaudiosession12)接口激活当前应用的音频会话。

应用在激活AudioSession时，需指定[音频会话策略（AudioSessionStrategy）](audio-playback-concurrency.md#音频会话策略audiosessionstrategy)。策略中包含参数concurrencyMode，其类型为[AudioConcurrencyMode](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audioconcurrencymode12)，用于声明音频并发策略。

<!-- @[active_audiosession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let strategy: audio.AudioSessionStrategy = {
  concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
};

// 激活AudioSession，即抢占焦点
audioSessionManager.activateAudioSession(strategy).then(() => {
  console.info('Succeeded in doing activateAudioSession.');
  // ...
}).catch((err: BusinessError) => {
  console.error(`Failed to activateAudioSession. Code: ${err.code}, message: ${err.message}`);
  // ...
});
```

## 查询音频会话是否已激活

应用可以通过[isAudioSessionActivated](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#isaudiosessionactivated12)接口检查当前应用的音频会话是否已激活。

<!-- @[audiosession_checkisactivated](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let isActivated = audioSessionManager.isAudioSessionActivated();
```

## 停用音频会话

应用可以通过[deactivateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#deactivateaudiosession12)接口停用当前应用的音频会话。

<!-- @[deactive_audiosession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
async function deactiveSession(){
  // 结束AudioSession，即释放焦点
  audioSessionManager.deactivateAudioSession().then(() => {
    console.info('Succeeded in doing deactivateAudioSession.');
    // ...
  }).catch((err: BusinessError) => {
    console.error(`Failed to deactivateAudioSession. Code: ${err.code}, message: ${err.message}`);
    // ...
  });
```

## 监听音频会话停用事件

应用可以通过[on('audioSessionDeactivated')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#onaudiosessiondeactivated12)接口监听[音频会话停用事件（AudioSessionDeactivatedEvent）](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessiondeactivatedevent12)。

当AudioSession被停用（非主动停用）时，应用会收到[音频会话停用事件（AudioSessionDeactivatedEvent）](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessiondeactivatedevent12)，其中包含[音频会话停用原因（AudioSessionDeactivatedReason）](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audiosessiondeactivatedreason12)。

在收到AudioSessionDeactivatedEvent时，应用可根据自身业务需求，做相应的处理，例如释放相应资源、重新激活AudioSession等。

<!-- @[listen_audiosessiondeactiveevent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
audioSessionManager.on('audioSessionDeactivated', (audioSessionDeactivatedEvent: audio
  .AudioSessionDeactivatedEvent) => {
    console.info(`reason of audioSessionDeactivated: ${audioSessionDeactivatedEvent.reason} `);
    // ...
  });
```

## 取消监听音频会话停用事件

应用可以通过[off('audioSessionDeactivated')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#offaudiosessiondeactivated12)接口取消监听音频会话停用事件。

<!-- @[cancellisten_audiosessiondeactiveevent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
audioSessionManager.off('audioSessionDeactivated');
```

**音频会话从创建到激活并监听的完整示例：**

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

## 通过设置AudioSession场景参数申请焦点
应用通过AudioSession申请焦点。首先要调用接口[setAudioSessionScene](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setaudiosessionscene20)设置场景参数，然后调用[activateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#activateaudiosession12)接口激活AudioSession。

<!-- @[set_audioscene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
audioSessionManager.setAudioSessionScene(audio.AudioSessionScene.AUDIO_SESSION_SCENE_MEDIA);
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
```

## 启用混音播放下静音建议通知
从API version 23开始，当本应用在并发模式为CONCURRENCY_MIX_WITH_OTHERS下进行播放时，如果有其他应用的音频同时播放，此时两者会混合播放。部分场景下（如游戏或广播），应用可以通过启用静音建议通知，以给用户提供更好的体验。

启用静音建议通知后，本应用播放音频的同时，其他应用播放了不可与本应用并发播放的音频，本应用会收到静音建议通知，此时本应用可以选择不做处理，让本应用和其他应用进行并发播放；也可以选择将自身静音播放，让其他应用单独播放音频。

启用混音播放下静音建议通知，需要先调用接口[setAudioSessionScene](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setaudiosessionscene20)设置场景参数并订阅音频会话状态更改事件[AudioSessionStateChangedEvent](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessionstatechangedevent20)，启用后再调用[activateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#activateaudiosession12)接口激活AudioSession。启用静音建议通知的前提是[AudioConcurrencyMode](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audioconcurrencymode12)模式必须为CONCURRENCY_MIX_WITH_OTHERS。

<!-- @[enable_muteSuggestion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
audioSessionManager.setAudioSessionScene(audio.AudioSessionScene.AUDIO_SESSION_SCENE_MEDIA);
// ...
audioSessionManager.enableMuteSuggestionWhenMixWithOthers(true);
// ...
let strategy: audio.AudioSessionStrategy = {
  concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
};

// 激活AudioSession，即抢占焦点
audioSessionManager.activateAudioSession(strategy).then(() => {
  console.info('Succeeded in doing activateAudioSession.');
  // ...
}).catch((err: BusinessError) => {
  console.error(`Failed to activateAudioSession. Code: ${err.code}, message: ${err.message}`);
  // ...
});
```

## 监听AudioSession焦点状态变化事件

通过[AudioSession焦点状态事件（AudioSessionStateChangedEvent）](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessionstatechangedevent20)监听音频会话焦点状态的变化。

**AudioSession申请焦点以及监听焦点变化事件的完整示例：**

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
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_MUTE_SUGGESTION:
      // 此分支表示其他应用开始播放非混音音频，系统可自行决定是否静音。
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE_SUGGESTION:
      // 此分支表示其他应用的非混音音频播放结束，系统可自行决定是否取消静音。
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
  // 示例中选择了CONCURRENCY_MIX_WITH_OTHERS策略，请根据具体场景修改该参数。
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