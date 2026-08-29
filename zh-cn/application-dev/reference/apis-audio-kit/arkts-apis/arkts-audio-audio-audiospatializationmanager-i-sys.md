# AudioSpatializationManager

空间音频管理。在使用AudioSpatializationManager的接口前，需要使用 [getSpatializationManager](arkts-audio-audio-audiomanager-i.md#getspatializationmanager)获取 AudioSpatializationManager实例。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## downloadPersonalizedHRTF

```TypeScript
downloadPersonalizedHRTF(hrtfDescriptor: AudioHRTFAnonymousDescriptor): Promise<void>
```

从匿名文件描述符下载个性化HRTF数据。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hrtfDescriptor | [AudioHRTFAnonymousDescriptor](arkts-audio-audio-audiohrtfanonymousdescriptor-i-sys.md) | 是 | 个性化HRTF数据描述符，用于下载。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise 对象，返回 void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability is not supported in this device. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, hrtfDescriptor is invalid. |
| [6800105](../errorcode-audio.md#6800105-处理超时) | Time out when saving HRTF on disk. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System internal error, fail to save HRTF on disk, like service died. |

## getCurrentSpatialAudioSourceType

```TypeScript
getCurrentSpatialAudioSourceType(): SpatialAudioSourceType
```

获取当前空间音频源类型。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md) | 当前设备的空间音频源类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

**示例**

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

查询当前空间音频渲染场景类型，同步返回结果。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioSpatializationSceneType](arkts-audio-audio-audiospatializationscenetype-e-sys.md) | 返回当前空间音频渲染场景类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

**示例**

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

检查指定设备是否启用了自适应空间渲染。

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 目标设备，用于检查是否启用了自适应空间渲染。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 指定设备是否启用了自适应空间渲染。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

