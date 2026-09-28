# Switching Audio Input Devices
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d538122145fbb0d7b382ef7934270d2fe6f83e9d translatedAt=2026-09-02T07:32:23.072Z pushedAt=2026-09-02T07:41:09.103Z -->

Starting from API version 21, support for switching audio input device routes is available.

When an application performs audio input, the system selects the corresponding input device based on the audio stream type. (If the audio stream type is **SOURCE_TYPE_MIC**, the built-in microphone is used for recording. If the audio stream type is **SOURCE_TYPE_VOICE_COMMUNICATION**, the input device follows the current output device.) If the default input device does not meet the application requirements, the application can call [setBluetoothAndNearlinkPreferredRecordCategory](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setbluetoothandnearlinkpreferredrecordcategory21) or [selectMediaInputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#selectmediainputdevice21) to switch the audio input device.

Starting from API version 26.0.0, PCs/2-in-1 devices also support input device switching based on [AudioDeviceEnhanceManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md) and [native_audio_device_enhance_manager.h](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md). You can specify the input device precisely at the application level or audio stream level to control the audio capture source in multi-device scenarios.

The code snippets in the following steps are fragments. You can obtain the [complete sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample) from the link at the lower right of the sample code. For the complete sample of [input device switching on PCs/2-in-1 devices](#input-device-switching-on-pcs2-in-1-devices), see the [ArkTS sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS) and [C/C++ sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC).

## Preferring Bluetooth or NearLink Devices for Recording

Applications can use [setBluetoothAndNearlinkPreferredRecordCategory](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setbluetoothandnearlinkpreferredrecordcategory21) of AudioSessionManager to express a preference for Bluetooth or NearLink devices when they become available.

> **NOTE**
>
> In call scenarios, if a Bluetooth or NearLink device is online, the system uses the Bluetooth or NearLink device as the input device by default.

<!-- @[setBluetoothAndNearlinkPreferredRecordCategory](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioInputDeviceSwitcher.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

let audioManager = audio.getAudioManager();
let audioSessionManager = audioManager.getSessionManager();
// ...

  audioSessionManager.setBluetoothAndNearlinkPreferredRecordCategory(audio.BluetoothAndNearlinkPreferredRecordCategory.
    PREFERRED_DEFAULT).then(() => {
    console.info('Succeeded in setting bluetooth and nearlink preferred record category.');
    // ...
  }).catch((err: BusinessError) => {
    console.error(`Failed to set bluetooth and nearlink preferred record category. Code: ${err.code}, message: ${err.message}`);
    // ...
  });
```

## Manually Selecting Input Devices

Applications can use [selectMediaInputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#selectmediainputdevice21) of AudioSessionManager to select an input device.

> **NOTE**
>
> In call scenarios, the input device follows the current output device, and other concurrent recording streams also follow the call input device.

<!-- @[selectMediaInputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioInputDeviceSwitcher.ets) -->  

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

let audioManager = audio.getAudioManager();
let audioSessionManager = audioManager.getSessionManager();
// ...

  try {
    // Listen for the current input device change event. This callback is triggered after an input device is successfully selected.
    audioSessionManager.on('currentInputDeviceChanged', (currentInputDeviceChangedEvent: audio.CurrentInputDeviceChangedEvent) => {
      console.info(`Succeeded in using on function. CurrentInputDeviceChangedEvent: ${JSON.stringify(currentInputDeviceChangedEvent)}`);
      // ...
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to use on function. Code: ${error.code}, message: ${error.message}`);
    // ...
  }
  // ...

  try {
    // Listen for the connection status change event of available audio input devices. A callback notification is received when an input device goes online or offline.
    audioSessionManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_INPUT_DEVICES, (deviceChanged: audio.DeviceChangeAction) => {
      console.info(`Succeeded in using on function. DeviceChangeAction: ${JSON.stringify(deviceChanged)}`);
      // ...
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to use on function. Code: ${error.code}, message: ${error.message}`);
    // ...
  }
  // ...

  try {
    // Obtain the list of currently available audio input devices.
    let data = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_INPUT_DEVICES);
    console.info(`Succeeded in getting available devices. AudioDeviceDescriptors: ${JSON.stringify(data)}`);
    // You can select a device when the list of available audio input devices is not empty.
    if (data[1] || data[0]) {
      // Select an input device.
      audioSessionManager.selectMediaInputDevice(data[1] ? data[1] : data[0]).then(() => {
        console.info('Succeeded in selecting media input device.');
        // ...
      }).catch((err: BusinessError) => {
        console.error(`Failed to select media input device. Code: ${err.code}, message: ${err.message}`);
        // ...
      });
    }
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to getAvailableDevices. Code: ${error.code}, message: ${error.message}`);
    // ...
  }
  // ...

  try {
    // You can query whether the input device selection is successful through this API.
    let device = audioSessionManager.getSelectedMediaInputDevice();
    console.info(`Succeeded in getting selected media input device. Device: ${JSON.stringify(device)}`);
    // ...
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to get selected media input device. Code: ${error.code}, message: ${error.message}`);
    // ...
  }
  // ...

  // Clear the input device selected via selectMediaInputDevice.
  audioSessionManager.clearSelectedMediaInputDevice().then(() => {
    console.info('Succeeded in clearing selected media input device.');
    // ...
  }).catch((err: BusinessError) => {
    console.error(`Failed to clear selected media input device. Code: ${err.code}, message: ${err.message}`);
    // ...
  });
```

## Input Device Switching on PCs/2-in-1 Devices

PCs/2-in-1 devices often have multiple input devices available (such as the built-in microphone and USB/Bluetooth headset microphones). The system default device selection policy may not meet the input requirements of applications in various scenarios. With this capability, you can precisely specify the input device at the **application level** or **audio stream level**, meeting the requirement for controlling the audio capture source in multi-device scenarios.

### Checking Whether the Capability Is Supported

Before use, call [isEnhancedRoutingSupported](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md#isenhancedroutingsupported) or [OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_isenhancedroutingsupported) to check whether the system supports this capability. If the capability is not supported, calling the input device switching APIs does not take effect, and the current input device continues to be used.

ArkTS sample code:

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

### Switching Input Devices

Input device switching supports two granularities: application level and audio stream level. The application level takes effect on all recording streams under an application, while the audio stream level takes effect only on a specified recording stream. The audio stream level has a higher priority than the application level.

> **NOTE**
>
> If a recording stream has been assigned a dedicated input device through an audio stream-level API, that stream uses its dedicated input device, while other recording streams in the application still use the input device set at the application level or the system default input device.

ArkTS sample code:

- **Application level:** Use [selectInputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md#selectinputdevice) to select a specified input device. After the setting succeeds, it takes effect on all recording streams created under the application.

  <!-- @[select_InputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  // ...
    let audioManager = audio.getAudioManager();
    let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
    // Select an input device for the application. For details about how to obtain device, see the complete ArkTS example.
    audioDeviceEnhanceManager.selectInputDevice(device).then(() => {
      console.info('Succeeded in selecting input device.');
      // ...
    }).catch((err: BusinessError) => {
      console.error(`Failed to select input device. Code: ${err.code}, message: ${err.message}`);
      // ...
    });
  ```

- **Audio stream level:** Use [selectInputDeviceForAudioCapturer](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md#selectinputdeviceforaudiocapturer) to select an input device for a specified audio recording stream. After the setting succeeds, it takes effect only on that recording stream.

  <!-- @[select_InputDeviceForAudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  // ...
    let audioManager = audio.getAudioManager();
    let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
    // Set the preferred input device for the specified audio recording stream. For details about how to obtain capturer and inputDevice, see the complete ArkTS example.
    audioDeviceEnhanceManager.selectInputDeviceForAudioCapturer(capturer, inputDevice).then(() => {
      console.info('Succeeded in selecting input device for audio capturer.');
      // ...
    }).catch((err: BusinessError) => {
      console.error(`Failed to select input device for audio capturer. Code: ${err.code}, message: ${err.message}`);
      // ...
    });
  ```

C/C++ example:

- **Application level:** Use [OH_AudioDeviceEnhanceManager_SelectInputDevice](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_selectinputdevice) to select a specified input device.

  <!-- @[select_InputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC/entry/src/main/cpp/EnhancedDeviceRouting.cpp) -->

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
  
  // Obtain the selectable audio devices.
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
  // Select an input device for the application.
  napi_value SelectInputDevice(napi_env env, napi_callback_info info)
  {
      int32_t deviceId = 0;
      ParseInt32Arg(env, info, deviceId);
      std::string errorMsg;
      OH_AudioDeviceEnhanceManager *enhanceManager = GetEnhanceManager(errorMsg);
      // ...
  
      DeviceSearchResult search = FindDescriptorById(deviceId, AUDIO_DEVICE_USAGE_MEDIA_INPUT);
      OH_AudioCommon_Result result = OH_AudioDeviceEnhanceManager_SelectInputDevice(
          enhanceManager, search.targetDescriptor);
      ReleaseDeviceSearch(search);
      // ...
  }
  ```

- **Audio stream level:** Use [OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_selectinputdeviceforaudiocapturer) to select an input device for a specified audio recording stream.

  <!-- @[select_InputDeviceForAudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC/entry/src/main/cpp/EnhancedDeviceRouting.cpp) -->

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
  // Create an audio capturer.
  static OH_AudioCapturer *CreateAudioCapturer()
  {
      OH_AudioStreamBuilder *builder = nullptr;
      if (OH_AudioStreamBuilder_Create(&builder, AUDIOSTREAM_TYPE_CAPTURER) != AUDIOSTREAM_SUCCESS) {
          return nullptr;
      }
      OH_AudioStreamBuilder_SetSamplingRate(builder, SAMPLE_RATE_48K);
      OH_AudioStreamBuilder_SetChannelCount(builder, CHANNEL_COUNT_STEREO);
      OH_AudioStreamBuilder_SetSampleFormat(builder, AUDIOSTREAM_SAMPLE_S16LE);
      OH_AudioStreamBuilder_SetEncodingType(builder, AUDIOSTREAM_ENCODING_TYPE_RAW);
      OH_AudioStreamBuilder_SetCapturerInfo(builder, AUDIOSTREAM_SOURCE_TYPE_VOICE_COMMUNICATION);
      OH_AudioCapturer *capturer = nullptr;
      OH_AudioStreamBuilder_GenerateCapturer(builder, &capturer);
      OH_AudioStreamBuilder_Destroy(builder);
      return capturer;
  }
  
  // ...
  // Set the preferred input device for the specified audio capture stream.
  napi_value SelectInputDeviceForAudioCapturer(napi_env env, napi_callback_info info)
  {
      int32_t deviceId = 0;
      ParseInt32Arg(env, info, deviceId);
      std::string errorMsg;
      OH_AudioDeviceEnhanceManager *enhanceManager = GetEnhanceManager(errorMsg);
      // ...
      OH_AudioCapturer *capturer = CreateAudioCapturer();
      // ...
  
      DeviceSearchResult search = FindDescriptorById(deviceId, AUDIO_DEVICE_USAGE_MEDIA_INPUT);
      OH_AudioCommon_Result result = OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer(
          enhanceManager, capturer, search.targetDescriptor);
      ReleaseDeviceSearch(search);
      // ...
  }
  ```