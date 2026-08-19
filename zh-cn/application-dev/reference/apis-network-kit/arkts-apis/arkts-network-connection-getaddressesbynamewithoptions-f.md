# getAddressesByNameWithOptions

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getAddressesByNameWithOptions

```TypeScript
function getAddressesByNameWithOptions(host: string, option?: QueryOptions): Promise<Array<NetAddress>>
```

使用当前默认网络基于指定IP类型进行DNS解析。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-connection-function getAddressesByNameWithOptions(host: string, option?: QueryOptions): Promise<Array<NetAddress>>--><!--Device-connection-function getAddressesByNameWithOptions(host: string, option?: QueryOptions): Promise<Array<NetAddress>>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要解析的主机名。例如："www.example.com"。 |
| option | [QueryOptions](arkts-network-connection-queryoptions-i.md) | 否 | 需要查询的IP类型，默认值为FAMILY_TYPE_ALL。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;NetAddress&gt;&gt; | Promise对象，返回查询到的IP地址。返回值中的port字段固定为0，无需关注。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
let option: connection.QueryOptions = {
  family: connection.FamilyType.FAMILY_TYPE_IPV4
};
connection.getAddressesByNameWithOptions("www.example.com", option).then((data: connection.NetAddress[]) => {
  console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get msg. Code:${err.code}, message:${err.message}`)
});
```

