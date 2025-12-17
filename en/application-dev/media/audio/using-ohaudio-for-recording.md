# Using OHAudio for Audio Recording (C/C++)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

OHAudio is a set of C APIs introduced in API version 10. These APIs are normalized in design and support both common and low-latency audio channels. They support the PCM format only. They are suitable for applications that implement audio input at the native layer.

OHAudio audio capturer state transition

![OHAudioCapturer status change](figures/ohaudiocapturer-status-change.png)

## Prerequisites

To use the recording capability of OHAudio, you must first import the corresponding header files.

### Linking the Dynamic Library in the CMake Script

``` cmake
target_link_libraries(sample PUBLIC libohaudio.so)
```
### Adding Header Files
Include the <[native_audiostreambuilder.h](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md)> and <[native_audiocapturer.h](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md)> header files so that the application can use the functions related to audio recording.

```cpp
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

```cpp
OH_AudioStreamBuilder* builder;
OH_AudioStreamBuilder_Create(&builder, streamType);
```

After the audio service is complete, call [OH_AudioStreamBuilder_Destroy](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_destroy) to destroy the builder.

```cpp
OH_AudioStreamBuilder_Destroy(builder);
```

The following walks you through how to implement simple recording:

### Implementing Audio Recording

1. Create an audio stream builder.

    ```cpp
    OH_AudioStreamBuilder* builder;
    OH_AudioStreamBuilder_Create(&builder, AUDIOSTREAM_TYPE_CAPTURER);
    ```

2. Set audio stream parameters.

    After creating the builder for audio recording, set the parameters required.

    ```cpp
    // Set the audio sampling rate.
    OH_AudioStreamBuilder_SetSamplingRate(builder, 48000);
    // Set the number of audio channels.
    OH_AudioStreamBuilder_SetChannelCount(builder, 2);
    // Set the audio sampling format.
    OH_AudioStreamBuilder_SetSampleFormat(builder, AUDIOSTREAM_SAMPLE_S16LE);
    // Set the encoding type of the audio stream.
    OH_AudioStreamBuilder_SetEncodingType(builder, AUDIOSTREAM_ENCODING_TYPE_RAW);
    // Set the usage scenario of the audio capturer.
    OH_AudioStreamBuilder_SetCapturerInfo(builder, AUDIOSTREAM_SOURCE_TYPE_MIC);
    ```

    The audio data for recording must be read through a callback function, and you must implement the callback function. Starting from API version 12, you can use [OH_AudioStreamBuilder_SetCapturerReadDataCallback](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturerreaddatacallback) to set the callback function. For details about its declaration, see [OH_AudioCapturer_OnReadDataCallback](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_onreaddatacallback).

3. Set the callback functions.

    For details about concurrent processing of multiple audio streams, see [Processing Audio Interruption Events](audio-playback-concurrency.md). The procedure is similar, and the only difference is the API programming language in use.

    ```cpp
    // Customize a data reading function.
    void MyOnReadData(
        OH_AudioCapturer* capturer,
        void* userData,
        void* audioData,
        int32_t audioDataSize)
    {
        // Obtain the recording data of the specified length from the buffer.
    }
    // Customize an audio interruption event function.
    void MyOnInterruptEvent(
        OH_AudioCapturer* capturer,
        void* userData,
        OH_AudioInterrupt_ForceType type,
        OH_AudioInterrupt_Hint hint)
    {
        // Update the capturer status and UI based on the audio interruption information indicated by type and hint.
    }
    // Customize an exception callback function.
    void MyOnError(
        OH_AudioCapturer* capturer,
        void* userData,
        OH_AudioStream_Result error)
    {
        // Perform operations based on the audio exception information indicated by error.
    }

    // Configure the callback function for interruption events.
    OH_AudioCapturer_OnInterruptCallback OnIntereruptCb = MyOnInterruptEvent;
    OH_AudioStreamBuilder_SetCapturerInterruptCallback(builder, OnIntereruptCb, nullptr);

    // Configure the callback function for audio exceptions.
    OH_AudioCapturer_OnErrorCallback OnErrorCb = MyOnError;
    OH_AudioStreamBuilder_SetCapturerErrorCallback(builder, OnErrorCb, nullptr);

    // Configure the callback for audio input streams.
    OH_AudioCapturer_OnReadDataCallback OnReadDataCb = MyOnReadData;
    OH_AudioStreamBuilder_SetCapturerReadDataCallback(builder, OnReadDataCb, nullptr);
    ```

4. Create an audio capturer instance.

    ```cpp
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

6. Destroy the audio stream builder.

    When the builder is no longer used, release related resources.

    ```cpp
    OH_AudioStreamBuilder_Destroy(builder);
    ```

### Setting the Low Latency Mode

If the device supports the low-latency channel, you can use the low-latency mode to create an audio capturer for a low-latency audio experience.

