# getSessionDescriptorsForAudioZone（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## getSessionDescriptorsForAudioZone

```TypeScript
function getSessionDescriptorsForAudioZone(userId: number): Promise<Array<Readonly<AVSessionDescriptor>>>
```

获取根据userid查询对应音区的会话

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avSession-function getSessionDescriptorsForAudioZone(userId: int): Promise<Array<Readonly<AVSessionDescriptor>>>--><!--Device-avSession-function getSessionDescriptorsForAudioZone(userId: int): Promise<Array<Readonly<AVSessionDescriptor>>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户userid |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Readonly&lt;AVSessionDescriptor&gt;&gt;&gt; | 返回对应音区的会话列表 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

