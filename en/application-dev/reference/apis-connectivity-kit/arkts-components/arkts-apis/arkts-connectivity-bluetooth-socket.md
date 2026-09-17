# @ohos.bluetooth.socket

Provides methods to operate or manage bluetooth socket connection.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getDeviceId](arkts-connectivity-socket-getdeviceid-f.md) | Obtain the device id in the client socket. |
| [getL2capPsm](arkts-connectivity-socket-getl2cappsm-f.md) | Get l2cap socket psm. |
| [getMaxReceiveDataSize](arkts-connectivity-socket-getmaxreceivedatasize-f.md) | Obtain the maximum data size that can be received through this socket channel. |
| [getMaxTransmitDataSize](arkts-connectivity-socket-getmaxtransmitdatasize-f.md) | Obtain the maximum data size that can be transmitted through this socket channel. |
| [isConnected](arkts-connectivity-socket-isconnected-f.md) | Check whether the current socket connection has been established. |
| [off](arkts-connectivity-socket-off-f.md#offsppread) | Unsubscribe the event reported when data is read from the socket. |
| [on](arkts-connectivity-socket-on-f.md#onsppread) | Subscribe the event reported when data is read from the socket. |
| [sppAccept](arkts-connectivity-socket-sppaccept-f.md) | Waits for a remote device to connect. |
| [sppCloseClientSocket](arkts-connectivity-socket-sppcloseclientsocket-f.md) | Disables an spp client socket and releases related resources. |
| [sppCloseServerSocket](arkts-connectivity-socket-sppcloseserversocket-f.md) | Disables an spp server socket and releases related resources. |
| [sppConnect](arkts-connectivity-socket-sppconnect-f.md) | Connects to a remote device over the socket. |
| [sppListen](arkts-connectivity-socket-spplisten-f.md) | Creates a Bluetooth server listening socket. |
| [sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md) | Asynchronous interface for reading data from the socket. |
| [sppWrite](arkts-connectivity-socket-sppwrite-f.md) | Write data through the socket. |
| [sppWriteAsync](arkts-connectivity-socket-sppwriteasync-f.md) | Asynchronous interface for writing data to the socket. |

### Interfaces

| Name | Description |
| --- | --- |
| [SppOptions](arkts-connectivity-socket-sppoptions-i.md) | Describes the spp parameters. |

### Enums

| Name | Description |
| --- | --- |
| [SppType](arkts-connectivity-socket-spptype-e.md) | The enum of SPP type. |
