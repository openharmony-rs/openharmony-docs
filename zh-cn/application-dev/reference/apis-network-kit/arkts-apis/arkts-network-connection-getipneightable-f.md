# getIpNeighTable

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getIpNeighTable

```TypeScript
function getIpNeighTable(): Promise<Array<NetIpMacInfo>>
```

获取本地设备IP邻居表条目信息，包括IPv4和IPv6，每个条目信息包括IP地址、MAC地址、网卡名。使用Promise异步回调。 > **说明：** > > 该接口获取IP邻居表的缓存的数据，并非局域网内所有连接的数据。 > > 开发者可使用此接口排查网络异常、解析IP地址与MAC地址映射。

**起始版本：** 22

**需要权限：** ohos.permission.GET_NETWORK_INFO and ohos.permission.GET_IP_MAC_INFO

<!--Device-connection-function getIpNeighTable(): Promise<Array<NetIpMacInfo>>--><!--Device-connection-function getIpNeighTable(): Promise<Array<NetIpMacInfo>>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[NetIpMacInfo](arkts-network-connection-netipmacinfo-i.md)&gt;&gt; | Promise对象，返回ip邻居表条目信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getIpNeighTable().then((data: connection.NetIpMacInfo[]) => {
  if (data.length !== 0) {
    console.info(`Succeeded to get ipAddress: ${JSON.stringify(data.ipAddress)}`);
    console.info(`Succeeded to get iface: ${JSON.stringify(data.iface)}`);
    console.info(`Succeeded to get macAddress: ${JSON.stringify(data.macAddress)}`);
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to get ip neigh table. Code:${error.code}, message:${error.message}`);
});
```

