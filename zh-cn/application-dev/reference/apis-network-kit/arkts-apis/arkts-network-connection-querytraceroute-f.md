# queryTraceRoute

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## queryTraceRoute

```TypeScript
function queryTraceRoute(destination: string, option?: TraceRouteOptions): Promise<TraceRouteInfo[]>
```

查询网络路由跟踪信息，使用Promise方式作为异步方法。 > **说明：** > > 应用调用该接口需申请精确位置权限。<!--RP1-->根据[申请位置权限开发指导](../../../device/location/location-permission-guidelines.md)&lt;!--RP1End- &gt; ->，调用方需同时申请ohos.permission.APPROXIMATELY_LOCATION和ohos.permission.LOCATION。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.INTERNET and ohos.permission.ACCESS_NET_TRACE_INFO and ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-connection-function queryTraceRoute(destination: string, option?: TraceRouteOptions): Promise<TraceRouteInfo[]>--><!--Device-connection-function queryTraceRoute(destination: string, option?: TraceRouteOptions): Promise<TraceRouteInfo[]>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| destination | string | 是 | 目标域名或IP地址，例如www.example.com、8.8.8.8。 |
| option | [TraceRouteOptions](arkts-network-connection-tracerouteoptions-i.md) | 否 | 路由跟踪的选项参数，缺省则使用默认配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[TraceRouteInfo](arkts-network-connection-tracerouteinfo-i.md)[]&gt; | Promise对象，返回路由跟踪信息数组。 |

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
let options: connection.TraceRouteOptions = {
    maxJumpNumber: 30,
    packetsType: connection.PacketsType.NETCONN_PACKETS_ICMP
};

connection.queryTraceRoute(dest, options).then((data: connection.TraceRouteInfo[]) => {
    console.info('Succeeded to getDefaultHttpProxy:' + JSON.stringify(data));
}).catch((err: BusinessError) => {
    console.error(`Failed to get request. Code:${err.code}, message:${err.message}`);
});
```

