# getTrafficPlanInfo（系统接口）

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getTrafficPlanInfo

```TypeScript
function getTrafficPlanInfo(simId: number, planParam: TrafficPlanParam): Promise<number>
```

获取流量计划信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_NETWORK_STATS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| simId | number | 是 | The id of the specified sim card. |
| planParam | [TrafficPlanParam](arkts-network-statistics-trafficplanparam-e-sys.md) | 是 | The param of the specified traffic plan. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | The value of parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Nonsystem applications use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value, such as simId error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
