# setNetQuotaPolicies（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## setNetQuotaPolicies

```TypeScript
function setNetQuotaPolicies(quotaPolicies: Array<NetQuotaPolicy>, callback: AsyncCallback<void>): void
```

设置计量网络策略，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function setNetQuotaPolicies(quotaPolicies: Array<NetQuotaPolicy>, callback: AsyncCallback<void>): void--><!--Device-policy-function setNetQuotaPolicies(quotaPolicies: Array<NetQuotaPolicy>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| quotaPolicies | Array&lt;[NetQuotaPolicy](arkts-network-policy-netquotapolicy-i-sys.md)&gt; | 是 | 计量网络策略。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。成功返回空，失败返回错误码错误信息。 |

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
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netQuotaPolicyList: Array<policy.NetQuotaPolicy> = [];
let netQuotaPolicy: policy.NetQuotaPolicy = {
  networkMatchRule: {
    netType: connection.NetBearType.BEARER_CELLULAR,
    identity: '',
    simId: '1'
  },
  quotaPolicy: {
    periodDuration: 'M1',
    warningBytes: 40000,
    limitBytes: 50000,
    metered: true,
    limitAction: policy.LimitAction.LIMIT_ACTION_NONE
  }
}
netQuotaPolicyList.push(netQuotaPolicy);

policy.setNetQuotaPolicies(netQuotaPolicyList, (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```


## setNetQuotaPolicies

```TypeScript
function setNetQuotaPolicies(quotaPolicies: Array<NetQuotaPolicy>): Promise<void>
```

设置计量网络策略，使用 Promise 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function setNetQuotaPolicies(quotaPolicies: Array<NetQuotaPolicy>): Promise<void>--><!--Device-policy-function setNetQuotaPolicies(quotaPolicies: Array<NetQuotaPolicy>): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| quotaPolicies | Array&lt;[NetQuotaPolicy](arkts-network-policy-netquotapolicy-i-sys.md)&gt; | 是 | 计量网络策略。 |

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
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netQuotaPolicyList: Array<policy.NetQuotaPolicy> = [];
let netQuotaPolicy: policy.NetQuotaPolicy = {
  networkMatchRule: {
    netType: connection.NetBearType.BEARER_CELLULAR,
    identity: '',
    simId: '1'
  },
  quotaPolicy: {
    periodDuration: 'M1',
    warningBytes: 40000,
    limitBytes: 50000,
    metered: true,
    limitAction: policy.LimitAction.LIMIT_ACTION_NONE
  }
}
netQuotaPolicyList.push(netQuotaPolicy);

policy
  .setNetQuotaPolicies(netQuotaPolicyList)
  .then(() => {
    console.info('setNetQuotaPolicies success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

