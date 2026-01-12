# 移动全景声管理（仅对系统应用开放）
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

从API version 20开始，支持开放移动全景声管理功能给系统级应用。主要包括移动全景声相关状态的查询和设置（例如，移动全景声渲染的开启与关闭），以及移动全景声能力的查询等功能。

对于播放音频类的系统级应用，开发者可以设置和查询指定设备移动全景声的开关状态，以及系统是否支持移动全景声能力。

在使用此功能前，应用需要先申请权限`ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS`，申请方式请参考：[system_basic等级应用申请权限的方式](../../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)。

## 获取移动全景声管理接口

在调用AudioCollaborativeManager的API前，需要先使用[getCollaborativeManager](../../reference/apis-audio-kit/js-apis-audio-sys.md#getcollaborativemanager20)创建一个[AudioCollaborativeManager](../../reference/apis-audio-kit/js-apis-audio-sys.md#audiocollaborativemanager20)实例。

```ts
import { audio } from '@kit.AudioKit';
let audioManager = audio.getAudioManager();
let audioCollaborativeManager = audioManager.getCollaborativeManager();
```

## 查询系统是否支持移动全景声能力

系统应用开发者可以通过[isCollaborativePlaybackSupported](../../reference/apis-audio-kit/js-apis-audio-sys.md#iscollaborativeplaybacksupported20)接口查询当前系统是否具有移动全景声的能力。

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let isCollaborativeSupported: boolean = audioCollaborativeManager.isCollaborativePlaybackSupported();
  console.info(`AudioCollaborativeManager isCollaborativeSupported: ${isCollaborativeSupported}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## 开启或关闭指定设备的移动全景声效果

系统应用开发者可以通过[setCollaborativePlaybackEnabledForDevice](../../reference/apis-audio-kit/js-apis-audio-sys.md#setcollaborativeplaybackenabledfordevice20)接口开启或关闭指定设备的移动全景声效果，该接口需要传递两个参数：AudioDeviceDescriptor和enabled。

- [AudioDeviceDescriptor](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiodevicedescriptor)：用于指定音频设备。建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。

- enabled：布尔值类型，用于控制指定设备的移动全景声开关。入参为true时表示开启移动全景声，入参为false时表示关闭空间移动全景声。

在开启移动全景声时，需要先确保系统和指定设备都具有移动全景声的能力。

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
};
let enabled: boolean = true;
audioCollaborativeManager.setCollaborativePlaybackEnabledForDevice(deviceDescriptor, enabled).then(() => {
  console.info(`setSpatializationEnabled success`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

## 查询指定设备的移动全景声开关状态

系统应用开发者可以通过[isCollaborativePlaybackEnabledForDevice](../../reference/apis-audio-kit/js-apis-audio-sys.md#iscollaborativeplaybackenabledfordevice20)接口查询指定设备的移动全景声开关状态。使用AudioDeviceDescriptor作为入参来指定设备，建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。

该接口返回为true表示开启移动全景声，false表示关闭移动全景声。返回值为[setCollaborativePlaybackEnabledForDevice](../../reference/apis-audio-kit/js-apis-audio-sys.md#setcollaborativeplaybackenabledfordevice20)接口中成功设置的指定设备空间音频渲染开关状态，默认为关闭。该状态仅为开关状态，实际是否生效还需依赖系统和指定设备是否支持移动全景声能力。

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
let deviceDescriptor: audio.AudioDeviceDescriptor = {
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 1,
  name : "",
  address : "123",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : ""
}
try {
  let isCollaborativeEnabled: boolean = audioCollaborativeManager.isCollaborativePlaybackEnabledForDevice(deviceDescriptor);
  console.info(`AudioCollaborativeManager isCollaborativeEnabled: ${isCollaborativeEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```
