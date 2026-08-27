# getDefaultNet

## 导入模块

```TypeScript
```

## getDefaultNet

```TypeScript
function getDefaultNet(callback: AsyncCallback<NetHandle>): void
```

获取系统默认使用的网络句柄，包含网络ID。使用callback异步回调。

> **说明：**
> 
> - 系统默认使用的网络，该网络的capabilities必须具备[NET_CAPABILITY_INTERNET](arkts-network-connection-netcap-e.md)且不是VPN类型的网络。
> 
> - 该接口的返回由系统决定，与应用是否指定网络无关。
> 
> - 一般情况下优先级为：以太网（PC）|蓝牙（手表）
> WIFI
> 蜂窝，特殊情况以实际返回结果为准。
> 
> - [NetHandle](arkts-network-connection-nethandle-i.md)为网络唯一标识，当无网络可用时，返回0。其可用于
> [getNetCapabilities](arkts-network-connection-getnetcapabilities-f.md)继续查询更多网络信息。

**起始版本：** 8

**需要权限：** ohos.permission.GET_NETWORK_INFO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;NetHandle&gt; | 是 | 回调函数。当成功获取默认激活网络的网络句柄时，error为undefined，data为默认网络的网络句柄；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet((error: BusinessError, data: connection.NetHandle) => {
  if (error) {
    console.error(`Failed to get default net. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```


## getDefaultNet

```TypeScript
function getDefaultNet(): Promise<NetHandle>
```

获取系统默认使用的网络句柄，包含网络ID。使用Promise异步回调。

> **说明：**
> 
> - 系统默认使用的网络，该网络的capabilities必须具备[NET_CAPABILITY_INTERNET](arkts-network-connection-netcap-e.md)且不是VPN类型的网络。
> 
> - 该接口的返回由系统决定，与应用是否指定网络无关。
> 
> - 一般情况下，优先级：以太网（PC）|蓝牙（手表）
> WIFI
> 蜂窝，特殊情况以实际返回结果为准。
> 
> - [NetHandle](arkts-network-connection-nethandle-i.md)为网络唯一标识，当无网络可用时，返回0。其可用于
> [getNetCapabilities](arkts-network-connection-getnetcapabilities-f.md)继续查询更多网络信息。

**起始版本：** 8

**需要权限：** ohos.permission.GET_NETWORK_INFO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;NetHandle & gt; | 以Promise形式返回默认网络的网络句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((data: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```
