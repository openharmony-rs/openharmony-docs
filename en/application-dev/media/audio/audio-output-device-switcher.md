# Switching Audio Output Devices
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=033a67b0a75a80d42a891cac89b2daf9850f8c21 translatedAt=2026-09-01T02:33:11.403Z pushedAt=2026-09-02T02:55:30.808Z -->

When an app outputs audio, the system automatically matches the corresponding output device based on the audio stream type. If the system output device does not meet the app's requirements, the app can implement audio output device routing switch through `AVCastPicker` or `setDefaultOutputDevice`. When an external audio device (such as a Bluetooth headset or a wired headset) is connected, the app can also force media output to switch to the speaker through `setMediaOutputDevice`.

Starting from API version 26.0.0, PCs/2-in-1 devices also support output device switching based on [AudioDeviceEnhanceManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md) and [native_audio_device_enhance_manager.h](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md). You can specify the output device precisely at the application level or audio stream level to control the audio output destination in multi-device scenarios.

The code snippets in the following steps are fragments. You can obtain the [complete sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample) from the link at the lower right of the sample code. For the complete sample of [output device switching on PCs/2-in-1 devices](#output-device-switching-on-pcs2-in-1-devices), see the [ArkTS sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS) and [C/C++ sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC).

## When to Use

1. If an app needs to provide a visual and interactive entry for switching audio output devices, you can use the `AVCastPicker` component. Simply place this component in the layout, and the system automatically detects the list of currently available audio output devices. The user can then tap to complete the routing switch.
2. Apps have different requirements for the default output device in different scenarios. For example, voice message streams are typically played through the speaker by default so that users can listen directly. However, in certain private scenarios, an app may want to set voice messages to play through the earpiece by default to protect user privacy. In such cases, you can use the `setDefaultOutputDevice` API to flexibly change the default output device for voice messages to meet specific business requirements.
3. When an external device such as a Bluetooth headset or a wired headset is connected, the system plays audio from the external device by priority. However, in some scenarios, the app expects to force media audio to switch to the speaker even when an external device is connected (for example, playing real-time translation to the other party). Starting from API version 26.0.0, you can call the `setMediaOutputDevice` API to force the media output device to switch to the speaker by setting the parameter to `audio.DeviceType.SPEAKER` when an external device is connected. To restore the system default routing, call the `setMediaOutputDevice` API again and set the parameter to `audio.DeviceType.DEFAULT`.

## Switching Output Device Routing for Media Streams

Apps can use the [AVCastPicker](../../reference/apis-avsession-kit/ohos-multimedia-avcastpicker.md#avcastpicker) component to provide users with an entry for selecting a device.

This component integrates capabilities such as device discovery, connection, and authentication, and can be embedded into the app UI. When the user taps it, the system automatically identifies and displays the list of currently switchable devices, supporting seamless switching among output devices such as speakers, headphones, and smart speakers.

## Switching Output Device Routing for Call Streams

The `AVCastPicker` component is also applicable to call scenarios. Apps can [use the call device switching component](../avsession/using-switch-call-devices.md) to provide users with an entry for switching among call devices such as the earpiece, speaker, and headphones, allowing users to flexibly adjust the audio output device during a call.

## Setting the Default Output Device

If no external device (such as a Bluetooth headset) is connected, audio is played through the earpiece by default in voice call scenarios and through the speaker in other scenarios. After an external device is connected, the system prioritizes playback through the external device. Apps can change the default output device by calling `setDefaultOutputDevice`, but this takes effect only for the following three [StreamUsage](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage) types:

| Name | Value | Description |
| -------- | -------- | -------- |
| STREAM_USAGE_VOICE_MESSAGE | 5 | Voice message. |
| STREAM_USAGE_VOICE_COMMUNICATION | 2 | VoIP voice call. |
| STREAM_USAGE_VIDEO_COMMUNICATION | 17 | VoIP video call. |

Supported device types:

| Name | Value | Description |
| -------- | -------- | -------- |
| EARPIECE | 1 | Earpiece. |
| SPEAKER | 2 | Speaker. |
| DEFAULT | 1000 | Follow the system. |

After this API is called, the system records the specified default output device. When no external device is connected, the audio stream is routed to the specified default output device for playback. When an external device is connected, the system prioritizes playback through the external device, and automatically switches back to the configured default output device after the external device is disconnected.

### How to Develop

Both `AudioRenderer` and `AudioSessionManager` provide the `setDefaultOutputDevice` API for setting the default output device for calls or voice.

- Audio stream level: The `AudioRenderer` API takes effect at the individual stream level, affecting only the audio stream corresponding to the current `AudioRenderer` instance.
- App level: The `AudioSessionManager` API takes effect for all voice and call audio streams within the current app, not limited to a single `AudioRenderer` instance.

The app-level API has a higher priority than the audio stream-level API. If both APIs are called, the `AudioSessionManager` setting overrides the `AudioRenderer` setting, and the `AudioRenderer` setting no longer takes effect.

**Audio Stream-Level Setting API**

Starting from API version 12, apps can use the [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setdefaultoutputdevice12) API of AudioRenderer to set the default device to the earpiece or speaker. Before calling this API, you need to obtain an [AudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-f.md#audiocreateaudiorenderer8) instance. The lifecycle of the default device setting follows the audio stream. To cancel the default output device set by calling `setDefaultOutputDevice`, you can set the parameter to `audio.DeviceType.DEFAULT`, which returns the audio output device selection to the system.

   > **NOTE**
   >
   > - AudioRenderer operates at the stream level. Therefore, the default audio output device set via this API takes effect only for the current stream.
   > - This API has a lower priority than [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20) of AudioSessionManager. If [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20) of AudioSessionManager has been used to set the default audio output device, the settings made via this API do not take effect.

   <!-- @[audioRenderer_setDefaultOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceSwitcher.ets) -->  

   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
   
       // Set the default output device to the speaker.
       audioRenderer.setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
         console.info('Succeeded in setting default output device.');
         // ...
       }).catch((err: BusinessError) => {
         console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
         // ...
       });
       // ...
   
       // Set the default output device to the earpiece.
       audioRenderer.setDefaultOutputDevice(audio.DeviceType.EARPIECE).then(() => {
         console.info('Succeeded in setting default output device.');
         // ...
       }).catch((err: BusinessError) => {
         console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
         // ...
       });
   ```

**App-Level Setting API**

Starting from API version 20, after activating an [AudioSession](../audio/audio-session-management.md), apps can use the [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20) API of AudioSessionManager to set the default output device, and check whether the default device is set successfully through `AudioSessionManager.getDefaultOutputDevice`. The lifecycle of the default device setting follows the `AudioSession`. To cancel the default output device set by calling `setDefaultOutputDevice`, you can set the parameter to `audio.DeviceType.DEFAULT`, which returns the audio output device selection to the system.

   > **NOTE**
   >
   > AudioSessionManager operates at the application level. Therefore, calling this API to set the default audio output device takes effect for all applicable audio streams within the current application and overrides the default audio output device settings made via [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setdefaultoutputdevice12) of AudioRenderer.

   <!-- @[audioSessionManager_setDefaultOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceSwitcher.ets) -->  

   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
   
   let audioManager = audio.getAudioManager();
   let audioSessionManager = audioManager.getSessionManager();
   // ...
   
     // The app sets an audio session scene that suits its business scenario. When AudioSession is activated, the system requests the corresponding audio focus based on the audio session scene selected by the app.
     audioSessionManager.setAudioSessionScene(audio.AudioSessionScene.AUDIO_SESSION_SCENE_VOICE_COMMUNICATION);
   
     // Set the audio session strategy.
     let strategy: audio.AudioSessionStrategy = {
       concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
     };
   
     // Activate AudioSession.
     audioSessionManager.activateAudioSession(strategy).then(() => {
       console.info('Succeeded in activating audio session.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to activate audio session. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
     // ...
   
     // Set the default output device to the speaker.
     audioSessionManager.setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
       console.info('Succeeded in setting default output device.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
     // ...
   
     // Set the default output device to the earpiece.
     audioSessionManager.setDefaultOutputDevice(audio.DeviceType.EARPIECE).then(() => {
       console.info('Succeeded in setting default output device.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
   ```

## Forcing Media Output Device Switching When an External Device Is Connected

When the system is connected to an external device such as a Bluetooth headset or a wired headset, the system plays from the external device by priority. Starting from API version 26.0.0, an app can use [setMediaOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setmediaoutputdevice) of `AudioSessionManager` to force the media output device to switch to the speaker, so that audio is still played from the speaker even when an external device is connected.

   > **NOTE**
   >
   > - This API takes effect only on media streams and applies to all media streams in the app. Call streams are not affected. The app must be in the foreground and have a running media stream; otherwise, the setting does not take effect and is automatically cleared after the app exits.
   > - The output device set by this API and the output device set in [Switching Output Device Routing for Media Streams](#switching-output-device-routing-for-media-streams) overwrite each other (the one called later overwrites the output device set by the one called earlier).
   > - The output device set by this API does not overwrite the output device set in [Setting the Default Output Device](#setting-the-default-output-device).
   > - You can listen for the [CurrentOutputDeviceChangedEvent](../../reference/apis-audio-kit/arkts-apis-audio-i.md#currentoutputdevicechangedevent20) event to obtain the current output device information and check whether the configured output device takes effect.
   > - On devices without a built-in speaker (such as a smart screen), calling this API to switch the output device to the speaker does not take effect, but the API call still returns success and does not throw an error or trigger an error callback.

### How to Develop

An app can use [setMediaOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setmediaoutputdevice) of `AudioSessionManager` to force the media output device to switch to the speaker. After calling `setMediaOutputDevice`, to cancel the forced switching and restore the system default routing rule, set the parameter to `audio.DeviceType.DEFAULT`.

Supported device types:

| Name | Value | Description |
| -------- | -------- | -------- |
| SPEAKER | 2 | Speaker. Forces media output to switch to the speaker. |
| DEFAULT | 1000 | System default device. Clears the forced switch and restores the system default routing policy. |

   <!-- @[audioSessionManager_setMediaOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceSwitcher.ets) -->

   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
   
   let audioManager = audio.getAudioManager();
   let audioSessionManager = audioManager.getSessionManager();
   // ...
   
     // After a Bluetooth headset is connected, force the media output device to switch to the speaker.
     audioSessionManager.setMediaOutputDevice(audio.DeviceType.SPEAKER).then(() => {
       console.info('Succeeded in setting media output device to speaker.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to set media output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
     // ...
   
     // Cancel the forced switch and return the media output device selection to the system default routing rules.
     audioSessionManager.setMediaOutputDevice(audio.DeviceType.DEFAULT).then(() => {
       console.info('Succeeded in setting media output device to default.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to set media output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
   ```

## Output Device Switching on PCs/2-in-1 Devices

PCs/2-in-1 devices often have multiple output devices available (such as the built-in speaker, external speakers, and USB/Bluetooth headsets). The system default device selection policy may not meet the output requirements of applications in various scenarios. With this capability, you can precisely specify the output device at the **application level** or **audio stream level**, meeting the requirement for controlling the audio output destination in multi-device scenarios.

### Checking Whether the Capability Is Supported

Before use, call [isEnhancedRoutingSupported](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md#isenhancedroutingsupported) or [OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_isenhancedroutingsupported) to check whether the system supports this capability. If the capability is not supported, calling the output device switching APIs does not take effect, and the current output device continues to be used.

ArkTS example:

<!-- @[isEnhancedRoutingSupported](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...
  let audioManager = audio.getAudioManager();
  let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
  // Query whether the system supports the enhanced routing capability provided by the current manager.
  let isSupported: boolean = audioDeviceEnhanceManager.isEnhancedRoutingSupported();
  console.info(`Succeeded in querying whether enhanced routing is supported. Result: ${isSupported}.`);
```

C/C++ example:

Add the following header files before use:

<!-- @[header_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC/entry/src/main/cpp/EnhancedDeviceRouting.cpp) -->

``` C++
#include <ohaudio/native_audio_device_enhance_manager.h>
#include <ohaudio/native_audio_routing_manager.h>
#include <ohaudio/native_audio_device_base.h>
#include <ohaudio/native_audiocapturer.h>
#include <ohaudio/native_audiorenderer.h>
#include <ohaudio/native_audiostreambuilder.h>
```

<!-- @[isEnhancedRoutingSupported](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC/entry/src/main/cpp/EnhancedDeviceRouting.cpp) -->

``` C++
napi_value IsEnhancedRoutingSupported(napi_env env, napi_callback_info info)
{
    OH_AudioDeviceEnhanceManager *enhanceManager = nullptr;
    OH_AudioCommon_Result result = OH_AudioManager_GetAudioDeviceEnhanceManager(&enhanceManager);
    bool isSupported = false;
    // Query whether the system supports the enhanced routing capability provided by the current manager.
    result = OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(enhanceManager, &isSupported);
    // ...
}
```

### Switching the Output Device

Output device switching supports two granularities: application level and audio stream level. The application level takes effect on all playback streams under an application, while the audio stream level takes effect only on a specified playback stream. The audio stream level has a higher priority than the application level.

> **NOTE**
>
> If a playback stream has been assigned a dedicated output device through an audio stream-level API, that stream uses its dedicated output device, while other playback streams in the application still use the output device set at the application level or the system default output device.

ArkTS example:

- **Application level:** Use [selectOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md#selectoutputdevice) to select a specified output device. After the setting succeeds, it takes effect on all playback streams created under the application.

  <!-- @[select_OutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  // ...
    let audioManager = audio.getAudioManager();
    let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
    // Select an output device for the application. For details about how to obtain the device, see the complete ArkTS example.
    audioDeviceEnhanceManager.selectOutputDevice(device).then(() => {
      console.info('Succeeded in selecting output device.');
      // ...
    }).catch((err: BusinessError) => {
      console.error(`Failed to select output device. Code: ${err.code}, message: ${err.message}`);
      // ...
    });
  ```

- **Audio stream level:** Use [selectOutputDeviceForAudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md#selectoutputdeviceforaudiorenderer) to select an output device for a specified audio playback stream. After the setting succeeds, it takes effect only on that playback stream.

  <!-- @[select_OutputDeviceForAudioRenderer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  // ...
    let audioManager = audio.getAudioManager();
    let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
    // Set the preferred output device for the specified audio playback stream. For details about how to obtain the renderer and outputDevice, see the complete ArkTS example.
    audioDeviceEnhanceManager.selectOutputDeviceForAudioRenderer(renderer, outputDevice).then(() => {
      console.info('Succeeded in selecting output device for audio renderer.');
      // ...
    }).catch((err: BusinessError) => {
      console.error(`Failed to select output device for audio renderer. Code: ${err.code}, message: ${err.message}`);
      // ...
    });
  ```

C/C++ example:

- **Application level:** Use [OH_AudioDeviceEnhanceManager_SelectOutputDevice](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_selectoutputdevice) to select a specified output device.

  <!-- @[select_OutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC/entry/src/main/cpp/EnhancedDeviceRouting.cpp) -->

  ``` C++
  // Obtain the audio device enhancement manager.
  static OH_AudioDeviceEnhanceManager *GetEnhanceManager(std::string &errorMsg)
  {
      OH_AudioDeviceEnhanceManager *manager = nullptr;
      OH_AudioCommon_Result result = OH_AudioManager_GetAudioDeviceEnhanceManager(&manager);
      if (result != AUDIOCOMMON_RESULT_SUCCESS || manager == nullptr) {
          errorMsg = "Failed to obtain AudioDeviceEnhanceManager";
          return nullptr;
      }
      bool isSupported = false;
      OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(manager, &isSupported);
      if (!isSupported) {
          errorMsg = "Enhanced routing is not supported, and this feature will not take effect";
          return nullptr;
      }
      return manager;
  }
  
  struct DeviceSearchResult {
      OH_AudioRoutingManager *routingManager;
      OH_AudioDeviceDescriptorArray *deviceArray;
      OH_AudioDeviceDescriptor *targetDescriptor;
  };
  
  // Obtain the available audio devices.
  static DeviceSearchResult FindDescriptorById(int32_t deviceId, OH_AudioDevice_Usage usage)
  {
      DeviceSearchResult search = {nullptr, nullptr, nullptr};
      OH_AudioManager_GetAudioRoutingManager(&search.routingManager);
      OH_AudioRoutingManager_GetAvailableDevices(search.routingManager, usage, &search.deviceArray);
      if (search.deviceArray == nullptr) {
          return search;
      }
      for (uint32_t i = 0; i < search.deviceArray->size; i++) {
          uint32_t id = 0;
          OH_AudioDeviceDescriptor_GetDeviceId(search.deviceArray->descriptors[i], &id);
          if (id == static_cast<uint32_t>(deviceId)) {
              search.targetDescriptor = search.deviceArray->descriptors[i];
              break;
          }
      }
      return search;
  }
  
  static void ReleaseDeviceSearch(DeviceSearchResult &search)
  {
      if (search.routingManager != nullptr && search.deviceArray != nullptr) {
          OH_AudioRoutingManager_ReleaseDevices(search.routingManager, search.deviceArray);
      }
  }
  // ...
  // Select an output device for the application.
  napi_value SelectOutputDevice(napi_env env, napi_callback_info info)
  {
      int32_t deviceId = 0;
      ParseInt32Arg(env, info, deviceId);
      std::string errorMsg;
      OH_AudioDeviceEnhanceManager *enhanceManager = GetEnhanceManager(errorMsg);
      // ...
  
      DeviceSearchResult search = FindDescriptorById(deviceId, AUDIO_DEVICE_USAGE_MEDIA_OUTPUT);
      OH_AudioCommon_Result result = OH_AudioDeviceEnhanceManager_SelectOutputDevice(
          enhanceManager, search.targetDescriptor);
      ReleaseDeviceSearch(search);
      // ...
  }
  ```

- **Audio stream level:** Use [OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_selectoutputdeviceforaudiorenderer) to select an output device for a specified audio playback stream.

  <!-- @[select_OutputDeviceForAudioRenderer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC/entry/src/main/cpp/EnhancedDeviceRouting.cpp) -->

  ``` C++
  // Obtain the audio device enhancement manager.
  static OH_AudioDeviceEnhanceManager *GetEnhanceManager(std::string &errorMsg)
  {
      OH_AudioDeviceEnhanceManager *manager = nullptr;
      OH_AudioCommon_Result result = OH_AudioManager_GetAudioDeviceEnhanceManager(&manager);
      if (result != AUDIOCOMMON_RESULT_SUCCESS || manager == nullptr) {
          errorMsg = "Failed to obtain AudioDeviceEnhanceManager";
          return nullptr;
      }
      bool isSupported = false;
      OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(manager, &isSupported);
      if (!isSupported) {
          errorMsg = "Enhanced routing is not supported, and this feature will not take effect";
          return nullptr;
      }
      return manager;
  }
  
  struct DeviceSearchResult {
      OH_AudioRoutingManager *routingManager;
      OH_AudioDeviceDescriptorArray *deviceArray;
      OH_AudioDeviceDescriptor *targetDescriptor;
  };
  
  // Obtain the available audio devices.
  static DeviceSearchResult FindDescriptorById(int32_t deviceId, OH_AudioDevice_Usage usage)
  {
      DeviceSearchResult search = {nullptr, nullptr, nullptr};
      OH_AudioManager_GetAudioRoutingManager(&search.routingManager);
      OH_AudioRoutingManager_GetAvailableDevices(search.routingManager, usage, &search.deviceArray);
      if (search.deviceArray == nullptr) {
          return search;
      }
      for (uint32_t i = 0; i < search.deviceArray->size; i++) {
          uint32_t id = 0;
          OH_AudioDeviceDescriptor_GetDeviceId(search.deviceArray->descriptors[i], &id);
          if (id == static_cast<uint32_t>(deviceId)) {
              search.targetDescriptor = search.deviceArray->descriptors[i];
              break;
          }
      }
      return search;
  }
  
  static void ReleaseDeviceSearch(DeviceSearchResult &search)
  {
      if (search.routingManager != nullptr && search.deviceArray != nullptr) {
          OH_AudioRoutingManager_ReleaseDevices(search.routingManager, search.deviceArray);
      }
  }
  // Create an audio renderer.
  static OH_AudioRenderer *CreateAudioRenderer()
  {
      OH_AudioStreamBuilder *builder = nullptr;
      if (OH_AudioStreamBuilder_Create(&builder, AUDIOSTREAM_TYPE_RENDERER) != AUDIOSTREAM_SUCCESS) {
          return nullptr;
      }
      OH_AudioStreamBuilder_SetSamplingRate(builder, SAMPLE_RATE_48K);
      OH_AudioStreamBuilder_SetChannelCount(builder, CHANNEL_COUNT_STEREO);
      OH_AudioStreamBuilder_SetSampleFormat(builder, AUDIOSTREAM_SAMPLE_S16LE);
      OH_AudioStreamBuilder_SetEncodingType(builder, AUDIOSTREAM_ENCODING_TYPE_RAW);
      OH_AudioStreamBuilder_SetRendererInfo(builder, AUDIOSTREAM_USAGE_VOICE_COMMUNICATION);
      OH_AudioRenderer *renderer = nullptr;
      OH_AudioStreamBuilder_GenerateRenderer(builder, &renderer);
      OH_AudioStreamBuilder_Destroy(builder);
      return renderer;
  }
  
  // ...
  // Set the preferred output device for the specified audio playback stream.
  napi_value SelectOutputDeviceForAudioRenderer(napi_env env, napi_callback_info info)
  {
      int32_t deviceId = 0;
      ParseInt32Arg(env, info, deviceId);
      std::string errorMsg;
      OH_AudioDeviceEnhanceManager *enhanceManager = GetEnhanceManager(errorMsg);
      // ...
      OH_AudioRenderer *renderer = CreateAudioRenderer();
      // ...
  
      DeviceSearchResult search = FindDescriptorById(deviceId, AUDIO_DEVICE_USAGE_MEDIA_OUTPUT);
      OH_AudioCommon_Result result = OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer(
          enhanceManager, renderer, search.targetDescriptor);
      ReleaseDeviceSearch(search);
      // ...
  }
  ```