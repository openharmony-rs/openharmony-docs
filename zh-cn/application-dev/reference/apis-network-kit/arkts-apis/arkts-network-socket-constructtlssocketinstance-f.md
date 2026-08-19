# constructTLSSocketInstance

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructTLSSocketInstance

```TypeScript
function constructTLSSocketInstance(): TLSSocket
```

创建并返回一个TLSSocket对象。

**起始版本：** 9

<!--Device-socket-function constructTLSSocketInstance(): TLSSocket--><!--Device-socket-function constructTLSSocketInstance(): TLSSocket-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TLSSocket](arkts-network-socket-tlssocket-i.md) | 返回一个TLSSocket对象。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
```


## constructTLSSocketInstance

```TypeScript
function constructTLSSocketInstance(tcpSocket: TCPSocket): TLSSocket
```

将TCPSocket升级为TLSSocket，创建并返回一个TLSSocket对象。 > **说明：** > > 需要确保TCPSocket已连接，并且当前已经没有传输数据，再调用constructTLSSocketInstance升级TLSSocket。当升级成功后，无需对TCPSocket对象调用close方法。

**起始版本：** 12

<!--Device-socket-function constructTLSSocketInstance(tcpSocket: TCPSocket): TLSSocket--><!--Device-socket-function constructTLSSocketInstance(tcpSocket: TCPSocket): TLSSocket-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tcpSocket | TCPSocket | 是 | 需要进行升级的TCPSocket对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TLSSocket](arkts-network-socket-tlssocket-i.md) | 返回一个TLSSocket对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| 2303602 | Socket is not connected. |
| 2303601 | Invalid socket FD. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}

tcp.connect(tcpconnectoptions, (err: BusinessError) => {
  if (err) {
    console.error('connect fail');
    return;
  }
  console.info('connect success');

  // 确保TCPSocket已连接后，再升级TLSSocket
  let tls: socket.TLSSocket = socket.constructTLSSocketInstance(tcp);
})
```

