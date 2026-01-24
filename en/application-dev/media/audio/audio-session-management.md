# Audio Session Management
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

For scenarios involving concurrent playback of multiple audio streams, the system has preset a default [Audio Focus Strategy](audio-playback-concurrency.md#audio-focus-strategy), which enforces unified focus management for all audio streams (including playback and recording).

When the default focus policy provided by the system fails to meet the application's requirements, the application can use the APIs provided by audio session management to manage the focus of audio streams within the application, customize the focus policy for audio streams, and adjust the timing of releasing focus for audio streams to meet specific needs. All sample codes in this document are in ArkTS. If you need to develop with OHAudio, refer to [Using OHAudio for Audio Session (C/C++)](using-ohaudio-for-session.md).

Using audio session-related APIs enables the following functions:

- When the system's default focus policy cannot meet the application's current needs, the application can [modify the focus policy using AudioSession](#modifying-the-focus-policy-using-audiosession) to adapt a focus policy suitable for itself.

  Typical scenario: When an application plays short videos, it interrupts background music. The application expects the background music to resume automatically after its own audio stream stops. This scenario requires the application to activate an **AudioSession** before starting the audio stream and deactivate it after the audio stream stops.

- When an application needs to start multiple audio streams in a service process and ensure the integrity of the entire process, the application can [apply for a focus policy using AudioSession](#applying-for-a-focus-policy-using-audiosession) to adapt a focus policy suitable for its service scenario.

  Typical scenario: When an application plays multiple audio files continuously, it does not want other interrupted background audio to resume automatically during the gaps between audio playback, and expects to maintain the continuity of audio focus throughout the playback process. This scenario requires the application to activate an **AudioSession** before the start of the entire playback process and deactivate it after the entire playback process ends).

> **NOTE**
>
> - The priority of audio concurrency policies is: **STOP** > **PAUSE** > **DUCK** > **PLAYBOTH**. If the specified audio session policy has a higher priority than the default concurrency policy, the specified audio session policy will not take effect.
> - The application must ensure that the audio session is activated before starting audio playback or recording; otherwise, the custom focus policy of the audio session will not take effect. If the application uses asynchronous APIs, special attention must be paid to the timing of asynchronous operations.

## Obtaining an Audio Session Manager

Before using the APIs of **AudioSessionManager**, you need to obtain a singleton **AudioSessionManager** object through [getSessionManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioManager.md#getsessionmanager12).

For development with OHAudio, see [Obtaining an Audio Session Manager](using-ohaudio-for-session.md#obtaining-an-audio-session-manager).

<!-- @[get_sessionmanager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
```

## Audio Session Strategy

Before activating an audio session, you must first specify an [audio session strategy (AudioSessionStrategy)](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessionstrategy12) by setting an [audio concurrency mode (AudioConcurrencyMode)](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audioconcurrencymode12).

For development with OHAudio, see [OH_AudioSession_Strategy](../../reference/apis-audio-kit/capi-ohaudio-oh-audiosession-strategy.md).

The preset audio concurrency modes are as follows:

- **CONCURRENCY_DEFAULT**: default [audio focus strategy](audio-playback-concurrency.md#audio-focus-strategy) of the system.

- **CONCURRENCY_MIX_WITH_OTHERS**: concurrent playback with other audio streams.

    **Typical scenarios:**
    - When an application plays music, it is interrupted by subsequent music or video playback. The application expects its own audio stream to be concurrent with the subsequent music or video. This scenario requires the application to activate an **AudioSession** before starting the audio stream).

    - When an application records audio, it interrupts background music or video playback. The application expects its own audio stream to be concurrent with the background music or video. This scenario requires the application to activate an **AudioSession** before starting the audio stream.

- **CONCURRENCY_DUCK_OTHERS**: concurrent with other audio streams and reduces the volume of other audio streams.

    **Typical scenario**: When an application plays game sound effects, it is concurrent with background music playback. The application expects to lower the volume of the background music when its own audio stream is concurrent with it (this scenario requires the application to activate an **AudioSession** before starting the audio stream).

- **CONCURRENCY_PAUSE_OTHERS**: pauses other audio streams and notifies them to resume after releasing the focus.

    **Typical scenario**: When an application plays short videos, it interrupts background music. The application expects the background music to resume automatically after its own audio stream stops. This scenario requires the application to activate an **AudioSession** before starting the audio stream and deactivate it after the audio stream stops.

> **NOTE**
>
> - When an application uses the above modes through **AudioSession**, the system will try to meet its focus policy but cannot guarantee fulfillment in all scenarios.
> - The **CONCURRENCY_MIX_WITH_OTHERS** mode takes effect both when the application applies for focus and when other applications apply for focus subsequently. The **CONCURRENCY_DUCK_OTHERS** and **CONCURRENCY_PAUSE_OTHERS** modes only take effect when the application applies for focus; when other applications apply for focus subsequently, the concurrency mode of the other applications is followed first.

## Modifying the Focus Policy Using AudioSession

When the system's default focus policy cannot meet the application's current needs, the application can modify the focus policy by specifying an [Audio Session Strategy](#audio-session-strategy) and then activating an **AudioSession**.

After the **AudioSession** is successfully activated, new audio streams started by the application will follow the modified focus policy.

When the focus policy is modified using **AudioSession**, the **AudioSession** does not hold the focus. The focus is still held by each individual audio stream.

For development with OHAudio, see [Using OHAudio for Audio Session (C/C++)](using-ohaudio-for-session.md).

> **NOTE**
> 
> When an **AudioSession** is deactivated due to timeout, audio streams whose volume was lowered (duck) by it will trigger an unduck operation, and audio streams that were paused by it will trigger a stop operation.

### AudioSession Deactivation Event

During the use of **AudioSession**, it is recommended that the application listen to the **AudioSessionDeactivatedEvent**. When the **AudioSession** is deactivated (not actively), the application will receive this event notification. The application can take corresponding actions according to its service needs, such as releasing relevant resources or reactivating the **AudioSession**.

The **AudioSessionDeactivatedEvent** contains the parameter **AudioSessionDeactivatedReason**, which indicates the reason for the deactivation of the **AudioSession**. There are two main reasons:

1. **DEACTIVATED_LOWER_PRIORITY**: When all focus held by the audio streams of the application is preempted by other applications, the **AudioSession** is deactivated at the same time.

2. **DEACTIVATED_TIMEOUT**: If the **AudioSession** is in the activated state but there are no running audio streams in the application, the **AudioSession** will be deactivated due to timeout after a specified period of time.

### How to Develop

1. Specify the audio session strategy (**AudioSessionStrategy**) and activate an **AudioSession**.

   Call [activateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#activateaudiosession12) to activate an **AudioSession**.

   Specify the [audio session policy](#audio-session-policy) when activating the **AudioSession**. The strategy contains the **concurrencyMode** parameter, which is of the [AudioConcurrencyMode](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audioconcurrencymode12) type and is used to declare the audio concurrency strategy.

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

2. (Optional) Check whether the audio session is activated.

   Call [isAudioSessionActivated](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#isaudiosessionactivated12) to check whether the audio session is activated.

   ```ts
   let isActivated = audioSessionManager.isAudioSessionActivated();
   ```

3. (Optional) Listen for the audio session deactivation event.

   Call [on('audioSessionDeactivated')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#onaudiosessiondeactivated12) to listen for the [AudioSessionDeactivatedEvent](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessiondeactivatedevent12) event.

   When an audio session is deactivated (not proactively), the application receives the [AudioSessionDeactivatedEvent](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiosessiondeactivatedevent12), which contains the parameter [AudioSessionDeactivatedReason](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audiosessiondeactivatedreason12).

   Upon this event, the application can perform operations based on service requirements, for example, releasing resources or reactivating the audio session.

   The application can call [off('audioSessionDeactivated')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#offaudiosessiondeactivated12) to cancel listening for the **AudioSessionDeactivatedEvent**.

   ```ts
   import { audio } from '@kit.AudioKit';

   audioSessionManager.on('audioSessionDeactivated', (audioSessionDeactivatedEvent: audio.AudioSessionDeactivatedEvent) => {
     console.info(`Succeeded in using on function. AudioSessionDeactivatedEvent: ${JSON.stringify(audioSessionDeactivatedEvent)}`);
   });
   ```

4. Deactivate the **AudioSession**.

   Call [deactivateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#deactivateaudiosession12) to deactivate the **AudioSession**.

   > **NOTE**
   >
   > After the **AudioSession** is deactivated, new audio streams started by the application will follow the default focus policy.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';

   audioSessionManager.deactivateAudioSession().then(() => {
     console.info('Succeeded in deactivating audio session.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to deactivate audio session. Code: ${err.code}, message: ${err.message}`);
   });
   ```

### Sample Code

The following shows the sample code for modifying the focus policy using **AudioSession**.

<!-- @[all_sessionprocess](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
// ...
  let strategy: audio.AudioSessionStrategy = {
    concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
  };

  // Activate the audio session to gain focus.
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
  // Deactivate the audio session to release focus.
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
## Applying for a Focus Policy Using AudioSession

When an application needs to start multiple audio streams and ensure the continuity of the process, it can apply for focus through an **AudioSession** to ensure the continuity of playback of multiple audio streams.

During the activation of **AudioSession**, the system applies for the corresponding audio focus based on the [audio session scene](#audio-session-scene) selected by the application, and the **AudioSession** will hold the focus. Subsequent playback streams started by the application through **AudioRenderer** will no longer apply for audio focus.

For development with OHAudio, see [Using OHAudio for Audio Session (C/C++)](using-ohaudio-for-session.md).

Typical usage scenarios are as follows:
- When sliding to play multiple short videos, frequent application and release of focus by multiple audio streams may cause audio leakage. Applying for focus once through **AudioSession** can avoid frequent application and release of focus during the playback of multiple audio streams, thereby preventing audio leakage.
- In VoIP call scenarios, it may be necessary to start a ringtone stream, a recording stream, and a playback stream. These audio streams have different focus priorities, and some audio streams may be interrupted by audio streams of other applications. To maintain a continuous user experience, you can use **AudioSession** to request focus and avoid interruptions to the audio streams.
- The application uses the SDK of the player to play audio streams and does not hold the **AudioRenderer** object, but expects to listen for focus changes.

> **NOTE**
>
> - The focus applied for through **AudioSession** is at the application level. If the application contains different modules, the modules must coordinate with each other to avoid situations where one module applies for focus using **AudioSession**, causing audio streams of another module to be controlled by the focus of **AudioSession** and producing unintended effects.
> - Applying for focus through **AudioSession** is only valid for playback streams, and invalid for recording streams and some playback audio streams (such as **STREAM_USAGE_ALARM**, **STREAM_USAGE_NOTIFICATION**, and **STREAM_USAGE_ACCESSIBILITY**).
> - If the **AudioSessionScene** is dynamically modified during the activation of the **AudioSession**, **activateAudioSession** must be called again to take effect.
> - After the focus is applied for through **AudioSession**, the focus is held by the **AudioSession**. Once the current playback of the application ends, the application needs to actively deactivate the **AudioSession** to release the focus. This prevents the focus from being held abnormally after the playback stream stops.

### Audio Session Scene

When you use **AudioSession** to apply for a focus policy, the system provides three audio session scenes. Before activating the **AudioSession**, you need to set the corresponding audio session scene through [setAudioSessionScene](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setaudiosessionscene20). When the **AudioSession** is activated subsequently, the system will apply for the corresponding audio focus according to the audio session scene selected by the application.

| Name                  | Value| Description     |
| :--------------------- |:--|:--------|
| AUDIO_SESSION_SCENE_MEDIA | 0 | Media audio session.    |
| AUDIO_SESSION_SCENE_GAME | 1 | Game audio session.    |
| AUDIO_SESSION_SCENE_VOICE_COMMUNICATION  | 2 | VoIP voice call audio session.|

### Listening for AudioSession Focus State Change Events

The focus applied for through **AudioSession** is equivalent to that applied for through **AudioRenderer**.

The application can listen for focus state changes of the **AudioSession** through [on('audioSessionStateChanged')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#onaudiosessionstatechanged20). To maintain state consistency between the application and the system, the application should listen for the **AudioSession** focus state events and make necessary responses when the focus changes.

[on('audioSessionStateChanged')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#onaudiosessionstatechanged20) contains information about the [AudioSession deactivation event](#audiosession-deactivation-event). When [applying for a focus policy using AudioSession](#applying-for-a-focus-policy-using-audiosession), you do not need to listen for the **AudioSessionDeactivatedEvent**.

> **NOTE**
>
> If the application registers a listener for focus events of **AudioRenderer** at the same time, note the following:
> 1. The application will receive callbacks ([InterruptEvent](../../reference/apis-audio-kit/arkts-apis-audio-i.md#interruptevent9)) for both **AudioSession** focus state changes and **AudioRenderer** focus changes. Handle these callbacks as needed.
> 2. If the focus of the **AudioSession** is paused, only the **AudioSession** will receive the focus resume event when it is resumed, and the **AudioRenderer** will not receive the focus resume event.

### How to Develop

1. Specify the **AudioSessionScene** and **AudioSessionStrategy**, and activate an **AudioSession**.

   The application applies for focus through the **AudioSession**. Call [setAudioSessionScene](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setaudiosessionscene20) to set the scene parameters, and then call [activateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#activateaudiosession12) to activate the **AudioSession**. During the activation of **AudioSession**, the system will apply for the corresponding audio focus according to the audio session scene selected by the application.

   > **NOTE**
   >
   > - During the activation of **AudioSession**, the system will apply for the corresponding audio focus according to the audio session scene selected by the application. Subsequent playback streams started by the application through **AudioRenderer** will no longer apply for audio focus.
   > - If there are already active audio playback streams in the application before the **AudioSession** is activated, the system will release the focus held by these audio playback streams and manage it uniformly through the **AudioSession**.

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

2. (Optional) Check whether the audio session is activated.

   Call [isAudioSessionActivated](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#isaudiosessionactivated12) to check whether the audio session is activated.

   ```ts
   let isActivated = audioSessionManager.isAudioSessionActivated();
   ```

3. Listen for **AudioSession** focus state change events.

   Call [on('audioSessionStateChanged')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#onaudiosessionstatechanged20) to listen for focus state changes of the **AudioSession**.

   ```ts
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   let audioSessionStateChangedCallback = (audioSessionStateChangedEvent: audio.AudioSessionStateChangedEvent) => {
     console.info(`hint of audioSessionStateChanged: ${audioSessionStateChangedEvent.stateChangeHint} `);

     switch (audioSessionStateChangedEvent.stateChangeHint) {
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE:
         // The system has paused the audio stream. The application should switch to the audio paused state.
         // Temporarily losing focus: When other audio streams release focus, the application will receive a resume event and can resume playback.
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_RESUME:
         // The system has resumed the AudioSession.
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_STOP:
         // The system has stopped the audio stream (focus is permanently lost). To ensure state consistency, the application should switch to the audio paused state.
         // Permanently losing focus: No audio focus event will be received. The user must manually trigger the operation to resume playback.
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP:
         // The system has stopped the AudioSession (permanently losing focus) due to inactivity. The application should switch to the audio paused state.
         // Permanently losing focus: No audio focus event will be received. The user must manually trigger the operation to resume playback.
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_DUCK:
         // The system has ducked the volume down (to 20% of the normal volume by default).
         break;
       case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK:
         // The system has restored the audio volume to normal.
         break;
       default:
         break;
     }
   };

   audioSessionManager.on('audioSessionStateChanged', audioSessionStateChangedCallback);
   ```

3. Deactivate the **AudioSession**.

   Call [deactivateAudioSession](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#deactivateaudiosession12) to deactivate the **AudioSession**.

   > **NOTE**
   >
   > - When the **AudioSession** is deactivated, the system releases the focus applied by the **AudioSession** and stops all audio streams being played by the application.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';

   audioSessionManager.deactivateAudioSession().then(() => {
     console.info('Succeeded in doing deactivateAudioSession.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to deactivateAudioSession. Code: ${err.code}, message: ${err.message}`);
   });
   ```

### Sample Code

The following shows the sample code for applying for a focus policy using **AudioSession**.

<!-- @[all_focusprocess](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';  // Import the audio module.
import { BusinessError } from '@kit.BasicServicesKit'; // Import BusinessError.

// ...

let audioSessionStateChangedCallback = (audioSessionStateChangedEvent: audio.AudioSessionStateChangedEvent) => {
  console.info(`hint of audioSessionStateChanged: ${audioSessionStateChangedEvent.stateChangeHint} `);

  // ...

  switch (audioSessionStateChangedEvent.stateChangeHint) {
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE:
      // The system has paused the audio stream. The application should switch to the audio paused state.
      // Temporarily losing focus: When other audio streams release focus, the application will receive a resume event and can resume playback.
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_RESUME:
      // The system has resumed the AudioSession.
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_STOP:
      // The system has stopped the audio stream (focus is permanently lost). To ensure state consistency, the application should switch to the audio paused state.
      // Permanently losing focus: No audio focus event will be received. The user must manually trigger the operation to resume playback.
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP:
      // The system has stopped the AudioSession (permanently losing focus) due to inactivity. The application should switch to the audio paused state.
      // Permanently losing focus: No audio focus event will be received. The user must manually trigger the operation to resume playback.
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_DUCK:
      // The system has ducked the volume down (to 20% of the normal volume by default).
      break;
    case audio.AudioSessionStateChangeHint.AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK:
      // The system has restored the audio volume to normal.
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
  // Activate the AudioSession to gain focus.
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
// Start multiple audio renderers or other audio playback as needed.
// ...
  // Deactivate the AudioSession to release focus.
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
