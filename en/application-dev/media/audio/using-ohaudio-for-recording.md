# (Recommended) Using OHAudio for Audio Recording (C/C++)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=fddad89e05987dcca3a716df75048e2f1e3a656b translatedAt=2026-10-22T03:46:32.161Z pushedAt=2026-10-22T07:34:29.695Z nl=1 -->

OHAudio is a set of C APIs introduced in API version 10. These APIs are normalized in design and support both common and low-latency audio channels. They support the PCM format only. They are suitable for applications that implement audio input at the native layer.

An audio stream occupies system audio stream resources while it is active (not in the released state). The system limits the number of audio streams. When an audio stream is temporarily not in use, call **OH_AudioCapturer_Release()** to release its audio resources and avoid failures when creating subsequent audio streams.

OHAudio audio capturer state transition

![OHAudioCapturer status change](figures/ohaudiocapturer-status-change.png)


## Prerequisites

To use the recording capability of OHAudio, you must first import the corresponding header files.

The examples in the following steps are code snippets. You can access the [complete sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioCapturerSampleC) through the link at the lower right of each example.

### Linking the Dynamic Library in the CMake Script

``` cmake
target_link_libraries(sample PUBLIC libohaudio.so)
```
### Adding Header Files
Include the <[native_audiostreambuilder.h](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md)> and <[native_audiocapturer.h](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md)> header files so that the application can use the functions related to audio recording.

