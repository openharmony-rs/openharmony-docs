# @ohos.nearlink.remoteDevice(NearLink Remote Device Connection Capability)

This module provides the capabilities of connecting to and managing NearLink remote devices, including connecting to and disconnecting from remote devices, pairing with a trusted device and confirmation, adjusting the connection interval, and subscribing to pairing requests.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createRemoteDevice](arkts-connectivity-remotedevice-createremotedevice-f.md) | Creates a **RemoteDevice** instance. |
| [offAcbStateChange](arkts-connectivity-remotedevice-offacbstatechange-f.md) | Unsubscribes from the logical link connection status change event. This API uses an asynchronous callback to return the result. |
| [offConnectionStateChange](arkts-connectivity-remotedevice-offconnectionstatechange-f.md) | Unsubscribes from the connection status change event. This API uses an asynchronous callback to return the result. |
| [offPairingStateChange](arkts-connectivity-remotedevice-offpairingstatechange-f.md) | Unsubscribes from pairing status change events. This API uses an asynchronous callback to return the result. |
| [onAcbStateChange](arkts-connectivity-remotedevice-onacbstatechange-f.md) | Subscribes to the logical link connection status change event. This API uses an asynchronous callback to return the result. This API is applicable when corresponding processing needs to be triggered when a logical link is established or disconnected, for example, checking whether the link is ready before data transfer or clearing resources after disconnection. Unlike [remoteDevice.onConnectionStateChange](arkts-connectivity-remotedevice-onconnectionstatechange-f.md) which listens for the connection status change at the device level, this API listens for the connection status change at the logical link level. |
| [onConnectionStateChange](arkts-connectivity-remotedevice-onconnectionstatechange-f.md) | Subscribes to the connection status change event. This API uses an asynchronous callback to return the result. Unlike [remoteDevice.onAcbStateChange](arkts-connectivity-remotedevice-onacbstatechange-f.md) which listens for the connection status change at the logical link level, this API listens for the connection status change at the device level. |
| [onPairingStateChange](arkts-connectivity-remotedevice-onpairingstatechange-f.md) | Subscribes to pairing status change events. This API uses an asynchronous callback to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [offPairingRequest](arkts-connectivity-remotedevice-offpairingrequest-f-sys.md) | Unsubscribes from pairing request events from remote NearLink devices. |
| [onPairingRequest](arkts-connectivity-remotedevice-onpairingrequest-f-sys.md) | Subscribes to pairing request events from remote NearLink devices. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AcbStateParam](arkts-connectivity-remotedevice-acbstateparam-i.md) | Represents the result of the logical link connection status change event. |
| [ConnectionStateParam](arkts-connectivity-remotedevice-connectionstateparam-i.md) | Describes the connection state parameters. |
| [DeviceInformation](arkts-connectivity-remotedevice-deviceinformation-i.md) | Describes the remote device information. |
| [PairingRequestParam](arkts-connectivity-remotedevice-pairingrequestparam-i.md) | Describes pairing request parameters. |
| [PairingStateParam](arkts-connectivity-remotedevice-pairingstateparam-i.md) | Describes the pairing state parameters. |
| [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i.md) | Provides the method for operating on a remote device. Before using this method, you need to call [remoteDevice.createRemoteDevice](arkts-connectivity-remotedevice-createremotedevice-f.md) to create a [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i.md) instance. You need to create only one instance for a device. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DeviceModel](arkts-connectivity-remotedevice-devicemodel-i-sys.md) | Describes the model of a remote device. |
| [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i-sys.md) | Provides the method for operating on a remote device. Before using this method, you need to call [remoteDevice.createRemoteDevice](arkts-connectivity-remotedevice-createremotedevice-f.md) to create a [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i.md) instance. You need to create only one instance for a device. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ConnectionReason](arkts-connectivity-remotedevice-connectionreason-e.md) | Enum for the connection reason. |
| [PairingReason](arkts-connectivity-remotedevice-pairingreason-e.md) | Enum for the pairing reason. |
| [PairingType](arkts-connectivity-remotedevice-pairingtype-e.md) | Enumerates the NearLink pairing types. |

### Types

| Name | Description |
| --- | --- |
| [AcbState](arkts-connectivity-remotedevice-acbstate-t.md) | Enumerates the logical link connection states with a remote device. |
| [ConnectionState](arkts-connectivity-remotedevice-connectionstate-t.md) | Enumerates the connection states with a remote device. |
| [DeviceClass](arkts-connectivity-remotedevice-deviceclass-t.md) | Enumerates the device types. |
| [PairingState](arkts-connectivity-remotedevice-pairingstate-t.md) | Enumerates the pairing statuses with a remote device. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [ConnectionInterval](arkts-connectivity-remotedevice-connectioninterval-t-sys.md) | Enumerates the connection intervals. |
<!--DelEnd-->
