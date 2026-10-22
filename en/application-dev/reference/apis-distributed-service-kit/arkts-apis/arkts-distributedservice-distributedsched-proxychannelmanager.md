# @ohos.distributedsched.proxyChannelManager(Proxy Channel Management)

DSoftBus provides stable and reliable underlying channels for cross-device communication. This module is developed based on DSoftBus. It supports data exchange between phones and wearables, providing users with a seamless device interconnection experience. It also simplifies cross-device communication for developers, eliminating the need to handle underlying communication protocols and process wakeup logic. Use scenarios: During collaboration between the phone app and wearable app, if the phone app is not running in the foreground, its downlink messages are forwarded to the notification server and then sent to the wearable through the proxy module. When the wearable sends data to the phone, the proxy module can dynamically wake up the corresponding app process on the phone to receive and process the data. The core functions of this module include proxy channel management, data route management, application state awareness and wakeup, and link state monitoring.

- Proxy channel management: Manages bidirectional data channels established between phones and wearables via the  
Bluetooth Basic Rate (BR) protocol. This ensures reliable cross-device data communication without the need to implement the underlying communication protocol. The supported data channel IDs range from 1 to 2147483647.  
- Data route management: Accurately forwards data of wearables based on the specified service UUID. This accurately  
routes data to the target service port, preventing data loss or incorrect data transmission. The UUID uniquely identifies the service listened for the peer device. The proxy module routes data to the corresponding service port based on the UUID of the peer device.  
- Application state awareness and wakeup: After a proxy channel is enabled and data sent by the wearable is received,  
the proxy module identifies the target app based on the **action** field (for example, **action.ohos.pull.listener**) configured in the **module.json5** file, and starts the corresponding app process on the phone to process the data. This allows the app to receive data without having to stay in the foreground, thereby saving system resources.  
- Link state monitoring: Monitors the connection status changes of the proxy channel throughout its lifecycle in real  
time through callbacks. This helps the phone app respond to connection exceptions in a timely manner and adjust service policies, thereby improving data transmission reliability. Connection exceptions include connection restoration, abnormal disconnection, and pairing relationship deletion.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace proxyChannelManager--><!--Device-unnamed-declare namespace proxyChannelManager-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Instructions

Before calling the APIs of this module, complete the following configurations:

1. You have requested the **ohos.permission.ACCESS_BLUETOOTH** permission. For details about how to configure and
apply for permissions, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md) and [Requesting User Authorization](../../../security/AccessToken/request-user-authorization.md).
2. In the **module.json5** file, you have configured the **action** field **action.ohos.pull.listener** for the
phone app process that needs to be started by the proxy module.

The typical calling process is as follows:

