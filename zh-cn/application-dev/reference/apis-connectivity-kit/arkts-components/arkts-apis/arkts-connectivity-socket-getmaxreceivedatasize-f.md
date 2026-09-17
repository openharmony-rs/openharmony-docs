# getMaxReceiveDataSize

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## getMaxReceiveDataSize

```TypeScript
function getMaxReceiveDataSize(clientSocket: number): number
```

客户端和服务端均可使用，获取当前套接字链路类型下最大接收数据的大小。通过[socket.sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md)或[socket.on('sppRead')](arkts-connectivity-socket-on-f.md#onsppread)接收数据时，单次接收的数据大小受此返回值约束（SPP_RFCOMM链路类型无此限制）。例如在文件传输、数据同步等需要接收大量数据的场景中，可调用此接口获取单次接收的最大数据量，以便对接收数据进行分片处理。

若客户端使用，需在调用[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)后，且连接成功后使用。若服务端使用，需在调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)后，且连接成功后使用。若套接字链路类型为[SPP_RFCOMM](arkts-connectivity-socket-spptype-e.md)时，最大接收数据大小无限制且返回值为0。

**起始版本：** 22

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientSocket | number | 是 | 客户端套接字的ID。该值是调用[sppAccept](arkts-connectivity-socket-sppaccept-f.md)或[sppConnect](arkts-connectivity-socket-sppconnect-f.md)接口，通过其异步callback获取到的。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回最大接收数据的大小，单位：Byte。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 入参clientNumber由sppAccept或sppConnect接口获取。
let clientSocket = 1;
try {
    let result: number = socket.getMaxReceiveDataSize(clientSocket);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
