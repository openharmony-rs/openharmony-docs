# sendSystemCommonCommand（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

<a id="sendsystemcommoncommand"></a>
## sendSystemCommonCommand

```TypeScript
function sendSystemCommonCommand(command: string, args: ExtraInfo): Promise<string>
```

发送通用事件命令

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avSession-function sendSystemCommonCommand(command: string, args: ExtraInfo): Promise<string>--><!--Device-avSession-function sendSystemCommonCommand(command: string, args: ExtraInfo): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | 通用的控制命令 |
| args | [ExtraInfo](arkts-avsession-avsession-extrainfo-t.md) | 是 | 事件参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | callback info for sync command |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

