# getDefaultNetSync

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getDefaultNetSync

```TypeScript
function getDefaultNetSync(): NetHandle
```

获取系统默认使用的网络句柄，包含网络ID。使用同步方式返回。 > **说明：** > > - 系统默认使用的网络，该网络的capabilities必须具备[NET_CAPABILITY_INTERNET](arkts-network-connection-netcap-e.md)且不是VPN类型的网络。 > > - 该接口的返回由系统决定，与应用是否指定网络无关。 > > - 一般情况下，优先级：以太网（PC）|蓝牙（手表）> WIFI > 蜂窝，特殊情况以实际返回结果为准。 > > - [NetHandle](arkts-network-connection-nethandle-i.md)为网络唯一标识，当无网络可用时，返回0。其可用于 > [getNetCapabilities](arkts-network-connection-getnetcapabilities-f.md)继续查询更多网络信息。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-connection-function getDefaultNetSync(): NetHandle--><!--Device-connection-function getDefaultNetSync(): NetHandle-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NetHandle | 以同步方式返回默认网络的网络句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let netHandle = connection.getDefaultNetSync();
```

