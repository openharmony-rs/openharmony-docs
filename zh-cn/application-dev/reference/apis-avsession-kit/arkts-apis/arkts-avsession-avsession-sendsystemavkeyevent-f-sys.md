# sendSystemAVKeyEvent（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## sendSystemAVKeyEvent

```TypeScript
function sendSystemAVKeyEvent(event: KeyEvent, callback: AsyncCallback<void>): void
```

发送按键事件给置顶会话。结果通过callback异步回调方式返回。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function sendSystemAVKeyEvent(event: KeyEvent, callback: AsyncCallback<void>): void--><!--Device-avSession-function sendSystemAVKeyEvent(event: KeyEvent, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [KeyEvent](../../apis-arkui/arkts-components/arkts-arkui-common-keyevent-i.md) | 是 | 按键事件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当事件发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |

**示例：**

```TypeScript
import { KeyEvent } from '@kit.InputKit';

let keyItem: KeyEvent.Key = {code:0x49, pressedTime:2, deviceId:0};
let event: KeyEvent.KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};

avSession.sendSystemAVKeyEvent(event, () => {
    console.info('Succeeded in sending system AV key event.');
});

```


## sendSystemAVKeyEvent

```TypeScript
function sendSystemAVKeyEvent(event: KeyEvent): Promise<void>
```

发送按键事件给置顶会话。结果通过Promise异步回调方式返回。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function sendSystemAVKeyEvent(event: KeyEvent): Promise<void>--><!--Device-avSession-function sendSystemAVKeyEvent(event: KeyEvent): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [KeyEvent](../../apis-arkui/arkts-components/arkts-arkui-common-keyevent-i.md) | 是 | 按键事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。当事件发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |

**示例：**

```TypeScript
import { KeyEvent } from '@kit.InputKit';

let keyItem: KeyEvent.Key = {code:0x49, pressedTime:2, deviceId:0};
let event: KeyEvent.KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};

avSession.sendSystemAVKeyEvent(event).then(() => {
  console.info('Succeeded in sending system AV key event.');
});

```

