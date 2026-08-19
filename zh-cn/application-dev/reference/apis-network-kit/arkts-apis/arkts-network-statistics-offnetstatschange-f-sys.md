# offNetStatsChange（系统接口）

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## offNetStatsChange

```TypeScript
function offNetStatsChange(callback?: Callback<NetStatsChangeInfo>): void
```

取消注册网络流量更新通知。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_STATS

<!--Device-statistics-function offNetStatsChange(callback?: Callback<NetStatsChangeInfo>): void--><!--Device-statistics-function offNetStatsChange(callback?: Callback<NetStatsChangeInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NetStatsChangeInfo](arkts-network-statistics-netstatschangeinfo-i-sys.md)&gt; | 否 | The callback of off. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

