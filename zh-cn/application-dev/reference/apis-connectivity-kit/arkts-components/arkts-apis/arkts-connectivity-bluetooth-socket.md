# @ohos.bluetooth.socket(蓝牙socket模块)

本模块提供一种蓝牙套接字功能，可实现设备间连接和数据传输。当两个设备间进行蓝牙套接字通信交互时，依据设备功能的不同，可区分客户端与服务端。

支持的套接字链路类型包括RFCOMM和L2CAP。RFCOMM链路类型也称为串口通信协议（Serial Port Profile, SPP），适用于传统蓝牙（BR/EDR）。L2CAP链路类型适用于传统蓝牙（BR/EDR）和低功耗蓝牙（BLE）。

通过[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)创建客户端套接字并向服务端发起连接。

通过[socket.sppListen](arkts-connectivity-socket-spplisten-f.md)创建服务端套接字并监听客户端的连接。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getDeviceId](arkts-connectivity-socket-getdeviceid-f.md) | 客户端和服务端均可使用，获取套接字连接中的对端设备蓝牙地址。若客户端使用，需在调用[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)后，且连接成功后使用。若服务端使用，需在调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)后，且连接成功后使用。 |
| [getL2capPsm](arkts-connectivity-socket-getl2cappsm-f.md) | 获取服务端L2CAP链路类型套接字的协议/服务多路复用器值（Protocol/Service Multiplexer, PSM），该值用于标识特定的服务数据传输通道。 |
| [getMaxReceiveDataSize](arkts-connectivity-socket-getmaxreceivedatasize-f.md) | 客户端和服务端均可使用，获取当前套接字链路类型下最大接收数据的大小。通过[socket.sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md)或[socket.on('sppRead')](arkts-connectivity-socket-on-f.md#onsppread)接收数据时，单次接收的数据大小受此返回值约束（SPP_RFCOMM链路类型无此限制）。例如在文件传输、数据同步等需要接收大量数据的场景中，可调用此接口获取单次接收的最大数据量，以便对接收数据进行分片处理。 |
| [getMaxTransmitDataSize](arkts-connectivity-socket-getmaxtransmitdatasize-f.md) | 客户端和服务端均可使用，获取套接字当前链路类型下最大发送数据的大小。调用[socket.sppWrite](arkts-connectivity-socket-sppwrite-f.md)或[socket.sppWriteAsync](arkts-connectivity-socket-sppwriteasync-f.md)发送数据时，单次发送的数据大小不应超过此返回值（SPP_RFCOMM链路类型无此限制）。例如在文件传输、音视频数据传输等需要发送大量数据的场景中，可调用此接口获取单次发送的最大数据量，以便对发送数据进行分片处理。 |
| [isConnected](arkts-connectivity-socket-isconnected-f.md) | 客户端和服务端均可使用，检查当前链路是否已连接。 |
| [off](arkts-connectivity-socket-off-f.md#offsppread) | 取消订阅套接字读请求事件。 |
| [on](arkts-connectivity-socket-on-f.md#onsppread) | 客户端和服务端均可使用，订阅套接字读请求事件。调用该接口后，当收到对端发送的数据会执行订阅的回调函数。 |
| [sppAccept](arkts-connectivity-socket-sppaccept-f.md) | 服务端使用，接受客户端的套接字连接请求。使用Callback异步回调。 |
| [sppCloseClientSocket](arkts-connectivity-socket-sppcloseclientsocket-f.md) | 客户端和服务端均可使用，关闭指定的客户端套接字，并断开客户端和服务端之间的连接。 |
| [sppCloseServerSocket](arkts-connectivity-socket-sppcloseserversocket-f.md) | 服务端使用，删除指定的服务端套接字。 |
| [sppConnect](arkts-connectivity-socket-sppconnect-f.md) | 客户端使用，创建一个客户端套接字，并向服务端的特定服务发起连接请求。 |
| [sppListen](arkts-connectivity-socket-spplisten-f.md) | 服务端使用，创建一个服务端监听套接字。使用Callback异步回调。 |
| [sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md) | 客户端和服务端均可使用，读取对端发送数据的异步接口。使用Promise异步回调。当连接断开时，该接口会抛出错误码并返回。 |
| [sppWrite](arkts-connectivity-socket-sppwrite-f.md) | 客户端和服务端均可使用，向对端设备发送数据。 |
| [sppWriteAsync](arkts-connectivity-socket-sppwriteasync-f.md) | 客户端和服务端均可使用，向对端设备发送数据。使用Promise异步回调。当连接断开时，该接口会抛出错误码并返回。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [SppOptions](arkts-connectivity-socket-sppoptions-i.md) | 描述套接字的配置参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SppType](arkts-connectivity-socket-spptype-e.md) | 枚举，蓝牙套接字链路类型。 |
