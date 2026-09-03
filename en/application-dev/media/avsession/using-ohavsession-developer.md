# AVSession Provider (C/C++)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=74c5c403cb641e8351820634af05f0bfefb8e44a translatedAt=2026-09-02T08:43:00.395Z pushedAt=2026-09-03T06:48:52.413Z -->

You can use the C APIs provided by the OHAVSession system to implement a media session provider, enabling media information to be displayed in media session controllers (such as Media Controller) and the provider to respond to playback control commands issued by the controllers.

## Prerequisites

To use [native_avsession.h](../../reference/apis-avsession-kit/capi-native-avsession-h.md) to implement media sessions, add the corresponding header files.

### Linking the Dynamic Libraries in the CMake Script

``` cmake
target_link_libraries(entry PUBLIC libohavsession.so)
```

### Including Header Files

<!-- @[avSession_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProviderNative/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include <multimedia/av_session/native_avmetadata.h>
#include <multimedia/av_session/native_avsession.h>
#include <multimedia/av_session/native_avsession_errors.h>
```

## How to Develop

To access a local session with the NDK, perform the following steps:
1. Create and activate a session. Pass the session type `AVSession_Type`, a custom TAG, and the bundle name and Ability name of the application.

   <!-- @[create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProviderNative/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   OH_AVSession* avsession;
   OH_AVSession_Create(SESSION_TYPE_AUDIO, "testsession", "com.example.application", "MainAbility", &avsession);
   OH_AVSession_Activate(avsession);
   ```

   **AVSession_Type** can be set to any of the following types:

   - SESSION_TYPE_AUDIO
   - SESSION_TYPE_VIDEO
   - SESSION_TYPE_VOICE_CALL 
   - SESSION_TYPE_VIDEO_CALL


2. Set the metadata of the media asset to be played.

   To set metadata, use `OH_AVMetadataBuilder` to construct specific data, generate an `OH_AVMetadata` instance, and finally set the generated `OH_AVMetadata` to the `OH_AVSession`.

   The code snippet below shows how to call **OH_AVMetadataBuilder** to construct metadata:

   <!-- @[construct_metadata](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProviderNative/entry/src/main/cpp/napi_init.cpp) --> 

   ``` C++
   // Create the OH_AVMetadataBuilder.
   OH_AVMetadataBuilder* builder;
   OH_AVMetadataBuilder_Create(&builder);
   
   OH_AVMetadata* ohMetadata;
   OH_AVMetadataBuilder_SetTitle(builder, "Anonymous title");
   OH_AVMetadataBuilder_SetArtist(builder, "Anonymous artist");
   OH_AVMetadataBuilder_SetAuthor(builder, "Anonymous author");
   OH_AVMetadataBuilder_SetAlbum(builder, "Anonymous album");
   OH_AVMetadataBuilder_SetWriter(builder, "Anonymous writer");
   OH_AVMetadataBuilder_SetComposer(builder, "Anonymous composer");
   OH_AVMetadataBuilder_SetDuration(builder, DURATION_TIME); // DURATION_TIME = 3600
   // MediaImageUri can only be set to a network address.
   OH_AVMetadataBuilder_SetMediaImageUri(builder, "https://example.com/images/cover.jpg");
   OH_AVMetadataBuilder_SetSubtitle(builder, "Anonymous subtitle");
   OH_AVMetadataBuilder_SetDescription(builder, "For somebody");
   // Lyric can only be set to the lyric content. (The application must combine the lyric content into a string.)
   OH_AVMetadataBuilder_SetLyric(builder, "balabala");
   OH_AVMetadataBuilder_SetAssetId(builder, "000");
   OH_AVMetadataBuilder_SetSkipIntervals(builder, SECONDS_15);
   OH_AVMetadataBuilder_SetDisplayTags(builder,  AVSESSION_DISPLAYTAG_AUDIO_VIVID);
   
   /**
    * Generate an AVMetadata object.
    */
   OH_AVMetadataBuilder_GenerateAVMetadata(builder, &ohMetadata);

   /**
    * Set the AVMetadata object.
    */
   OH_AVSession_SetAVMetadata(avsession, ohMetadata);
   ```

   After using `AVMetadata`, you should call `OH_AVMetadata_Destroy` to destroy the metadata object and `OH_AVMetadataBuilder_Destroy` to destroy the builder. The metadata object and builder must not be used after they are destroyed.

   <!-- @[destroy_metadata](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProviderNative/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   OH_AVMetadata_Destroy(ohMetadata);
   OH_AVMetadataBuilder_Destroy(builder);
   ```

3. Update the media playback status information.

   The information includes the playback state, playback position, playback speed, and favorite status. You can use the APIs to set the information.

   <!-- @[state_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProviderNative/entry/src/main/cpp/napi_init.cpp) --> 

   ``` C++
   AVSession_ErrCode ret = AV_SESSION_ERR_SUCCESS;
   
   // Set the playback state, which is in the range [0,11].
   AVSession_PlaybackState state = PLAYBACK_STATE_PREPARING;
   ret = OH_AVSession_SetPlaybackState(avsession, state);
   // ...
   
   // Set the playback position.
   AVSession_PlaybackPosition* playbackPosition = new AVSession_PlaybackPosition;
   playbackPosition->elapsedTime = ELAPSED_TIME; // ELAPSED_TIME = 1000
   playbackPosition->updateTime = UPDATE_TIME; // UPDATE_TIME = 16111150
   ret = OH_AVSession_SetPlaybackPosition(avsession, playbackPosition);
   delete playbackPosition;
   ```

4. Listen for playback control commands delivered by the controller, for example, Media Controller.

   > **NOTE**
   >
   > - When the media session provider registers listeners for the relevant fixed playback control command events, the listened events are reflected in the `getValidCommands()` method of the media session controller. That is, the media session controller considers these methods valid and therefore triggers the corresponding events when needed. To ensure that the playback control commands delivered by the media session controller can be executed properly, the media session provider must not register empty listeners that contain no logic.
   >
   > - After calling a registration API, call the corresponding unregistration API when the service ends to avoid exceptions.

   Currently, the following playback control commands are supported:
   - Play
   - Pause
   - Stop
   - Play previous
   - Play next
   - Rewind
   - Fast forward
   - Seek
   - Favorite

   <!-- @[control_command](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProviderNative/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   // Register the callbacks for the commands of play, pause, stop, play previous, and play next.
   // CONTROL_CMD_PLAY = 0; play.
   // CONTROL_CMD_PAUSE = 1; pause.
   // CONTROL_CMD_STOP = 2; stop.
   // CONTROL_CMD_PLAY_NEXT = 3; play next.
   // CONTROL_CMD_PLAY_PREVIOUS = 4; play previous.
   AVSession_ControlCommand command = CONTROL_CMD_PLAY;
   OH_AVSessionCallback_OnCommand commandCallback = [](OH_AVSession* session, AVSession_ControlCommand command,
       void* userData) -> AVSessionCallback_Result {
       return AVSESSION_CALLBACK_RESULT_SUCCESS;
   };
   int userData = 0;
   OH_AVSession_RegisterCommandCallback(avsession, command, commandCallback, (void *)(&userData));
   
   // Set the fast-forward callback.
   OH_AVSessionCallback_OnFastForward fastForwardCallback = [](OH_AVSession* session, uint32_t seekTime,
       void* userData) -> AVSessionCallback_Result {
       return AVSESSION_CALLBACK_RESULT_SUCCESS;
   };
   OH_AVSession_RegisterForwardCallback(avsession, fastForwardCallback, (void *)(&userData));
   ```

   The related callbacks are as follows:

   | API                                                        | Description        |
   | ------------------------------------------------------------ | ------------ |
   |OH_AVSession_RegisterCommandCallback(OH_AVSession* avsession, AVSession_ControlCommand   command, OH_AVSessionCallback_OnCommand callback, void* userData) | Registers a callback for a common playback control command, which can be play, pause, stop, play previous, or play next.    |
   |OH_AVSession_RegisterForwardCallback(OH_AVSession* avsession,   OH_AVSessionCallback_OnFastForward callback, void* userData) | Registers a callback for the fast-forward operation.  |
   |OH_AVSession_RegisterRewindCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnRewind   callback, void* userData) | Registers a callback for the rewind operation.    |
   |OH_AVSession_RegisterSeekCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSeek   callback, void* userData) | Registers a callback for the seek operation. |
   |OH_AVSession_RegisterToggleFavoriteCallback(OH_AVSession* avsession,   OH_AVSessionCallback_OnToggleFavorite callback, void* userData) | Registers a callback for the favorite operation. |
5. When the audio and video application exits and does not need to continue playback, cancel the listener and destroy the AVSession object. The example code is as follows:

   <!-- @[destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProviderNative/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   OH_AVSession_Destroy(avsession);
   ```

## Samples

The following samples are available for reference:

- [MediaProvider (C/C++) (API13)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVSession/MediaProvider)
