# createNetConnection

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## createNetConnection

```TypeScript
function createNetConnection(netSpecifier?: NetSpecifier, timeout?: int): NetConnection
```

创建一个NetConnection对象，可用于监听网络状态。[netSpecifier](arkts-network-connection-netspecifier-i.md)表示需要监听网络的网络特征；timeout是超时时间（单位：毫秒)； netSpecifier是timeout的必要条件，两者都没有则表示关注默认网络。 > **说明：** > > 若需要监听网络状态，创建一个NetConnection对象后，还需调用[register](arkts-network-connection-netconnection-i.md#register)注册指定网络状态变化的通知。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-connection-function createNetConnection(netSpecifier?: NetSpecifier, timeout?: int): NetConnection--><!--Device-connection-function createNetConnection(netSpecifier?: NetSpecifier, timeout?: int): NetConnection-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netSpecifier | [NetSpecifier](arkts-network-connection-netspecifier-i.md) | 否 | 需要监听网络的网络特征，缺省则表示监听默认网络。 |
| timeout | int | 否 | 获取netSpecifier指定网络时的超时时间，传入值需为uint32_t范围内的整数，仅netSpecifier存在时生效，默认值为0。 <br>**说明：**当监听网络不存在时，会尝试激活此网络。若超过设置的超时时间，且注册了网络状态监听，则会触发netUnavailable事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NetConnection](arkts-network-connection-netconnection-i.md) | 需要监听的网络连接对象的类型。 |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

// 示例1：仅关注默认网络, 无需指定netSpecifier参数，timeout参数未传入说明未使用超时时间，此时timeout为0。
let netConnection = connection.createNetConnection();

// 示例2：仅关注蜂窝网络，需要指定网络类型为蜂窝网络。
let timeout = 1000;
let netConnectionCellular = connection.createNetConnection({
  netCapabilities: {
    bearerTypes: [connection.NetBearType.BEARER_CELLULAR]
  }
}, timeout);

// 示例3：关注蜂窝或Wi-Fi网络，需要指定网络类型为蜂窝网络和Wi-Fi网络。
let netConnectionCellularAndWifi = connection.createNetConnection({
  netCapabilities: {
    bearerTypes: [connection.NetBearType.BEARER_CELLULAR,
      connection.NetBearType.BEARER_WIFI]
  }
});
```

