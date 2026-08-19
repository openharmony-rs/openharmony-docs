# setAppNet

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setAppNet

```TypeScript
function setAppNet(netHandle: NetHandle, callback: AsyncCallback<void>): void
```

将App绑定到特定的网络，绑定后App只能通过netHandle对应的网络访问网络。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET

<!--Device-connection-function setAppNet(netHandle: NetHandle, callback: AsyncCallback<void>): void--><!--Device-connection-function setAppNet(netHandle: NetHandle, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当成功绑定App到指定网络时，error为undefined，否则为错误对象。 |

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

// 创建NetConnection对象。仅关注WIFI网络，需要指定网络类型为WIFI网络。
let netCon = connection.createNetConnection({
  netCapabilities: {
    bearerTypes: [connection.NetBearType.BEARER_WIFI]
  }
});

// 使用on接口订阅网络可用事件
netCon.on('netAvailable', (netHandle: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(netHandle));
  connection.setAppNet(netHandle, (error: BusinessError, data: void) => {
    if (error) {
      console.error(`Failed to setAppNet. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to setAppNet, netid: " + JSON.stringify(netHandle.netId));
  });
});

// 使用on接口订阅网络丢失事件。
netCon.on('netLost', (netHandle: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(netHandle));
  // 网络丢失时，需要主动解除指定网络的绑定关系
  netHandle.netId = 0;
  connection.setAppNet(netHandle, (error: BusinessError, data: void) => {
    if (error) {
      console.error(`Failed to setAppNet. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to setAppNet, netid: " + JSON.stringify(netHandle.netId));
  });
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  if (error) {
    console.error(`Failed to get request. Code:${error.code}, message:${error.message}`);
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet((error: BusinessError|null, netHandle: connection.NetHandle|undefined) => {
  if (netHandle?.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  if (netHandle) {
    connection.setAppNet(netHandle, (error: BusinessError|null) => {
      if (error) {
        console.error(`Failed to setAppNet. Code:${error.code}, message:${error.message}`);
        return;
      }
    });
  }
});
```


## setAppNet

```TypeScript
function setAppNet(netHandle: NetHandle): Promise<void>
```

将App异步绑定到特定的网络，绑定后App只能通过netHandle对应的网络访问网络。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-connection-function setAppNet(netHandle: NetHandle): Promise<void>--><!--Device-connection-function setAppNet(netHandle: NetHandle): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

// 创建NetConnection对象。仅关注WIFI网络，需要指定网络类型为WIFI网络。
let netCon = connection.createNetConnection({
  netCapabilities: {
    bearerTypes: [connection.NetBearType.BEARER_WIFI]
  }
});

// 使用on接口订阅网络可用事件
netCon.on('netAvailable', (netHandle: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(netHandle));
  connection.setAppNet(netHandle).then(() => {
    console.info("Succeeded to setAppNet, netid: " + JSON.stringify(netHandle.netId));
  }).catch((error: BusinessError) => {
    console.error(`Failed to setAppNet. Code:${error.code}, message:${error.message}`);
  })
});

// 使用on接口订阅网络丢失事件。
netCon.on('netLost', (netHandle: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(netHandle));
  // 网络丢失时，需要主动解除指定网络的绑定关系
  netHandle.netId = 0;
  connection.setAppNet(netHandle).then(() => {
    console.info("Succeeded to setAppNet, netid: " + JSON.stringify(netHandle.netId));
  }).catch((error: BusinessError) => {
    console.error(`Failed to setAppNet. Code:${error.code}, message:${error.message}`);
  })
});

// 注册网络状态变化事件。此接口要在调用on后调用。
netCon.register((error: BusinessError) => {
  if (error) {
    console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return 0;
  }

  connection.setAppNet(netHandle).then(() => {
    console.info("Succeeded to setAppNet, netid: " + JSON.stringify(netHandle.netId));
  }).catch((error: Error) => {
    let businessError = error as BusinessError;
    console.error(`Failed to setAppNet. Code:${businessError.code}, message:${businessError.message}`);
  })
});
```

