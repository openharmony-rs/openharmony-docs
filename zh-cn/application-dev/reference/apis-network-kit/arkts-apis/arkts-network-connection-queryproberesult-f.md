# queryProbeResult

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## queryProbeResult

```TypeScript
function queryProbeResult(destination: string, duration: int): Promise<ProbeResultInfo>
```

查询网络探测结果。若出现异常（例如断网），导致发送请求失败，则接口会立即返回，不再进行后续探测。本接口使用Promise方式作为异步方法。 > **说明：** > > 此接口用于对目标主机进行一段持续时间的网络探测，以获取丢包率和RTT信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.INTERNET

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-connection-function queryProbeResult(destination: string, duration: int): Promise<ProbeResultInfo>--><!--Device-connection-function queryProbeResult(destination: string, duration: int): Promise<ProbeResultInfo>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| destination | string | 是 | 目标域名或IP地址，例如www.example.com、8.8.8.8。 |
| duration | int | 是 | 探测持续时间，单位为秒，取值范围[1, 1000]。探测间隔为1秒。若未出现异常（例如断网），探测时间到期后返回探测结果。该字段表示探测持续总时长，设置过长可能导致长时间占用应用 线程资源。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ProbeResultInfo](arkts-network-connection-proberesultinfo-i.md)&gt; | Promise对象，返回探测结果信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dest: string = "www.example.com";
let duration: number = 10;

connection.queryProbeResult(dest, duration).then((data: connection.ProbeResultInfo) => {
    console.info(`Succeeded to get LossRate: ${data.lossRate}, Succeeded to getRTT: ${data.rtt}`);
}).catch((err: BusinessError) => {
    console.error(`Failed to get request. Code:${err.code}, message:${err.message}`);
});
```

