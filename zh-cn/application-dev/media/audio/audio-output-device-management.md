---
kits: ["Audio Kit / 音频服务"]
description: "介绍音频输出设备管理能力，指导开发者通过AudioRoutingManager和AudioSession两种方式查询输出设备信息、监听设备连接与优先级变化。"
keywords: [音频输出设备, AudioRoutingManager, AudioSessionManager, getDevices, getPreferOutputDeviceForRendererInfo, setDefaultOutputDevice, 扬声器, 听筒, 蓝牙耳机, 外放, 设备监听, 设备查询]
doctype: guide
status: active
---
# 查询和监听音频输出设备
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
应用可通过以下两种方式查询和监听音频输出设备：
- 通常情况下，可以[通过AudioRoutingManager查询和监听音频输出设备](#通过audioroutingmanager查询和监听音频输出设备)。
- 从API version 20开始，AudioSessionManager提供了部分输出设备管理的接口，支持[通过AudioSession查询和监听音频输出设备](#通过audiosession查询和监听音频输出设备)，方便在使用AudioSession管理音频焦点的同时管理音频输出。

以下各步骤示例为片段代码，可通过示例代码右下方链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample)。

## 通过AudioRoutingManager查询和监听音频输出设备

本模块提供音频输出设备管理能力，包括查询设备信息和监听连接状态变化。具体API说明请参考文档[AudioRoutingManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioRoutingManager.md)。

### 创建AudioRoutingManager实例

在使用AudioRoutingManager管理音频设备前，需要先导入模块并创建实例。

<!-- @[getRoutingManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceManagement.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
// ...

let audioManager = audio.getAudioManager();
let audioRoutingManager = audioManager.getRoutingManager();
```

### 支持的音频输出设备类型

常见的音频输出设备类型如下表所示，类型定义请参考[DeviceType](../../reference/apis-audio-kit/arkts-apis-audio-e.md#devicetype)。实际可获取的设备取决于终端硬件能力和设备连接状态。

| 名称 | 值 | 说明 | 
| -------- | -------- | -------- |
| EARPIECE | 1 | 听筒。 | 
| SPEAKER | 2 | 扬声器。 | 
| WIRED_HEADSET | 3 | 有线耳机，带麦克风。 | 
| WIRED_HEADPHONES | 4 | 有线耳机，无麦克风。 | 
| BLUETOOTH_SCO | 7 | 蓝牙设备SCO（Synchronous&nbsp;Connection&nbsp;Oriented）连接。 | 
| BLUETOOTH_A2DP | 8 | 蓝牙设备A2DP（Advanced&nbsp;Audio&nbsp;Distribution&nbsp;Profile）连接。 | 
| USB_HEADSET | 22 | USB耳机，带麦克风。 | 
| NEARLINK | 31 | 星闪设备。 | 

上表为常用音频输出设备类型，其中听筒（EARPIECE）仅手机、平板等形态具备。在PC/2in1设备上，还支持以下音频外设作为输出设备：

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| DISPLAY_PORT | 23 | DP（DisplayPort）显示设备（如外接显示器）的音频输出。 |
| USB_DEVICE | 25 | USB音频设备（如USB音箱、USB声卡等非耳机类设备）的音频输出。 |
| HDMI | 27 | HDMI设备（如外接显示器、电视）的音频输出。 |
| LINE_DIGITAL | 28 | 数字音频接口（如光纤、同轴）的音频输出。 |

**PC/2in1设备的音频输出设备差异：**
1. **外设类型更丰富**：PC/2in1设备常通过DP、HDMI外接显示器，通过USB连接音箱等外设，因而额外支持上表四类输出设备，而手机形态一般仅有USB耳机、蓝牙、星闪、有线耳机等外设。
2. **无听筒设备**：PC/2in1设备没有听筒（EARPIECE），通话、语音等音频默认从扬声器或外接设备输出。
3. **多设备并发场景更常见**：PC/2in1设备经常同时连接多路输出设备（如内置扬声器+外接显示器+USB音箱）。从API版本26.0.0开始，应用可通过[AudioDeviceEnhanceManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md)按应用级或音频流级精确指定输出设备，满足多设备场景下对声音输出去向的控制需求。具体可参考[PC/2in1设备输出设备切换](audio-output-device-switcher.md#pc2in1设备输出设备切换)。

### 获取输出设备信息

使用[getDevices](../../reference/apis-audio-kit/arkts-apis-audio-AudioRoutingManager.md#getdevices9)方法，传入`audio.DeviceFlag.OUTPUT_DEVICES_FLAG`，可以获取当前输出设备的信息列表。

> **说明：**
>
> - 返回值为[AudioDeviceDescriptors](../../reference/apis-audio-kit/arkts-apis-audio-t.md#audiodevicedescriptors)，可通过设备描述符中的`id`、`deviceType`和`name`等属性识别设备。
>
> - 查询结果是调用时的设备列表，列表中的设备不一定是应用当前实际播放的设备。如需持续维护设备列表，应结合`deviceChange`事件处理设备连接和断开。
> - 如需查询指定音频流用途对应的最高优先级输出设备，请使用[getPreferOutputDeviceForRendererInfo](#获取最高优先级输出设备信息)。

<!-- @[getDevices](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceManagement.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

  audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG).then((audioDeviceDescriptors: audio.
    AudioDeviceDescriptors) => {
    console.info(`Succeeded in getting devices. AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}`);
    // ...
  }).catch((err: BusinessError) => {
    console.error(`Failed to get devices. Code: ${err.code}, message: ${err.message}`);
    // ...
  });
```

### 监听设备连接状态变化

设置监听事件以监控设备连接状态的变化，设备连接或断开时触发回调。

> **说明：**
>
> - 示例通过`audio.DeviceFlag.OUTPUT_DEVICES_FLAG`订阅输出设备的连接状态变化。回调参数`DeviceChangeAction.type`表示连接状态变化，`deviceDescriptors`提供发生变化的设备信息。
> - 不建议将设备连接状态变化直接作为自动暂停等业务处理的依据。应用如需处理自动暂停相关业务，可参考[音频流输出设备变更原因](audio-output-device-change.md#音频流输出设备变更原因)。
>
> - 不再需要监听时，应调用[off('deviceChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioRoutingManager.md#offdevicechange9)取消订阅。

<!-- @[onDeviceChange](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceManagement.ets) -->  

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

  try {
    // 监听音频输出设备状态变化。
    audioRoutingManager.on('deviceChange', audio.DeviceFlag.OUTPUT_DEVICES_FLAG, (deviceChanged: audio.DeviceChangeAction) => {
      console.info(`Succeeded in using on function. DeviceChangeAction: ${JSON.stringify(deviceChanged)}`);
      // ...
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to use on function. Code: ${error.code}, message: ${error.message}`);
    // ...
  }
```

<!--Del-->
### 选择音频输出设备（仅对系统应用开放）

选择音频输出设备，当前只能选择一个输出设备，以设备ID作为唯一标识。AudioDeviceDescriptors的具体信息可以参考[AudioDeviceDescriptors](../../reference/apis-audio-kit/arkts-apis-audio-t.md#audiodevicedescriptors)。

> **说明：**
>
> - 本接口仅对系统应用开放。应先查询输出设备列表，再将目标设备的描述符传入接口，避免直接使用示例中的设备ID和属性值。
> - 当前只能选择一个输出设备，传入的`AudioDeviceDescriptors`应包含一个目标设备描述符。
> - 用户可以选择连接一组音频设备（如一对蓝牙耳机），但系统侧只感知为一个设备，该组设备共用一个设备ID。

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let outputAudioDeviceDescriptor: audio.AudioDeviceDescriptors = [{
    deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
    deviceType : audio.DeviceType.SPEAKER,
    id : 1,
    name : "",
    address : "",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : ""
}];

async function selectOutputDevice() {
  audioRoutingManager.selectOutputDevice(outputAudioDeviceDescriptor).then(() => {
    console.info('Invoke selectOutputDevice succeeded.');
  }).catch((err: BusinessError) => {
    console.error(`Invoke selectOutputDevice failed, code is ${err.code}, message is ${err.message}`);
  });
}
```
<!--DelEnd-->

### 获取最高优先级输出设备信息

使用[getPreferOutputDeviceForRendererInfo](../../reference/apis-audio-kit/arkts-apis-audio-AudioRoutingManager.md#getpreferoutputdeviceforrendererinfo10)方法，可以获取当前最高优先级的输出设备。

> **说明：**
>
> - 最高优先级输出设备是系统根据传入的`AudioRendererInfo`和当前设备选择策略，为该类音频流确定的输出设备。`usage`应与业务实际使用的音频流用途一致，例如语音通话使用`STREAM_USAGE_VOICE_COMMUNICATION`。
> - 不同用途的音频流可能对应不同的输出设备，因此不能将某一种用途的查询结果作为所有音频流的输出设备。

<!-- @[getPreferOutputDeviceForRendererInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceManagement.ets) -->  

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

let audioRendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION, // 音频流使用类型：语音通话。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};
// ...

  audioRoutingManager.getPreferOutputDeviceForRendererInfo(audioRendererInfo).
    then((audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
    console.info(`Succeeded in getting prefer output device for renderer info. AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}`);
    // ...
  }).catch((err: BusinessError) => {
    console.error(`Failed to get prefer output device for renderer info. Code: ${err.code}, message: ${err.message}`);
    // ...
  });
```

### 监听最高优先级输出设备变化

调用[on('preferOutputDeviceChangeForRendererInfo')](../../reference/apis-audio-kit/arkts-apis-audio-AudioRoutingManager.md#onpreferoutputdevicechangeforrendererinfo10)，传入与业务场景一致的`AudioRendererInfo`。当该场景的最高优先级输出设备变化时，回调返回变化后的设备信息列表。

> **说明：**
>
> - 如需在界面首次展示时获取设备信息，应先调用查询接口，并结合监听接口更新后续变化。
> - 不再需要监听时，应调用[off('preferOutputDeviceChangeForRendererInfo')](../../reference/apis-audio-kit/arkts-apis-audio-AudioRoutingManager.md#offpreferoutputdevicechangeforrendererinfo10)取消订阅。

<!-- @[onPreferOutputDeviceChangeForRendererInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceManagement.ets) -->  

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

let audioRendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION, // 音频流使用类型：语音通话。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};
// ...

  try {
    audioRoutingManager.on('preferOutputDeviceChangeForRendererInfo', audioRendererInfo, (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
      console.info(`Succeeded in using on function. DeviceChangeAction: ${JSON.stringify(audioDeviceDescriptors)}`);
      // ...
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to use on function. Code: ${error.code}, message: ${error.message}`);
    // ...
  }
```

## 通过AudioSession查询和监听音频输出设备
应用使用播放器SDK播放音频流时，可能不持有[AudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md)对象，因此无法灵活控制播放设备的选择和状态监听。从API version 20开始，AudioSession在音频焦点管理的基础上提供了音频输出设备管理功能，包括设置默认输出设备和监听设备变化。请参考以下文档获取更多信息：
- ArkTS API：[AudioSessionManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md)
- C API：[native_audio_session_manager.h](../../reference/apis-audio-kit/capi-native-audio-session-manager-h.md)

### 创建AudioSession实例
在使用AudioSessionManager管理音频设备前，需要先导入模块并创建实例。

<!-- @[getSessionManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceManagement.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
// ...

let audioManager = audio.getAudioManager();
// ...
let audioSessionManager = audioManager.getSessionManager();
```

### 设置本机默认音频输出设备

[setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20)可以用于设置本机默认输出设备。
> **说明：**
> 
> - 本接口仅支持`audio.DeviceType.EARPIECE`（听筒）、`audio.DeviceType.SPEAKER`（扬声器）和`audio.DeviceType.DEFAULT`（系统默认设备），用于设置默认本机内置发声设备，不能用于指定蓝牙耳机或有线耳机。
> - AudioSessionManager是应用级设置，本接口会作用于当前应用所有适用范围内的音频流，并覆盖AudioRenderer的`setDefaultOutputDevice`接口设置的默认音频输出设备信息。
> - 调用`setDefaultOutputDevice`设置音频输出设备后，如需取消，可将参数设为`audio.DeviceType.DEFAULT`，将音频设备选择权交还给系统。未取消的配置会保留，并在后续激活AudioSession且满足上述适用条件时生效。

<!-- @[setDefaultOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceManagement.ets) -->  

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
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

### 查询本机默认音频输出设备

应用可以通过[getDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#getdefaultoutputdevice20)查询本机默认输出设备类型。
> **说明：**
>
> - 本接口返回通过[setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20)设置的默认输出设备类型，用于确认应用的配置。

<!-- @[getDefaultOutputDevice](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceManagement.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

  try {
    let deviceType = audioSessionManager.getDefaultOutputDevice();
    console.info(`Succeeded in getting default output device. DeviceType: ${deviceType}`);
    // ...
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to get default output device. Code: ${error.code}, message: ${error.message}`);
    // ...
  }
```

### 监听输出设备变化

应用可以通过[on('currentOutputDeviceChanged')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#oncurrentoutputdevicechanged20)监听当前输出设备变化，回调参数类型为[CurrentOutputDeviceChangedEvent](../../reference/apis-audio-kit/arkts-apis-audio-i.md#currentoutputdevicechangedevent20)。

> **说明：**
> 
> - 回调参数中的`devices`为变更后的输出设备信息，`changeReason`为设备变更原因，`recommendedAction`为设备变更后推荐的操作，取值请参考[OutputDeviceChangeRecommendedAction](../../reference/apis-audio-kit/arkts-apis-audio-e.md#outputdevicechangerecommendedaction20)。
>
> - 此事件用于感知当前输出设备变化，与`deviceChange`提供的设备连接状态变化含义不同。除外设连接或断开外，用户强制选择设备、音频会话激活或更高优先级音频流出现等情况也可能引起回调。
> - 不再需要监听时，应调用[off('currentOutputDeviceChanged')](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#offcurrentoutputdevicechanged20)取消订阅。

<!-- @[onCurrentOutputDeviceChanged](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample/entry/src/main/ets/pages/AudioOutputDeviceManagement.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

let currentOutputDeviceChangedCallback = (currentOutputDeviceChangedEvent: audio.CurrentOutputDeviceChangedEvent) => {
  console.info(`Succeeded in using on or off function. CurrentOutputDeviceChangedEvent: ${JSON.stringify(currentOutputDeviceChangedEvent)}`);
  // ...

  switch (currentOutputDeviceChangedEvent.changeReason) {
    case audio.AudioStreamDeviceChangeReason.REASON_OLD_DEVICE_UNAVAILABLE:
      // 响应设备不可用事件，如果应用处于播放状态，应暂停播放，更新UX界面。
      break;
    case audio.AudioStreamDeviceChangeReason.REASON_NEW_DEVICE_AVAILABLE:
      // 应用根据业务情况响应设备可用事件。
      break;
    case audio.AudioStreamDeviceChangeReason.REASON_OVERRODE:
      // 应用根据业务情况响应设备强选事件。
      break;
    case audio.AudioStreamDeviceChangeReason.REASON_SESSION_ACTIVATED:
      // 应用根据业务情况响应audioSession激活时的输出设备信息。
      break;
    case audio.AudioStreamDeviceChangeReason.REASON_STREAM_PRIORITY_CHANGED:
      // 应用根据业务情况响应其它更高优先级的音频流触发的设备变更事件。
      break;
    case audio.AudioStreamDeviceChangeReason.REASON_UNKNOWN:
      // 应用根据业务情况响应未知原因事件。
      break;
  }
};
// ...

  try {
    audioSessionManager.on('currentOutputDeviceChanged', currentOutputDeviceChangedCallback);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to use on function. Code: ${error.code}, message: ${error.message}`);
    // ...
  }
```

<!--Del-->
### 获取活跃输出设备信息（仅对系统应用开放）

从API版本26.0.0开始，使用[getActiveOutputDeviceDescriptors](../../reference/apis-audio-kit/js-apis-audio-sys.md#getactiveoutputdevicedescriptors)方法，可以获取当前音频设备场景下的活跃输出设备描述符。

> **说明：**
>
> - 本接口属于AudioRoutingManager，仅对系统应用开放，且仅可在Stage模型下使用。调用前应先[创建AudioRoutingManager实例](#创建audioroutingmanager实例)。
> 
> - 活跃输出设备是系统在当前音频设备场景下选择的输出设备。本接口返回活跃设备描述符列表；`getDevices(OUTPUT_DEVICES_FLAG)`返回输出设备列表，两者用途不同，不应将所有已连接设备都视为活跃设备。

```typescript
import { audio } from '@kit.AudioKit';  // 导入audio模块。
import { BusinessError } from '@kit.BasicServicesKit';

async function getActiveOutputDeviceDescriptors() {
  audioRoutingManager.getActiveOutputDeviceDescriptors().then((audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
    console.info(`Succeeded in getting active output device descriptors, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
    for (let i = 0; i < audioDeviceDescriptors.length; i++) {
      console.info(`Active Device ${i} - id: ${audioDeviceDescriptors[i].id}`);
      console.info(`Active Device ${i} - name: ${audioDeviceDescriptors[i].name}`);
      console.info(`Active Device ${i} - type: ${audioDeviceDescriptors[i].deviceType}`);
      console.info(`Active Device ${i} - role: ${audioDeviceDescriptors[i].deviceRole}`);
      console.info(`Active Device ${i} - address: ${audioDeviceDescriptors[i].address}`);
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get active output device descriptors. Code: ${err.code}, message: ${err.message}`);
  });
}
```
<!--DelEnd-->

## 相关主题推荐

- [实现音频输出设备路由切换](audio-output-device-switcher.md)
- [查询和监听音频输入设备](audio-input-device-management.md)
- [响应输出设备变更时合理暂停](audio-output-device-change.md)