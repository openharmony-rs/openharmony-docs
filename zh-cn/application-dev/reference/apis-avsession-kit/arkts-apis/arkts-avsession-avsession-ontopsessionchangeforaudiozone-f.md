# onTopSessionChangeForAudioZone

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## onTopSessionChangeForAudioZone

```TypeScript
function onTopSessionChangeForAudioZone(userId: number, callback: Callback<AVSessionDescriptor>): void
```

注册特定音区的top会话更改回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avSession-function onTopSessionChangeForAudioZone(userId: int, callback: Callback<AVSessionDescriptor>): void--><!--Device-avSession-function onTopSessionChangeForAudioZone(userId: int, callback: Callback<AVSessionDescriptor>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 属于音区的用户ID。<br>取值限定为整数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i.md)&gt; | 是 | 用于为（'topSessionChange'）命令注销侦听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | permission denied. |
| [6700101](../errorcode-avsession.md#6700101-会话服务未运行) | Session service is not running. |
