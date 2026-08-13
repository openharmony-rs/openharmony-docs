# offDeviceLogEvent（系统接口）

## offDeviceLogEvent

```TypeScript
function offDeviceLogEvent(callback?: Callback<DeviceLogEventCode>): void
```

UnRegister log event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-avSession-function offDeviceLogEvent(callback?: Callback<DeviceLogEventCode>): void--><!--Device-avSession-function offDeviceLogEvent(callback?: Callback<DeviceLogEventCode>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceLogEventCode](arkts-avsession-avsession-devicelogeventcode-e-sys.md)&gt; | 否 | Used to handle ('deviceLogEvent') command |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## 示例

```TypeScript
avSession.offDeviceLogEvent();
```

