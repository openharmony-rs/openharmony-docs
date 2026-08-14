# AudioSpatializationManager

空间音频管理。 在使用AudioSpatializationManager的接口之前，需先通过 [getSpatializationManager](arkts-audio-audio-audiomanager-i.md#getSpatializationManager)获取AudioSpatializationManager实例。 > **说明：** > > - 本Interface首批接口从API version 18开始支持。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-audio-interface AudioSpatializationManager--><!--Device-audio-interface AudioSpatializationManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

## downloadPersonalizedHRTF

```TypeScript
downloadPersonalizedHRTF(hrtfDescriptor: AudioHRTFAnonymousDescriptor): Promise<void>
```

从匿名文件描述符下载个性化HRTF数据。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSpatializationManager-downloadPersonalizedHRTF(hrtfDescriptor: AudioHRTFAnonymousDescriptor): Promise<void>--><!--Device-AudioSpatializationManager-downloadPersonalizedHRTF(hrtfDescriptor: AudioHRTFAnonymousDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hrtfDescriptor | [AudioHRTFAnonymousDescriptor](arkts-audio-audio-audiohrtfanonymousdescriptor-i-sys.md) | 是 | 要下载的个性化HRTF数据描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 201 - 权限被拒绝。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability is not supported in this device. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, hrtfDescriptor is invalid. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System internal error, fail to save HRTF on disk, like service died. |
| [6800105](../errorcode-audio.md#6800105-处理超时) | Time out when saving HRTF on disk. |

## getCurrentSpatialAudioSourceType

```TypeScript
getCurrentSpatialAudioSourceType(): SpatialAudioSourceType
```

查询当前空间音频源类型。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSpatializationManager-getCurrentSpatialAudioSourceType(): SpatialAudioSourceType--><!--Device-AudioSpatializationManager-getCurrentSpatialAudioSourceType(): SpatialAudioSourceType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md) | The spatial audio source type on the current device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let sourceType: audio.SpatialAudioSourceType = audioSpatializationManager.getCurrentSpatialAudioSourceType();
  console.info(`current spatial audio source type: ${sourceType}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error.code}, message: ${error.message}`);
}
```

## getSpatializationSceneType

```TypeScript
getSpatializationSceneType(): AudioSpatializationSceneType
```

Get spatialization rendering scene type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-getSpatializationSceneType(): AudioSpatializationSceneType--><!--Device-AudioSpatializationManager-getSpatializationSceneType(): AudioSpatializationSceneType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioSpatializationSceneType](arkts-audio-audio-audiospatializationscenetype-e-sys.md) | Current spatialization rendering scene type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let spatializationSceneType: audio.AudioSpatializationSceneType = audioSpatializationManager.getSpatializationSceneType();
  console.info(`AudioSpatializationManager spatializationSceneType: ${spatializationSceneType}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isAdaptiveSpatialRenderingEnabled

```TypeScript
isAdaptiveSpatialRenderingEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether the adaptive spatial rendering is enabled by the specified device.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-isAdaptiveSpatialRenderingEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean--><!--Device-AudioSpatializationManager-isAdaptiveSpatialRenderingEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | The target device to be check whether the adaptive spatial rendering is enabled. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether the adaptive spatial rendering is enabled by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 设备描述符，用于指定要查询的设备。实际使用时应通过音频框架接口获取真实设备信息，address等字段应使用真实值。
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

try {
  // 查询指定设备的自适应空间音频渲染效果开关状态。
  let isEnabled: boolean = audioSpatializationManager.isAdaptiveSpatialRenderingEnabled(deviceDescriptor);
  console.info(`isAdaptiveSpatialRenderingEnabled: ${isEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error.code}, message: ${error.message}`);
}
```

## isHeadTrackingEnabled

```TypeScript
isHeadTrackingEnabled(): boolean
```

Checks whether the head tracking is enabled.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** [isHeadTrackingEnabled](#isHeadTrackingEnabled)

<!--Device-AudioSpatializationManager-isHeadTrackingEnabled(): boolean--><!--Device-AudioSpatializationManager-isHeadTrackingEnabled(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether the head tracking is enabled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isHeadTrackingEnabled: boolean = audioSpatializationManager.isHeadTrackingEnabled();
  console.info(`AudioSpatializationManager isHeadTrackingEnabled: ${isHeadTrackingEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isHeadTrackingEnabled

```TypeScript
isHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether the head tracking is enabled by the specified device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-isHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean--><!--Device-AudioSpatializationManager-isHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | Audio device description. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether the head tracking is enabled by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

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

try {
  let isHeadTrackingEnabled: boolean = audioSpatializationManager.isHeadTrackingEnabled(deviceDescriptor);
  console.info(`AudioSpatializationManager isHeadTrackingEnabled: ${isHeadTrackingEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isHeadTrackingSupported

```TypeScript
isHeadTrackingSupported(): boolean
```

Checks whether head tracking is supported by system.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-isHeadTrackingSupported(): boolean--><!--Device-AudioSpatializationManager-isHeadTrackingSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether head tracking is supported by system. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isHeadTrackingSupported: boolean = audioSpatializationManager.isHeadTrackingSupported();
  console.info(`AudioSpatializationManager isHeadTrackingSupported: ${isHeadTrackingSupported}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isHeadTrackingSupportedForDevice

```TypeScript
isHeadTrackingSupportedForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether head tracking is supported by the specified device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-isHeadTrackingSupportedForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean--><!--Device-AudioSpatializationManager-isHeadTrackingSupportedForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | Audio device description. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether head tracking is supported by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

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

try {
  let isHeadTrackingSupportedForDevice: boolean = audioSpatializationManager.isHeadTrackingSupportedForDevice(deviceDescriptor);
  console.info(`AudioSpatializationManager isHeadTrackingSupportedForDevice: ${isHeadTrackingSupportedForDevice}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isPersonalizedSpatializationEnabled

```TypeScript
isPersonalizedSpatializationEnabled(selectedAudioDevice: AudioDeviceDescriptor): boolean
```

检查指定设备是否启用了个性化空间。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSpatializationManager-isPersonalizedSpatializationEnabled(selectedAudioDevice: AudioDeviceDescriptor): boolean--><!--Device-AudioSpatializationManager-isPersonalizedSpatializationEnabled(selectedAudioDevice: AudioDeviceDescriptor): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedAudioDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 音频设备描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the personalized spatialization is successfully enabled, otherwise returns false. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## isPersonalizedSpatializationSupported

```TypeScript
isPersonalizedSpatializationSupported(): boolean
```

检查系统是否支持个性化空间化。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSpatializationManager-isPersonalizedSpatializationSupported(): boolean--><!--Device-AudioSpatializationManager-isPersonalizedSpatializationSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether personalized spatialization is supported by system. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## isSpatializationEnabled

```TypeScript
isSpatializationEnabled(): boolean
```

Checks whether the spatialization is enabled.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** [isSpatializationEnabled](#isSpatializationEnabled)

<!--Device-AudioSpatializationManager-isSpatializationEnabled(): boolean--><!--Device-AudioSpatializationManager-isSpatializationEnabled(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether the spatialization is enabled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isSpatializationEnabled: boolean = audioSpatializationManager.isSpatializationEnabled();
  console.info(`AudioSpatializationManager isSpatializationEnabled: ${isSpatializationEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isSpatializationEnabled

```TypeScript
isSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether the spatialization is enabled by the specified device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-isSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean--><!--Device-AudioSpatializationManager-isSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | Audio device description. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether the spatialization is enabled by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

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

try {
  let isSpatializationEnabled: boolean = audioSpatializationManager.isSpatializationEnabled(deviceDescriptor);
  console.info(`AudioSpatializationManager isSpatializationEnabled: ${isSpatializationEnabled}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isSpatializationSupported

```TypeScript
isSpatializationSupported(): boolean
```

Checks whether spatialization is supported by system.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-isSpatializationSupported(): boolean--><!--Device-AudioSpatializationManager-isSpatializationSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether spatialization is supported by system. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let isSpatializationSupported: boolean = audioSpatializationManager.isSpatializationSupported();
  console.info(`AudioSpatializationManager isSpatializationSupported: ${isSpatializationSupported}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isSpatializationSupportedForDevice

```TypeScript
isSpatializationSupportedForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean
```

Checks whether spatialization is supported by the specified device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-isSpatializationSupportedForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean--><!--Device-AudioSpatializationManager-isSpatializationSupportedForDevice(deviceDescriptor: AudioDeviceDescriptor): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | Audio device description. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether spatialization is supported by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

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

try {
  let isSpatializationSupportedForDevice: boolean = audioSpatializationManager.isSpatializationSupportedForDevice(deviceDescriptor);
  console.info(`AudioSpatializationManager isSpatializationSupportedForDevice: ${isSpatializationSupportedForDevice}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## offAdaptiveSpatialRenderingEnabledChangeForAnyDevice

```TypeScript
offAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

Unsubscribes to the adaptive spatial rendering enable state change events.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-offAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-offAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 否 | Callback used to get the adaptive spatial rendering enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

// 取消该事件的所有监听。
audioSpatializationManager.offAdaptiveSpatialRenderingEnabledChangeForAnyDevice();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let adaptiveSpatialRenderingEnabledChangeForAnyDeviceCallback = (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${JSON.stringify(audioSpatialEnabledStateForDevice.deviceDescriptor)}`);
  console.info(`isAdaptiveSpatialRenderingEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
};

audioSpatializationManager.onAdaptiveSpatialRenderingEnabledChangeForAnyDevice(adaptiveSpatialRenderingEnabledChangeForAnyDeviceCallback);

audioSpatializationManager.offAdaptiveSpatialRenderingEnabledChangeForAnyDevice(adaptiveSpatialRenderingEnabledChangeForAnyDeviceCallback);
```

## offHeadTrackingEnabledChangeForAnyDevice

```TypeScript
offHeadTrackingEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

Unsubscribes to the head tracking enable state change events by the specified device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-offHeadTrackingEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-offHeadTrackingEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 否 | Callback used to get the head tracking enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

// 取消该事件的所有监听。
audioSpatializationManager.offHeadTrackingEnabledChangeForAnyDevice();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let headTrackingEnabledChangeForAnyDeviceCallback = (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
console.info(`isHeadTrackingEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
};

audioSpatializationManager.onHeadTrackingEnabledChangeForAnyDevice(headTrackingEnabledChangeForAnyDeviceCallback);

audioSpatializationManager.offHeadTrackingEnabledChangeForAnyDevice(headTrackingEnabledChangeForAnyDeviceCallback);
```

## offPersonalizedSpatializationEnabledChangeForAnyDevice

```TypeScript
offPersonalizedSpatializationEnabledChangeForAnyDevice(
      callback?: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void
```

取消订阅指定设备的个性化空间启用状态更改事件。 当状态发生变化时，已注册的客户端将收到回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSpatializationManager-offPersonalizedSpatializationEnabledChangeForAnyDevice(      callback?: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void--><!--Device-AudioSpatializationManager-offPersonalizedSpatializationEnabledChangeForAnyDevice(      callback?: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioPersonalizedSpatialEnabledChangeForAnyDevice](arkts-audio-audio-audiopersonalizedspatialenabledchangeforanydevice-i-sys.md)&gt; | 否 | 回调用于通过所述指定设备获取所述个性化空间化使能状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## offSpatialAudioSourceTypeChange

```TypeScript
offSpatialAudioSourceTypeChange(callback?: Callback<SpatialAudioSourceType>): void
```

取消订阅空间音频源类型变更事件。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSpatializationManager-offSpatialAudioSourceTypeChange(callback?: Callback<SpatialAudioSourceType>): void--><!--Device-AudioSpatializationManager-offSpatialAudioSourceTypeChange(callback?: Callback<SpatialAudioSourceType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md)&gt; | 否 | 回调用于 接收当前空间音频源类型变化 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

// 取消该事件的所有监听。
audioSpatializationManager.offSpatialAudioSourceTypeChange();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let spatialAudioSourceTypeChangeCallback = (spatialAudioSourceType: audio.SpatialAudioSourceType) => {
  console.info(`spatial audio source type changed to: ${spatialAudioSourceType}`);
};
audioSpatializationManager.onSpatialAudioSourceTypeChange(spatialAudioSourceTypeChangeCallback);
audioSpatializationManager.offSpatialAudioSourceTypeChange(spatialAudioSourceTypeChangeCallback);
```

## offSpatializationEnabledChangeForAnyDevice

```TypeScript
offSpatializationEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

Unsubscribes to the spatialization enable state change events by the specified device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-offSpatializationEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-offSpatializationEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 否 | Callback used to get the spatialization enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
audioSpatializationManager.offSpatializationEnabledChangeForAnyDevice();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let spatializationEnabledChangeForAnyDeviceCallback = (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
  console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
};

audioSpatializationManager.onSpatializationEnabledChangeForAnyDevice(spatializationEnabledChangeForAnyDeviceCallback);

audioSpatializationManager.offSpatializationEnabledChangeForAnyDevice(spatializationEnabledChangeForAnyDeviceCallback);
```

## off_headTrackingEnabledChange

```TypeScript
off(type: 'headTrackingEnabledChange', callback?: Callback<boolean>): void
```

Unsubscribes to the head tracking enable state change events.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** off

<!--Device-AudioSpatializationManager-off(type: 'headTrackingEnabledChange', callback?: Callback<boolean>): void--><!--Device-AudioSpatializationManager-off(type: 'headTrackingEnabledChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChange' | 是 | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | Callback used to get the head tracking enable state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

// 取消该事件的所有监听。
audioSpatializationManager.off('headTrackingEnabledChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let headTrackingEnabledChangeCallback = (isHeadTrackingEnabled: boolean) => {
  console.info(`isHeadTrackingEnabled: ${isHeadTrackingEnabled}`);
};

audioSpatializationManager.on('headTrackingEnabledChange', headTrackingEnabledChangeCallback);

audioSpatializationManager.off('headTrackingEnabledChange', headTrackingEnabledChangeCallback);
```

## off_headTrackingEnabledChangeForAnyDevice

```TypeScript
off(type: 'headTrackingEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

Unsubscribes to the head tracking enable state change events by the specified device.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-off(type: 'headTrackingEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-off(type: 'headTrackingEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChangeForAnyDevice' | 是 | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 否 | Callback used to get the head tracking enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

// 取消该事件的所有监听。
audioSpatializationManager.off('headTrackingEnabledChangeForAnyDevice');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let headTrackingEnabledChangeForAnyDeviceCallback = (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
  console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
};

audioSpatializationManager.on('headTrackingEnabledChangeForAnyDevice', headTrackingEnabledChangeForAnyDeviceCallback);

audioSpatializationManager.off('headTrackingEnabledChangeForAnyDevice', headTrackingEnabledChangeForAnyDeviceCallback);
```

## off_spatializationEnabledChange

```TypeScript
off(type: 'spatializationEnabledChange', callback?: Callback<boolean>): void
```

Unsubscribes to the spatialization enable state change events.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** off

<!--Device-AudioSpatializationManager-off(type: 'spatializationEnabledChange', callback?: Callback<boolean>): void--><!--Device-AudioSpatializationManager-off(type: 'spatializationEnabledChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChange' | 是 | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | Callback used to get the spatialization enable state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
audioSpatializationManager.off('spatializationEnabledChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let spatializationEnabledChangeCallback = (isSpatializationEnabled: boolean) => {
  console.info(`isSpatializationEnabled: ${isSpatializationEnabled}`);
};

audioSpatializationManager.on('spatializationEnabledChange', spatializationEnabledChangeCallback);

audioSpatializationManager.off('spatializationEnabledChange', spatializationEnabledChangeCallback);
```

## off_spatializationEnabledChangeForAnyDevice

```TypeScript
off(type: 'spatializationEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

Unsubscribes to the spatialization enable state change events by the specified device.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-off(type: 'spatializationEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-off(type: 'spatializationEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChangeForAnyDevice' | 是 | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 否 | Callback used to get the spatialization enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

// 取消该事件的所有监听。
audioSpatializationManager.off('spatializationEnabledChangeForAnyDevice');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let spatializationEnabledChangeForAnyDeviceCallback = (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
  console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
};

audioSpatializationManager.on('spatializationEnabledChangeForAnyDevice', spatializationEnabledChangeForAnyDeviceCallback);

audioSpatializationManager.off('spatializationEnabledChangeForAnyDevice', spatializationEnabledChangeForAnyDeviceCallback);
```

## onAdaptiveSpatialRenderingEnabledChangeForAnyDevice

```TypeScript
onAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

Subscribes to the adaptive spatial rendering enable state change events. When the adaptive spatial rendering enable state changes, registered clients will receive the callback.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-onAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-onAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 是 | Callback used to get the adaptive spatial rendering enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.onAdaptiveSpatialRenderingEnabledChangeForAnyDevice((audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${JSON.stringify(audioSpatialEnabledStateForDevice.deviceDescriptor)}`);
  console.info(`isAdaptiveSpatialRenderingEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
});
```

## onHeadTrackingEnabledChangeForAnyDevice

```TypeScript
onHeadTrackingEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

Subscribes to the head tracking enable state change events by the specified device. When the head tracking enable state changes, registered clients will receive the callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-onHeadTrackingEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-onHeadTrackingEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 是 | Callback used to get the head tracking enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
audioSpatializationManager.onHeadTrackingEnabledChangeForAnyDevice((audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
  console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
});
```

## onPersonalizedSpatializationEnabledChangeForAnyDevice

```TypeScript
onPersonalizedSpatializationEnabledChangeForAnyDevice(
      callback: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void
```

指定设备订阅个性化空间化使能状态变更事件。 当状态发生变化时，已注册的客户端将收到回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSpatializationManager-onPersonalizedSpatializationEnabledChangeForAnyDevice(      callback: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void--><!--Device-AudioSpatializationManager-onPersonalizedSpatializationEnabledChangeForAnyDevice(      callback: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioPersonalizedSpatialEnabledChangeForAnyDevice](arkts-audio-audio-audiopersonalizedspatialenabledchangeforanydevice-i-sys.md)&gt; | 是 | 回调用于 通过所述指定设备获取所述个性化空间化使能状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## onSpatialAudioSourceTypeChange

```TypeScript
onSpatialAudioSourceTypeChange(callback: Callback<SpatialAudioSourceType>): void
```

订阅空间音源类型变化事件。当当前空间音源类型发生变化时， 注册的客户端将收到回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSpatializationManager-onSpatialAudioSourceTypeChange(callback: Callback<SpatialAudioSourceType>): void--><!--Device-AudioSpatializationManager-onSpatialAudioSourceTypeChange(callback: Callback<SpatialAudioSourceType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md)&gt; | 是 | 回调用于 接收所述当前空间音源类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.onSpatialAudioSourceTypeChange((spatialAudioSourceType: audio.SpatialAudioSourceType) => {
  console.info(`spatial audio source type changed to: ${spatialAudioSourceType}`);
});
```

## onSpatializationEnabledChangeForAnyDevice

```TypeScript
onSpatializationEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

Subscribes to the spatialization enable state change events by the specified device. When the spatialization enable state changes, registered clients will receive the callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-onSpatializationEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-onSpatializationEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 是 | Callback used to get the spatialization enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.onSpatializationEnabledChangeForAnyDevice((audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
  console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
});
```

## on_headTrackingEnabledChange

```TypeScript
on(type: 'headTrackingEnabledChange', callback: Callback<boolean>): void
```

Subscribes to the head tracking enable state change events. When the head tracking enable state changes, registered clients will receive the callback.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** on

<!--Device-AudioSpatializationManager-on(type: 'headTrackingEnabledChange', callback: Callback<boolean>): void--><!--Device-AudioSpatializationManager-on(type: 'headTrackingEnabledChange', callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChange' | 是 | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | Callback used to get the head tracking enable state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.on('headTrackingEnabledChange', (isHeadTrackingEnabled: boolean) => {
  console.info(`isHeadTrackingEnabled: ${isHeadTrackingEnabled}`);
});
```

## on_headTrackingEnabledChangeForAnyDevice

```TypeScript
on(type: 'headTrackingEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

Subscribes to the head tracking enable state change events by the specified device. When the head tracking enable state changes, registered clients will receive the callback.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-on(type: 'headTrackingEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-on(type: 'headTrackingEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChangeForAnyDevice' | 是 | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 是 | Callback used to get the head tracking enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.on('headTrackingEnabledChangeForAnyDevice', (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
  console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
});
```

## on_spatializationEnabledChange

```TypeScript
on(type: 'spatializationEnabledChange', callback: Callback<boolean>): void
```

Subscribes to the spatialization enable state change events. When the spatialization enable state changes, registered clients will receive the callback.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** on

<!--Device-AudioSpatializationManager-on(type: 'spatializationEnabledChange', callback: Callback<boolean>): void--><!--Device-AudioSpatializationManager-on(type: 'spatializationEnabledChange', callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChange' | 是 | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | Callback used to get the spatialization enable state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.on('spatializationEnabledChange', (isSpatializationEnabled: boolean) => {
  console.info(`isSpatializationEnabled: ${isSpatializationEnabled}`);
});
```

## on_spatializationEnabledChangeForAnyDevice

```TypeScript
on(type: 'spatializationEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

Subscribes to the spatialization enable state change events by the specified device. When the spatialization enable state changes, registered clients will receive the callback.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-AudioSpatializationManager-on(type: 'spatializationEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void--><!--Device-AudioSpatializationManager-on(type: 'spatializationEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChangeForAnyDevice' | 是 | Type of the event to listen for. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 是 | Callback used to get the spatialization enable state by the specified device. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.on('spatializationEnabledChangeForAnyDevice', (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
  console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
});
```

## setAdaptiveSpatialRenderingEnabled

```TypeScript
setAdaptiveSpatialRenderingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>
```

Sets the adaptive spatial rendering enabled or disabled by the specified device. This method uses a promise to return the result. When the adaptive spatial rendering is enabled, spatial audio rendering will not take effect on stereo audio.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

<!--Device-AudioSpatializationManager-setAdaptiveSpatialRenderingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>--><!--Device-AudioSpatializationManager-setAdaptiveSpatialRenderingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | The target device to be set adaptive spatial rendering enabled. |
| enabled | boolean | 是 | Adaptive spatial rendering enable state. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported on the device. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 设备描述符，用于指定要设置的设备。实际使用时应通过音频框架接口获取真实设备信息，address等字段应使用真实值。
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

// 开启自适应空间音频渲染
audioSpatializationManager.setAdaptiveSpatialRenderingEnabled(deviceDescriptor, true).then(() => {
  console.info('Succeeded in setting adaptive spatial rendering enabled');
}).catch((err: BusinessError) => {
  console.error(`setAdaptiveSpatialRenderingEnabled failed: ${err.code}, message: ${err.message}`);
});
```

## setHeadTrackingEnabled

```TypeScript
setHeadTrackingEnabled(enable: boolean, callback: AsyncCallback<void>): void
```

Sets the head tracking enabled or disabled. This method uses an asynchronous callback to return the result.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** [setHeadTrackingEnabled](#setHeadTrackingEnabled)

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

<!--Device-AudioSpatializationManager-setHeadTrackingEnabled(enable: boolean, callback: AsyncCallback<void>): void--><!--Device-AudioSpatializationManager-setHeadTrackingEnabled(enable: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Head tracking enable state. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let enable: boolean = true;

audioSpatializationManager.setHeadTrackingEnabled(enable, (err: BusinessError) => {
  if (err) {
    console.error(`Result ERROR: ${err}`);
  } else {
    console.info(`setHeadTrackingEnabled success`);
  }
});
```

## setHeadTrackingEnabled

```TypeScript
setHeadTrackingEnabled(enable: boolean): Promise<void>
```

Sets the head tracking enabled or disabled. This method uses a promise to return the result.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** [setHeadTrackingEnabled](#setHeadTrackingEnabled)

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

<!--Device-AudioSpatializationManager-setHeadTrackingEnabled(enable: boolean): Promise<void>--><!--Device-AudioSpatializationManager-setHeadTrackingEnabled(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Head tracking enable state. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let enable: boolean = true;

audioSpatializationManager.setHeadTrackingEnabled(enable).then(() => {
  console.info(`setHeadTrackingEnabled success`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

## setHeadTrackingEnabled

```TypeScript
setHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>
```

Sets the head tracking enabled or disabled by the specified device. This method uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

<!--Device-AudioSpatializationManager-setHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>--><!--Device-AudioSpatializationManager-setHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | Audio device description. |
| enabled | boolean | 是 | Head tracking enable state. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

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
let enable: boolean = true;

audioSpatializationManager.setHeadTrackingEnabled(deviceDescriptor, enable).then(() => {
  console.info(`setHeadTrackingEnabled success`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

## setPersonalizedSpatializationEnabled

```TypeScript
setPersonalizedSpatializationEnabled(selectedAudioDevice: AudioDeviceDescriptor,
      enable: boolean): Promise<void>
```

设置由指定设备启用或禁用的个性化空间化。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSpatializationManager-setPersonalizedSpatializationEnabled(selectedAudioDevice: AudioDeviceDescriptor,      enable: boolean): Promise<void>--><!--Device-AudioSpatializationManager-setPersonalizedSpatializationEnabled(selectedAudioDevice: AudioDeviceDescriptor,      enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedAudioDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 音频设备描述。 |
| enable | boolean | 是 | 是否开启个性化空间化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise用于返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability is not supported in this device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## setSpatializationEnabled

```TypeScript
setSpatializationEnabled(enable: boolean, callback: AsyncCallback<void>): void
```

Sets the spatialization enabled or disabled. This method uses an asynchronous callback to return the result.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** [setSpatializationEnabled](#setSpatializationEnabled)

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

<!--Device-AudioSpatializationManager-setSpatializationEnabled(enable: boolean, callback: AsyncCallback<void>): void--><!--Device-AudioSpatializationManager-setSpatializationEnabled(enable: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Spatialization enable state. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let enable: boolean = true;

audioSpatializationManager.setSpatializationEnabled(enable, (err: BusinessError) => {
  if (err) {
    console.error(`Result ERROR: ${err}`);
  } else {
    console.info(`setSpatializationEnabled success`);
  }
});
```

## setSpatializationEnabled

```TypeScript
setSpatializationEnabled(enable: boolean): Promise<void>
```

Sets the spatialization enabled or disabled. This method uses a promise to return the result.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** [setSpatializationEnabled](#setSpatializationEnabled)

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

<!--Device-AudioSpatializationManager-setSpatializationEnabled(enable: boolean): Promise<void>--><!--Device-AudioSpatializationManager-setSpatializationEnabled(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | Spatialization enable state. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let enable: boolean = true;

audioSpatializationManager.setSpatializationEnabled(enable).then(() => {
  console.info(`setSpatializationEnabled success`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

## setSpatializationEnabled

```TypeScript
setSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>
```

Sets the spatialization enabled or disabled by the specified device. This method uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

<!--Device-AudioSpatializationManager-setSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>--><!--Device-AudioSpatializationManager-setSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | Audio device description. |
| enabled | boolean | 是 | Spatialization enable state. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

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

audioSpatializationManager.setSpatializationEnabled(deviceDescriptor, enabled).then(() => {
  console.info(`setSpatializationEnabled success`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

## setSpatializationSceneType

```TypeScript
setSpatializationSceneType(spatializationSceneType: AudioSpatializationSceneType): void
```

Set spatialization rendering scene type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

<!--Device-AudioSpatializationManager-setSpatializationSceneType(spatializationSceneType: AudioSpatializationSceneType): void--><!--Device-AudioSpatializationManager-setSpatializationSceneType(spatializationSceneType: AudioSpatializationSceneType): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spatializationSceneType | [AudioSpatializationSceneType](arkts-audio-audio-audiospatializationscenetype-e-sys.md) | 是 | Spatialization scene type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  audioSpatializationManager.setSpatializationSceneType(audio.AudioSpatializationSceneType.DEFAULT);
  console.info(`AudioSpatializationManager setSpatializationSceneType success`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## updateSpatialDeviceState

```TypeScript
updateSpatialDeviceState(spatialDeviceState: AudioSpatialDeviceState): void
```

Updates the spatial device state.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

<!--Device-AudioSpatializationManager-updateSpatialDeviceState(spatialDeviceState: AudioSpatialDeviceState): void--><!--Device-AudioSpatializationManager-updateSpatialDeviceState(spatialDeviceState: AudioSpatialDeviceState): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spatialDeviceState | [AudioSpatialDeviceState](arkts-audio-audio-audiospatialdevicestate-i-sys.md) | 是 | Spatial device state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let spatialDeviceState: audio.AudioSpatialDeviceState = {
  address: "123",
  isSpatializationSupported: true,
  isHeadTrackingSupported: true,
  spatialDeviceType: audio.AudioSpatialDeviceType.SPATIAL_DEVICE_TYPE_IN_EAR_HEADPHONE
};

try {
  audioSpatializationManager.updateSpatialDeviceState(spatialDeviceState);
  console.info(`AudioSpatializationManager updateSpatialDeviceState success`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