<!-- @[header_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
#include <ohaudio/native_audiocapturer.h>
#include <ohaudio/native_audiostreambuilder.h>
```

## How to Develop

Read [OHAudio](../../reference/apis-audio-kit/capi-ohaudio.md) for the API reference.

### Audio Stream Builder

OHAudio provides the **OH_AudioStreamBuilder** class, which complies with the builder design pattern and is used to build audio streams. You need to specify [OH_AudioStream_Type](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_type) based on your service scenarios.

**OH_AudioStream_Type** can be set to either of the following:

- AUDIOSTREAM_TYPE_RENDERER
- AUDIOSTREAM_TYPE_CAPTURER

The following code snippet shows how to use [OH_AudioStreamBuilder_Create](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create) to create a builder:

<!-- @[create_StreamType](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
OH_AudioStreamBuilder* builder;
OH_AudioStreamBuilder_Create(&builder, streamType);
```

After the audio service is complete, call [OH_AudioStreamBuilder_Destroy](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_destroy) to destroy the builder.

<!-- @[Destroy_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
OH_AudioStreamBuilder_Destroy(builder);
```

The following walks you through how to implement simple recording:

### Implementing Audio Recording

1. Create an audio stream builder.

   <!-- @[Create_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

   ``` C++
   OH_AudioStreamBuilder* builder;
   OH_AudioStreamBuilder_Create(&builder, AUDIOSTREAM_TYPE_CAPTURER);
   ```

2. Set audio stream parameters.

   After creating the builder for audio recording, set the parameters required.

   <!-- @[Configure_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

   ``` C++
   // Set the audio sampling rate.
   const int SAMPLING_RATE_48K = 48000;
   OH_AudioStreamBuilder_SetSamplingRate(builder, SAMPLING_RATE_48K);
   // Set the number of audio channels.
   const int channelCount = 2;
   OH_AudioStreamBuilder_SetChannelCount(builder, channelCount);
   // Set the audio sampling format.
   OH_AudioStreamBuilder_SetSampleFormat(builder, AUDIOSTREAM_SAMPLE_S16LE);
   // Set the audio stream encoding type.
   OH_AudioStreamBuilder_SetEncodingType(builder, AUDIOSTREAM_ENCODING_TYPE_RAW);
   // Set the audio capturer usage scenario.
   OH_AudioStreamBuilder_SetCapturerInfo(builder, AUDIOSTREAM_SOURCE_TYPE_MIC);
   ```

   The audio data for recording must be read through a callback function, and you must implement the callback function. Starting from API version 12, you can use [OH_AudioStreamBuilder_SetCapturerReadDataCallback](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturerreaddatacallback) to set the callback function. For details about its declaration, see [OH_AudioCapturer_OnReadDataCallback](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_onreaddatacallback).

3. Set the callback functions.

   For details about concurrent processing of multiple audio streams, see [Processing Audio Interruption Events](audio-playback-concurrency.md). The procedure is similar, and the only difference is the API programming language in use.

   <!-- @[Set_AudioCallbackFunction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->
   
   ``` C++
   void MyOnReadData_NewAPI(
       OH_AudioCapturer* capturer,
       void* userData,
       void* audioData,
       int32_t audioDataSize)
   {
       // Read the recording data of the specified length from the buffer.
   }
   
   void MyOnInterruptEvent_NewAPI(
       OH_AudioCapturer* capturer,
       void* userData,
       OH_AudioInterrupt_ForceType type,
       OH_AudioInterrupt_Hint hint)
   {
       // Update the capturer status and UI based on type and hint.
   }
   
   void MyOnError_NewAPI(
       OH_AudioCapturer* capturer,
       void* userData,
       OH_AudioStream_Result error)
   {
       // Handle audio exceptions based on error.
   }
   // ...
       // Configure the interruption callback.
       OH_AudioCapturer_OnInterruptCallback OnInterruptCb = MyOnInterruptEvent_NewAPI;
       OH_AudioStreamBuilder_SetCapturerInterruptCallback(builder, OnInterruptCb, nullptr);
   
       // Configure the error callback.
       OH_AudioCapturer_OnErrorCallback OnErrorCb = MyOnError_NewAPI;
       OH_AudioStreamBuilder_SetCapturerErrorCallback(builder, OnErrorCb, nullptr);
   
       // Configure the audio input callback.
       OH_AudioCapturer_OnReadDataCallback OnReadDataCb = MyOnReadData_NewAPI;
       OH_AudioStreamBuilder_SetCapturerReadDataCallback(builder, OnReadDataCb, nullptr);
   ```

4. Create an audio capturer instance.

   <!-- @[GenerateCapturer_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

   ``` C++
   OH_AudioCapturer* audioCapturer;
   OH_AudioStreamBuilder_GenerateCapturer(builder, &audioCapturer);
   ```

5. Use the audio capturer.

   You can use the APIs listed below to control the audio streams.

    | API                                                        | Description        |
    | ------------------------------------------------------------ | ------------ |
    | OH_AudioStream_Result OH_AudioCapturer_Start(OH_AudioCapturer* capturer) | Starts the audio capturer.   |
    | OH_AudioStream_Result OH_AudioCapturer_Pause(OH_AudioCapturer* capturer) | Pauses the audio capturer.    |
    | OH_AudioStream_Result OH_AudioCapturer_Stop(OH_AudioCapturer* capturer) | Stops the audio capturer.    |
    | OH_AudioStream_Result OH_AudioCapturer_Flush(OH_AudioCapturer* capturer) | Flushes obtained audio data.|
    | OH_AudioStream_Result OH_AudioCapturer_Release(OH_AudioCapturer* capturer) | Releases the audio capturer instance.|

    > **NOTE**
    >
    > Audio stream control APIs take time to execute. For example, a single call to **OH_AudioCapturer_Stop** generally takes more than 50 ms. Avoid calling these APIs directly on the main thread to prevent UI jank.

6. Destroy the audio stream builder.

   When the builder is no longer used, release related resources.

   <!-- @[Destroy_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

   ``` C++
   OH_AudioStreamBuilder_Destroy(builder);
   ```

### Setting the Low Latency Mode

If the device supports the low-latency channel, you can use the low-latency mode to create an audio capturer for a low-latency audio experience.

The development process is similar to that in the common recording scenario (described in [Implementing Audio Recording](#implementing-audio-recording)). The only difference is that you need to set the low delay mode by calling [OH_AudioStreamBuilder_SetLatencyMode()](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setlatencymode) when creating an audio stream builder in step 1.

> **NOTE**
>
> - In audio recording scenarios, if [OH_AudioStream_SourceType](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) is set to **AUDIOSTREAM_SOURCE_TYPE_VOICE_COMMUNICATION**, the low-latency mode cannot be set. The system determines the output audio channel based on the device capability.
> - In some scenarios (for example, incoming calls), the system capability is limited and the audio channel mode falls back to the common audio channel mode, and the buffer size changes accordingly. In this case, you need to obtain all data in the buffer at a time based on the buffer size, which is the same as that in the common audio channel mode. Otherwise, the recorded data will be discontinuous, resulting in noises.

<!-- @[latencyMode_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
OH_AudioStream_LatencyMode latencyMode = AUDIOSTREAM_LATENCY_MODE_FAST;
OH_AudioStreamBuilder_SetLatencyMode(builder, latencyMode);
```

### Capturing Audio with Loopback Effects

Since API version 26.0.0, if an application has enabled ear monitoring in [hardware loopback mode](../../media/audio/audio-ear-monitor-loopback.md#how-to-develop) and configured ear monitoring effects such as reverb in the same process, it can call [OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturerloopbackeffectenabled) when creating an audio capturer to capture audio processed with these effects. This capability is suitable for karaoke and live streaming scenarios that require recording the results of ear monitoring effects.

Call this API before calling [OH_AudioStreamBuilder_GenerateCapturer](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer) to create the audio capturer. The target audio stream must use the [AUDIOSTREAM_LATENCY_MODE_FAST](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode) low-latency mode.

<!-- @[SetCapturerLoopbackEffectEnabled](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
OH_AudioStream_Result result = OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled != nullptr ?
    OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled(builder, true) :
    AUDIOSTREAM_ERROR_ILLEGAL_STATE;
```

### Setting the Mute Interruption Mode
The mute interruption mode allows you to switch the interruption policy from stopping recording to muting recording, so that the recording will not be interrupted by the system based on the focus concurrency rule. In addition, recording of other apps is not affected during the recording. To ensure that the recording is not interrupted by the system's focus concurrency rules, a feature is introduced to change the interruption strategy from stopping the recording to simply muting it. You can control this behavior by calling [OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturerwillmutewheninterrupted) when creating an audio stream builder. By default, this mode is disabled, and the audio focus strategy manages the order of concurrent audio streams. When enabled, if the recording is interrupted by another application, it will go into a muted state instead of stopping or pausing. In this state, the audio captured is silent.

### Setting a Mute Hint for an Audio Capture Stream

Since API version 24, after an application mutes an audio capture stream in its own logic, it can call [OH_AudioCapturer_SetMuteHint](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_setmutehint) to report this state to the system audio module. The system audio module adjusts its policies based on the reported state to reduce power consumption. This feature currently takes effect only on certain PC and 2-in-1 devices. This API does not mute the stream or silence the captured data. It only informs the system audio module that the application has muted the current stream. The application must still process the audio data itself, for example, by not sending captured data or by sending silent data.

This API can be called only while the audio capture stream is running. Otherwise, it returns **AUDIOSTREAM_ERROR_ILLEGAL_STATE**. If both a stream-level mute hint and a session-level mute hint ([OH_AudioSessionManager_SetCaptureMuteHint](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setcapturemutehint)) are set for the same stream, the stream-level hint takes precedence. No system query API is currently available. To display the mute hint state in the UI, the application must track the most recent successfully set state.

<!-- @[cset_mute_hint](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) --> 

``` C++
bool mute = true;
OH_AudioStream_Result setResult = OH_AudioCapturer_SetMuteHint(audioCapturer, mute);
if (setResult != AUDIOSTREAM_SUCCESS) {
    // Handle errors such as AUDIOSTREAM_ERROR_ILLEGAL_STATE.
}

mute = false;
OH_AudioStream_Result unsetResult = OH_AudioCapturer_SetMuteHint(audioCapturer, mute);
```

### Echo Cancellation

Echo cancellation effectively eliminates echo interference during recording on supported devices, thereby improving audio capture quality. You can enable this feature by specifying particular audio input source types [OH_AudioStream_SourceType](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) (**AUDIOSTREAM_SOURCE_TYPE_VOICE_COMMUNICATION** or **AUDIOSTREAM_SOURCE_TYPE_LIVE**). Once enabled, the system automatically processes the captured audio signal to cancel echoes.

Before enabling this feature, you are advised to call [OH_AudioStreamManager_IsAcousticEchoCancelerSupported](../../reference/apis-audio-kit/capi-native-audio-stream-manager-h.md#oh_audiostreammanager_isacousticechocancelersupported) to check whether the device supports echo cancellation for the audio input source type [OH_AudioStream_SourceType](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_sourcetype). (This API is available since API version 20.) If supported, you can activate the echo cancellation processing by calling [OH_AudioStreamBuilder_SetCapturerInfo](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturerinfo) to set the corresponding audio input source type when creating the audio capturer.

### Samples
For details about the sample related to OHAudio audio recording, see [OHAudio Recording and Playback](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/OHAudio).

## Precautions

Starting from API version 12, using [OH_AudioCapturer_Callbacks](../../reference/apis-audio-kit/capi-ohaudio-oh-audiocapturer-callbacks-struct.md) to set audio callback functions is **no longer recommended**. If you must use it, complete initialization in either of the following ways before configuring the callback functions.

> **NOTE**
>
> You must initialize the `OH_AudioCapturer_Callbacks` structure. Uninitialized callback fields may contain random addresses, which the system may mistakenly execute as callback functions when triggering callbacks, resulting in wild pointers and process crashes.

- Method 1: Ensure that every callback in [OH_AudioCapturer_Callbacks](../../reference/apis-audio-kit/capi-ohaudio-oh-audiocapturer-callbacks-struct.md) is explicitly initialized with either a **custom callback** or a **null pointer**. Unused callbacks must be set to null pointers and must not retain uninitialized values.

  <!-- @[callback_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->
  
  ``` C++
  int32_t MyOnReadData_Legacy(
      OH_AudioCapturer* capturer,
      void* userData,
      void* buffer,
      int32_t length)
  {
      // Read the recording data of the specified length from the buffer.
      return 0;
  }
  int32_t MyOnInterruptEvent_Legacy(
      OH_AudioCapturer* capturer,
      void* userData,
      OH_AudioInterrupt_ForceType type,
      OH_AudioInterrupt_Hint hint)
  {
      // Update the capturer status and UI based on type and hint.
      return 0;
  }
  // ...
      // Assign custom callbacks for events that need to be monitored.
      callbacks.OH_AudioCapturer_OnReadData = MyOnReadData_Legacy;
      callbacks.OH_AudioCapturer_OnInterruptEvent = MyOnInterruptEvent_Legacy;
      
      // Required: Use null pointers for events that do not need to be monitored.
      callbacks.OH_AudioCapturer_OnStreamEvent = nullptr;
      callbacks.OH_AudioCapturer_OnError = nullptr;
  ```

- Method 2: Before use, initialize and zero out the structure to ensure that all unconfigured callback fields are null pointers.

  <!-- @[callbackNullptr_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->
  
  ``` C++
  int32_t MyOnReadData_Legacy(
      OH_AudioCapturer* capturer,
      void* userData,
      void* buffer,
      int32_t length)
  {
      // Read the recording data of the specified length from the buffer.
      return 0;
  }
  int32_t MyOnInterruptEvent_Legacy(
      OH_AudioCapturer* capturer,
      void* userData,
      OH_AudioInterrupt_ForceType type,
      OH_AudioInterrupt_Hint hint)
  {
      // Update the capturer status and UI based on type and hint.
      return 0;
  }
  // ...
      // Initialize and clear the struct before use.
      OH_AudioCapturer_Callbacks callbacks = {0};
      // Configure the required callbacks.
      callbacks.OH_AudioCapturer_OnReadData = MyOnReadData_Legacy;
      callbacks.OH_AudioCapturer_OnInterruptEvent = MyOnInterruptEvent_Legacy;
  ```
<!--RP1-->
<!--RP1End-->
