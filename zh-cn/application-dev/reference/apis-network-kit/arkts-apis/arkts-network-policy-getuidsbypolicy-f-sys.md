# getUidsByPolicy（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## getUidsByPolicy

```TypeScript
function getUidsByPolicy(policy: NetUidPolicy, callback: AsyncCallback<Array<int>>): void
```

通过策略获取跟策略匹配的所有 uid，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function getUidsByPolicy(policy: NetUidPolicy, callback: AsyncCallback<Array<int>>): void--><!--Device-policy-function getUidsByPolicy(policy: NetUidPolicy, callback: AsyncCallback<Array<int>>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | [NetUidPolicy](arkts-network-policy-netuidpolicy-e-sys.md) | 是 | 应用对应的计量网络下的策略。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;int&gt;&gt; | 是 | 回调函数。成功返回应用的 uid 数组，失败返回错误码错误信息。 |

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

policy.getUidsByPolicy(11111, (error: BusinessError, data: number[]) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


## getUidsByPolicy

```TypeScript
function getUidsByPolicy(policy: NetUidPolicy): Promise<Array<int>>
```

通过策略获取跟策略匹配的所有 uid，使用 Promise 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function getUidsByPolicy(policy: NetUidPolicy): Promise<Array<int>>--><!--Device-policy-function getUidsByPolicy(policy: NetUidPolicy): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | [NetUidPolicy](arkts-network-policy-netuidpolicy-e-sys.md) | 是 | app 对应的计量网络下的策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;int&gt;&gt; | 以 Promise 形式返回应用的 uid 数组，失败返回错误码错误信息。 |

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
  .getUidsByPolicy(11111)
  .then((data: object) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