1. Call **openProxyChannel** to open the proxy channel and obtain the channel ID.
2. Call **sendData** to send data, and subscribe to events based on service requirements. Call **on('receiveData')**
to receive data from the peer end, and call **on('channelStateChange')** to monitor channel connection state changes (such as disconnection and recovery). You can subscribe to both events at the same time. You are advised to use them together in data transmission scenarios so that data sending can be paused promptly and disconnection recovery logic can be handled when the channel is abnormal.
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
| [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md#closeproxychannel-1) | Closes a proxy channel that has been opened. This method is applicable to scenarios where the mobile app no longer needs to communicate with the wearable app, for example, when the channel resources need to be released after a data synchronization task is complete. This method must be used together with [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). After using the proxy channel, call this method to close the channel and release resources. After the channel is closed, the registered **receiveData** and **channelStateChange** callbacks will be automatically unregistered, and the data that is being transmitted will be interrupted. If the proxy channel is not closed in a timely manner, a channel resource leak may occur. |
| [off('receiveData')](arkts-distributedservice-proxychannelmanager-off-f.md#offreceivedata) | Unsubscribes from data receiving events. Data will no longer be received through a callback. This method is applicable when the phone app no longer needs to receive data from the wearable app, for example, when the user switches to another function module. You can unsubscribe from data receiving events only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). This method must be used together with [on('receiveData')](arkts-distributedservice-proxychannelmanager-on-f.md#onreceivedata) to unregister the data receiving callback registered using **on('receiveData')**. |
| [off('channelStateChange')](arkts-distributedservice-proxychannelmanager-off-f.md#offchannelstatechange) | Unsubscribes from channel state change events. This method is applicable when the phone app no longer needs to listen for the proxy channel connection state change events, for example, when the user exits the related service page or the data transmission process is completed. You can unsubscribe from data receiving events only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). This method must be used together with [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) to unregister the channel state change callback registered using **on('channelStateChange')**. |
| [on('receiveData')](arkts-distributedservice-proxychannelmanager-on-f.md#onreceivedata) | Subscribes to data receiving events. This API uses an asynchronous callback to return the result. This method is applicable when the phone app needs to continuously receive data reported by the wearable app, for example, receiving the wearable app data. The proxy module receives data from the peer device based on the peer UUID configured when **openProxyChannel** is called, and transfers the received wearable app data to the subscriber through a callback. You can subscribe to data receiving events only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). To enable the proxy channel to wake up the phone app process to receive and process data from the peer device, set the **action** field to **action.ohos.pull.listener** in the **module.json5** file. After the subscription, call [off('receiveData')](arkts-distributedservice-proxychannelmanager-off-f.md#offreceivedata) to cancel the subscription to prevent the callback from being continuously triggered. |
| [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) | Subscribes to channel state change events. This API uses an asynchronous callback to return the result. This method is applicable to scenarios where the phone app needs to detect the proxy channel connection state in real time. For example, the app can pause data transmission after the channel is disconnected and automatically retry services after the channel is reconnected. The proxy module monitors the BR link status in real time. When an event such as connection restoration, abnormal disconnection, or pairing relationship deletion occurs, the proxy module reports **ChannelStateInfo** using a callback. You can subscribe to channel state change events only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). After the subscription, call [off('channelStateChange')](arkts-distributedservice-proxychannelmanager-off-f.md#offchannelstatechange) to cancel the subscription to prevent the callback from being continuously triggered. After the channel is closed by calling [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md), the registered **channelStateChange** callback will be automatically unsubscribed from. |
| [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md#openproxychannel-1) | Opens a proxy channel. This API uses a promise to return the result. Based on the link type and peer device information configured in **ChannelInfo**, it negotiates with the peer device via the Bluetooth BR protocol to establish a bidirectional data channel and returns a channel ID that uniquely identifies the channel. This is applicable to scenarios where a phone-side app needs to establish a bidirectional data channel with a wearable device-side app, such as message notification forwarding. After calling this method, you must call [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md) to close the channel and release resources when the proxy channel is no longer needed. |
| [sendData](arkts-distributedservice-proxychannelmanager-senddata-f.md#senddata-1) | Sends data to the peer end. This API uses a promise to return the result. This method is applicable to scenarios where a phone app sends instructions or data to a wearable app through the proxy channel, for example, sending configuration updates and notifications. This method can be called to send data only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). This method will fail to be called if the proxy channel is unavailable (for example, in the [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md).CHANNEL_WAIT_RESUME, **CHANNEL_EXCEPTION_SOFTWARE_FAILED**, or **CHANNEL_BR_NO_PAIRED** state). You are advised to subscribe to the [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) event to monitor the channel status. When the channel is unavailable, suspend data transmission. When the channel recovers, resume data transmission. Data is transmitted to the peer device through the established proxy channel over the BR link. The maximum data length is 4096 bytes. If the data length exceeds 4096 bytes, error code 32390103 will be returned. |

### Interfaces

| Name | Description |
| --- | --- |
| [ChannelInfo](arkts-distributedservice-proxychannelmanager-channelinfo-i.md) | Represents the proxy channel information, including the link type of the proxy channel, MAC address of the peer device, and service UUID. |
| [ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md) | Represents the connection state information of the proxy channel. |
| [DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md) | Represents the received data, including the channel ID and data. |

### Enums

| Name | Description |
| --- | --- |
| [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md) | Enumerates the connection states of the proxy channel. |
| [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md) | Enumerates the link types. |
