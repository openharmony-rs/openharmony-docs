# AudioRecordingManager

录音策略管理，提供协同录音和录音控制能力。 在使用AudioRecordingManager的接口之前，需先通过 [getRecordingManager](arkts-audio-audio-audiomanager-i-sys.md#getrecordingmanager)获取AudioRecordingManager实例 。

> **说明：**
> 
> - 本模块首批接口从API版本26.0.0开始支持。
> 
> - 本模块接口仅可在Stage模型下使用。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getCurrentCollaborativeRecordingConfiguration

```TypeScript
getCurrentCollaborativeRecordingConfiguration(): CollaborativeRecordingConfiguration
```

获取当前的协作录制配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CollaborativeRecordingConfiguration](arkts-audio-audio-collaborativerecordingconfiguration-i-sys.md) | 协作录音配置，若开启该功能，返回值中将包含音频设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs, like service died. |

## getSupportedCollaborativeRecordingDevices

```TypeScript
getSupportedCollaborativeRecordingDevices(): AudioDeviceDescriptors
```

获取支持协作录音的音频设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | 支持协同录制的设备。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## isCollaborativeRecordingEnabled

```TypeScript
isCollaborativeRecordingEnabled(): boolean
```

检查该设备是否支持协同录制。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 该设备是否支持协同录制。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## offSystemRecordControllerEnabledChange

```TypeScript
offSystemRecordControllerEnabledChange(callback?: Callback<SystemRecordControllerChangeInfo>): void
```

取消订阅系统录制控制器面板启用状态变更事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SystemRecordControllerChangeInfo](arkts-audio-audio-systemrecordcontrollerchangeinfo-i-sys.md)&gt; | 否 | 订阅中使用的回调函数 用于取消订阅的函数。如果不使用此参数，将取消当前进程中之前订阅的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioRecordingManager.offSystemRecordControllerEnabledChange();
```

## onSystemRecordControllerEnabledChange

```TypeScript
onSystemRecordControllerEnabledChange(callback: Callback<SystemRecordControllerChangeInfo>): void
```

订阅系统录制控制器面板启用状态变更事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SystemRecordControllerChangeInfo](arkts-audio-audio-systemrecordcontrollerchangeinfo-i-sys.md)&gt; | 是 | 回调函数，用于监听系统录音控制器面板使能状态变化事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800102](../errorcode-audio.md#6800102-分配内存失败) | Memory allocation failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

audioRecordingManager.onSystemRecordControllerEnabledChange((changeInfo: audio.SystemRecordControllerChangeInfo) => {
  console.info(`System record controller enabled state changed: ${changeInfo.enabled}, uid: ${changeInfo.uid}, sourceType: ${changeInfo.sourceType}`);
});
```

## setCollaborativeRecordingEnabledForDevices

```TypeScript
setCollaborativeRecordingEnabledForDevices(enable: boolean, devices: AudioDeviceDescriptors): Promise<void>
```

为特定音频设备启用协作录音功能。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 确实可以实现协作录制。 |
| devices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | 是 | 目标音频设备用于协同录制， 应使用 [getSupportedCollaborativeRecordingDevices](#getsupportedcollaborativerecordingdevices) 来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise 对象，返回 void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, the devices are invalid. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs, like service died. |
