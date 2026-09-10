# @ohos.distributedsched.proxyChannelManager (Proxy Channel Management)

<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @jzy_123-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=6bfcf5261eb2f83e0869ab9ec15c9d0a1edd6edd translatedAt=2026-08-04T03:18:45.226Z pushedAt=2026-08-10T09:31:58.457Z -->

DSoftBus provides stable and reliable underlying channels for cross-device communication. This module is developed based on DSoftBus. It supports data exchange between phones and wearables, providing users with a seamless device interconnection experience. It also simplifies cross-device communication for developers, eliminating the need to handle underlying communication protocols and process wakeup logic. Use scenarios: During collaboration between the phone app and wearable app, if the phone app is not running in the foreground, its downlink messages are forwarded to the notification server and then sent to the wearable through the proxy module. When the wearable sends data to the phone, the proxy module can dynamically wake up the corresponding app process on the phone to receive and process the data. The core functions of this module include proxy channel management, data route management, application state awareness and wakeup, and link state monitoring.

- Proxy channel management: Manages bidirectional data channels established between phones and wearables via the Bluetooth Basic Rate (BR) protocol. This ensures reliable cross-device data communication without the need to implement the underlying communication protocol. The supported data channel IDs range from 1 to 2147483647.

- Data route management: Accurately forwards data of wearables based on the specified service UUID. This accurately routes data to the target service port, preventing data loss or incorrect data transmission. The UUID uniquely identifies the service listened for the peer device. The proxy module routes data to the corresponding service port based on the UUID of the peer device.

- Application state awareness and wakeup: After a proxy channel is enabled and data sent by the wearable is received, the proxy module identifies the target app based on the **action** field (for example, **action.ohos.pull.listener**) configured in the **module.json5** file, and starts the corresponding app process on the phone to process the data. This allows the app to receive data without having to stay in the foreground, thereby saving system resources.

- Link state monitoring: Monitors the connection status changes of the proxy channel throughout its lifecycle in real time through callbacks. This helps the phone app respond to connection exceptions in a timely manner and adjust service policies, thereby improving data transmission reliability. Connection exceptions include connection restoration, abnormal disconnection, and pairing relationship deletion.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> **Model restriction**: This API can be used only in the stage model.

## Modules to Import

