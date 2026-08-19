# getNetworkAccessPolicy（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## getNetworkAccessPolicy

```TypeScript
function getNetworkAccessPolicy(uid: int): Promise<NetworkAccessPolicy>
```

获取指定 uid 能否访问网络策略，使用 Promise 异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function getNetworkAccessPolicy(uid: int): Promise<NetworkAccessPolicy>--><!--Device-policy-function getNetworkAccessPolicy(uid: int): Promise<NetworkAccessPolicy>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | app 唯一标识符，取值范围为int32_t范围内的正整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[NetworkAccessPolicy](arkts-network-policy-networkaccesspolicy-i-sys.md)&gt; | 以 Promise 形式返回设定结果。 |

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
  .getNetworkAccessPolicy(11111)
  .then((data: policy.NetworkAccessPolicy) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```


## getNetworkAccessPolicy

```TypeScript
function getNetworkAccessPolicy(): Promise<UidNetworkAccessPolicy>
```

获取当前用户下所有应用 app 能否访问网络策略信息，使用 Promise 异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function getNetworkAccessPolicy(): Promise<UidNetworkAccessPolicy>--><!--Device-policy-function getNetworkAccessPolicy(): Promise<UidNetworkAccessPolicy>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[UidNetworkAccessPolicy](arkts-network-policy-uidnetworkaccesspolicy-i.md)&gt; | 以 Promise 形式返回设定结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .getNetworkAccessPolicy()
  .then((data: policy.UidNetworkAccessPolicy) => {
    let keyMap: Map<string, object> = new Map<string, object>(Object.entries(data));
    let uid:number = 0;
    let allowWiFi: string = "";
    let allowCellular: string = "";

    keyMap.forEach((value:object, key:string) => {
      let valueMap: Map<string, string> = new Map<string, string>(Object.entries(value));
      uid = Number.parseInt(key);
      valueMap.forEach((value:string, key:string)=>{
        if (key == "allowWiFi") {
          allowWiFi = value;
        }
        if (key == "allowCellular") {
          allowCellular = value;
        }
      })
    })
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

