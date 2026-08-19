# NetHandle

网络句柄。 在调用NetHandle的方法之前，需要先获取NetHandle对象。例如可通过[getDefaultNet](arkts-network-connection-getdefaultnet-f.md)获取系统当前默认网络的网络句柄。

**起始版本：** 23

<!--Device-connection-export interface NetHandle--><!--Device-connection-export interface NetHandle-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## bindSocket

```TypeScript
bindSocket(socketParam: TCPSocket | UDPSocket, callback: AsyncCallback<void>): void
```

将TCPSocket或UDPSocket绑定到当前NetHandle对应的网络。使用callback异步回调。

**起始版本：** 9

<!--Device-NetHandle-bindSocket(socketParam: TCPSocket | UDPSocket, callback: AsyncCallback<void>): void--><!--Device-NetHandle-bindSocket(socketParam: TCPSocket | UDPSocket, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| socketParam | TCPSocket \| UDPSocket | 是 | 待绑定的TCPSocket或UDPSocket对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当TCPSocket或UDPSocket成功绑定到当前网络，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection, socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface Data {
  message: ArrayBuffer,
  remoteInfo: socket.SocketRemoteInfo
}

  connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
  }
  let tcp : socket.TCPSocket = socket.constructTCPSocketInstance();
  let udp : socket.UDPSocket = socket.constructUDPSocketInstance();
  let socketType = "TCPSocket";
  if (socketType == "TCPSocket") {
    tcp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: Error) => {
      if (error) {
        console.error(`Failed to bind. Code:${error.code}, message:${error.message}`);
        return;
      }
      netHandle.bindSocket(tcp, (error: BusinessError, data: void) => {
        if (error) {
          console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
          return;
        } else {
          console.info('Succeeded to getdefaultHttpProxy:' + JSON.stringify(data));
        }
      });
    });
  } else {
    let callback: (value: Data) => void = (value: Data) => {
      console.info("Succeeded to get message, message:" + value.message + ", Succeeded to get remoteInfo:" + value.remoteInfo);
    };
    udp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to bind. Code:${error.code}, message:${error.message}`);
        return;
      }
      udp.on('message', (data: Data) => {
        console.info("Succeeded to get data: " + JSON.stringify(data));
      });
      netHandle.bindSocket(udp, (error: BusinessError, data: void) => {
        if (error) {
          console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
          return;
        } else {
          console.info('Succeeded to get defaultHttpProxy: ' + JSON.stringify(data));
        }
      });
    });
  }
})
```

## bindSocket

```TypeScript
bindSocket(socketParam: TCPSocket | UDPSocket): Promise<void>
```

将TCPSocket或UDPSocket绑定到当前NetHandle对应的网络。使用Promise异步回调。

**起始版本：** 9

<!--Device-NetHandle-bindSocket(socketParam: TCPSocket | UDPSocket): Promise<void>--><!--Device-NetHandle-bindSocket(socketParam: TCPSocket | UDPSocket): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| socketParam | TCPSocket \| UDPSocket | 是 | 待绑定的TCPSocket或UDPSocket对象。 |

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

**示例**

```TypeScript
import { connection, socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface Data {
  message: ArrayBuffer,
  remoteInfo: socket.SocketRemoteInfo
}

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let tcp : socket.TCPSocket = socket.constructTCPSocketInstance();
  let udp : socket.UDPSocket = socket.constructUDPSocketInstance();
  let socketType = "TCPSocket";
  if (socketType == "TCPSocket") {
    tcp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: Error) => {
      if (error) {
        console.error('Failed to bind');
        return;
      }
      netHandle.bindSocket(tcp).then(() => {
        console.info("Succeeded to bind socket");
      }).catch((error: BusinessError) => {
        console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
      });
    });
  } else {
    let callback: (value: Data) => void = (value: Data) => {
      console.info("on message, message:" + value.message + ", remoteInfo:" + value.remoteInfo);
    }
    udp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to bind. Code:${error.code}, message:${error.message}`);
        return;
      }
      udp.on('message', (data: Data) => {
        console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
      });
      netHandle.bindSocket(udp).then(() => {
        console.info("Succeeded to bind socket");
      }).catch((error: BusinessError) => {
        console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
      });
    });
  }
});
```

## getAddressByName

```TypeScript
getAddressByName(host: string, callback: AsyncCallback<NetAddress>): void
```

使用当前NetHandle对应的网络解析主机名获取到的第一个IP地址。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.INTERNET

<!--Device-NetHandle-getAddressByName(host: string, callback: AsyncCallback<NetAddress>): void--><!--Device-NetHandle-getAddressByName(host: string, callback: AsyncCallback<NetAddress>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要解析的主机名。例如："www.example.com"。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;NetAddress&gt; | 是 | 回调函数。当使用对应网络解析主机名获取第一个IP地址成功，error为undefined，data为获取的第一个IP地址；否则为错 误对象。 |

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
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressByName(host, (error: BusinessError, data: connection.NetAddress) => {
    if (error) {
      console.error(`Failed to get address. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  });
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let host = "xxxx";
  netHandle.getAddressByName(host, (error: BusinessError|null, data: connection.NetAddress|undefined) => {
    if (error) {
      console.error(`Failed to get address. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  });
});
```

## getAddressByName

```TypeScript
getAddressByName(host: string): Promise<NetAddress>
```

使用当前NetHandle对应的网络解析主机名获取到的第一个IP地址。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.INTERNET

<!--Device-NetHandle-getAddressByName(host: string): Promise<NetAddress>--><!--Device-NetHandle-getAddressByName(host: string): Promise<NetAddress>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要解析的主机名。例如："www.example.com"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NetAddress&gt; | Promise对象，返回获取到的第一个IP地址。 |

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

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandler的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let host = "xxxx";
  netHandle.getAddressByName(host).then((data: connection.NetAddress) => {
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  });
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandler的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return 0;
  }
  let host = "xxxx";
  netHandle.getAddressByName(host).then((data: connection.NetAddress) => {
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  });
});
```

## getAddressesByName

```TypeScript
getAddressesByName(host: string, callback: AsyncCallback<Array<NetAddress>>): void
```

使用当前NetHandle对应的网络解析主机名获取到的所有IP地址。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NetHandle-getAddressesByName(host: string, callback: AsyncCallback<Array<NetAddress>>): void--><!--Device-NetHandle-getAddressesByName(host: string, callback: AsyncCallback<Array<NetAddress>>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要解析的主机名。例如："www.example.com"。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;NetAddress&gt;&gt; | 是 | 回调函数。当使用对应网络解析主机名成功获取所有IP地址，error为undefined，data为获取到的所有IP地 址；否则为错误对象。 |

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

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressesByName(host, (error: BusinessError, data: connection.NetAddress[]) => {
    if (error) {
      console.error(`Failed to get addresses. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  });
});
```

## getAddressesByName

```TypeScript
getAddressesByName(host: string): Promise<Array<NetAddress>>
```

使用当前NetHandle对应的网络解析主机名获取到的所有IP地址。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NetHandle-getAddressesByName(host: string): Promise<Array<NetAddress>>--><!--Device-NetHandle-getAddressesByName(host: string): Promise<Array<NetAddress>>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要解析的主机名。例如："www.example.com"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;NetAddress&gt;&gt; | Promise对象，返回所有IP地址。 |

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

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressesByName(host).then((data: connection.NetAddress[]) => {
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  });
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressesByName(host).then((data: Array<connection.NetAddress>|undefined) => {
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  });
});
```

