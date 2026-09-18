# getMaxTransmitDataSize

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## getMaxTransmitDataSize

```TypeScript
function getMaxTransmitDataSize(clientSocket: number): number
```

客户端和服务端均可使用，获取套接字当前链路类型下最大发送数据的大小。调用[socket.sppWrite](arkts-connectivity-socket-sppwrite-f.md)或[socket.sppWriteAsync](arkts-connectivity-socket-sppwriteasync-f.md)发送数据时，单次发送的数据大小不应超过此返回值（SPP_RFCOMM链路类型无此限制）。例如在文件传输、音视频数据传输等需要发送大量数据的场景中，可调用此接口获取单次发送的最大数据量，以便对发送数据进行分片处理。

若客户端使用，需在调用[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)后，且连接成功后使用。若服务端使用，需在调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)后，且连接成功后使用。若套接字链路类型为[SPP_RFCOMM](arkts-connectivity-socket-spptype-e.md)时，最大发送数据大小无限制且返回值为0。

**起始版本：** 22

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientSocket | number | 是 | 客户端套接字的ID。<br>该值是调用[sppAccept](arkts-connectivity-socket-sppaccept-f.md)或[sppConnect](arkts-connectivity-socket-sppconnect-f.md)接口，通过其异步callback获取到的。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回最大发送数据的大小，单位：Byte。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 入参clientNumber由sppAccept或sppConnect接口获取。
let clientSocket = 1;
try {
    let result: number = socket.getMaxTransmitDataSize(clientSocket);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