```js
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## Instructions

Before calling the APIs of this module, complete the following configurations:

1. You have requested the **ohos.permission.ACCESS_BLUETOOTH** permission. For details about how to configure and apply for permissions, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md) and [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).

2. In the **module.json5** file, you have configured the **action** field **action.ohos.pull.listener** for the phone app process that needs to be started by the proxy module.

The typical calling process is as follows:

1. Call **openProxyChannel** to open the proxy channel and obtain the channel ID.

2. Call **sendData** to send data, and subscribe to events based on service requirements. Call **on('receiveData')** to receive data from the peer end, and call **on('channelStateChange')** to monitor channel connection state changes (such as disconnection and recovery). You can subscribe to both events at the same time. You are advised to use them together in data transmission scenarios so that data sending can be paused promptly and disconnection recovery logic can be handled when the channel is abnormal.

3. After using the event, call **off('receiveData')** or **off('channelStateChange')** to unsubscribe from the event.

4. Call **closeProxyChannel** to close the proxy channel and release resources.

## proxyChannelManager.openProxyChannel

openProxyChannel(channelInfo:&nbsp;ChannelInfo):&nbsp;Promise&lt;number&gt;

Opens a proxy channel. This API uses a promise to return the result. A bidirectional data channel is established with the peer device through the BR protocol negotiation based on the link type and peer device information configured in **ChannelInfo**, and the unique ID of the channel (**channelId**) is returned. This method is applicable to scenarios where a bidirectional data channel needs to be established between an app on the phone and an app on the wearable, for example, message notification forwarding. After calling this method, you must call [closeProxyChannel](#proxychannelmanagercloseproxychannel) to close the proxy channel when it is no longer needed to release resources.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called on phones and tablets. If this API is called on other devices that support distributed services, error code 32390101 will be returned. If it is called on wearables that do not support distributed services, error code 801 will be returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| channelInfo | [ChannelInfo](#channelinfo) | Yes | Proxy channel information, including the link type, MAC address of the peer device, and service UUID of the peer device. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| &nbsp;Promise&lt;number&gt; | Promise used to return the result. If the proxy channel is successfully opened, the return value of **resolve** is the channel ID, and value range is [1, 2147483647]. The lifecycle of the channel ID is the same as that of the proxy channel. If the proxy channel is not closed, the same input parameter will return the same channel ID. If the proxy channel fails to be opened, the return value of **reject** is an error message. For details about the error codes, see the error code table. |

**Error codes**

For details about the following error codes, see [Proxy Channel Management Error Codes](errorcode-proxyChannelManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 801      | Capability not supported because bluetooth proxy function has been trimmed.<br>Applicable versions: 26.0.0+|
| 32390001      | BR is disabled.|
| 32390002 | Device not paired.  |
| 32390006 | Parameter error.|
| 32390100 | Internal error.|
| 32390101 | Call is restricted.|
| 32390102 | Operation failed or Connection timed out.|

**Example**

```ts
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('Test')
        .onClick(() => {
          let channelInfo: proxyChannelManager.ChannelInfo = {
            linkType: proxyChannelManager.LinkType.LINK_BR,
            peerDevAddr: 'xx:xx:xx:xx:xx:xx', // Bluetooth MAC address of the wearable
            peerUuid: 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx', // Service UUID of the peer device
          };
          // The following sample code uses try/catch as an example.
          try {
            proxyChannelManager.openProxyChannel(channelInfo)
              .then((channelId: number) => {
                // Obtain the channel ID.
              })
              .catch((error: BusinessError) => {
                console.error(`Failed to open proxy channel. Code: ${error.code}, message: ${error.message}`);
              });
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to open proxy channel. Code: ${error.code}, message: ${error.message}`);
            // If the returned error.code is undefined and error.message is "Cannot read property openProxyChannel of undefined", this API is not supported in the current image.
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## proxyChannelManager.closeProxyChannel

closeProxyChannel(channelId:&nbsp;number):&nbsp;void

Closes a proxy channel that has been opened. This method is applicable to scenarios where the mobile app no longer needs to communicate with the wearable app, for example, when the channel resources need to be released after a data synchronization task is complete. This method must be used together with [openProxyChannel](#proxychannelmanageropenproxychannel). After using the proxy channel, call this method to close the channel and release resources. After the channel is closed, the registered **receiveData** and **channelStateChange** callbacks will be automatically unregistered, and the data that is being transmitted will be interrupted. If the proxy channel is not closed in a timely manner, a channel resource leak may occur.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called on phones and tablets. If this API is called on other devices that support distributed services, error code 32390006 will be returned. If it is called on wearables that do not support distributed services, error code 801 will be returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable.  |

**Error codes**

For details about the following error codes, see [Proxy Channel Management Error Codes](errorcode-proxyChannelManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 801      | Capability not supported because bluetooth proxy function has been trimmed.<br>Applicable versions: 26.0.0+|
| 32390004 | ChannelId is invalid or unavailable.|
| 32390006 | Parameter error.|
| 32390100 | Internal error.|
| 32390101 | Call is restricted.|

**Example**

```ts
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('Test')
        .onClick(() => {
          // The following sample code uses try/catch as an example.
          try {
            proxyChannelManager.closeProxyChannel(channelId); // Obtain channelId from the promise returned by openProxyChannel.
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to close proxy channel. Code: ${error.code}, message: ${error.message}`);
            // If error.code is undefined and error.message is "Cannot read property closeProxyChannel of undefined", this API is not supported in the current image.
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## proxyChannelManager.sendData

sendData(channelId:&nbsp;number, data:&nbsp;ArrayBuffer):&nbsp;Promise&lt;void&gt;

Sends data to the peer end. This API uses a promise to return the result. This method is applicable to scenarios where a phone app sends instructions or data to a wearable app through the proxy channel, for example, sending configuration updates and notifications. This method can be called to send data only after the proxy channel is successfully opened by calling [openProxyChannel](#proxychannelmanageropenproxychannel). This method will fail to be called if the proxy channel is unavailable (for example, in the [ChannelState](#channelstate).CHANNEL_WAIT_RESUME, **CHANNEL_EXCEPTION_SOFTWARE_FAILED**, or **CHANNEL_BR_NO_PAIRED** state). You are advised to subscribe to the [on('channelStateChange')](#proxychannelmanageronchannelstatechange) event to monitor the channel status. When the channel is unavailable, suspend data transmission. When the channel recovers, resume data transmission. Data is transmitted to the peer device through the established proxy channel over the BR link. The maximum data length is 4096 bytes. If the data length exceeds 4096 bytes, error code 32390103 will be returned.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called on phones and tablets. If this API is called on other devices that support distributed services, error code 32390006 will be returned. If it is called on wearables that do not support distributed services, error code 801 will be returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable.  |
| data      | ArrayBuffer | Yes | Binary data sent to the peer device. The data format is defined by the app layer. The maximum length is 4096 bytes. If the length exceeds the upper limit, error code 32390103 is returned. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| &nbsp;Promise&lt;void&gt; | Promise that returns no value. If the data is sent successfully, **resolve** returns a value. If the data fails to be sent, **reject** returns an error message. |

**Error codes**

For details about the following error codes, see [Proxy Channel Management Error Codes](errorcode-proxyChannelManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 801      | Capability not supported because bluetooth proxy function has been trimmed.<br>Applicable versions: 26.0.0+|
| 32390004 | ChannelId is invalid or unavailable.|
| 32390006 | Parameter error.|
| 32390100 | Internal error.|
| 32390101 | Call is restricted.|
| 32390103 | Data too long.|
| 32390104 | Send failed.|

**Example**

```ts
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('Test')
        .onClick(() => {
          const data = new ArrayBuffer(10); // Create an ArrayBuffer with a length of 10.
          try {
            proxyChannelManager.sendData(channelId, data) // Obtain channelId from the promise returned by openProxyChannel.
              .then(() => {
              })
              .catch((error: BusinessError) => {
                console.error(`Failed to send data. Code: ${error.code}, message: ${error.message}`);
              });
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to send data. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## proxyChannelManager.on('receiveData')

on(type:&nbsp;'receiveData', channelId:&nbsp;number, callback:&nbsp;Callback&lt;DataInfo&gt;):&nbsp;void

Subscribes to data receiving events. This API uses an asynchronous callback to return the result. This method is applicable when the phone app needs to continuously receive data reported by the wearable app, for example, receiving the wearable app data. The proxy module receives data from the peer device based on the peer UUID configured when **openProxyChannel** is called, and transfers the received wearable app data to the subscriber through a callback. You can subscribe to data receiving events only after the proxy channel is successfully opened by calling [openProxyChannel](#proxychannelmanageropenproxychannel). To enable the proxy channel to wake up the phone app process to receive and process data from the peer device, set the **action** field to **action.ohos.pull.listener** in the **module.json5** file. After the subscription, call [off('receiveData')](#proxychannelmanageroffreceivedata) to cancel the subscription to prevent the callback from being continuously triggered.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called on phones and tablets. If this API is called on other devices that support distributed services, error code 32390004 will be returned. If it is called on wearables that do not support distributed services, no error code or exception will be returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type      | string | Yes| Event type. The value **receiveData** indicates the data receiving event.|
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable.  |
| callback | Callback&lt;[DataInfo](#datainfo)&gt; | Yes | Callback used to receive data from the proxy channel. The callback parameter is a [DataInfo](#datainfo) object, which contains the **channelId** (channel ID) and **data** (received data, in bytes) fields. You can receive data only after the proxy channel is opened by calling **openProxyChannel**. If the callback function is registered multiple times, only the last registered one takes effect. |

**Error codes**

For details about the following error codes, see [Proxy Channel Management Error Codes](errorcode-proxyChannelManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 32390004 | ChannelId is invalid or unavailable.|
| 32390006 | Parameter error.|
| 32390100 | Internal error.|
| 32390101 | Call is restricted.|

**Example**

```ts
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('Test')
        .onClick(() => {
          const receiveDataCallback = (dataInfo: proxyChannelManager.DataInfo) => {
          };
          try {
            proxyChannelManager.on('receiveData', channelId, receiveDataCallback); // Obtain channelId from the promise returned by openProxyChannel.
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to register receiveData callback. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## proxyChannelManager.off('receiveData')

off(type:&nbsp;'receiveData', channelId:&nbsp;number, callback?:&nbsp;Callback&lt;DataInfo&gt;):&nbsp;void

Unsubscribes from data receiving events. Data will no longer be received through a callback. This method is applicable when the phone app no longer needs to receive data from the wearable app, for example, when the user switches to another function module. You can unsubscribe from data receiving events only after the proxy channel is successfully opened by calling [openProxyChannel](#proxychannelmanageropenproxychannel). This method must be used together with [on('receiveData')](#proxychannelmanageronreceivedata) to unregister the data receiving callback registered using **on('receiveData')**.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called on phones and tablets. If this API is called on other devices that support distributed services, error code 32390004 will be returned. If it is called on wearables that do not support distributed services, no error code or exception will be returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type      | string | Yes| Event type. The value **receiveData** indicates the data receiving event.|
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable.  |
| callback | Callback&lt;[DataInfo](#datainfo)&gt; | No | Registered callback. If this parameter is not passed, all data receiving events are unsubscribed from. This parameter is not passed by default. The callback last registered using **on** needs to be passed to unsubscribe from the data receiving events. If any other callback function is passed, the unsubscription will fail. |

**Error codes**

For details about the following error codes, see [Proxy Channel Management Error Codes](errorcode-proxyChannelManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 32390004 | ChannelId is invalid or unavailable.|
| 32390006 | Parameter error.|
| 32390100 | Internal error.|
| 32390101 | Call is restricted.|

**Example**

```ts
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('Test')
        .onClick(() => {
          try {
            proxyChannelManager.off('receiveData', channelId); // Obtain channelId from the promise returned by openProxyChannel.
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to unregister receiveData callback. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## proxyChannelManager.on('channelStateChange')

on(type:&nbsp;'channelStateChange', channelId:&nbsp;number, callback:&nbsp;Callback&lt;ChannelStateInfo&gt;):&nbsp;void

Subscribes to channel state change events. This API uses an asynchronous callback to return the result. This method is applicable to scenarios where the phone app needs to detect the proxy channel connection state in real time. For example, the app can pause data transmission after the channel is disconnected and automatically retry services after the channel is reconnected. The proxy module monitors the BR link status in real time. When an event such as connection restoration, abnormal disconnection, or pairing relationship deletion occurs, the proxy module reports **ChannelStateInfo** using a callback. You can subscribe to channel state change events only after the proxy channel is successfully opened by calling [openProxyChannel](#proxychannelmanageropenproxychannel). After the subscription, call [off('channelStateChange')](#proxychannelmanageroffchannelstatechange) to cancel the subscription to prevent the callback from being continuously triggered. After the channel is closed by calling [closeProxyChannel](#proxychannelmanagercloseproxychannel), the registered **channelStateChange** callback will be automatically unsubscribed from.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called on phones and tablets. If this API is called on other devices that support distributed services, error code 32390004 will be returned. If it is called on wearables that do not support distributed services, no error code or exception will be returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type      | string | Yes| Event type. The value **channelStateChange** indicates the channel state change event. |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable.  |
| callback | Callback&lt;[ChannelStateInfo](#channelstateinfo)&gt; | Yes | Callback used to receive the proxy channel state change information. The callback parameter is a [ChannelStateInfo](#channelstateinfo) object, which contains the **channelId** (channel ID) and **state** (channel connection status) fields. You can receive the channel state information only after the proxy channel is opened by calling **openProxyChannel**. If the callback function is registered for multiple times, only the last registered callback function takes effect. |

**Error codes**

For details about the following error codes, see [Proxy Channel Management Error Codes](errorcode-proxyChannelManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 32390004 | ChannelId is invalid or unavailable.|
| 32390006 | Parameter error.|
| 32390100 | Internal error.|
| 32390101 | Call is restricted.|

**Example**

```ts
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('Test')
        .onClick(() => {
          const channelStateChangeCallback = (channelStateInfo: proxyChannelManager.ChannelStateInfo) => {
          };
          try {
            proxyChannelManager.on('channelStateChange', channelId, channelStateChangeCallback); // Obtain channelId from the promise returned by openProxyChannel.
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to register channelStateChange callback. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## proxyChannelManager.off('channelStateChange')

off(type:&nbsp;'channelStateChange', channelId:&nbsp;number, callback?:&nbsp;Callback&lt;ChannelStateInfo&gt;):&nbsp;void

Unsubscribes from channel state change events. This method is applicable when the phone app no longer needs to listen for the proxy channel connection state change events, for example, when the user exits the related service page or the data transmission process is completed. You can unsubscribe from data receiving events only after the proxy channel is successfully opened by calling [openProxyChannel](#proxychannelmanageropenproxychannel). This method must be used together with [on('channelStateChange')](#proxychannelmanageronchannelstatechange) to unregister the channel state change callback registered using **on('channelStateChange')**.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called on phones and tablets. If this API is called on other devices that support distributed services, error code 32390004 will be returned. If it is called on wearables that do not support distributed services, no error code or exception will be returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type      | string | Yes| Event type. The value **channelStateChange** indicates the channel state change event. |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable.  |
| callback | Callback&lt;[ChannelStateInfo](#channelstateinfo)&gt; | No | Registered callback. If this parameter is not passed, all channel state events are unsubscribed from. This parameter is not passed by default. The callback last registered using **on** needs to be passed to unsubscribe from the channel state events. If any other callback function is passed, the unsubscription will fail. |

**Error codes**

For details about the following error codes, see [Proxy Channel Management Error Codes](errorcode-proxyChannelManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 32390004 | ChannelId is invalid or unavailable.|
| 32390006 | Parameter error.|
| 32390100 | Internal error.|
| 32390101 | Call is restricted.|

**Example**

```ts
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('Test')
        .onClick(() => {
          try {
            proxyChannelManager.off('channelStateChange', channelId); // Obtain channelId from the promise returned by openProxyChannel.
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to unregister channelStateChange callback. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## DataInfo

Represents the received data, including the channel ID and data.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type                                      | Read-Only  | Optional  | Description      |
| --------- | ---------------------------------------- | ---- | ---- | -------- |
| channelId | number | No | No | Proxy channel ID. The value ranges from 1 to 2147483647. |
| data | ArrayBuffer | No | No | Received data, in bytes. The maximum value is **4096**. |

## ChannelInfo

Represents the proxy channel information, including the link type of the proxy channel, MAC address of the peer device, and service UUID.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type                                      | Read-Only  | Optional  | Description      |
| --------- | ---------------------------------------- | ---- | ---- | -------- |
| linkType | [LinkType](#linktype) | No | No | Link type of the proxy channel. For details about the value range, see [LinkType](#linktype). Currently, only **LINK_BR** (BR protocol) is supported. |
| peerDevAddr | string | No | No | MAC address of the peer device, in the format of **XX:XX:XX:XX:XX:XX**, where **XX** is a hexadecimal character (0 to 9, A to F, or a to f). The peer device must have been paired. If not, error code 32390002 will be returned. If the format does not meet requirements, error code 32390006 will be returned. |
| peerUuid | string | No | No | Service UUID of the peer device. The value is a standard UUID string, for example, **xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx**. If the format does not meet requirements, error code 32390006 will be returned. |

## ChannelStateInfo

Represents the connection state information of the proxy channel.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type                                      | Read-Only  | Optional  | Description      |
| --------- | ---------------------------------------- | ---- | ---- | -------- |
| channelId | number | No | No | Proxy channel ID. The value ranges from 1 to 2147483647. |
| state | [ChannelState](#channelstate) | No | No | Channel connection states. For details, see [ChannelState](#channelstate). You are advised to adjust service policies based on different status values. For example, suspend data transmission when the channel is disconnected and retry services after the channel is reconnected. |

## ChannelState

Enumerates the connection states of the proxy channel.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Value                                      | Description      |
| --------- | ---------------------------------------- |  -------- |
| CHANNEL_WAIT_RESUME | 0 | The connection is disconnected, and the channel is unavailable.|
| CHANNEL_RESUME | 1 | The connection is restored, and the channel is available.|
| CHANNEL_EXCEPTION_SOFTWARE_FAILED | 2 | The channel is unavailable due to a software exception, such as an internal protocol stack error or resource allocation failure. You are advised to check the logs to locate the cause. |
| CHANNEL_BR_NO_PAIRED | 3 | The Bluetooth pairing relationship is deleted, and the channel is unavailable.|

## LinkType

Enumerates the link types.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Value                                      | Description      |
| --------- | ---------------------------------------- |  -------- |
| LINK_BR | 0 | BR protocol, which is used to establish a bidirectional data channel with a wearable device through a BR link. |