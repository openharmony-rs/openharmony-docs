# setTrafficPlanInfo（系统接口）

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## setTrafficPlanInfo

```TypeScript
function setTrafficPlanInfo(simId: int, planParam: TrafficPlanParam, value: long): Promise<void>
```

设置流量计划信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_NETWORK_STATS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-statistics-function setTrafficPlanInfo(simId: int, planParam: TrafficPlanParam, value: long): Promise<void>--><!--Device-statistics-function setTrafficPlanInfo(simId: int, planParam: TrafficPlanParam, value: long): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| simId | int | 是 | The ID of the specified sim card. |
| planParam | [TrafficPlanParam](arkts-network-statistics-trafficplanparam-e-sys.md) | 是 | The param of the specified traffic plan. |
| value | long | 是 | The value of parameter. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value, such as simId error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Nonsystem applications use system APIs. |

