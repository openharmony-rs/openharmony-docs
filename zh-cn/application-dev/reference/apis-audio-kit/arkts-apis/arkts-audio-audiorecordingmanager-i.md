# AudioRecordingManager

提供录像策略管理，包括协同录音
和录制控制能力。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## enableSystemRecordController

```TypeScript
enableSystemRecordController(show: boolean, config: SystemRecordControllerConfig): Promise<void>
```

启用或禁用系统录像控制器面板。
应用程序在启动录制码流之前，可以调用此接口拉起录制控制器面板。
允许用户完成录音设备或音效参数的选择。
然后可以启动录音服务，避免在
记录过程。
应用程序必须在前台才能启用面板；启用操作不生效
如果应用程序在后台。禁用面板不受应用程序的限制
前台或后台状态。
该接口使用promise返回结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean | 是 | 一个布尔值，指示是显示（true）还是隐藏(false)系统记录控制器面板 |
| config | SystemRecordControllerConfig | 是 | 系统录像控制器面板配置 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |

