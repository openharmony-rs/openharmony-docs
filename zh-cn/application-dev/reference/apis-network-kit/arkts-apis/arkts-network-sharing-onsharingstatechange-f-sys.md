# on_sharingStateChange（系统接口）

## 导入模块

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## on('sharingStateChange')

```TypeScript
function on(type: 'sharingStateChange', callback: Callback<boolean>): void
```

注册网络共享状态变化事件，使用 callback 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

<!--Device-sharing-function on(type: 'sharingStateChange', callback: Callback<boolean>): void--><!--Device-sharing-function on(type: 'sharingStateChange', callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sharingStateChange' | 是 | 订阅的事件类型。'sharingStateChange'：注册网络共享状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | 回调函数，返回网络共享状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';

sharing.on('sharingStateChange', (data: boolean) => {
  console.info('on sharingStateChange: ' + JSON.stringify(data));
});
```

