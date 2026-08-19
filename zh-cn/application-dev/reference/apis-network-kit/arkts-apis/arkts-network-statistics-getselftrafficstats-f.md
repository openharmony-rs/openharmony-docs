# getSelfTrafficStats

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getSelfTrafficStats

```TypeScript
function getSelfTrafficStats(networkInfo: NetworkInfo): Promise<NetStatsInfo>
```

获取指定时间段内，本应用在指定网络中的流量使用情况。使用Promise异步回调。 > **说明：** > > - 当前只支持获取蜂窝和Wi-Fi流量使用情况。 > - 当前只支持获取31天之内的流量使用情况，如果参数中传入的时间戳早于当前系统时间31天，会返回错误码2103019。 > > - 本接口会有一定耗时，调用时请注意切勿频繁调用。

**起始版本：** 22

<!--Device-statistics-function getSelfTrafficStats(networkInfo: NetworkInfo): Promise<NetStatsInfo>--><!--Device-statistics-function getSelfTrafficStats(networkInfo: NetworkInfo): Promise<NetStatsInfo>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkInfo | NetworkInfo | 是 | 指定查询的网络信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md)&gt; | Promise对象，返回应用历史流量统计信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2103017](../errorcode-net-statistics.md#2103017-读取数据库失败) | Failed to read the database. |
| [2103019](../errorcode-net-statistics.md#2103019-时间戳无效) | The timestamp in param is invalid. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { connection, statistics } from '@kit.NetworkKit';

let networkInfo: statistics.NetworkInfo = {
    type: connection.NetBearType.BEARER_CELLULAR,
    startTime: Math.floor(Date.now() / 1000) - 86400 * 31,
    endTime: Math.floor(Date.now() / 1000),
    simId: 1,
}

statistics.getSelfTrafficStats(networkInfo).then((stats: statistics.NetStatsInfo) => {
    console.info('getSelfTrafficStats success : ' + JSON.stringify(stats));
}).catch((err: BusinessError) => {
    console.error('getSelfTrafficStats error. code: ' + `${err.code}` + ', message: ' + `${err.message}`);
});
```

