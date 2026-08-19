# reportNetDisconnected

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## reportNetDisconnected

```TypeScript
function reportNetDisconnected(netHandle: NetHandle, callback: AsyncCallback<void>): void
```

向网络管理上报网络处于不可用状态。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

<!--Device-connection-function reportNetDisconnected(netHandle: NetHandle, callback: AsyncCallback<void>): void--><!--Device-connection-function reportNetDisconnected(netHandle: NetHandle, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄，参考[NetHandle](arkts-network-connection-nethandle-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当向网络管理报告网络处于不可用状态成功时，error为undefined，否则为错误对象。 |

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
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet((error: BusinessError, netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  connection.reportNetDisconnected(netHandle, (error: BusinessError, data: void) => {
    if (error) {
      console.error(`Failed to get default net. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to report");
  });
});
```


## reportNetDisconnected

```TypeScript
function reportNetDisconnected(netHandle: NetHandle): Promise<void>
```

向网络管理上报网络处于不可用状态。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

<!--Device-connection-function reportNetDisconnected(netHandle: NetHandle): Promise<void>--><!--Device-connection-function reportNetDisconnected(netHandle: NetHandle): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄。 |

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
  connection.reportNetDisconnected(netHandle).then( () => {
    console.info(`Succeeded to report`);
  });
});
```

