# sendNotice（系统接口）

## sendNotice

```TypeScript
function sendNotice(noticeType: NoticeType, eventData: string): void
```

发送来自身份认证组件的通知。在使用统一身份认证控件进行用户身份认证时，该接口用于接收来自统一身份认证组件的通知，并将通知发送给用户认证框架。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SUPPORT_USER_AUTH

<!--Device-userAuth-function sendNotice(noticeType: NoticeType, eventData: string): void--><!--Device-userAuth-function sendNotice(noticeType: NoticeType, eventData: string): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| noticeType | [NoticeType](arkts-userauthentication-userauth-noticetype-e-sys.md) | 是 | 通知类型。用于标识通知的来源，当前支持WIDGET_NOTICE（1），表示来自身份认证组件的通知。 |
| eventData | string | 是 | 事件数据。JSON格式的字符串，包含通知的具体内容，如认证类型就绪事件等。数据长度范围为(0, 65536)字节。JSON对象应包含widgetContextId（ number类型，控件上下文ID）、event（string类型，事件类型）、version（string类型，版本号）、payload（object类型，事件载荷对象）等字段。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. &lt;br&gt;3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Called by non-system application. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

## 示例

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface  EventData {
  widgetContextId: number;
  event: string;
  version: string;
  payload: Payload;
}
interface Payload {
  type: string[];
}
try {
  const eventData : EventData = {
    widgetContextId: 123456,
    event: 'EVENT_AUTH_TYPE_READY',
    version: '1',
    payload: {
      type: ['pin']
    } as Payload,
  };
  const jsonEventData = JSON.stringify(eventData);
  let noticeType = userAuth.NoticeType.WIDGET_NOTICE;
  userAuth.sendNotice(noticeType, jsonEventData);
  console.info('sendNotice successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`sendNotice failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

