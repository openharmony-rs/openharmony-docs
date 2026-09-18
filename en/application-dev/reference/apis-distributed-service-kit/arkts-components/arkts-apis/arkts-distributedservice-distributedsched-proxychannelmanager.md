# @ohos.distributedsched.proxyChannelManager(Proxy Channel Management)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Instructions

Before calling the APIs of this module, complete the following configurations:

1. You have requested the **ohos.permission.ACCESS_BLUETOOTH** permission. For details about how to configure and apply for permissions, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md) and [Requesting User Authorization](../../../security/AccessToken/request-user-authorization.md).
 2. In the **module.json5** file, you have configured the **action** field **action.ohos.pull.listener** for the phone app process that needs to be started by the proxy module.

The typical calling process is as follows:

1. Call **openProxyChannel** to open the proxy channel and obtain the channel ID.
 2. Call **sendData** to send data, and subscribe to events based on service requirements. Call **on('receiveData')** to receive data from the peer end, and call **on('channelStateChange')** to monitor channel connection state changes (such as disconnection and recovery). You can subscribe to both events at the same time. It is recommended to use them together in data transmission scenarios so that data sending can be paused promptly and disconnection recovery logic can be handled when the channel is abnormal.
 3. After using the event, call **off('receiveData')** or **off('channelStateChange')** to unsubscribe from the event.
 4. Call **closeProxyChannel** to close the proxy channel and release resources.

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md) | Closes an opened proxy channel. This is applicable to scenarios where the phone-side app no longer needs to communicate with the wearable device-side app, such as actively releasing channel resources after completing a data synchronization task. This method must be used in pair with [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). Call this method to close the channel and release resources after use. After the channel is closed, the registered **receiveData** and **channelStateChange** callbacks are automatically unsubscribed, and data being transmitted is interrupted. Failure to close the proxy channel in a timely manner may cause channel resource leakage. |
| [off](arkts-distributedservice-proxychannelmanager-off-f.md#offreceivedata) | Unsubscribes from data receive events and no longer receives data through the callback. This is applicable to scenarios where the phone-side app no longer needs to receive data from the wearable device-side app, such as when the user switches to another functional module. You must call [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) to successfully open a proxy channel before unsubscribing. This method must be used in pair with [on('receiveData')](arkts-distributedservice-proxychannelmanager-on-f.md#onreceivedata) to cancel the data receive callback previously registered through **on('receiveData')**. |
| [off](arkts-distributedservice-proxychannelmanager-off-f.md#offchannelstatechange) | Unsubscribes from channel state events. This is applicable to scenarios where the phone-side app no longer needs to listen for proxy channel connection state changes, such as when the user exits the relevant service page or completes the data transmission process. You must call [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) to successfully open a proxy channel before unsubscribing. This method must be used in pair with [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) to cancel the channel state callback previously registered through **on('channelStateChange')**. |
| [on](arkts-distributedservice-proxychannelmanager-on-f.md#onreceivedata) | Subscribes to data receive events. This API uses an asynchronous callback to return the result. This is applicable to scenarios where the phone-side app needs to continuously receive data reported by the wearable device-side app, such as receiving data from the wearable device-side app. The proxy module receives data from the peer end based on the peer UUID configured when **openProxyChannel** is called, and passes the received wearable device-side app data to the subscriber through the callback. You must call [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) to successfully open a proxy channel before subscribing to data receive events. If you need to proxy-wake the phone-side app process to receive and process peer data, configure the **action** field as **action.ohos.pull.listener** in the **module.json5** file before use. After subscribing, call [off('receiveData')](arkts-distributedservice-proxychannelmanager-off-f.md#offreceivedata) to unsubscribe and prevent the callback from being triggered continuously. |
| [on](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) | Subscribes to channel state events. This API uses an asynchronous callback to return the result. This is applicable to scenarios where the phone-side app needs to monitor the proxy channel connection state in real time, such as pausing data sending after detecting channel disconnection and automatically retrying services after channel recovery. The proxy module monitors Bluetooth BR link state changes in real time, and reports **ChannelStateInfo** through the callback when events such as connection recovery, abnormal disconnection, and pairing relationship deletion occur. You must call [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) to successfully open a proxy channel before subscribing to channel state events. After subscribing, call [off('channelStateChange')](arkts-distributedservice-proxychannelmanager-off-f.md#offchannelstatechange) to unsubscribe and prevent the callback from being triggered continuously. After calling [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md) to close the channel, the registered **channelStateChange** callback is automatically unsubscribed. |
| [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) | Opens a proxy channel. This API uses a promise to return the result. Based on the link type and peer device information configured in **ChannelInfo**, it negotiates with the peer device via the Bluetooth BR protocol to establish a bidirectional data channel and returns a channel ID that uniquely identifies the channel. This is applicable to scenarios where a phone-side app needs to establish a bidirectional data channel with a wearable device-side app, such as message notification forwarding. After calling this method, you must call [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md) to close the channel and release resources when the proxy channel is no longer needed. |
| [sendData](arkts-distributedservice-proxychannelmanager-senddata-f.md) | Sends data to the peer end. This API uses a promise to return the result. This is applicable to scenarios where the phone-side app sends instructions or data to the wearable device-side app through the proxy channel, such as sending configuration updates or notification messages. This method can be called to send data only after [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) successfully opens a proxy channel. When the proxy channel is in an unavailable state (such as [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md). CHANNEL_WAIT_RESUME, CHANNEL_EXCEPTION_SOFTWARE_FAILED, or CHANNEL_BR_NO_PAIRED), calling this method will fail. It is recommended to subscribe to the [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) event to monitor the channel state, pause data sending when the channel is unavailable, and resume sending after the channel recovers. Data is transmitted to the peer device through the established proxy channel via the Bluetooth BR link. The maximum data length is 4096 bytes. Exceeding this limit will return error code 32390103. |

### Interfaces

| Name | Description |
| --- | --- |
| [ChannelInfo](arkts-distributedservice-proxychannelmanager-channelinfo-i.md) | Input parameters of the function for opening a proxy channel, including the link type of the proxy channel, the MAC address of the peer device, and the UUID of the listening service. |
| [ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md) | Represents the connection state information of the proxy channel. |
| [DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md) | Represents the received data information, including the channel ID and data. |

### Enums

| Name | Description |
| --- | --- |
| [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md) | Enumerates the connection states of the proxy channel. |
| [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md) | Enumerates the link types. |
