# getConnectOwnerUid

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getConnectOwnerUid

```TypeScript
function getConnectOwnerUid(protocol: ProtocolType, local: NetAddress, remote: NetAddress): Promise<int>
```

用于查询发起指定网络连接的应用UID。使用Promise异步回调。 > **说明：** > > - 该接口仅限在VPN应用中调用。 > > - 调用接口时请设置local和remote参数的端口号。若未设置端口号或将端口号设置为0，接口会基于其他参数筛选出符合条件的UID的集合，并从中返回一个匹配的UID。 > > - protocol参数为PROTO_TYPE_UDP时，若通过local，remote参数未筛选出符合条件的UID，则仅基于local参数筛选并返回匹配的UID。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function getConnectOwnerUid(protocol: ProtocolType, local: NetAddress, remote: NetAddress): Promise<int>--><!--Device-connection-function getConnectOwnerUid(protocol: ProtocolType, local: NetAddress, remote: NetAddress): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| protocol | ProtocolType | 是 | 网络协议的类型。 |
| local | NetAddress | 是 | 源网络地址。 |
| remote | NetAddress | 是 | 目标网络地址。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回应用程序的UID。如果不存在匹配的UID则返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2100301](../errorcode-net-connection.md#2100301-调用方身份验证不通过非vpn应用) | Incorrect usage in non-VPN application. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let protocol = connection.ProtocolType.PROTO_TYPE_TCP;
let local: connection.NetAddress = { address: '192.168.1.100', family: 1, port: 6666 };
let remote: connection.NetAddress = { address: '192.168.1.200', family: 1, port: 8888 };
connection.getConnectOwnerUid(protocol, local, remote).then((uid) => {
  console.info(`Succeeded to get uid: ${uid}`);
}).catch((error: BusinessError) => {
  console.error(`Failed to get ConnectOwnerUid. errorCode: ${error.code} message:${error.message}`);
});
```

