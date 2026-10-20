# @ohos.nearlink.dataTransfer(NearLink Data Transfer Capability)

This module provides the NearLink data transfer capability, including port channel management, connection management, data sending and receiving, and connection status query and subscription.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace dataTransfer--><!--Device-unnamed-declare namespace dataTransfer-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [connect](arkts-connectivity-datatransfer-connect-f.md#connect) | Connects to a remote device. This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [createPort](arkts-connectivity-datatransfer-createport-f.md#createport) | Registers a port channel. A port channel can be used to connect to a remote device only after being registered. If the port channel is no longer needed after use, call [dataTransfer.destroyPort](arkts-connectivity-datatransfer-destroyport-f.md) to destroy it. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [destroyPort](arkts-connectivity-datatransfer-destroyport-f.md#destroyport) | Destroys the port channel. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [disconnect](arkts-connectivity-datatransfer-disconnect-f.md#disconnect) | Disconnects from the remote device. This method is called to disconnect from the remote device after it is successfully connected using [dataTransfer.connect](arkts-connectivity-datatransfer-connect-f.md). This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [getConnectionState](arkts-connectivity-datatransfer-getconnectionstate-f.md#getconnectionstate) | Obtains the port channel connection state with a remote device. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [offConnectionStateChanged](arkts-connectivity-datatransfer-offconnectionstatechanged-f.md#offconnectionstatechanged) | Unsubscribes from the connection state change event of the port channel. This API uses an asynchronous callback to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [offReadData](arkts-connectivity-datatransfer-offreaddata-f.md#offreaddata) | Unsubscribes from the port channel data receiving event. This API uses an asynchronous callback to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [onConnectionStateChanged](arkts-connectivity-datatransfer-onconnectionstatechanged-f.md#onconnectionstatechanged) | Subscribes to the connection state change event of the port channel. This API uses an asynchronous callback to return the result. |
| [onReadData](arkts-connectivity-datatransfer-onreaddata-f.md#onreaddata) | Subscribes to the port channel data receiving event. This API uses an asynchronous callback to return the result. |
| [writeData](arkts-connectivity-datatransfer-writedata-f.md#writedata) | Sends data to a remote device using the device address and UUID. This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |

### Interfaces

| Name | Description |
| --- | --- |
| [ConnectionParams](arkts-connectivity-datatransfer-connectionparams-i.md) | Defines the parameters for initiating a port connection. |
| [ConnectionResult](arkts-connectivity-datatransfer-connectionresult-i.md) | Represents the result of port connection parameter negotiation with a remote device. |
| [ConnectionStateParams](arkts-connectivity-datatransfer-connectionstateparams-i.md) | Defines the parameters for obtaining the port channel connection state. |
| [DataParams](arkts-connectivity-datatransfer-dataparams-i.md) | Defines the parameters for port data sending and receiving. |

### Types

| Name | Description |
| --- | --- |
| [ConnectionState](arkts-connectivity-datatransfer-connectionstate-t.md) | Enumerates the connection states with a remote device. |

### Enums

| Name | Description |
| --- | --- |
| [TransferMode](arkts-connectivity-datatransfer-transfermode-e.md) | Enumerates the data transfer modes with a remote device. |
