# getNetQuotaPolicies（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## getNetQuotaPolicies

```TypeScript
function getNetQuotaPolicies(callback: AsyncCallback<Array<NetQuotaPolicy>>): void
```

获取计量网络策略，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[NetQuotaPolicy](arkts-network-policy-netquotapolicy-i-sys.md)&gt;&gt; | 是 | 回调函数。返回获取结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

policy.getNetQuotaPolicies((error: BusinessError, data: policy.NetQuotaPolicy[]) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


## getNetQuotaPolicies

```TypeScript
function getNetQuotaPolicies(): Promise<Array<NetQuotaPolicy>>
```

获取计量网络策略，使用 Promise 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[NetQuotaPolicy](arkts-network-policy-netquotapolicy-i-sys.md)&gt;&gt; | 以 Promise 形式返回设定结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .getNetQuotaPolicies()
  .then((data: policy.NetQuotaPolicy[]) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```