The development process is similar to that in the common recording scenario (described in [Implementing Audio Recording](#implementing-audio-recording)). The only difference is that you need to set the low delay mode by calling [OH_AudioStreamBuilder_SetLatencyMode()](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setlatencymode) when creating an audio stream builder in step 1.

> **NOTE**
>
> - In audio recording scenarios, if [OH_AudioStream_SourceType](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) is set to **AUDIOSTREAM_SOURCE_TYPE_VOICE_COMMUNICATION**, the low-latency mode cannot be set. The system determines the output audio channel based on the device capability.
> - In some scenarios (for example, incoming calls), the system capability is limited and the audio channel mode falls back to the common audio channel mode, and the buffer size changes accordingly. In this case, you need to obtain all data in the buffer at a time based on the buffer size, which is the same as that in the common audio channel mode. Otherwise, the recorded data will be discontinuous, resulting in noises.

```cpp
OH_AudioStream_LatencyMode latencyMode = AUDIOSTREAM_LATENCY_MODE_FAST;
OH_AudioStreamBuilder_SetLatencyMode(builder, latencyMode);
```

### Setting the Mute Interruption Mode
The mute interruption mode allows you to switch the interruption policy from stopping recording to muting recording, so that the recording will not be interrupted by the system based on the focus concurrency rule. In addition, recording of other apps is not affected during the recording. To ensure that the recording is not interrupted by the system's focus concurrency rules, a feature is introduced to change the interruption strategy from stopping the recording to simply muting it. You can control this behavior by calling [OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturerwillmutewheninterrupted) when creating an audio stream builder. By default, this mode is disabled, and the audio focus strategy manages the order of concurrent audio streams. When enabled, if the recording is interrupted by another application, it will go into a muted state instead of stopping or pausing. In this state, the audio captured is silent.

### Echo Cancellation

Echo cancellation effectively eliminates echo interference during recording on supported devices, thereby improving audio capture quality. You can enable this feature by specifying particular audio input source types [OH_AudioStream_SourceType](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) (**AUDIOSTREAM_SOURCE_TYPE_VOICE_COMMUNICATION** or **AUDIOSTREAM_SOURCE_TYPE_LIVE**). Once enabled, the system automatically processes the captured audio signal to cancel echoes.

Before enabling this feature, you are advised to call [OH_AudioStreamManager_IsAcousticEchoCancelerSupported](../../reference/apis-audio-kit/capi-native-audio-stream-manager-h.md#oh_audiostreammanager_isacousticechocancelersupported) to check whether the device supports echo cancellation for the audio input source type [OH_AudioStream_SourceType](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_sourcetype). (This API is available since API version 20.) If supported, you can activate the echo cancellation processing by calling [OH_AudioStreamBuilder_SetCapturerInfo](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturerinfo) to set the corresponding audio input source type when creating the audio capturer.

### Samples
For details about the sample related to OHAudio audio recording, see [OHAudio Recording and Playback](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/OHAudio).

## Precautions

Starting from API version 12, the [OH_AudioCapturer_Callbacks](../../reference/apis-audio-kit/capi-ohaudio-oh-audiocapturer-callbacks-struct.md) API is no longer recommended for setting audio callback functions. If this API must be used, you should ensure that the audio callback function is set properly to avoid unexpected behavior. You can do this in one of two ways:

- Initialize each callback in [OH_AudioCapturer_Callbacks](../../reference/apis-audio-kit/capi-ohaudio-oh-audiocapturer-callbacks-struct.md) by a custom callback method or a null pointer.

    ```cpp
    // Customize a data reading function.
    int32_t MyOnReadData(
        OH_AudioCapturer* capturer,
        void* userData,
        void* buffer,
        int32_t length)
    {
        // Obtain the recording data of the specified length from the buffer.
        return 0;
    }
    // Customize an audio interruption event function.
    int32_t MyOnInterruptEvent(
        OH_AudioCapturer* capturer,
        void* userData,
        OH_AudioInterrupt_ForceType type,
        OH_AudioInterrupt_Hint hint)
    {
        // Update the capturer status and UI based on the audio interruption information indicated by type and hint.
        return 0;
    }
    OH_AudioCapturer_Callbacks callbacks;

    // Configure a callback function. If listening is required, assign a value.
    callbacks.OH_AudioCapturer_OnReadData = MyOnReadData;
    callbacks.OH_AudioCapturer_OnInterruptEvent = MyOnInterruptEvent;

    // (Mandatory) If listening is not required, use a null pointer for initialization.
    callbacks.OH_AudioCapturer_OnStreamEvent = nullptr;
    callbacks.OH_AudioCapturer_OnError = nullptr;
    ```

- Initialize and clear the struct before using it.

    ```cpp
    // Customize a data reading function.
    int32_t MyOnReadData(
        OH_AudioCapturer* capturer,
        void* userData,
        void* buffer,
        int32_t length)
    {
        // Obtain the recording data of the specified length from the buffer.
        return 0;
    }
    // Customize an audio interruption event function.
    int32_t MyOnInterruptEvent(
        OH_AudioCapturer* capturer,
        void* userData,
        OH_AudioInterrupt_ForceType type,
        OH_AudioInterrupt_Hint hint)
    {
        // Update the capturer status and UI based on the audio interruption information indicated by type and hint.
        return 0;
    }
    OH_AudioCapturer_Callbacks callbacks;

    // Initialize and clear the struct before using it.
    memset(&callbacks, 0, sizeof(OH_AudioCapturer_Callbacks));

    // Configure the required callback functions.
    callbacks.OH_AudioCapturer_OnReadData = MyOnReadData;
    callbacks.OH_AudioCapturer_OnInterruptEvent = MyOnInterruptEvent;
    ```
<!--RP1-->
<!--RP1End-->
