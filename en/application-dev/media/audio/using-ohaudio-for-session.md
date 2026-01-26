# Using OHAudio for Audio Session (C/C++)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

In the scenario where multiple audio streams are concurrently playing, the system has preset a [default audio focus strategy](audio-playback-concurrency.md#audio-focus-strategy) for unified audio focus management of all streams (including playback and recording).

An application can use an audio session provided by the audio session manager to actively manage the audio focus. Specifically, it can customize an audio focus strategy and determine the timing for releasing the audio focus, thereby meeting its specific service needs.

This document mainly introduces the usage and precautions of the AudioSession-related C APIs. For more information about audio focus and audio sessions, see [Introduction to Audio Focus](audio-playback-concurrency.md) and [Audio Session Management](audio-session-management.md).

## Prerequisites

To use the audio session manager provided by OHAudio, add the corresponding header file.

### Linking the Dynamic Library in the CMake Script

``` cmake
target_link_libraries(sample PUBLIC libohaudio.so)
```

### Adding a Header File

Include the [native_audio_session_manager.h](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md) header file so that the application can use the functions related to audio playback.

<!-- @[cimport_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
#include "ohaudio/native_audio_session_manager.h"
```

## Obtaining an Audio Session Manager

Create an [OH_AudioSessionManager](../../reference/apis-audio-kit/capi-ohaudio-oh-audiosessionmanager.md) instance. Before using any APIs of OH_AudioSessionManager, you must use [OH_AudioManager_GetAudioSessionManager](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) to obtain an OH_AudioSessionManager instance.

<!-- @[cget_sessionmanager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
OH_AudioSessionManager *audioSessionManager;
// ...
    OH_AudioCommon_Result resultManager = OH_AudioManager_GetAudioSessionManager(&audioSessionManager);
    OH_AudioCommon_Result result = OH_AudioSessionManager_RegisterStateChangeCallback(audioSessionManager,
                                                                                      AudioSessionStateChangedCallback);
    if (resultManager == 0) {
        OH_LOG_Print(LOG_APP, LOG_INFO, g_audioSessionVariable->globalResmgr, SESSION_TAG,
                     " OH_AudioManager_GetAudioSessionManager success! ");
    }
```

## Activating an Audio Session

Call [OH_AudioSessionManager_ActivateAudioSession](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosessionmanager_activateaudiosession) to activate an audio session.

During the activation, specify an [audio session strategy](../../reference/apis-audio-kit/capi-ohaudio-oh-audiosession-strategy.md). The strategy contains the [OH_AudioSession_ConcurrencyMode](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosession_concurrencymode) parameter, which is used to declare the audio concurrency strategy.

<!-- @[cactive_sessionmanager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
// In this example, CONCURRENCY_MIX_WITH_OTHERS is selected. You can change the strategy as needed.
OH_AudioSession_Strategy strategy = {CONCURRENCY_MIX_WITH_OTHERS};
    
// Set an audio concurrency mode and activate an audio session.
OH_AudioSessionManager_ActivateAudioSession(audioSessionManager, &strategy);
```

## Checking Whether an Audio Session Is Activated

Call [OH_AudioSessionManager_IsAudioSessionActivated](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosessionmanager_isaudiosessionactivated) to check whether an audio session is activated.

<!-- @[ccheck_isactivated](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
bool isActivated = OH_AudioSessionManager_IsAudioSessionActivated(audioSessionManager);
```

## Deactivating an Audio Session

Call [OH_AudioSessionManager_DeactivateAudioSession](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosessionmanager_deactivateaudiosession) to deactivate an audio session.

<!-- @[cdeactive_audiosession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
OH_AudioCommon_Result result;
// ...
result = OH_AudioSessionManager_DeactivateAudioSession(audioSessionManager);
```

## Listening for Audio Session Deactivation Events

When using the audio session, you are advised to listen for the [OH_AudioSession_DeactivatedEvent](../../reference/apis-audio-kit/capi-ohaudio-oh-audiosession-deactivatedevent.md) event.

When an audio session is deactivated (not proactively), the application receives [OH_AudioSession_DeactivatedEvent](../../reference/apis-audio-kit/capi-ohaudio-oh-audiosession-deactivatedevent.md), which contains [OH_AudioSession_DeactivatedReason](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedreason).

Upon this event, the application can perform operations based on service requirements, for example, releasing resources or reactivating the audio session.

### Defining a Callback

<!-- @[cint_deacticatedcallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
int32_t MyAudioSessionDeactivatedCallback(OH_AudioSession_DeactivatedEvent event)
{
    switch (event.reason) {
        case DEACTIVATED_LOWER_PRIORITY:
          // The application focus is preempted.
            return 0;
        case DEACTIVATED_TIMEOUT:
          // A timeout error occurs.
            return 0;
    }
}

OH_AudioSessionManager *audioSessionManager;
```

### Registering a Callback to Listen for Audio Session Deactivation Events

Call [OH_AudioSessionManager_RegisterSessionDeactivatedCallback](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registersessiondeactivatedcallback) to register a callback to listen for audio session deactivation events.

<!-- @[cregist_deacticatedcallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
OH_AudioCommon_Result resultRegister = OH_AudioSessionManager_RegisterSessionDeactivatedCallback(
    audioSessionManager, MyAudioSessionDeactivatedCallback);
```

### Unregistering the Callback Used to Listen for Audio Session Deactivation Events

Call [OH_AudioSessionManager_UnregisterSessionDeactivatedCallback](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosessionmanager_unregistersessiondeactivatedcallback) to cancel listening for audio session deactivation events.

<!-- @[cunregist_deacticatedcallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
OH_AudioCommon_Result resultUnregister = OH_AudioSessionManager_UnregisterSessionDeactivatedCallback(
    audioSessionManager, MyAudioSessionDeactivatedCallback);
```

**Below is a comprehensive example of creating, activating, and listening for an audio session:**

Refer to the sample code below to complete the process of creating, activating, and listening of an audio session.

<!-- @[csessionactive_process](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
#include <cstdint>
#include "ohaudio/native_audio_session_manager.h"
// ...
int32_t MyAudioSessionDeactivatedCallback(OH_AudioSession_DeactivatedEvent event)
{
    switch (event.reason) {
        case DEACTIVATED_LOWER_PRIORITY:
          // The application focus is preempted.
            return 0;
        case DEACTIVATED_TIMEOUT:
          // A timeout error occurs.
            return 0;
    }
}

OH_AudioSessionManager *audioSessionManager;
// ...
    OH_AudioCommon_Result resultManager = OH_AudioManager_GetAudioSessionManager(&audioSessionManager);
    // ...
    OH_AudioSession_Strategy strategy = {CONCURRENCY_MIX_WITH_OTHERS};
    
    // Set an audio concurrency mode and activate an audio session.
    OH_AudioSessionManager_ActivateAudioSession(audioSessionManager, &strategy);
    // Check whether the audio session is activated.
    bool isActivated = OH_AudioSessionManager_IsAudioSessionActivated(audioSessionManager);
    if (isActivated) {
        OH_LOG_Print(LOG_APP, LOG_INFO, g_audioSessionVariable->globalResmgr, SESSION_TAG,
                     " AudioSessionManager is activated! ");
    }
    // Listen for audio session deactivation events.
    OH_AudioCommon_Result resultRegister = OH_AudioSessionManager_RegisterSessionDeactivatedCallback(
        audioSessionManager, MyAudioSessionDeactivatedCallback);
    // ...
    // Cancel listening for audio session deactivation events.
    result = OH_AudioSessionManager_UnregisterStateChangeCallback(audioSessionManager,
                                                                  AudioSessionStateChangedCallback);
    // ...
    // Deactivate the audio session.
    result = OH_AudioSessionManager_DeactivateAudioSession(audioSessionManager);
  ```
## Requesting Focus by Setting Audio Session Scene Parameters
The application requests focus using an audio session. Call [OH_AudioSessionManager_SetScene](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) to set the scene parameters, and then call [OH_AudioSessionManager_ActivateAudioSession](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosessionmanager_activateaudiosession) to activate the audio session.

<!-- @[cset_audioscene](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
// In this example, AUDIO_SESSION_SCENE_MEDIA is selected. You can change the session scene as needed.
OH_AudioSessionManager_SetScene(audioSessionManager, AUDIO_SESSION_SCENE_MEDIA);
// ...
// In this example, CONCURRENCY_MIX_WITH_OTHERS is selected. You can change the strategy as needed.
OH_AudioSession_Strategy strategy = {CONCURRENCY_MIX_WITH_OTHERS};
    
// Set an audio concurrency mode and activate an audio session.
OH_AudioSessionManager_ActivateAudioSession(audioSessionManager, &strategy);
  ```

## Listening for Audio Session Focus State Change events
Listen for audio session focus state changes through [OH_AudioSession_StateChangedEvent](../../reference/apis-audio-kit/capi-ohaudio-oh-audiosession-statechangedevent.md).

**Below is a comprehensive example of requesting focus for an audio session and listening for focus change events:**

<!-- @[clistencallback_process](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` cpp
OH_AudioSessionManager *audioSessionManager;

void AudioSessionStateChangedCallback(OH_AudioSession_StateChangedEvent event)
{
    switch (event.stateChangeHint) {
        case AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE:
          // The system has paused the audio stream (focus is temporarily lost). To ensure state consistency, the application needs to switch to the audio paused state.
          // Temporarily losing focus: When other audio streams release focus, the application will receive a resume event and can resume playback.
            break;
        case AUDIO_SESSION_STATE_CHANGE_HINT_RESUME:
          // The system has resumed the audio session.
            break;
        case AUDIO_SESSION_STATE_CHANGE_HINT_STOP:
          // The system has stopped the audio stream (focus is permanently lost). To ensure state consistency, the application should switch to the audio paused state.
          // Permanently losing focus: No audio focus event will be received. The user must manually trigger the operation to resume playback.
            break;
        case AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP:
          // This branch indicates that the system has stopped the AudioSession (permanently losing focus) due to no audio stream playback for an extended period.
          // This prevents long-term invalid occupation of system resources. To maintain state consistency, the application needs to switch to the audio pause state.
          // Permanently losing focus: No audio focus event will be received. The user must manually trigger the operation to resume playback.
            break;
        case AUDIO_SESSION_STATE_CHANGE_HINT_DUCK:
          // The system has ducked the volume down (to 20% of the normal volume by default).
            break;
        case AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK:
          // The system has restored the audio volume to normal.
            break;
        default:
            break;
    }
}
// ...
    OH_AudioCommon_Result result = OH_AudioSessionManager_RegisterStateChangeCallback(audioSessionManager,
                                                                                      AudioSessionStateChangedCallback);
    // ...
    // In this example, AUDIO_SESSION_SCENE_MEDIA is selected. You can change the session scene as needed.
    OH_AudioSessionManager_SetScene(audioSessionManager, AUDIO_SESSION_SCENE_MEDIA);
    // In this example, CONCURRENCY_MIX_WITH_OTHERS is selected. You can change the strategy as needed.
    OH_AudioSession_Strategy strategy = {CONCURRENCY_MIX_WITH_OTHERS};
    
    // Set an audio concurrency mode and activate an audio session.
    OH_AudioSessionManager_ActivateAudioSession(audioSessionManager, &strategy);
    // ...
    result = OH_AudioSessionManager_DeactivateAudioSession(audioSessionManager);
    // ...
    OH_AudioCommon_Result resultUnregister = OH_AudioSessionManager_UnregisterSessionDeactivatedCallback(
        audioSessionManager, MyAudioSessionDeactivatedCallback);
  ```
