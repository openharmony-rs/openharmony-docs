# @ohos.nearlink.dataTransfer(NearLink Data Transfer Capability)

This module provides the NearLink data transfer capability, including port channel management, connection management, data sending and receiving, and connection status query and subscription.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [connect](arkts-connectivity-datatransfer-connect-f.md) | Connects to a remote device. This API uses a promise to return the result. |
| [createPort](arkts-connectivity-datatransfer-createport-f.md) | Registers a port channel. A port channel can be used to connect to a remote device only after being registered. If the port channel is no longer needed after use, call [dataTransfer.destroyPort](arkts-connectivity-datatransfer-destroyport-f.md) to destroy it. |
| [destroyPort](arkts-connectivity-datatransfer-destroyport-f.md) | Destroys the port channel. |
| [disconnect](arkts-connectivity-datatransfer-disconnect-f.md) | Disconnects from the remote device. This method is called to disconnect from the remote device after it is successfully connected using [dataTransfer.connect](arkts-connectivity-datatransfer-connect-f.md). This API uses a promise to return the result. |
| [getConnectionState](arkts-connectivity-datatransfer-getconnectionstate-f.md) | Obtains the port channel connection state with a remote device. |
| [offConnectionStateChanged](arkts-connectivity-datatransfer-offconnectionstatechanged-f.md) | Unsubscribes from the connection state change event of the port channel. This API uses an asynchronous callback to return the result. |
| [offReadData](arkts-connectivity-datatransfer-offreaddata-f.md) | Unsubscribes from the port channel data receiving event. This API uses an asynchronous callback to return the result. |
| [onConnectionStateChanged](arkts-connectivity-datatransfer-onconnectionstatechanged-f.md) | Subscribes to the connection state change event of the port channel. This API uses an asynchronous callback to return the result. |
| [onReadData](arkts-connectivity-datatransfer-onreaddata-f.md) | Subscribes to the port channel data receiving event. This API uses an asynchronous callback to return the result. |
| [writeData](arkts-connectivity-datatransfer-writedata-f.md) | Sends data to a remote device using the device address and UUID. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [ConnectionParams](arkts-connectivity-datatransfer-connectionparams-i.md) | Defines the parameters for initiating a port connection. |
| [ConnectionResult](arkts-connectivity-datatransfer-connectionresult-i.md) | Represents the result of port connection parameter negotiation with a remote device. |
| [ConnectionStateParams](arkts-connectivity-datatransfer-connectionstateparams-i.md) | Defines the parameters for obtaining the port channel connection state. |
| [DataParams](arkts-connectivity-datatransfer-dataparams-i.md) | Defines the parameters for port data sending and receiving. |

### Enums

| Name | Description |
| --- | --- |
| [TransferMode](arkts-connectivity-datatransfer-transfermode-e.md) | Enumerates the data transfer modes with a remote device. |

### Types

| Name | Description |
| --- | --- |
| [ConnectionState](arkts-connectivity-datatransfer-connectionstate-t.md) | Enumerates the connection states with a remote device. |
