# onAudioZoneSessionChange（系统接口）

## onAudioZoneSessionChange

```TypeScript
function onAudioZoneSessionChange(userId: int, callback: Callback<AVSessionDescriptor>): void
```

注册音区会话变化回调

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avSession-function onAudioZoneSessionChange(userId: int, callback: Callback<AVSessionDescriptor>): void--><!--Device-avSession-function onAudioZoneSessionChange(userId: int, callback: Callback<AVSessionDescriptor>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | int | 是 | 当前userId最终归属的音区 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i-sys.md)&gt; | 是 | 返回的会话列表 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