获取头动跟踪是否开启，同步返回结果。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [isHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean](#isheadtrackingenabled)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [isHeadTrackingEnabled](#isheadtrackingenabled)

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回头动跟踪是否开启，true为开启，false为未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

**示例**

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

获取指定设备的头动跟踪是否开启，同步返回结果。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 指定设备的描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定设备的头动跟踪是否开启，true为开启，false为未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

获取系统是否支持头动跟踪，同步返回结果。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回系统是否支持头动跟踪，true为支持，false为不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

**示例**

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

获取指定设备是否支持头动跟踪，同步返回结果。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 指定设备的描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定设备是否支持头动跟踪，true为支持，false为不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

检查指定设备是否启用了个性化空间化功能。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedAudioDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 音频设备描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果个性化空间化成功启用，则返回 true，否则返回 false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## isPersonalizedSpatializationSupported

```TypeScript
isPersonalizedSpatializationSupported(): boolean
```

检查系统是否支持个性化空间化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 系统是否支持个性化空间化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## isSpatializationEnabled

```TypeScript
isSpatializationEnabled(): boolean
```

获取空间音频渲染是否开启，同步返回结果。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [isSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor): boolean](#isspatializationenabled)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [isSpatializationEnabled](#isspatializationenabled)

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回空间音频渲染是否开启，true为开启，false为未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

**示例**

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

获取指定设备的空间音频渲染是否开启，同步返回结果。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 指定设备的描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定设备的空间音频渲染是否开启，true为开启，false为未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

获取系统是否支持空间音频，同步返回结果。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回系统是否支持空间音频，true为支持，false为不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

**示例**

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

获取指定设备是否支持空间音频，同步返回结果。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 指定设备的描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定设备是否支持空间音频，true为支持，false为不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

## off('spatializationEnabledChange')

```TypeScript
off(type: 'spatializationEnabledChange', callback?: Callback<boolean>): void
```

取消监听空间音频渲染开关状态变化事件。使用callback异步回调。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [off('spatializationEnabledChangeForAnyDevice')](#offspatializationenabledchangeforanydevice)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** off

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChange' | 是 | 事件回调类型，支持的事件为'spatializationEnabledChange'，当取消监听空间音频渲染开关状态变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 回调函数。返回true表示音频渲染已打开；返回false表示音频渲染已关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

## off('spatializationEnabledChangeForAnyDevice')

```TypeScript
off(type: 'spatializationEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

取消监听空间音频渲染开关状态变化事件。使用callback异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChangeForAnyDevice' | 是 | 事件回调类型，支持的事件为'spatializationEnabledChangeForAnyDevice'，当取消监听 空间音频渲染开关状态变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 否 | 回调函数，返回设备信息和空间音频渲染开关状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

## off('headTrackingEnabledChange')

```TypeScript
off(type: 'headTrackingEnabledChange', callback?: Callback<boolean>): void
```

取消监听头动跟踪开关状态变化事件。使用callback异步回调。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [off('headTrackingEnabledChangeForAnyDevice')](#offheadtrackingenabledchangeforanydevice)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** off

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChange' | 是 | 事件回调类型，支持的事件为'headTrackingEnabledChange'，当取消监听头动跟踪开关状态变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 回调函数。返回true表示头动跟踪已打开；返回false表示头动跟踪已关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

## off('headTrackingEnabledChangeForAnyDevice')

```TypeScript
off(type: 'headTrackingEnabledChangeForAnyDevice', callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

取消监听头动跟踪开关状态变化事件。使用callback异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChangeForAnyDevice' | 是 | 事件回调类型，支持的事件为'headTrackingEnabledChangeForAnyDevice'，当取消监听头动跟踪 开关状态变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 否 | 回调函数。返回true表示头动跟踪已打开；返回false表示头动跟踪已关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

## offAdaptiveSpatialRenderingEnabledChangeForAnyDevice

```TypeScript
offAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback?: Callback<AudioSpatialEnabledStateForDevice>): void
```

取消订阅指定设备的自适应空间渲染启用状态变更事件。

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 否 | 回调函数，用于通过指定设备获取自适应空间渲染的启用状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

## offPersonalizedSpatializationEnabledChangeForAnyDevice

```TypeScript
offPersonalizedSpatializationEnabledChangeForAnyDevice(
      callback?: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void
```

取消订阅由指定设备触发的个性化空间化状态变更事件。当状态发生变化时，已注册的客户端将收到回调通知。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioPersonalizedSpatialEnabledChangeForAnyDevice](arkts-audio-audio-audiopersonalizedspatialenabledchangeforanydevice-i-sys.md)&gt; | 否 | 回调函数， 用于获取指定设备上已启用的个性化空间化状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## offSpatialAudioSourceTypeChange

```TypeScript
offSpatialAudioSourceTypeChange(callback?: Callback<SpatialAudioSourceType>): void
```

取消订阅空间音频源类型更改事件。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md)&gt; | 否 | 回调函数，用于接收当前空间音频源类型变更。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

## on('spatializationEnabledChange')

```TypeScript
on(type: 'spatializationEnabledChange', callback: Callback<boolean>): void
```

监听空间音频渲染开关状态变化事件（当空间音频渲染开关状态发生变化时触发）。使用callback异步回调。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [on(type: 'spatializationEnabledChangeForAnyDevice', callback: Callback&lt;AudioSpatialEnabledStateForDevice\&gt;): void](#onspatializationenabledchangeforanydevice)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** on

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChange' | 是 | 事件回调类型，支持的事件为'spatializationEnabledChange'，当空间音频渲染开关状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示音频渲染已打开；返回false表示音频渲染已关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.on('spatializationEnabledChange', (isSpatializationEnabled: boolean) => {
  console.info(`isSpatializationEnabled: ${isSpatializationEnabled}`);
});
```

## on('spatializationEnabledChangeForAnyDevice')

```TypeScript
on(type: 'spatializationEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

监听空间音频渲染开关状态变化事件（当空间音频渲染开关状态发生变化时触发）。使用callback异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChangeForAnyDevice' | 是 | 事件回调类型，支持的事件为'spatializationEnabledChangeForAnyDevice'，当空间音频 渲染开关状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 是 | 回调函数，返回设备信息和空间音频渲染开关状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.on('spatializationEnabledChangeForAnyDevice', (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
  console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
});
```

## on('headTrackingEnabledChange')

```TypeScript
on(type: 'headTrackingEnabledChange', callback: Callback<boolean>): void
```

监听头动跟踪开关状态变化事件（当动跟踪开关状态发生变化时触发）。使用callback异步回调。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [on(type: 'headTrackingEnabledChangeForAnyDevice', callback: Callback&lt;AudioSpatialEnabledStateForDevice\&gt;): void](#onheadtrackingenabledchangeforanydevice)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** on

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChange' | 是 | 事件回调类型，支持的事件为'headTrackingEnabledChange'，当动跟踪开关状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示头动跟踪已打开；返回false表示头动跟踪已关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.on('headTrackingEnabledChange', (isHeadTrackingEnabled: boolean) => {
  console.info(`isHeadTrackingEnabled: ${isHeadTrackingEnabled}`);
});
```

## on('headTrackingEnabledChangeForAnyDevice')

```TypeScript
on(type: 'headTrackingEnabledChangeForAnyDevice', callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

监听头动跟踪开关状态变化事件（当动跟踪开关状态发生变化时触发）。使用callback异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headTrackingEnabledChangeForAnyDevice' | 是 | 事件回调类型，支持的事件为'headTrackingEnabledChangeForAnyDevice'，当动跟踪开关状态发 生变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 是 | 回调函数。返回true表示头动跟踪已打开；返回false表示头动跟踪已关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.on('headTrackingEnabledChangeForAnyDevice', (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
  console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
});
```

## onAdaptiveSpatialRenderingEnabledChangeForAnyDevice

```TypeScript
onAdaptiveSpatialRenderingEnabledChangeForAnyDevice(callback: Callback<AudioSpatialEnabledStateForDevice>): void
```

