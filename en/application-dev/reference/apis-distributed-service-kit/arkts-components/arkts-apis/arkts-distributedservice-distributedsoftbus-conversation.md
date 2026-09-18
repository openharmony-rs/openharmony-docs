# @ohos.distributedSoftBus.conversation(Cross-Device Wakeup and Message Transfer)

The DSoftBus module **conversation** provides APIs for cross-device interaction of apps, including obtaining the trusted device list, and sending and receiving session data. With this module, your app can obtain trusted devices under the same account, register a listener to receive cross-device data, and send data to a specified device through a session channel. This module is applicable to scenarios that require cross-device collaboration and multi-device data transfer, simplifying the development of cross-device interaction.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getTrustedDevices](arkts-distributedservice-conversation-gettrusteddevices-f-sys.md) | Obtains the list of historical trusted devices. Typical use scenarios include querying available target devices before sending data across devices. |
| [postConversationData](arkts-distributedservice-conversation-postconversationdata-f-sys.md) | Sends session data to the target device. The target device must be a trusted device under the same account. The network ID or UDID of the target device is used for device addressing. Data is sent to the app with the registered listener on the target device based on the specified bundle name and ability name. Typical use scenarios include sending collaboration commands across devices. |
| [registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md) | Registers a listener to receive data from trusted devices under the same account. When the remote device sends data to the local device by calling [postConversationData](arkts-distributedservice-conversation-postconversationdata-f-sys.md), the data is distributed to the registered callback based on the specified bundle name and ability name. Only one listener can be registered for the same bundle name and ability name. Duplicate registration will overwrite the previously registered listener. |
| [unregisterConversationListener](arkts-distributedservice-conversation-unregisterconversationlistener-f-sys.md) | Unregisters the listener with the specified bundle name and ability name. This API must be used in pairs with [registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md) to unregister a registered listener. When the listener is no longer needed, call this API to unregister the listener to release resources. If the listener is not unregistered, resources will be continuously occupied. Only one listener can be registered for the same bundle name and ability name. Duplicate registration will overwrite the previously registered listener. After the listener is unregistered, the listener that is currently in effect will be removed. After this API is called, the app will no longer receive session data of the specified bundle name and ability name. If no listener has been registered for the specified bundle name and ability name, this API returns a success message. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DeviceNodeInfo](arkts-distributedservice-conversation-devicenodeinfo-i-sys.md) | Defines the device node information, including the network ID, device name, device type ID, near-field status, and UDID. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [DataCallback](arkts-distributedservice-conversation-datacallback-t-sys.md) | Defines a callback for receiving data. |
<!--DelEnd-->
