# @ohos.bluetooth.socket

Provides methods to operate or manage bluetooth socket connection.

**Since:** 10

<!--Device-unnamed-declare namespace socket--><!--Device-unnamed-declare namespace socket-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getDeviceId](arkts-connectivity-socket-getdeviceid-f.md#getdeviceid-1) | Obtain the device id in the client socket. |
| [getL2capPsm](arkts-connectivity-socket-getl2cappsm-f.md#getl2cappsm-1) | Get l2cap socket psm. |
| [getMaxReceiveDataSize](arkts-connectivity-socket-getmaxreceivedatasize-f.md#getmaxreceivedatasize-1) | Obtain the maximum data size that can be received through this socket channel. |
| [getMaxTransmitDataSize](arkts-connectivity-socket-getmaxtransmitdatasize-f.md#getmaxtransmitdatasize-1) | Obtain the maximum data size that can be transmitted through this socket channel. |
| [isConnected](arkts-connectivity-socket-isconnected-f.md#isconnected-1) | Check whether the current socket connection has been established. |
| [off('sppRead')](arkts-connectivity-socket-off-f.md#offsppread) | Unsubscribe the event reported when data is read from the socket. |
| [on('sppRead')](arkts-connectivity-socket-on-f.md#onsppread) | Subscribe the event reported when data is read from the socket. |
| [sppAccept](arkts-connectivity-socket-sppaccept-f.md#sppaccept-1) | Waits for a remote device to connect. |
| [sppCloseClientSocket](arkts-connectivity-socket-sppcloseclientsocket-f.md#sppcloseclientsocket-1) | Disables an spp client socket and releases related resources. |
| [sppCloseServerSocket](arkts-connectivity-socket-sppcloseserversocket-f.md#sppcloseserversocket-1) | Disables an spp server socket and releases related resources. |
| [sppConnect](arkts-connectivity-socket-sppconnect-f.md#sppconnect-1) | Connects to a remote device over the socket. |
| [sppListen](arkts-connectivity-socket-spplisten-f.md#spplisten-1) | Creates a Bluetooth server listening socket. |
| [sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md#sppreadasync-1) | Asynchronous interface for reading data from the socket. |
| [sppWrite](arkts-connectivity-socket-sppwrite-f.md#sppwrite-1) | Write data through the socket. |
| [sppWriteAsync](arkts-connectivity-socket-sppwriteasync-f.md#sppwriteasync-1) | Asynchronous interface for writing data to the socket. |

### Interfaces

| Name | Description |
| --- | --- |
| [SppOptions](arkts-connectivity-socket-sppoptions-i.md) | Describes the spp parameters. |

### Enums

| Name | Description |
| --- | --- |
| [SppType](arkts-connectivity-socket-spptype-e.md) | The enum of SPP type. |
