# updateIfacesStats（系统接口）

## 导入模块

```TypeScript
```

## updateIfacesStats

```TypeScript
function updateIfacesStats(iface: string, start: number, end: number, stats: NetStatsInfo): Promise<void>
```

更新网络接口统计数据。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_NETWORK_STATS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iface | string | 是 | Network interface name. |
| start | number | 是 | Start timestamp for the statistics data to update. |
| end | number | 是 | End timestamp for the statistics data to update. |
| stats | [NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md) | 是 | Network statistics information. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
