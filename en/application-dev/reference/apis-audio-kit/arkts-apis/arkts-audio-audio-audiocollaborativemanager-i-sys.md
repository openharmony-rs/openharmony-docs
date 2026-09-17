# AudioCollaborativeManager (System API)

Implements audio collaborative management.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## isCollaborativePlaybackEnabledForDevice

```TypeScript
isCollaborativePlaybackEnabledForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether collaborative playback is enabled for the specified device.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device descriptor. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns the check result. The value true means that collaborative playback is enabled for the specified device, and false means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
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

## isCollaborativePlaybackSupported

```TypeScript
isCollaborativePlaybackSupported(): boolean
```

Checks whether the collaborative playback is supported by system.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the collaborative playback is supported by system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isCollaborativeSupported: boolean = audioCollaborativeManager.isCollaborativePlaybackSupported();
  console.info(`AudioCollaborativeManager isCollaborativeSupported: ${isCollaborativeSupported}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isCollaborativePlaybackSupportedForDevice

```TypeScript
isCollaborativePlaybackSupportedForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether the collaborative playback is supported for the specified device.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device descriptor to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the collaborative playback is supported for the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

## setCollaborativePlaybackEnabledForDevice

```TypeScript
setCollaborativePlaybackEnabledForDevice(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>
```

Enables or disables collaborative playback for the specified device. Currently, only A2DP audio devices support collaborative playback. If the system is using the specified device for audio output, the audio will be played from both the local speaker and the specified device after this API is called.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device descriptor. |
| enabled | boolean | Yes | Whether to enable or disable collaborative playback. The value true means to enable it, and false means to disable it. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Possible causes: 1. The specified device is not an A2DP device. 2. The specified device is not connected. |

**Examples**

```TypeScript
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
