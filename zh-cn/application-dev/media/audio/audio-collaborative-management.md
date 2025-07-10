# 移动全景声管理
移动全景声管理主要包含移动全景声相关状态和能力的查询、设置。

移动全景声管理仅开放给系统级应用，主要包括移动全景声相关状态（移动全景声渲染的开启与关闭）的查询、设置，移动全景声能力的查询。

对于播放音频类的系统级应用，开发者可以设置和查询指定设备移动全景声的开关状态，以及系统是否支持移动全景声能力。

在使用此功能前，应用需要先申请权限`ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS`，申请方式请参考：[申请应用权限](../../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)。

## 获取移动全景声管理接口

创建AudioCollaborativeManager实例。在使用AudioCollaborativeManager的API前，需要使用getCollaborativeManager()创建一个AudioCollaborativeManager实例。

  ```ts
  import { audio } from '@kit.AudioKit';

  let audioManager = audio.getAudioManager();
  let audioCollaborativeManager = audioManager.getCollaborativeManager();
  ```

## 查询系统是否支持移动全景声能力

系统应用开发者可以通过[isCollaborativePlaybackSupported](../../reference/apis-audio-kit/js-apis-audio-sys.md#isspatializationsupported11)接口查询当前系统是否具有移动全景声的能力。

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

## 开启/关闭指定设备的移动全景声效果

系统应用开发者可以通过[setCollaborativePlaybackEnabledForDevice](../../reference/apis-audio-kit/js-apis-audio-sys.md#setspatializationenabled12)接口开启/关闭指定设备的移动全景声效果，该接口需要传递两个参数：AudioDeviceDescriptor和enabled。

AudioDeviceDescriptor：用于指定音频设备。建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。AudioDeviceDescriptor的具体信息可以参考[AudioDeviceDescriptor](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiodevicedescriptor)。
enabled：布尔值类型，用于控制指定设备的移动全景声开关。入参为true时为开启移动全景声，入参为false时为关闭空间移动全景声。

在使用此功能前，应用需要先申请权限`ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS`，申请方式请参考：[申请应用权限](../../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)。

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

系统应用开发者可以通过[isCollaborativePlaybackEnabledForDevice](../../reference/apis-audio-kit/js-apis-audio-sys.md#isspatializationenabled12)接口查询指定设备的空间音频渲染效果开关状态，开发者需要使用AudioDeviceDescriptor作为入参来指定设备，建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。AudioDeviceDescriptor的具体信息可以参考[AudioDeviceDescriptor](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiodevicedescriptor)。该接口返回为true表示移动全景声开启，false表示移动全景声关闭。返回值为setCollaborativePlaybackEnabledForDevice接口中成功设置的指定设备空间音频渲染开关状态，默认为关闭。该状态仅为开关状态，实际是否生效还需依赖系统和指定设备是否支持移动全景声能力。

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
