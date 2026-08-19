# setNetworkAccessPolicy（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## setNetworkAccessPolicy

```TypeScript
function setNetworkAccessPolicy(uid: int, policy: NetworkAccessPolicy, isReconfirmed?: boolean): Promise<void>
```

设置指定 uid 应用能否能访问网络的策略，使用 Promise 异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function setNetworkAccessPolicy(uid: int, policy: NetworkAccessPolicy, isReconfirmed?: boolean): Promise<void>--><!--Device-policy-function setNetworkAccessPolicy(uid: int, policy: NetworkAccessPolicy, isReconfirmed?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | app 唯一标识符，取值范围为int32_t范围内的正整数。 |
| policy | [NetworkAccessPolicy](arkts-network-policy-networkaccesspolicy-i-sys.md) | 是 | 网络策略。 |
| isReconfirmed | boolean | 否 | 默认false；false 表示需要重确认，应用访问网络会弹框; true 表示不需要重确认，无弹框。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以 Promise 形式返回设定结果。成功返回空，失败返回错误码错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accessPolicy: policy.NetworkAccessPolicy = {
  allowWiFi: false,
  allowCellular: true,
}
policy
  .setNetworkAccessPolicy(11111, accessPolicy)
  .then(() => {
    console.info('setNetworkAccessPolicy success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

