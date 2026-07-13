# AudioRecordingManager

提供录像策略管理，包括协同录音
和录制控制能力。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## offSystemRecordControllerEnabledChange

```TypeScript
offSystemRecordControllerEnabledChange(callback?: Callback<SystemRecordControllerChangeInfo>): void
```

取消订阅系统录像控制器面板启用状态更改事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;SystemRecordControllerChangeInfo&gt; | 否 | 订阅中使用的回调取消订阅功能。如果不使用此参数，则当前订阅的所有回调之前的流程将被取消订阅 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |

## onSystemRecordControllerEnabledChange

```TypeScript
onSystemRecordControllerEnabledChange(callback: Callback<SystemRecordControllerChangeInfo>): void
```

订阅系统录像控制器面板使能状态变化事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;SystemRecordControllerChangeInfo&gt; | 是 | 用于监听的回调系统记录控制器面板启用状态更改事件 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800102](../errorcode-audio.md#6800102-分配内存失败) | Memory allocation failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |

