# Using AVPlayer to Play Streaming Media (C/C++)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia--> 
<!--Owner: @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T07:17:18.344Z pushedAt=2026-06-03T10:17:55.661Z -->

Starting from API version 11, you can use [AVPlayer](../../reference/apis-media-kit/capi-avplayer.md) to implement end-to-end streaming media playback. This development guide uses a complete streaming media playback example to explain the streaming playback features of AVPlayer to developers.

The full playback process includes: creating an AVPlayer, setting callback listener functions, setting playback resources, setting playback parameters (volume/speed/focus mode), setting the playback window, playback control (play/pause/seek/stop), resetting, and destroying the player instance.

During application development, developers can proactively obtain playback process information through the AVPlayer information listener callback [OH_AVPlayerOnInfoCallback](../../reference/apis-media-kit/capi-avplayer-base-h.md#oh_avplayeroninfocallback) and the error listener callback [OH_AVPlayerOnErrorCallback](../../reference/apis-media-kit/capi-avplayer-base-h.md#oh_avplayeronerrorcallback). If the application performs an operation when the video player is in an error state, the system may throw an exception or generate other undefined behaviors.

For details about the states, see [AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate). When playback is in the prepared/playing/paused/completed state, the playback engine is in a working state, which consumes more system running memory. When the client is not using the player temporarily, call reset() or release() to reclaim memory resources and use resources properly.

**Playback state change diagram:**
![Playback status change](figures/playback-status-change-ndk.png)

## Development Suggestions

This guide only describes how to implement streaming media resource playback. For local resource playback, see [Using AVPlayer for Video Playback (C/C++)](using-ndk-avplayer-for-video-playback.md). If your application development involves background playback, playback conflicts, or similar scenarios, refer to the following instructions as needed.

Prevent playback from being forcibly interrupted by the system. This feature is only applicable to ArkTS API. To use this feature, see [Using AVPlayer for Video Playback (ArkTS)](video-playback.md).
- During playback, if the media data involves audio, the playback may be interrupted by other applications according to the system audio management policy (see [Handling Audio Focus Changes](../audio/audio-playback-concurrency.md#handling-audio-focus-changes)). It is recommended to actively listen for audio interruption events [AVPlayerOnInfoType](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayeroninfotype).AV_INFO_TYPE_INTERRUPT_EVENT through [OH_AVPlayer_SetOnInfoCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setoninfocallback), and take appropriate actions based on the specific prompts to avoid inconsistencies between the application state and the expected behavior.
- When a device is connected to multiple audio output devices simultaneously, it is recommended to actively listen for audio output device change events [AVPlayerOnInfoType](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayeroninfotype).AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE via [OH_AVPlayer_SetOnInfoCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setoninfocallback) and handle them accordingly.
- During playback, exceptions may occur within the system due to network data download failures, abnormal termination of media services, etc. It is recommended to set an error listener callback via the [OH_AVPlayer_SetOnErrorCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setonerrorcallback) interface, and handle different error types accordingly to avoid playback anomalies.

## How to Develop and Precautions

- Link the dynamic library in the CMake script.

  ```C++
  target_link_libraries(sample PUBLIC libavplayer.so)
  ```

- To set the info listener callback and error listener callback using the [OH_AVPlayer_SetOnInfoCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setonerrorcallback) interfaces, you need to link the following dynamic library in the CMake script.

  ```C++
  target_link_libraries(sample PUBLIC libnative_media_core.so)
  ```

- When using system logging capabilities, developers need to include the following header file.

  ```C++
  #include <hilog/log.h>
  ```

  And link the following dynamic library in the CMake script.

  ```C++
  target_link_libraries(sample PUBLIC libhilog_ndk.z.so)
  ```

Developers use streaming playback related APIs by including the [avplayer.h](../../reference/apis-media-kit/capi-avplayer-h.md), [avplayer_base.h](../../reference/apis-media-kit/capi-avplayer-base-h.md), and [native_averrors.h](../../reference/apis-avcodec-kit/capi-native-averrors-h.md) header files.

For details, see [AVPlayer](../../reference/apis-media-kit/capi-avplayer.md).

1. Create an AVPlayer instance: Call the [OH_AVPlayer_Create()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_create) API. The AVPlayer is initialized to the [AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_IDLE state.

   <!-- @[OH_AVPlayer_Create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   OH_AVPlayer *player = OH_AVPlayer_Create();
   ```

2. Set callback listeners: Use the [OH_AVPlayer_SetOnInfoCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setonerrorcallback) APIs to set the info listener callback and error listener callback for use in full-process scenarios. While obtaining more information, you can also distinguish different playback instances by setting userData.

   The supported listener events are as follows:

   | Event Type | Description |
   | -------- | -------- |
   | OH_AVPlayerOnInfoCallback | Mandatory event, listens for process information of the player.<br>The listener must be set when the player is in the AV_IDLE state and before calling the resource setting API. If the listener is set after calling the resource setting API, the OH_AVPlayerOnInfoCallback event reported during resource setting cannot be received. |
   | OH_AVPlayerOnErrorCallback | Mandatory event, listens for error information of the player.<br>The listener must be set when the player is in the AV_IDLE state and before calling the resource setting API. If the listener is set after calling the resource setting API, the OH_AVPlayerOnErrorCallback event reported during resource setting cannot be received. |

   <!-- @[OH_AVPlayer_SetOnInfoCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   // Set the callback to listen for information.
   LOG("call OH_AVPlayer_SetPlayerOnInfoCallback");
   int32_t ret = OH_AVPlayer_SetOnInfoCallback(player, OHAVPlayerOnInfoCallback, nullptr);
   LOG("OH_AVPlayer_SetPlayerOnInfoCallback ret:%{public}d", ret);
   ```

   <!-- @[OH_AVPlayer_SetOnErrorCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   LOG("call OH_AVPlayer_SetPlayerOnErrorCallback");
   ret = OH_AVPlayer_SetOnErrorCallback(player, OHAVPlayerOnErrorCallback, nullptr);
   LOG("OH_AVPlayer_SetPlayerOnErrorCallback ret:%{public}d", ret);
   ```

3. Set the resource: Call [OH_AVPlayer_SetURLSource()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_seturlsource) to set the attribute URL (supporting on-demand and live sources). The AVPlayer enters the [AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_INITIALIZED state.

   <!-- @[OH_AVPlayer_SetURLSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   LOG("player %{public}s >> URL source", url);
   LOG("call %{public}s", "OH_AVPlayer_SetUrlSource");
   ret = OH_AVPlayer_SetURLSource(player, url);
   LOG("OH_AVPlayer_SetUrlSource ret:%{public}d", ret);
   ```

4. (Optional) Set smart frame tracking: In live streaming scenarios, call [OH_AVPlayer_SetPlaybackStrategy()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setplaybackstrategy) to enable smart frame tracking for the AVPlayer.

   <!-- @[OH_AVPlayer_SetPlaybackStrategy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   void OHAVPlayerSetPlaybackStrategy(OH_AVPlayer *player)
   {
       // Set the playback strategy.
       OH_AVPlaybackStrategy *myStrategy = OH_AVPlaybackStrategy_Create();
       double waterLine = 6.0;
       OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay(myStrategy, waterLine); // Set smart frame tracking for live streaming scenarios.rame tracking for live streaming scenarios.
       int32_t ret = OH_AVPlayer_SetPlaybackStrategy(player, myStrategy);
       LOG("OH_AVPlayer_SetPlaybackStrategy ret:%{public}d", ret);
       OH_AVPlaybackStrategy_Destroy(myStrategy);
   }
   ```

5. (Optional) Set the audio stream type: Call [OH_AVPlayer_SetAudioRendererInfo()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setaudiorendererinfo) to set the audio stream type for the AVPlayer.

   <!-- @[OH_AVPlayer_SetAudioRendererInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   // Set the audio stream type.
   LOG("call %{public}s", "OH_AVPlayer_SetAudioRendererInfo");
   OH_AudioStream_Usage streamUsage = OH_AudioStream_Usage::AUDIOSTREAM_USAGE_UNKNOWN;
   ret = OH_AVPlayer_SetAudioRendererInfo(player, streamUsage);
   LOG("OH_AVPlayer_SetAudioRendererInfo ret:%{public}d", ret);
   ```

6. (Optional) Set the audio interruption mode: Call [OH_AVPlayer_SetAudioInterruptMode()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setaudiointerruptmode) to set the AVPlayer audio stream interruption mode.

   <!-- @[OH_AVPlayer_SetAudioInterruptMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   // Set the audio stream interruption mode.
   LOG("call OH_AVPlayer_SetAudioInterruptMode");
   OH_AudioInterrupt_Mode interruptMode = OH_AudioInterrupt_Mode::AUDIOSTREAM_INTERRUPT_MODE_INDEPENDENT;
   ret = OH_AVPlayer_SetAudioInterruptMode(player, interruptMode);
   LOG("OH_AVPlayer_SetAudioInterruptMode ret:%{public}d", ret);
   ```

7. Set the playback video window: Call [OH_AVPlayer_SetVideoSurface()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setvideosurface) to set the playback video window. This function must be called after SetSource and before Prepare.

   <!-- @[OH_AVPlayer_SetVideoSurface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   ret = OH_AVPlayer_SetVideoSurface(player, context->nativeWindow_);
   LOG("OH_AVPlayer_SetVideoSurface ret:%{public}d", ret);
   ```

8. Prepare for playback: Call [OH_AVPlayer_Prepare()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_prepare), and AVPlayer enters the [AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_PREPARED (prepared) state. At this point, you can obtain the duration and set the volume.

   <!-- @[OH_AVPlayer_Prepare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   ret = OH_AVPlayer_Prepare(player); // This state is reported after the playback source is set.reported after the playback source is set.
   if (ret != AV_ERR_OK) {
       // Handle exceptions.
       LOG("player %{public}s", "OH_AVPlayer_Prepare Err");
   }
   ```

9. (Optional) Set the audio effect mode: Call [OH_AVPlayer_SetAudioEffectMode()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setaudioeffectmode) to set the audio effect mode of the AVPlayer.

   <!-- @[OH_AVPlayer_SetAudioEffectMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   LOG("AVPlayerState AV_PREPARED");
   ret = OH_AVPlayer_SetAudioEffectMode(player, EFFECT_NONE); // Set the audio effect mode.udio effect mode.
   LOG("OH_AVPlayer_SetAudioEffectMode ret:%{public}d", ret);
   ```

10. Playback control: Includes operations such as play [OH_AVPlayer_Play()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_play), pause [OH_AVPlayer_Pause()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_pause), seek [OH_AVPlayer_Seek()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_seek), and stop [OH_AVPlayer_Stop()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_stop).

    <!-- @[OH_AVPlayer_Play](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    static napi_value NAPI_Global_Play(napi_env env, napi_callback_info info) {
        int ret = -1;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Play(context->player_);
            LOG("OH_AVPlayer_Play ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

    <!-- @[OH_AVPlayer_Pause](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    static napi_value NAPI_Global_Pause(napi_env env, napi_callback_info info) {
        int ret = 100;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Pause(context->player_);
            LOG("OH_AVPlayer_Pause ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

    <!-- @[OH_AVPlayer_Seek](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    static napi_value NAPI_Global_Seek(napi_env env, napi_callback_info info) {
        size_t argc = 2;
        napi_value args[2] = {nullptr};
        napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
        int seekValue;
        napi_get_value_int32(env, args[0], &seekValue);
        int mode;
        napi_get_value_int32(env, args[1], &mode);
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            int ret;
            switch (mode) {
            case 0:
                LOG("call NAPI_Global_Seek value:%{public}d  mode:AV_SEEK_NEXT_SYNC", seekValue);
                ret = OH_AVPlayer_Seek(context->player_, seekValue, AV_SEEK_NEXT_SYNC);
                break;
            case 1:
                LOG("call NAPI_Global_Seek value:%{public}d  mode:AV_SEEK_PREVIOUS_SYNC", seekValue);
                ret = OH_AVPlayer_Seek(context->player_, seekValue, AV_SEEK_PREVIOUS_SYNC);
                break;
            case 2:
                LOG("call NAPI_Global_Seek value:%{public}d  mode:AV_SEEK_CLOSEST", seekValue);
                ret = OH_AVPlayer_Seek(context->player_, seekValue, AV_SEEK_CLOSEST);
                break;
            default:
                LOG("call NAPI_Global_Seek value:%{public}d  mode:AV_SEEK_PREVIOUS_SYNC", seekValue);
                ret = OH_AVPlayer_Seek(context->player_, seekValue, AV_SEEK_PREVIOUS_SYNC);
                break;
            }
            LOG("OH_AVPlayer_Seek ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, 0, &value);
        return value;
    }
    ```

    <!-- @[OH_AVPlayer_Stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    static napi_value NAPI_Global_Stop(napi_env env, napi_callback_info info) {
        int ret = 100;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Stop(context->player_);
            LOG("OH_AVPlayer_Stop ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

11. (Optional) Change resource: Call [OH_AVPlayer_Reset()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_reset) to reset the resource. AVPlayer re-enters the [AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_IDLE state, allowing the resource URL to be changed.

    <!-- @[OH_AVPlayer_Reset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    static napi_value NAPI_Global_Reset(napi_env env, napi_callback_info info) {
        int ret = 100;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Reset(context->player_);
            LOG("OH_AVPlayer_Reset ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

12. Exit playback: Call [OH_AVPlayer_Release()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_release) to destroy the instance. AVPlayer enters the [AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_RELEASED state and exits playback. If the AVPlayer instance is operated again afterward, the behavior is undefined, which may cause the application process to crash or exit abnormally.

    <!-- @[OH_AVPlayer_Release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    static napi_value NAPI_Global_Release(napi_env env, napi_callback_info info) {
        int ret = -1;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Release(context->player_);
            LOG("OH_AVPlayer_Release ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

## Running the Complete Example

1. Create a new project and download the [sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia).
2. Compile the new project and run it.