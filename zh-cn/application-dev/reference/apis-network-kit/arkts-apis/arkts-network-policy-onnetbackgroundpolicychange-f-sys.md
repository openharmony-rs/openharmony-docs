# on_netBackgroundPolicyChange（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## on('netBackgroundPolicyChange')

```TypeScript
function on(type: 'netBackgroundPolicyChange', callback: Callback<boolean>): void
```

注册后台网络策略发生改变时的回调，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function on(type: 'netBackgroundPolicyChange', callback: Callback<boolean>): void--><!--Device-policy-function on(type: 'netBackgroundPolicyChange', callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netBackgroundPolicyChange' | 是 | 订阅的事件类型。'netBackgroundPolicyChange'：注册后台网络策略发生改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | 回调函数。注册后台网络策略发生改变时调用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

