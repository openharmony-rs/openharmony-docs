# Collaborative Audio Management (for System Applications Only)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

Starting from API version 20, collaborative audio management is available to system applications. This includes checking whether the feature is supported, and controlling its state (such as turning it on or off for specific devices).

For audio‑playback system applications, you can set and query the status of collaborative audio for specific devices, as well as check whether the system supports this feature.

To use this feature, the application must request the ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS permission. For details, see [Requesting Permissions for system_basic Applications](../../security/AccessToken/determine-application-mode.md#requesting-permissions-for-system_basic-applications).

## Obtaining an AudioCollaborativeManager Instance

Before calling the APIs of AudioCollaborativeManager, call [getCollaborativeManager](../../reference/apis-audio-kit/js-apis-audio-sys.md#getcollaborativemanager20) to obtain an [AudioCollaborativeManager](../../reference/apis-audio-kit/js-apis-audio-sys.md#audiocollaborativemanager20) instance.

```ts
import { audio } from '@kit.AudioKit';
let audioManager = audio.getAudioManager();
let audioCollaborativeManager = audioManager.getCollaborativeManager();
```

## Checking Whether the System Supports Collaborative Audio

Call [isCollaborativePlaybackSupported](../../reference/apis-audio-kit/js-apis-audio-sys.md#iscollaborativeplaybacksupported20) to check whether the system supports collaborative audio.

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

## Enabling or Disabling Collaborative Audio for a Device

Call [setCollaborativePlaybackEnabledForDevice](../../reference/apis-audio-kit/js-apis-audio-sys.md#setcollaborativeplaybackenabledfordevice20) to enable or disable collaborative audio for a device. This API contains two parameters:

- [AudioDeviceDescriptor](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiodevicedescriptor): specifies an audio device. You are advised to use other audio APIs to obtain **AudioDeviceDescriptor** of a connected device or the current audio device.

- **enabled**: specifies the status of collaborative audio of the specified device. The value **true** means to enable collaborative audio, and **false** means to disable it.

Before enabling collaborative audio, ensure that both the system and the specified device support the capability.

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

## Checking the Status of Collaborative Audio for a Device

Call [isCollaborativePlaybackEnabledForDevice](../../reference/apis-audio-kit/js-apis-audio-sys.md#iscollaborativeplaybackenabledfordevice20) to check whether collaborative audio is enabled for a specific device. Use **AudioDeviceDescriptor** to specify the device. You are advised to use other audio APIs to obtain **AudioDeviceDescriptor** of a connected device or the current audio device.

If the return value is **true**, collaborative audio is enabled. If the return value is **false**, it is disabled. This API returns the value passed in [setCollaborativePlaybackEnabledForDevice](../../reference/apis-audio-kit/js-apis-audio-sys.md#setcollaborativeplaybackenabledfordevice20). The default value is **false**. Note that collaborative audio takes effect only when the system and the specified device support the capability.

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
