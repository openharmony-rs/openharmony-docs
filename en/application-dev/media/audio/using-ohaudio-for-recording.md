# Using OHAudio for Audio Recording (C/C++)

OHAudio is a set of C APIs introduced in API version 10. These APIs are normalized in design and support both common and low-latency audio channels. They support the PCM format only. They are suitable for playback applications that implement audio input at the native layer.

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
## Audio Stream Builder

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

## How to Develop

Read [OHAudio](../../reference/apis-audio-kit/capi-ohaudio.md) for the API reference.

The following walks you through how to implement simple recording:

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

    Note that the audio data captured is read through callbacks. You must call **OH_AudioStreamBuilder_SetCapturerCallback** to implement the callbacks. For details about the declaration of the callback functions, see [OH_AudioCapturer_Callbacks](../../reference/apis-audio-kit/capi-oh-audiocapturer-callbacks-struct.md).

3. Set the callback functions.

    For details about concurrent processing of multiple audio streams, see [Processing Audio Interruption Events](audio-playback-concurrency.md). The procedure is similar, and the only difference is the API programming language in use.

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
    // Customize an audio stream event function.
    int32_t MyOnStreamEvent(
        OH_AudioCapturer* capturer,
        void* userData,
        OH_AudioStream_Event event)
    {
        // Update the player status and UI based on the audio stream event information indicated by the event.
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
    // Customize an exception callback function.
    int32_t MyOnError(
        OH_AudioCapturer* capturer,
        void* userData,
        OH_AudioStream_Result error)
    {
        // Perform operations based on the audio exception information indicated by error.
        return 0;
    }

    OH_AudioCapturer_Callbacks callbacks;

    // Set the callbacks.
    callbacks.OH_AudioCapturer_OnReadData = MyOnReadData;
    callbacks.OH_AudioCapturer_OnStreamEvent = MyOnStreamEvent;
    callbacks.OH_AudioCapturer_OnInterruptEvent = MyOnInterruptEvent;
    callbacks.OH_AudioCapturer_OnError = MyOnError;

    // Set the callbacks for audio input streams.
    OH_AudioStreamBuilder_SetCapturerCallback(builder, callbacks, nullptr);
    ```

    To avoid unexpected behavior, you can set the audio callback functions in either of the following ways:

    - Initialize each callback in [OH_AudioCapturer_Callbacks](../../reference/apis-audio-kit/capi-oh-audiocapturer-callbacks-struct.md) by a custom callback method or a null pointer.

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

## Setting the Low Latency Mode

If the device supports the low-latency channel, you can use the low-latency mode to create an audio capturer for a higher-quality audio experience.

The development process is similar to that in the common recording scenario. The only difference is that you need to set the low-latency mode by calling [OH_AudioStreamBuilder_SetLatencyMode()](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setlatencymode) when creating an audio stream builder.

> **NOTE**
>
> In audio recording scenarios, if [OH_AudioStream_SourceType](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) is set to **AUDIOSTREAM_SOURCE_TYPE_VOICE_COMMUNICATION**, the low-latency mode cannot be set. The system determines the output audio channel based on the device capability.

Code snippet:

```cpp
OH_AudioStream_LatencyMode latencyMode = AUDIOSTREAM_LATENCY_MODE_FAST;
OH_AudioStreamBuilder_SetLatencyMode(builder, latencyMode);
```


<!--RP1-->
<!--RP1End-->
