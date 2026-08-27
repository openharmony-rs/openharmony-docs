# getTrafficStatsByIface（系统接口）

## 导入模块

```TypeScript
```

## getTrafficStatsByIface

```TypeScript
function getTrafficStatsByIface(ifaceInfo: IfaceInfo, callback: AsyncCallback<NetStatsInfo>): void
```

获取指定网卡历史流量信息，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.GET_NETWORK_STATS

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ifaceInfo | [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md) | 是 | 指定查询的网卡信息，参见[IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md)&gt; | 是 | 回调函数。成功时 statsInfo 返回包含网卡历史流量信息，error 为 undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2103017](../errorcode-net-statistics.md#2103017-读取数据库失败) | Failed to read the database. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let iFaceInfo: statistics.IfaceInfo | null = null;
if (iFaceInfo) {
  statistics.getTrafficStatsByIface(iFaceInfo as statistics.IfaceInfo, (error: BusinessError, statsInfo: statistics.NetStatsInfo) => {
    console.error(JSON.stringify(error));
    console.info(
      "getTrafficStatsByIface bytes of received = " +
      JSON.stringify(statsInfo.rxBytes)
    );
    console.info(
      "getTrafficStatsByIface bytes of sent = " +
      JSON.stringify(statsInfo.txBytes)
    );
    console.info(
      "getTrafficStatsByIface packets of received = " +
      JSON.stringify(statsInfo.rxPackets)
    );
    console.info(
      "getTrafficStatsByIface packets of sent = " +
      JSON.stringify(statsInfo.txPackets)
    );
  });
}
```


## getTrafficStatsByIface

```TypeScript
function getTrafficStatsByIface(ifaceInfo: IfaceInfo): Promise<NetStatsInfo>
```

获取指定网卡历史流量信息，使用 Promise 异步回调。  
| 参数名 | 类型 | 必填 | 说明 | | --------- | ------------------------- | ---- | --------------------------------------------------- | | ifaceInfo | [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md) | 是 | 指定查询的网卡信息，参见[IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md)。 |

**起始版本：** 10

**需要权限：** ohos.permission.GET_NETWORK_STATS

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ifaceInfo | [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md) | 是 | Detailed query content. See [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md)&gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2103017](../errorcode-net-statistics.md#2103017-读取数据库失败) | Failed to read the database. |

**示例**

```TypeScript
import { statistics } from '@kit.NetworkKit';

let iFaceInfo: statistics.IfaceInfo | null = null;
if (iFaceInfo) {
  statistics.getTrafficStatsByIface(iFaceInfo as statistics.IfaceInfo).then((statsInfo: statistics.NetStatsInfo) => {
    console.info(
      "getTrafficStatsByIface bytes of received = " +
      JSON.stringify(statsInfo.rxBytes)
    );
    console.info(
      "getTrafficStatsByIface bytes of sent = " +
      JSON.stringify(statsInfo.txBytes)
    );
    console.info(
      "getTrafficStatsByIface packets of received = " +
      JSON.stringify(statsInfo.rxPackets)
    );
    console.info(
      "getTrafficStatsByIface packets of sent = " +
      JSON.stringify(statsInfo.txPackets)
    );
  });
}
```