订阅指定设备的自适应空间渲染启用状态变更事件。当自适应空间渲染启用状态发生变化时，已注册的客户端将收到回调。

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md)&gt; | 是 | 回调函数，用于通过指定设备获取自适应空间渲染的启用状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.onAdaptiveSpatialRenderingEnabledChangeForAnyDevice((audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
  console.info(`deviceDescriptor: ${JSON.stringify(audioSpatialEnabledStateForDevice.deviceDescriptor)}`);
  console.info(`isAdaptiveSpatialRenderingEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
});
```

## onPersonalizedSpatializationEnabledChangeForAnyDevice

```TypeScript
onPersonalizedSpatializationEnabledChangeForAnyDevice(
      callback: Callback<AudioPersonalizedSpatialEnabledChangeForAnyDevice>): void
```

订阅由指定设备触发的个性化空间化状态变更事件。当状态发生变化时，已注册的客户端将收到回调通知。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioPersonalizedSpatialEnabledChangeForAnyDevice](arkts-audio-audio-audiopersonalizedspatialenabledchangeforanydevice-i-sys.md)&gt; | 是 | 回调函数， 用于获取指定设备上已启用的个性化空间化状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## onSpatialAudioSourceTypeChange

```TypeScript
onSpatialAudioSourceTypeChange(callback: Callback<SpatialAudioSourceType>): void
```

订阅空间音频源类型更改事件。当当前空间音频源类型发生变化时，注册的客户端将收到回调通知。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md)&gt; | 是 | 回调函数，用于接收当前空间音频源类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioSpatializationManager.onSpatialAudioSourceTypeChange((spatialAudioSourceType: audio.SpatialAudioSourceType) => {
  console.info(`spatial audio source type changed to: ${spatialAudioSourceType}`);
});
```

## setAdaptiveSpatialRenderingEnabled

```TypeScript
setAdaptiveSpatialRenderingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise<void>
```

设置指定设备是否启用自适应空间渲染。 该方法使用 Promise 返回结果。 当启用自适应空间渲染时，空间音频渲染将不会对立体声音频生效。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 目标设备需启用自适应空间渲染功能。 |
| enabled | boolean | 是 | 自适应空间渲染启用状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported on the device. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

根据输入指令，开启/关闭头动跟踪效果。使用callback异步回调。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [setHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise\&lt;void&gt;](#setheadtrackingenabled)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [setHeadTrackingEnabled](#setheadtrackingenabled)

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示开启/关闭头动跟踪。true为开启，false为关闭。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当开启/关闭头动跟踪效果成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

根据输入指令，开启/关闭头动跟踪效果。使用Promise异步回调。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [setHeadTrackingEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise\&lt;void&gt;](#setheadtrackingenabled)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [setHeadTrackingEnabled](#setheadtrackingenabled)

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示开启/关闭头动跟踪。true为开启，false为关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

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

根据输入指令，开启/关闭指定设备的头动跟踪效果。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 设备描述符。 |
| enabled | boolean | 是 | 表示开启/关闭头动跟踪。true为开启，false为关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

设置指定设备是否启用个性化空间化。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedAudioDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 音频设备描述。 |
| enable | boolean | 是 | 是否启用个性化空间化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 承诺用于返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability is not supported in this device. |

## setSpatializationEnabled

```TypeScript
setSpatializationEnabled(enable: boolean, callback: AsyncCallback<void>): void
```

根据输入指令，开启/关闭空间音频渲染效果。使用callback异步回调。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [setSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise\&lt;void&gt;](#setspatializationenabled)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [setSpatializationEnabled](#setspatializationenabled)

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示开启/关闭空间音频渲染。true为开启，false为关闭。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当开启/关闭空间音频渲染效果成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

根据输入指令，开启/关闭空间音频渲染效果。使用Promise异步回调。

> **说明：**
> 
> 从 API version 11 开始支持，从 API version 12 开始废弃，建议使用
> [setSpatializationEnabled(deviceDescriptor: AudioDeviceDescriptor, enabled: boolean): Promise\&lt;void&gt;](#setspatializationenabled)
> 替代。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [setSpatializationEnabled](#setspatializationenabled)

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示开启/关闭空间音频渲染。true为开启，false为关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

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

根据输入指令，开启/关闭指定设备的空间音频渲染效果。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 指定设备的描述。 |
| enabled | boolean | 是 | 表示开启/关闭空间音频渲染。true为开启，false为关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

设置空间音频渲染场景类型，同步返回结果。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spatializationSceneType | [AudioSpatializationSceneType](arkts-audio-audio-audiospatializationscenetype-e-sys.md) | 是 | 需要设置的空间音频渲染场景类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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

更新空间化设备状态，同步返回结果。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spatialDeviceState | [AudioSpatialDeviceState](arkts-audio-audio-audiospatialdevicestate-i-sys.md) | 是 | 需要更新的空间化设备状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

**示例**

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
