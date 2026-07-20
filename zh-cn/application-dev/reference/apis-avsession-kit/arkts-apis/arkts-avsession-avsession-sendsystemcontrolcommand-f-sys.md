# sendSystemControlCommand（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

<a id="sendsystemcontrolcommand"></a>
## sendSystemControlCommand

```TypeScript
function sendSystemControlCommand(command: AVControlCommand, callback: AsyncCallback<void>): void
```

发送控制命令给置顶会话。结果通过callback异步回调方式返回。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function sendSystemControlCommand(command: AVControlCommand, callback: AsyncCallback<void>): void--><!--Device-avSession-function sendSystemControlCommand(command: AVControlCommand, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | 是 | AVSession的相关命令和命令相关参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

**示例：**

```TypeScript
let cmd : avSession.AVControlCommandType = 'play';
// let cmd : avSession.AVControlCommandType = 'pause';
// let cmd : avSession.AVControlCommandType = 'stop';
// let cmd : avSession.AVControlCommandType = 'playNext';
// let cmd : avSession.AVControlCommandType = 'playPrevious';
// let cmd : avSession.AVControlCommandType = 'fastForward';
// let cmd : avSession.AVControlCommandType = 'rewind';
let avcommand: avSession.AVControlCommand = {command:cmd};
// let cmd: avSession.AVControlCommandType = 'seek';
// let avcommand = {command:cmd, parameter:10};
// let cmd : avSession.AVControlCommandType = 'setSpeed';
// let avcommand = {command:cmd, parameter:2.6};
// let cmd : avSession.AVControlCommandType = 'setLoopMode';
// let avcommand = {command:cmd, parameter:avSession.LoopMode.LOOP_MODE_SINGLE};
// let cmd : avSession.AVControlCommandType = 'toggleFavorite';
// let avcommand = {command:cmd, parameter:"false"};
avSession.sendSystemControlCommand(avcommand, () => {
    console.info('Succeeded in sending system control command.');
});

```


<a id="sendsystemcontrolcommand-1"></a>
## sendSystemControlCommand

```TypeScript
function sendSystemControlCommand(command: AVControlCommand): Promise<void>
```

发送控制命令给置顶会话。结果通过Promise异步回调方式返回。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function sendSystemControlCommand(command: AVControlCommand): Promise<void>--><!--Device-avSession-function sendSystemControlCommand(command: AVControlCommand): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | 是 | AVSession的相关命令和命令相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当命令发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

**示例：**

```TypeScript

let cmd : avSession.AVControlCommandType = 'play';
// let cmd : avSession.AVControlCommandType = 'pause';
// let cmd : avSession.AVControlCommandType = 'stop';
// let cmd : avSession.AVControlCommandType = 'playNext';
// let cmd : avSession.AVControlCommandType = 'playPrevious';
// let cmd : avSession.AVControlCommandType = 'fastForward';
// let cmd : avSession.AVControlCommandType = 'rewind';
let avcommand: avSession.AVControlCommand = {command:cmd};
// let cmd : avSession.AVControlCommandType = 'seek';
// let avcommand = {command:cmd, parameter:10};
// let cmd : avSession.AVControlCommandType = 'setSpeed';
// let avcommand = {command:cmd, parameter:2.6};
// let cmd : avSession.AVControlCommandType = 'setLoopMode';
// let avcommand = {command:cmd, parameter:avSession.LoopMode.LOOP_MODE_SINGLE};
// let cmd : avSession.AVControlCommandType = 'toggleFavorite';
// let avcommand = {command:cmd, parameter:"false"};
avSession.sendSystemControlCommand(avcommand).then(() => {
  console.info('Succeeded in sending system control command.');
});

```