## getAddressesByNameWithOptions

```TypeScript
getAddressesByNameWithOptions(host: string, option?: QueryOptions): Promise<Array<NetAddress>>
```

使用当前NetHandle对应的网络基于指定IP类型进行DNS解析。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NetHandle-getAddressesByNameWithOptions(host: string, option?: QueryOptions): Promise<Array<NetAddress>>--><!--Device-NetHandle-getAddressesByNameWithOptions(host: string, option?: QueryOptions): Promise<Array<NetAddress>>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要解析的主机名。例如："www.example.com"。 |
| option | [QueryOptions](arkts-network-connection-queryoptions-i.md) | 否 | 需要查询的IP类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;NetAddress&gt;&gt; | Promise对象，返回查询到的IP地址。返回值中的port字段固定为0，无需关注。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let host = "www.example.com";
  let option: connection.QueryOptions = {
      family: connection.FamilyType.FAMILY_TYPE_IPV4
    };
  netHandle.getAddressesByNameWithOptions(host, option).then((data: connection.NetAddress[]) => {
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get addresses by name. Code:${err.code}, message:${err.message}`);
  });
});
```

## netId

```TypeScript
netId: int
```

网络ID，取值为0代表没有默认网络，其余有效取值必须大于等于100。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetHandle-netId: int--><!--Device-NetHandle-netId: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

