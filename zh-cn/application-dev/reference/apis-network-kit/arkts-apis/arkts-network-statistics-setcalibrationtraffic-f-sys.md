# setCalibrationTraffic（系统接口）

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## setCalibrationTraffic

```TypeScript
function setCalibrationTraffic(simId: int, remainTraffic: long, totalTraffic?: long): Promise<void>
```

设置流量校准数据。在做流量校准时，可通过本接口设置相关流量数据。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_NETWORK_STATS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-statistics-function setCalibrationTraffic(simId: int, remainTraffic: long, totalTraffic?: long): Promise<void>--><!--Device-statistics-function setCalibrationTraffic(simId: int, remainTraffic: long, totalTraffic?: long): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| simId | int | 是 | SIM卡ID。 |
| remainTraffic | long | 是 | 当前剩余流量，单位：Byte。 |
| totalTraffic | long | 否 | 套餐总流量，单位：Byte。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value, such as simId error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error, such as nullptr. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Nonsystem applications use system APIs. |

**示例**

```TypeScript
import { connection, statistics } from '@kit.NetworkKit';

let simId:number = 1;
let remainData:number = 600*1024*1024;   // 当前剩余流量为600MB。
let totalData:number = 1024*1024*1024;   // 套餐总流量为1GB。
statistics.setCalibrationTraffic(simId, remainData, totalData).then(() => {
  console.info(`setCalibrationTraffic succ`);
}).catch((error: BusinessError) => {
  console.info(`setCalibrationTraffic error. code:${error.code}, message:${error.message}`);
});
```

