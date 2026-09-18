# @ohos.net.sharing(Network Sharing)

This module allows you to share your device's network connectivity with other connected devices.

**Since:** 9

**System capability:** SystemCapability.Communication.NetManager.NetSharing

## Modules to Import

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getSharableRegexes](arkts-network-sharing-getsharableregexes-f-sys.md) | Obtains regular expressions of NICs of a specified type. This API uses an asynchronous callback to return the result. |
| [getSharableRegexes](arkts-network-sharing-getsharableregexes-f-sys.md) | Obtains regular expressions of NICs of a specified type. This API uses a promise to return the result. |
| [getSharingIfaces](arkts-network-sharing-getsharingifaces-f-sys.md) | Obtains the names of NICs in the specified network sharing state. This API uses an asynchronous callback to return the result. |
| [getSharingIfaces](arkts-network-sharing-getsharingifaces-f-sys.md) | Obtains the names of NICs in the specified network sharing state. This API uses a promise to return the result. |
| [getSharingState](arkts-network-sharing-getsharingstate-f-sys.md) | Obtains the network sharing state of the specified type. This API uses an asynchronous callback to return the result. |
| [getSharingState](arkts-network-sharing-getsharingstate-f-sys.md) | Obtains the network sharing state of the specified type. This API uses a promise to return the result. |
| [getStatsRxBytes](arkts-network-sharing-getstatsrxbytes-f-sys.md) | Obtains the volume of mobile data traffic received via network sharing. This API uses an asynchronous callback to return the result. |
| [getStatsRxBytes](arkts-network-sharing-getstatsrxbytes-f-sys.md) | Obtains the volume of mobile data traffic received via network sharing. This API uses a promise to return the result. |
| [getStatsTotalBytes](arkts-network-sharing-getstatstotalbytes-f-sys.md) | Obtains the total volume of mobile data traffic sent via network sharing. This API uses an asynchronous callback to return the result. |
| [getStatsTotalBytes](arkts-network-sharing-getstatstotalbytes-f-sys.md) | Obtains the total volume of mobile data traffic sent via network sharing. This API uses a promise to return the result. |
| [getStatsTxBytes](arkts-network-sharing-getstatstxbytes-f-sys.md) | Obtains the volume of mobile data traffic sent via network sharing. This API uses an asynchronous callback to return the result. |
| [getStatsTxBytes](arkts-network-sharing-getstatstxbytes-f-sys.md) | Obtains the volume of mobile data traffic sent via network sharing. This API uses a promise to return the result. |
| [isSharing](arkts-network-sharing-issharing-f-sys.md) | Obtains the current network sharing status. This API uses an asynchronous callback to return the result. |
| [isSharing](arkts-network-sharing-issharing-f-sys.md) | Obtains the current network sharing status. This API uses a promise to return the result. |
| [isSharingSupported](arkts-network-sharing-issharingsupported-f-sys.md) | Checks whether network sharing is supported. This API uses an asynchronous callback to return the result. |
| [isSharingSupported](arkts-network-sharing-issharingsupported-f-sys.md) | Checks whether network sharing is supported. This API uses a promise to return the result. |
| [off](arkts-network-sharing-off-f-sys.md#offsharingstatechange) | Unregisters the network sharing status change event. This method uses an asynchronous callback to return the result. |
| [off](arkts-network-sharing-off-f-sys.md#offinterfacesharingstatechange) | Unsubscribes from network sharing state changes of a specified NIC. This API uses an asynchronous callback to return the result. |
| [off](arkts-network-sharing-off-f-sys.md#offsharingupstreamchange) | Unsubscribes from upstream network changes. This API uses an asynchronous callback to return the result. |
| [on](arkts-network-sharing-on-f-sys.md#onsharingstatechange) | Registers the network sharing status change event. This API uses an asynchronous callback to return the result. |
| [on](arkts-network-sharing-on-f-sys.md#oninterfacesharingstatechange) | Subscribes to network sharing state changes of a specified NIC. This API uses an asynchronous callback to return the result. |
| [on](arkts-network-sharing-on-f-sys.md#onsharingupstreamchange) | Subscribes to upstream network changes. This API uses an asynchronous callback to return the result. |
| [startSharing](arkts-network-sharing-startsharing-f-sys.md) | Enables sharing of a specified type. This API uses an asynchronous callback to return the result. |
| [startSharing](arkts-network-sharing-startsharing-f-sys.md) | Enables sharing of a specified type. This API uses a promise to return the result. |
| [stopSharing](arkts-network-sharing-stopsharing-f-sys.md) | Disables sharing of a specified type. This API uses an asynchronous callback to return the result. |
| [stopSharing](arkts-network-sharing-stopsharing-f-sys.md) | Disables sharing of a specified type. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [InterfaceSharingStateInfo](arkts-network-sharing-interfacesharingstateinfo-i-sys.md) | Wakes up the listener for network sharing state changes of an NIC. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [SharingIfaceState](arkts-network-sharing-sharingifacestate-e-sys.md) | Enumerates the network sharing states of an NIC. |
| [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md) | Enumerates the network sharing types of an NIC. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [NetHandle](arkts-network-sharing-nethandle-t.md) | Defines the handle of the data network. Before calling the **NetHandle** function, call the **getNetHandle** function to obtain a **NetHandle** object. |
