# 实现音频输出设备路由切换
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

当应用进行音频输出时，系统将依据音频流类型自动匹配对应的输出设备。如果系统输出设备不满足应用需求，应用可通过`AVCastPicker`或`setDefaultOutputDevice`实现音频输出设备路由切换。在连接音频外设（如蓝牙耳机、有线耳机）的情况下，应用还可通过`setMediaOutputDevice`强制将媒体输出切换到扬声器。

从API版本26.0.0开始，PC/2in1设备还支持基于[AudioDeviceEnhanceManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md)和[native_audio_device_enhance_manager.h](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md)的输出设备切换能力，应用可按应用级或音频流级精确指定输出设备，满足多设备场景下对声音输出去向的控制需求。

以下各步骤示例为片段代码，可通过示例代码右下方链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample)。其中，[PC/2in1设备输出设备切换](#pc2in1设备输出设备切换)的完整示例请参见[ArkTS示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS)和[C/C++示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC)。

## 使用场景

1. 若应用需要为用户提供可视化、可交互的音频输出设备切换入口时，可以使用`AVCastPicker`组件，开发者只需在布局中放置该组件，系统会自动检测当前可用的音频输出设备列表，用户点击后即可完成路由切换。
2. 扬声器/听筒设备切换典型场景：
   - **语音消息私密播放**：语音消息流（STREAM_USAGE_VOICE_MESSAGE）默认从扬声器播放，便于用户直接收听。但在会议、公共场合等私密场景下，应用希望语音消息默认从听筒播放，以保护用户隐私。此时应用可调用`setDefaultOutputDevice`将默认输出设备设置为听筒（EARPIECE）。
   - **VoIP通话听筒/扬声器切换**：VoIP通话（STREAM_USAGE_VOICE_COMMUNICATION）过程中，用户可在听筒和扬声器之间切换。应用可通过`setDefaultOutputDevice`设置通话流的默认输出设备；通话中如需临时切换，可再次调用`setDefaultOutputDevice`将输出设备更新为新的目标设备。
   - **视频通话外放场景**：视频通话（STREAM_USAGE_VIDEO_COMMUNICATION）时，用户通常希望声音从扬声器外放。应用可将默认输出设备设置为扬声器（SPEAKER），在无外设连接时，视频通话声音从扬声器输出。
   - **外设断开后的回落播放**：设置了默认输出设备后，当蓝牙耳机、有线耳机等外设断开时，系统会自动将音频切换回设置的默认输出设备播放，应用无需主动切换设备。
3. 连接蓝牙耳机或有线耳机等外设时，系统优先从外设播放。但某些场景下，应用希望即使外设已连接，仍将媒体音频强制切换到扬声器播放（如实时翻译对话给对方）。从API版本26.0.0开始，开发者可调用`setMediaOutputDevice`接口，在连接外设的情况下通过将参数设为`audio.DeviceType.SPEAKER`强制切换媒体输出设备为扬声器；需要恢复系统默认路由时，可再次调用`setMediaOutputDevice`接口，将参数设为`audio.DeviceType.DEFAULT`即可。

## 实现媒体流输出设备路由切换

应用可以通过使用[AVCastPicker](../../reference/apis-avsession-kit/ohos-multimedia-avcastpicker.md#avcastpicker)组件为用户提供选择设备的入口。

该组件集成了设备发现、连接、认证等能力，可嵌入应用界面。用户点击后，系统自动识别并展示当前可切换的设备列表，支持在扬声器、耳机、智能音箱等输出设备间自由切换。

## 实现通话流输出设备路由切换

`AVCastPicker`组件也适用于通话场景，应用可使用[通话设备切换组件](../avsession/using-switch-call-devices.md)为用户提供听筒、扬声器、耳机等通话设备的切换入口，方便用户在通话过程中灵活调整音频输出设备。

## 设置默认输出设备

如果系统未连接外设（如蓝牙耳机），语音通话场景音频默认听筒播放，其他场景音频默认扬声器播放；外设接入后，系统优先从外设播放。应用可通过`setDefaultOutputDevice`更改默认输出设备，但仅对以下三种[StreamUsage](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)生效：

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| STREAM_USAGE_VOICE_MESSAGE | 5 | 语音消息。 |
| STREAM_USAGE_VOICE_COMMUNICATION | 2 | VoIP语音通话。 |
| STREAM_USAGE_VIDEO_COMMUNICATION | 17 | VoIP视频通话。 |

支持的设备类型：

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| EARPIECE | 1 | 听筒。 |
| SPEAKER | 2 | 扬声器。 |
| DEFAULT | 1000 | 跟随系统。 |

调用此接口后，系统会记录指定的默认输出设备。当无外接设备连接时，音频流将路由至指定默认输出设备播放；当外设接入时，系统优先从外设播放，外设断开后自动切换至设置的默认输出设备。

### 开发步骤

`AudioRenderer`和`AudioSessionManager`都提供了`setDefaultOutputDevice`接口，用于设置通话或语音的默认输出设备。

- 音频流级：`AudioRenderer`接口生效范围为单流级别，仅对当前`AudioRenderer`实例对应的音频流生效。
- 应用级：`AudioSessionManager`接口对当前应用内所有语音和通话音频流生效，不限于单个`AudioRenderer`实例。

应用级接口优先级高于音频流级，如果同时调用了两个接口，`AudioSessionManager`的设置会覆盖`AudioRenderer`，`AudioRenderer`的设置将不再生效。

**音频流级设置接口**

从API version 12开始，应用可使用AudioRenderer的[setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setdefaultoutputdevice12)设置默认设备为听筒和扬声器，调用前需要先获取[AudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-f.md#audiocreateaudiorenderer8)实例，设置默认设备的生命周期跟随音频流。调用`setDefaultOutputDevice`设置音频输出设备后，如需取消，可将参数设为`audio.DeviceType.DEFAULT`，将音频输出设备选择权交还给系统。

   > **说明：**
   >
   > - 由于AudioRenderer是流级别，调用本接口设置的默认音频输出设备仅对当前流生效。
   > - 本接口优先级低于AudioSessionManager的[setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20)。如果使用AudioSessionManager的[setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20)设置了默认音频输出设备，本接口的设置将不会生效。

   ArkTS-Dyn示例：

   <!-- @[audioRenderer_setDefaultOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceSwitcher.ets) -->  
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
   
       // 设置默认输出设备为扬声器。
       audioRenderer.setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
         console.info('Succeeded in setting default output device.');
         // ...
       }).catch((err: BusinessError) => {
         console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
         // ...
       });
       // ...
   
       // 设置默认输出设备为听筒。
       audioRenderer.setDefaultOutputDevice(audio.DeviceType.EARPIECE).then(() => {
         console.info('Succeeded in setting default output device.');
         // ...
       }).catch((err: BusinessError) => {
         console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
         // ...
       });
   ```

   ArkTS-Sta示例：

   <!-- @[audioRenderer_setDefaultOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Audio/AudioRoutingAndVolumeManagerSample-Sta/entry/src/main/ets/pages/AudioOutputDeviceSwitcher.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
   
       // 设置默认输出设备为本机扬声器。
       (audioRenderer as audio.AudioRenderer).setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
         console.info('Succeeded in setting default output device.');
         // ...
       }).catch((err) => {
         console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
         // ...
       });
       // ...
   
       // 设置默认输出设备为本机听筒。
       (audioRenderer as audio.AudioRenderer).setDefaultOutputDevice(audio.DeviceType.EARPIECE).then(() => {
         console.info('Succeeded in setting default output device.');
         // ...
       }).catch((err) => {
         console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
         // ...
       });
   ```

**应用级设置接口**

从API version 20开始，应用激活[AudioSession](../audio/audio-session-management.md)后，可使用AudioSessionManager的[setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20)设置默认输出设备，并通过`AudioSessionManager.getDefaultOutputDevice`查看默认设备是否设置成功，设置默认设备的生命周期跟随`AudioSession`。调用`setDefaultOutputDevice`设置音频输出设备后，如需取消，可将参数设为`audio.DeviceType.DEFAULT`，将音频输出设备选择权交还给系统。

   > **说明：**
   >
   > 由于AudioSessionManager是应用级设置，调用本接口设置默认音频输出设备，会对当前应用所有适用范围内的音频流生效，且会覆盖AudioRenderer的[setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setdefaultoutputdevice12)接口设置的默认音频输出设备信息。

   ArkTS-Dyn示例：

   <!-- @[audioSessionManager_setDefaultOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceSwitcher.ets) -->  
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
   
   let audioManager = audio.getAudioManager();
   let audioSessionManager = audioManager.getSessionManager();
   // ...
   
     // 应用根据业务场景设置适合自己的音频会话场景，激活AudioSession时，系统会根据应用选择的音频会话场景申请对应的音频焦点。
     audioSessionManager.setAudioSessionScene(audio.AudioSessionScene.AUDIO_SESSION_SCENE_VOICE_COMMUNICATION);
   
     // 设置音频会话策略。
     let strategy: audio.AudioSessionStrategy = {
       concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
     };
   
     // 激活AudioSession。
     audioSessionManager.activateAudioSession(strategy).then(() => {
       console.info('Succeeded in activating audio session.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to activate audio session. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
     // ...
   
     // 设置默认输出设备为扬声器。
     audioSessionManager.setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
       console.info('Succeeded in setting default output device.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
     // ...
   
     // 设置默认输出设备为听筒。
     audioSessionManager.setDefaultOutputDevice(audio.DeviceType.EARPIECE).then(() => {
       console.info('Succeeded in setting default output device.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
   ```

   ArkTS-Sta示例：

   <!-- @[audioSessionManager_setDefaultOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Audio/AudioRoutingAndVolumeManagerSample-Sta/entry/src/main/ets/pages/AudioOutputDeviceSwitcher.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
   
   let audioManager = audio.getAudioManager();
   let audioSessionManager = audioManager.getSessionManager();
   // ...
   
     // 设置音频会话策略。
     let strategy: audio.AudioSessionStrategy = {
       concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
     };
   
     // 激活AudioSession。
     audioSessionManager.activateAudioSession(strategy).then(() => {
       console.info('Succeeded in activating audio session.');
       // ...
     }).catch((err) => {
       console.error(`Failed to activate audio session. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
     // ...
   
     // 设置默认输出设备为本机扬声器。
     audioSessionManager.setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
       console.info('Succeeded in setting default output device.');
       // ...
     }).catch((err) => {
       console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
     // ...
   
     // 设置默认输出设备为本机听筒。
     audioSessionManager.setDefaultOutputDevice(audio.DeviceType.EARPIECE).then(() => {
       console.info('Succeeded in setting default output device.');
       // ...
     }).catch((err) => {
       console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
   ```

## 连接外设时强制切换媒体输出设备

当系统连接蓝牙耳机或有线耳机等外设时，系统优先从外设播放。从API版本26.0.0开始，应用可使用`AudioSessionManager`的[setMediaOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setmediaoutputdevice)接口，强制将媒体输出设备切换为扬声器，使音频在连接外设的情况下仍从扬声器播放。

   > **说明：**
   >
   > - 本接口仅对媒体流生效，作用于应用内所有媒体流，通话流不受影响。应用需处于前台且有正在运行的媒体流，否则设置不生效且应用退出后自动清除。
   > - 本接口设置的输出设备与[实现媒体流输出设备路由切换](#实现媒体流输出设备路由切换)设置的输出设备会相互覆盖（后调用者会覆盖先调用者设置的输出设备）。
   > - 本接口设置的输出设备不会覆盖通过[设置默认输出设备](#设置默认输出设备)设置的输出设备。
   > - 应用可通过监听[CurrentOutputDeviceChangedEvent](../../reference/apis-audio-kit/arkts-apis-audio-i.md#currentoutputdevicechangedevent20)事件获取当前输出设备信息，以确认设置的输出设备是否生效。
   > - 在无内置扬声器的设备（如智慧屏）上调用本接口将输出设备切换为扬声器不会生效，但接口调用仍会返回成功，不会抛出错误或触发错误回调。

### 开发步骤

应用可使用`AudioSessionManager`的[setMediaOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setmediaoutputdevice)接口强制将媒体输出设备切换为扬声器。调用`setMediaOutputDevice`后，如需取消强制切换、恢复系统默认路由规则，可将参数设为`audio.DeviceType.DEFAULT`。

支持的设备类型：

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| SPEAKER | 2 | 扬声器，强制将媒体输出切换到扬声器。 |
| DEFAULT | 1000 | 系统默认设备，清除强制切换，恢复系统默认路由规则。 |

   ArkTS-Dyn示例：

   <!-- @[audioSessionManager_setMediaOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceSwitcher.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
   
   let audioManager = audio.getAudioManager();
   let audioSessionManager = audioManager.getSessionManager();
   // ...
   
     // 连接蓝牙耳机后，强制将媒体输出设备切换为扬声器。
     audioSessionManager.setMediaOutputDevice(audio.DeviceType.SPEAKER).then(() => {
       console.info('Succeeded in setting media output device to speaker.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to set media output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
     // ...
   
     // 取消强制切换，将媒体输出设备选择权交还给系统默认路由规则。
     audioSessionManager.setMediaOutputDevice(audio.DeviceType.DEFAULT).then(() => {
       console.info('Succeeded in setting media output device to default.');
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to set media output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
   ```

   ArkTS-Sta示例：

   <!-- @[audioSessionManager_setMediaOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Audio/AudioRoutingAndVolumeManagerSample-Sta/entry/src/main/ets/pages/AudioOutputDeviceSwitcher.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
   
   let audioManager = audio.getAudioManager();
   let audioSessionManager = audioManager.getSessionManager();
   // ...
   
     // 连接蓝牙耳机后，强制将媒体输出设备切换为扬声器。
     audioSessionManager.setMediaOutputDevice(audio.DeviceType.SPEAKER).then(() => {
       console.info('Succeeded in setting media output device to speaker.');
       // ...
     }).catch((err) => {
       console.error(`Failed to set media output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
     // ...
   
     // 取消强制切换，将媒体输出设备选择权交还给系统默认路由策略。
     audioSessionManager.setMediaOutputDevice(audio.DeviceType.DEFAULT).then(() => {
       console.info('Succeeded in setting media output device to default.');
       // ...
     }).catch((err) => {
       console.error(`Failed to set media output device. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
   ```

## PC/2in1设备输出设备切换

PC/2in1设备经常存在多路输出设备可用（如内置扬声器、外接音箱、USB/蓝牙耳机等），系统默认的设备选择策略可能无法满足应用在各种场景下的输出需求。通过本能力，应用可按**应用级**或**音频流级**精确指定输出设备，满足多设备场景下对声音输出去向的控制需求。

### 查询能力是否支持

使用前需先通过[isEnhancedRoutingSupported](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md#isenhancedroutingsupported)或[OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_isenhancedroutingsupported)查询系统是否支持该能力，不支持时调用输出设备切换接口不生效，将继续使用当前输出设备。

ArkTS示例：

ArkTS-Dyn示例：

<!-- @[isEnhancedRoutingSupported](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...
  let audioManager = audio.getAudioManager();
  let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
  // 查询系统是否支持当前管理器提供的增强路由能力。
  let isSupported: boolean = audioDeviceEnhanceManager.isEnhancedRoutingSupported();
  console.info(`Succeeded in querying whether enhanced routing is supported. Result: ${isSupported}.`);
```

ArkTS-Sta示例：

<!-- @[isEnhancedRoutingSupported](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Audio/AudioEnhanceDeviceSample-Sta/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

``` TypeScript
import audio from '@ohos.multimedia.audio';
import common from '@ohos.app.ability.common';
import abilityAccessCtrl from '@ohos.abilityAccessCtrl';
// ...

let audioManager = audio.getAudioManager();
let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();

// ...
  let isSupported: boolean = audioDeviceEnhanceManager.isEnhancedRoutingSupported();
  console.info(`Succeeded in querying whether enhanced routing is supported. Result: ${isSupported}.`);
  // ...
```

C/C++示例：

使用前需添加头文件：

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
    // 查询系统是否支持当前管理器提供的增强路由能力。
    result = OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(enhanceManager, &isSupported);
    // ...
}
```

### 切换输出设备

输出设备切换支持应用级和音频流级两种粒度，应用级对应用下所有播放流生效，音频流级仅对指定播放流生效，且音频流级的优先级高于应用级。

> **说明：**
>
> 若某条播放流已通过音频流级接口指定了专属输出设备，则该流使用其专属输出设备，应用内其他播放流仍使用应用级设置的输出设备或系统默认输出设备。

ArkTS示例：

- **应用级：** 通过[selectOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md#selectoutputdevice)选择指定的输出设备，设置成功后对应用下创建的所有播放流生效。

  ArkTS-Dyn示例：

  <!-- @[select_OutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  // ...
    let audioManager = audio.getAudioManager();
    let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
    // 为应用选择输出设备，此处device可通过ArkTS完整示例查看获取方式。
    audioDeviceEnhanceManager.selectOutputDevice(device).then(() => {
      console.info('Succeeded in selecting output device.');
      // ...
    }).catch((err: BusinessError) => {
      console.error(`Failed to select output device. Code: ${err.code}, message: ${err.message}`);
      // ...
    });
  ```

  ArkTS-Sta示例：

  <!-- @[select_OutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Audio/AudioEnhanceDeviceSample-Sta/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

  ``` TypeScript
  import audio from '@ohos.multimedia.audio';
  import common from '@ohos.app.ability.common';
  import abilityAccessCtrl from '@ohos.abilityAccessCtrl';
  // ...
  
  let audioManager = audio.getAudioManager();
  let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
  
  let audioSessionManager = audioManager.getSessionManager();
  
  // ...
    try {
      await audioDeviceEnhanceManager.selectOutputDevice(device);
      console.info('Succeeded in selecting output device.');
      // ...
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to select output device. Code: ${error.code}, message: ${error.message}`);
      // ...
    }
  ```

- **音频流级：** 通过[selectOutputDeviceForAudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md#selectoutputdeviceforaudiorenderer)为指定音频播放流选择输出设备，设置成功后仅对该播放流生效。

  ArkTS-Dyn示例：

  <!-- @[select_OutputDeviceForAudioRenderer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  // ...
    let audioManager = audio.getAudioManager();
    let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
    // 为指定音频播放流设置首选输出设备，此处renderer和outputDevice可通过ArkTS完整示例查看获取方式。
    audioDeviceEnhanceManager.selectOutputDeviceForAudioRenderer(renderer, outputDevice).then(() => {
      console.info('Succeeded in selecting output device for audio renderer.');
      // ...
    }).catch((err: BusinessError) => {
      console.error(`Failed to select output device for audio renderer. Code: ${err.code}, message: ${err.message}`);
      // ...
    });
  ```

  ArkTS-Sta示例：

  <!-- @[select_OutputDeviceForAudioRenderer](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/Audio/AudioEnhanceDeviceSample-Sta/entry/src/main/ets/pages/EnhancedDeviceRouting.ets) -->

  ``` TypeScript
  import audio from '@ohos.multimedia.audio';
  import common from '@ohos.app.ability.common';
  import abilityAccessCtrl from '@ohos.abilityAccessCtrl';
  // ...
  
  let audioManager = audio.getAudioManager();
  let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
  
  let audioSessionManager = audioManager.getSessionManager();
  
  // ...
  let audioRenderer: audio.AudioRenderer | undefined = undefined;
  // ...
    try {
      await audioDeviceEnhanceManager.selectOutputDeviceForAudioRenderer(renderer, outputDevice);
      console.info('Succeeded in selecting output device for audio renderer.');
      // ...
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to select output device for audio renderer. Code: ${error.code}, message: ${error.message}`);
      // ...
    }
  ```

C/C++示例：

- **应用级：** 通过[OH_AudioDeviceEnhanceManager_SelectOutputDevice](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_selectoutputdevice)选择指定的输出设备。

  <!-- @[select_OutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC/entry/src/main/cpp/EnhancedDeviceRouting.cpp) -->

  ``` C++
  // 获取音频设备增强管理器。
  static OH_AudioDeviceEnhanceManager *GetEnhanceManager(std::string &errorMsg)
  {
      OH_AudioDeviceEnhanceManager *manager = nullptr;
      OH_AudioCommon_Result result = OH_AudioManager_GetAudioDeviceEnhanceManager(&manager);
      if (result != AUDIOCOMMON_RESULT_SUCCESS || manager == nullptr) {
          errorMsg = "获取AudioDeviceEnhanceManager失败";
          return nullptr;
      }
      bool isSupported = false;
      OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(manager, &isSupported);
      if (!isSupported) {
          errorMsg = "Enhanced routing不支持，该功能不会生效";
          return nullptr;
      }
      return manager;
  }
  
  struct DeviceSearchResult {
      OH_AudioRoutingManager *routingManager;
      OH_AudioDeviceDescriptorArray *deviceArray;
      OH_AudioDeviceDescriptor *targetDescriptor;
  };
  
  // 获取音频可选设备。
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
  // 为应用选择输出设备。
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

- **音频流级：** 通过[OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer](../../reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_selectoutputdeviceforaudiorenderer)为指定音频播放流选择输出设备。

  <!-- @[select_OutputDeviceForAudioRenderer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC/entry/src/main/cpp/EnhancedDeviceRouting.cpp) -->

  ``` C++
  // 获取音频设备增强管理器。
  static OH_AudioDeviceEnhanceManager *GetEnhanceManager(std::string &errorMsg)
  {
      OH_AudioDeviceEnhanceManager *manager = nullptr;
      OH_AudioCommon_Result result = OH_AudioManager_GetAudioDeviceEnhanceManager(&manager);
      if (result != AUDIOCOMMON_RESULT_SUCCESS || manager == nullptr) {
          errorMsg = "获取AudioDeviceEnhanceManager失败";
          return nullptr;
      }
      bool isSupported = false;
      OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(manager, &isSupported);
      if (!isSupported) {
          errorMsg = "Enhanced routing不支持，该功能不会生效";
          return nullptr;
      }
      return manager;
  }
  
  struct DeviceSearchResult {
      OH_AudioRoutingManager *routingManager;
      OH_AudioDeviceDescriptorArray *deviceArray;
      OH_AudioDeviceDescriptor *targetDescriptor;
  };
  
  // 获取音频可选设备。
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
  // 创建音频渲染器。
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
  // 为指定音频播放流设置首选输出设备。
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

## 扬声器/听筒设备切换常见问题

### 设置了默认输出设备但未生效

调用`setDefaultOutputDevice`设置扬声器或听筒后，实际播放设备未变化，常见原因如下：

- **流类型不受支持**：
  - **可能原因**：`setDefaultOutputDevice`仅对以下三种[StreamUsage](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)生效：`STREAM_USAGE_VOICE_MESSAGE`、`STREAM_USAGE_VOICE_COMMUNICATION`、`STREAM_USAGE_VIDEO_COMMUNICATION`。媒体播放（如音乐、视频）等流类型调用本接口不会生效。
  - **解决措施**：改用上述三种受支持的流类型创建音频流后，再调用本接口。
- **外设仍处于连接状态**：
  - **可能原因**：外设（如蓝牙耳机、有线耳机）接入时，系统优先从外设播放，设置的默认输出设备仅在无外设连接时生效。
  - **解决措施**：断开外设后系统会自动回落至设置的默认输出设备；如需在外设连接状态下强制切换到扬声器，可参考[连接外设时强制切换媒体输出设备](#连接外设时强制切换媒体输出设备)。
- **应用级设置覆盖流级设置**：
  - **可能原因**：如果同时通过`AudioSessionManager.setDefaultOutputDevice`和`AudioRenderer.setDefaultOutputDevice`设置了默认输出设备，应用级设置会覆盖流级设置，`AudioRenderer`的设置将不生效。
  - **解决措施**：检查是否同时设置了应用级与流级默认输出设备，确认[设置默认输出设备](#设置默认输出设备)中两种方式的优先级，按需移除其一。
- **设备无听筒**：
  - **可能原因**：在无听筒（EARPIECE）的设备（如智慧屏、部分平板）上，将默认输出设备设置为听筒不会生效，系统将继续使用扬声器或其他可用设备播放。
  - **解决措施**：先通过[getDevicesSync](../../reference/apis-audio-kit/arkts-apis-audio-AudioRoutingManager.md#getdevicessync10)查询确认设备是否支持听筒，若不支持则改用扬声器或其他可用设备作为目标设备。

### 通话时无法切换到听筒或扬声器

**可能原因**：当前通话使用的音频流[StreamUsage](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)不是`STREAM_USAGE_VOICE_COMMUNICATION`或`STREAM_USAGE_VIDEO_COMMUNICATION`。

**解决措施**：若使用其他流类型（如媒体流）进行通话，需先调整为上述流类型或改用其他切换方式。

### 设置默认输出设备后外设接入，声音从外设播放

系统默认策略为外设接入后优先从外设播放，设置的默认输出设备仅在外设断开后生效，这是为了尊重用户显式连接外设的意图。该行为符合预期。

### 不确定默认输出设备是否生效

应用可通过[AudioSessionManager.getDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#getdefaultoutputdevice20)查询通过`setDefaultOutputDevice`设置的默认输出设备类型；也可监听[CurrentOutputDeviceChangedEvent](../../reference/apis-audio-kit/arkts-apis-audio-i.md#currentoutputdevicechangedevent20)事件获取当前实际输出设备，以确认设备切换是否生效。