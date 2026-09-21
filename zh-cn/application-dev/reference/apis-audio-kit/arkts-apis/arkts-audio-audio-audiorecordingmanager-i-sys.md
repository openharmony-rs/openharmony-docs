# AudioRecordingManager

```TypeScript
interface AudioRecordingManager
```

录音策略管理，提供协同录音和录音控制能力。通过[getRecordingManager](arkts-audio-audio-audiomanager-i.md#getrecordingmanager)获取AudioRecordingManager实例。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## offSystemRecordControllerEnabledChange

```TypeScript
offSystemRecordControllerEnabledChange(callback?: Callback<SystemRecordControllerChangeInfo>): void
```

取消订阅系统录音控制面板使能状态变化事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SystemRecordControllerChangeInfo](arkts-audio-audio-systemrecordcontrollerchangeinfo-i-sys.md)&gt; | 否 | 待取消的系统录音控制面板使能状态变化回调函数。不填写时取消该事件的所有回调。 |

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

订阅系统录音控制面板使能状态变更事件。订阅后，有应用调用[enableSystemRecordController](arkts-audio-audio-audiorecordingmanager-i.md#enablesystemrecordcontroller)时，会触发回调。系统录音控制面板的使能状态可由应用通过[enableSystemRecordController](arkts-audio-audio-audiorecordingmanager-i.md#enablesystemrecordcontroller)接口设定，其他应用程序可以使用本接口订阅状态变更事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SystemRecordControllerChangeInfo](arkts-audio-audio-systemrecordcontrollerchangeinfo-i-sys.md)&gt; | 是 | 回调函数。当系统录音控制面板使能状态变化时，返回变更信息。 |

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
