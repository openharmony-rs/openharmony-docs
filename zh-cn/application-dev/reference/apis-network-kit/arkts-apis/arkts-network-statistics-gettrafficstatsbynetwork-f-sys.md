# getTrafficStatsByNetwork（系统接口）

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getTrafficStatsByNetwork

```TypeScript
function getTrafficStatsByNetwork(networkInfo: NetworkInfo): Promise<UidNetStatsInfo>
```

获取指定时间段内所有应用在指定网络中的流量使用详情，使用 Promise 异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_STATS

<!--Device-statistics-function getTrafficStatsByNetwork(networkInfo: NetworkInfo): Promise<UidNetStatsInfo>--><!--Device-statistics-function getTrafficStatsByNetwork(networkInfo: NetworkInfo): Promise<UidNetStatsInfo>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkInfo | NetworkInfo | 是 | 指定查询的网络信息，参见[NetworkInfo](arkts-network-statistics-networkinfo-i-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[UidNetStatsInfo](arkts-network-statistics-uidnetstatsinfo-t-sys.md)&gt; | 以 Promise 形式返回获取结果。返回所有应用历史流量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2103017](../errorcode-net-statistics.md#2103017-读取数据库失败) | Failed to read the database. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
import { connection, statistics } from '@kit.NetworkKit';

let networkInfo: statistics.NetworkInfo = {
  type: connection.NetBearType.BEARER_CELLULAR,
  startTime: Math.floor(Date.now() / 1000) - 86400 * 7, 
  endTime: Math.floor(Date.now() / 1000) + 5,
  simId: 1,
}

statistics.getTrafficStatsByNetwork(networkInfo).then((statsInfo: statistics.UidNetStatsInfo) => {
  let rank: Map<string, object> = new Map<string, object>(Object.entries(statsInfo));
  rank.forEach((value: object, key: string) => {
    console.info("getTrafficStatsByNetwork key=" + key + ", value=" + JSON.stringify(value));
  })
})
```

