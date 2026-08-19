# reportNetConnected

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## reportNetConnected

```TypeScript
function reportNetConnected(netHandle: NetHandle, callback: AsyncCallback<void>): void
```

向网络管理上报网络处于可用状态。使用callback方式异步回调。 > **说明：** > > 该接口用于浏览器连接portal网络，网络认证成功后，向网络管理上报网络连接成功，网络管理会触发网络探测，更新网络状态。

**起始版本：** 8

**需要权限：** ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

<!--Device-connection-function reportNetConnected(netHandle: NetHandle, callback: AsyncCallback<void>): void--><!--Device-connection-function reportNetConnected(netHandle: NetHandle, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄，参考[NetHandle](arkts-network-connection-nethandle-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当向网络管理报告网络处于可用状态成功，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  connection.reportNetConnected(netHandle, (error: BusinessError) => {
    console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
  });
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  connection.reportNetConnected(netHandle, (error: BusinessError|null) => {
    console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
  });
});
```


## reportNetConnected

```TypeScript
function reportNetConnected(netHandle: NetHandle): Promise<void>
```

向网络管理报告网络处于可用状态。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

<!--Device-connection-function reportNetConnected(netHandle: NetHandle): Promise<void>--><!--Device-connection-function reportNetConnected(netHandle: NetHandle): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄，参考[NetHandle](arkts-network-connection-nethandle-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  connection.reportNetConnected(netHandle).then(() => {
    console.info(`Succeeded to report`);
  });
});
```

