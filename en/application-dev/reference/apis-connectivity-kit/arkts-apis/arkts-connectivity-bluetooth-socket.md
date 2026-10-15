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
| [getDeviceId](arkts-connectivity-socket-getdeviceid-f.md#getdeviceid) | Obtain the device id in the client socket. |
| [getL2capPsm](arkts-connectivity-socket-getl2cappsm-f.md#getl2cappsm) | Get l2cap socket psm. |
| [getMaxReceiveDataSize](arkts-connectivity-socket-getmaxreceivedatasize-f.md#getmaxreceivedatasize) | Obtain the maximum data size that can be received through this socket channel. |
| [getMaxTransmitDataSize](arkts-connectivity-socket-getmaxtransmitdatasize-f.md#getmaxtransmitdatasize) | Obtain the maximum data size that can be transmitted through this socket channel. |
| [isConnected](arkts-connectivity-socket-isconnected-f.md#isconnected) | Check whether the current socket connection has been established. |
| [off('sppRead')](arkts-connectivity-socket-off-f.md#offsppread) | Unsubscribe the event reported when data is read from the socket. |
| [on('sppRead')](arkts-connectivity-socket-on-f.md#onsppread) | Subscribe the event reported when data is read from the socket. |
| [sppAccept](arkts-connectivity-socket-sppaccept-f.md#sppaccept) | Waits for a remote device to connect. |
| [sppCloseClientSocket](arkts-connectivity-socket-sppcloseclientsocket-f.md#sppcloseclientsocket) | Disables an spp client socket and releases related resources. |
| [sppCloseServerSocket](arkts-connectivity-socket-sppcloseserversocket-f.md#sppcloseserversocket) | Disables an spp server socket and releases related resources. |
| [sppConnect](arkts-connectivity-socket-sppconnect-f.md#sppconnect) | Connects to a remote device over the socket. |
| [sppListen](arkts-connectivity-socket-spplisten-f.md#spplisten) | Creates a Bluetooth server listening socket. |
| [sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md#sppreadasync) | Asynchronous interface for reading data from the socket. |
| [sppWrite](arkts-connectivity-socket-sppwrite-f.md#sppwrite) | Write data through the socket. |
| [sppWriteAsync](arkts-connectivity-socket-sppwriteasync-f.md#sppwriteasync) | Asynchronous interface for writing data to the socket. |

### Interfaces

| Name | Description |
| --- | --- |
| [SppOptions](arkts-connectivity-socket-sppoptions-i.md) | Describes the spp parameters. |

### Enums

| Name | Description |
| --- | --- |
| [SppType](arkts-connectivity-socket-spptype-e.md) | The enum of SPP type. |
