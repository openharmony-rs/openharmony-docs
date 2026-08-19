# setPolicyByUid（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## setPolicyByUid

```TypeScript
function setPolicyByUid(uid: int, policy: NetUidPolicy, callback: AsyncCallback<void>): void
```

设置对应 uid 应用是否能够访问计量网络的策略，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function setPolicyByUid(uid: int, policy: NetUidPolicy, callback: AsyncCallback<void>): void--><!--Device-policy-function setPolicyByUid(uid: int, policy: NetUidPolicy, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | app 唯一标识符，取值范围为int32_t范围内的正整数。 |
| policy | [NetUidPolicy](arkts-network-policy-netuidpolicy-e-sys.md) | 是 | 应用对应的策略。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，成功返回空，失败返回错误码错误信息。 |

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

policy.setPolicyByUid(11111, policy.NetUidPolicy.NET_POLICY_NONE, (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```


## setPolicyByUid

```TypeScript
function setPolicyByUid(uid: int, policy: NetUidPolicy): Promise<void>
```

设置对应 uid 应用是否能够访问计量网络的策略，使用 Promise 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function setPolicyByUid(uid: int, policy: NetUidPolicy): Promise<void>--><!--Device-policy-function setPolicyByUid(uid: int, policy: NetUidPolicy): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | app 唯一标识符，取值范围为int32_t范围内的正整数。 |
| policy | [NetUidPolicy](arkts-network-policy-netuidpolicy-e-sys.md) | 是 | 应用对应的策略。 |

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

policy
  .setPolicyByUid(11111, policy.NetUidPolicy.NET_POLICY_NONE)
  .then(() => {
    console.info('setPolicyByUid success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

