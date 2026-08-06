# @ohos.distributedsched.proxyChannelManager (Proxy Channel Management)

<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @jzy_123-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=6bfcf5261eb2f83e0869ab9ec15c9d0a1edd6edd translatedAt=2026-08-04T03:18:45.226Z pushedAt=2026-08-06T11:21:57.677Z -->

DSoftBus provides stable and reliable underlying channels for cross-device communication. This module is developed based on DSoftBus. It supports data exchange between phones and wearables, providing users with a seamless device interconnection experience. It also simplifies cross-device communication for developers, eliminating the need to handle underlying communication protocols and process wakeup logic. Use scenarios: During collaboration between the phone app and wearable app, if the phone app is not running in the foreground, its downlink messages are forwarded to the notification server and then sent to the wearable through the proxy module. When the wearable sends data to the phone, the proxy module can dynamically wake up the corresponding app process on the phone to receive and process the data. The core functions of this module include proxy channel management, data route management, application state awareness and wakeup, and link state monitoring.

- Proxy channel management: Manages bidirectional data channels established between phones and wearables via the Bluetooth Basic Rate (BR) protocol. This ensures reliable cross-device data communication without the need to implement the underlying communication protocol. The supported data channel IDs range from 1 to 2147483647.

- Data route management: Accurately forwards data of wearables based on the specified service UUID. This accurately routes data to the target service port, preventing data loss or incorrect data transmission. The UUID uniquely identifies the service listened for the peer device. The proxy module routes data to the corresponding service port based on the UUID of the peer device.

- Application state awareness and wakeup: After a proxy channel is enabled and data sent by the wearable is received, the proxy module identifies the target app based on the **action** field (for example, **action.ohos.pull.listener**) configured in the **module.json5** file, and starts the corresponding app process on the phone to process the data. This allows the app to receive data without having to stay in the foreground, thereby saving system resources.

- Link state monitoring: Monitors the connection status changes of the proxy channel throughout its lifecycle in real time through callbacks. This helps the phone app respond to connection exceptions in a timely manner and adjust service policies, thereby improving data transmission reliability.

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

2. Call **sendData** to send data, and subscribe to events based on service requirements. Call **on('receiveData')** to receive data from the peer end, and call **on('channelStateChange')** to monitor channel connection state changes (such as disconnection and recovery). You can subscribe to both events at the same time. It is recommended to use them together in data transmission scenarios so that data sending can be paused promptly and disconnection recovery logic can be handled when the channel is abnormal.

3. After using the event, call **off('receiveData')** or **off('channelStateChange')** to unsubscribe from the event.

4. Call **closeProxyChannel** to close the proxy channel and release resources.

## proxyChannelManager.openProxyChannel

openProxyChannel(channelInfo:&nbsp;ChannelInfo):&nbsp;Promise&lt;number&gt;

Opens a proxy channel. This API uses a promise to return the result. Based on the link type and peer device information configured in **ChannelInfo**, it negotiates with the peer device via the Bluetooth BR protocol to establish a bidirectional data channel and returns a channel ID that uniquely identifies the channel. This is applicable to scenarios where a phone-side app needs to establish a bidirectional data channel with a wearable device-side app, such as message notification forwarding. After calling this method, you must call [closeProxyChannel](#proxychannelmanagercloseproxychannel) to close the channel and release resources when the proxy channel is no longer needed.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called normally on Phone/Tablet devices. On other devices that support distributed services, error code 32390101 is returned. On wearable devices that do not support distributed services, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| channelInfo | [ChannelInfo](#channelinfo) | Yes | Link type of the proxy channel, MAC address of the peer device, and UUID of the listening service on the peer device. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| &nbsp;Promise&lt;number&gt; | Promise used to return the result. When the proxy channel is opened successfully, the promise is resolved, and the channelId of the proxy channel is returned. The value ranges from 1 to 2147483647. The lifecycle of the channelId is the same as that of the proxy channel. If the proxy is not closed, passing the same input parameters returns the same channelId. If the operation fails, the promise is rejected with error information. For details about the error codes, see the error code table. |

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
            peerDevAddr: 'xx:xx:xx:xx:xx:xx', // Bluetooth MAC address of the wearable device.
            peerUuid: 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx', // UUID listened on by the wearable side.
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
            // If the returned error.code is undefined and error.message is "Cannot read property openProxyChannel of undefined", the current image does not support this API.
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

Closes an opened proxy channel. This is applicable to scenarios where the phone-side app no longer needs to communicate with the wearable device-side app, such as actively releasing channel resources after completing a data synchronization task. This method must be used in pair with [openProxyChannel](#proxychannelmanageropenproxychannel). Call this method to close the channel and release resources after use. After the channel is closed, the registered **receiveData** and **channelStateChange** callbacks are automatically unsubscribed, and data being transmitted is interrupted. Failure to close the proxy channel in a timely manner may cause channel resource leakage.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called normally on Phone/Tablet devices. On other devices that support distributed services, error code 32390006 is returned. On wearable devices that do not support distributed services, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| channelId | number | Yes | Channel ID obtained when opening the proxy channel. The value range is 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004. If the value is out of range, error code 32390006 is returned. The channelId takes effect only when the proxy channel is available, and becomes unavailable after the channel is closed or disconnected. |

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
            // If error.code is undefined and error.message is "Cannot read property closeProxyChannel of undefined", the current image does not support this API.
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

Sends data to the peer end. This API uses a promise to return the result. This is applicable to scenarios where the phone-side app sends instructions or data to the wearable device-side app through the proxy channel, such as sending configuration updates or notification messages. This method can be called to send data only after [openProxyChannel](#proxychannelmanageropenproxychannel) successfully opens a proxy channel. When the proxy channel is in an unavailable state (such as [ChannelState](#channelstate).CHANNEL_WAIT_RESUME, CHANNEL_EXCEPTION_SOFTWARE_FAILED, or CHANNEL_BR_NO_PAIRED), calling this method will fail. It is recommended to subscribe to the [on('channelStateChange')](#proxychannelmanageronchannelstatechange) event to monitor the channel state, pause data sending when the channel is unavailable, and resume sending after the channel recovers. Data is transmitted to the peer device through the established proxy channel via the Bluetooth BR link. The maximum data length is 4096 bytes. Exceeding this limit will return error code 32390103.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called normally on Phone/Tablet devices. On other devices that support distributed services, error code 32390006 is returned. On wearable devices that do not support distributed services, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| channelId | number | Yes | Channel ID obtained when opening the proxy channel. The value range is 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004, and exceeding the value range returns error code 32390006. The channelId takes effect only when the proxy channel is available and becomes unavailable after the channel is closed or disconnected. |
| data | ArrayBuffer | Yes | Binary data to send to the peer end. The data format is defined by the app layer, with a maximum length of 4096 bytes. Exceeding the length limit returns error code 32390103. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| &nbsp;Promise&lt;void&gt; | Promise that returns no value. It is resolved when data is sent successfully and rejected with error information when the sending fails. |

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
            proxyChannelManager.sendData(channelId, data) // Obtain channelId from the Promise return value of the openProxyChannel API.
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

Subscribes to data receive events. This API uses an asynchronous callback to return the result. This is applicable to scenarios where the phone-side app needs to continuously receive data reported by the wearable device-side app, such as receiving data from the wearable device-side app. The proxy module receives data from the peer end based on the peer UUID configured when **openProxyChannel** is called, and passes the received wearable device-side app data to the subscriber through the callback. You must call [openProxyChannel](#proxychannelmanageropenproxychannel) to successfully open a proxy channel before subscribing to data receive events. If you need to proxy-wake the phone-side app process to receive and process peer data, configure the **action** field as **action.ohos.pull.listener** in the **module.json5** file before use. After subscribing, call [off('receiveData')](#proxychannelmanageroffreceivedata) to unsubscribe and prevent the callback from being triggered continuously.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called normally on Phone/Tablet devices. On other devices that support distributed services, error code 32390004 is returned. On wearable devices that do not support distributed services, no error code is returned and no exception is thrown.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type      | string | Yes| Event type. The value **receiveData** indicates the data receiving event.|
| channelId | number | Yes | Channel ID obtained when opening a proxy channel. The value range is 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004. If the value is out of range, error code 32390006 is returned. The channelId takes effect only when the proxy channel is available, and becomes unavailable after the channel is closed or disconnected. |
| callback | Callback&lt;[DataInfo](#datainfo)&gt; | Yes | Callback invoked to return the data received through the proxy channel. The callback parameter is a [DataInfo](#datainfo) object, which contains channelId (channel ID) and data (received byte data). Data can be received only after a proxy channel is opened by calling openProxyChannel. If registered multiple times, only the last registration takes effect. |

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
            proxyChannelManager.on('receiveData', channelId, receiveDataCallback); // Obtain channelId from the Promise return value of the openProxyChannel API.
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

Unsubscribes from data receive events and no longer receives data through the callback. This is applicable to scenarios where the phone-side app no longer needs to receive data from the wearable device-side app, such as when the user switches to another functional module. You must call [openProxyChannel](#proxychannelmanageropenproxychannel) to successfully open a proxy channel before unsubscribing. This method must be used in pair with [on('receiveData')](#proxychannelmanageronreceivedata) to cancel the data receive callback previously registered through **on('receiveData')**.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called normally on Phone/Tablet devices. On other devices that support distributed services, error code 32390004 is returned. On wearable devices that do not support distributed services, no error code is returned and no exception is thrown.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type      | string | Yes| Event type. The value **receiveData** indicates the data receiving event.|
| channelId | number | Yes | Channel ID obtained when opening the proxy channel, with a value range of 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004, and exceeding the value range returns error code 32390006. The channelId takes effect only when the proxy channel is available, and becomes unavailable after the channel is closed or disconnected. |
| callback | Callback&lt;[DataInfo](#datainfo)&gt; | No | Callback for the data receive event. Default behavior: when this parameter is not passed, all data receive event subscriptions are unsubscribed. The callback passed must be the last one registered via the on method to unsubscribe that callback; passing any other callback will not take effect. |

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
            proxyChannelManager.off('receiveData', channelId); // Obtain channelId from the Promise return value of the openProxyChannel API.
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

Subscribes to channel state events. This API uses an asynchronous callback to return the result. This is applicable to scenarios where the phone-side app needs to monitor the proxy channel connection state in real time, such as pausing data sending after detecting channel disconnection and automatically retrying services after channel recovery. The proxy module monitors Bluetooth BR link state changes in real time, and reports **ChannelStateInfo** through the callback when events such as connection recovery, abnormal disconnection, and pairing relationship deletion occur. You must call [openProxyChannel](#proxychannelmanageropenproxychannel) to successfully open a proxy channel before subscribing to channel state events. After subscribing, call [off('channelStateChange')](#proxychannelmanageroffchannelstatechange) to unsubscribe and prevent the callback from being triggered continuously. After calling [closeProxyChannel](#proxychannelmanagercloseproxychannel) to close the channel, the registered **channelStateChange** callback is automatically unsubscribed.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called normally on Phone/Tablet devices. On other devices that support distributed services, error code 32390004 is returned. On wearable devices that do not support distributed services, no error code is returned and no exception is thrown.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type      | string | Yes| Event type. The value **channelStateChange** indicates the channel state change event.|
| channelId | number | Yes | Channel ID obtained when opening the proxy channel. The value range is 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004, and exceeding the value range returns error code 32390006. The channelId takes effect only when the proxy channel is available, and becomes unavailable after the channel is closed or disconnected. |
| callback | Callback&lt;[ChannelStateInfo](#channelstateinfo)&gt; | Yes | Callback invoked to return the proxy channel state change information. The callback parameter is a [ChannelStateInfo](#channelstateinfo) object, which contains channelId (channel ID) and state (channel connection state). The proxy channel must be opened through openProxyChannel before receiving the channel state. If registered multiple times, only the last registered callback takes effect. |

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
            proxyChannelManager.on('channelStateChange', channelId, channelStateChangeCallback); // channelId is obtained through the Promise return value of the openProxyChannel API.
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

Unsubscribes from channel state events. This is applicable to scenarios where the phone-side app no longer needs to listen for proxy channel connection state changes, such as when the user exits the relevant service page or completes the data transmission process. You must call [openProxyChannel](#proxychannelmanageropenproxychannel) to successfully open a proxy channel before unsubscribing. This method must be used in pair with [on('channelStateChange')](#proxychannelmanageronchannelstatechange) to cancel the channel state callback previously registered through **on('channelStateChange')**.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior difference**: This API can be called normally on Phone/Tablet devices. On other devices that support distributed services, error code 32390004 is returned. On wearable devices that do not support distributed services, no error code is returned and no exception is thrown.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type      | string | Yes | Sets the subscription type. The value is fixed to **'channelStateChange'**. |
| channelId | number | Yes    | Channel ID obtained when opening a proxy channel. Value range: 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004, and exceeding the value range returns error code 32390006. The channelId takes effect only when the proxy channel is available and becomes unavailable after the channel is closed or disconnected. |
| callback  | Callback&lt;[ChannelStateInfo](#channelstateinfo)&gt; | No | Registered callback. Default behavior: if this parameter is not passed, all channel state event subscriptions are unsubscribed. The callback passed must be the one last registered through the **on** method to unsubscribe from that callback; passing any other callback will not take effect. |

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
            proxyChannelManager.off('channelStateChange', channelId); // Obtain channelId from the promise return value of the openProxyChannel API.
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

Represents the received data information, including the channel ID and data.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type                                      | Read-Only  | Optional  | Description      |
| --------- | ---------------------------------------- | ---- | ---- | -------- |
| channelId | number | No | No | Channel ID of the proxy channel. The value range is 1 to 2147483647. |
| data | ArrayBuffer | No | No | Received byte data. The maximum length is 4096 bytes. |

## ChannelInfo

Input parameters of the function for opening a proxy channel, including the link type of the proxy channel, the MAC address of the peer device, and the UUID of the listening service.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type                                      | Read-Only  | Optional  | Description      |
| --------- | ---------------------------------------- | ---- | ---- | -------- |
| linkType | [LinkType](#linktype) | No | No | Link type of the proxy channel. For details about the value range, see [LinkType](#linktype). Currently, only **LINK_BR** (Bluetooth BR protocol) is supported. |
| peerDevAddr | string | No | No | MAC address of the peer device, in the format of XX:XX:XX:XX:XX:XX, where XX is a hexadecimal character (0-9, A-F, or a-f). The peer device must be paired. Error code 32390002 is returned if the device is not paired. Error code 32390006 is returned if the format does not meet the requirements. |
| peerUuid | string | No | No | UUID of the service listened on by the peer device, in the standard UUID string format, for example, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx. Error code 32390006 is returned if the format does not meet the requirements. |

## ChannelStateInfo

Represents the connection state information of the proxy channel.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type                                      | Read-Only  | Optional  | Description      |
| --------- | ---------------------------------------- | ---- | ---- | -------- |
| channelId | number | No | No | Channel ID of the proxy channel. The value range is 1 to 2147483647. |
| state | [ChannelState](#channelstate) | No | No | Connection state of the channel. For the value range, see [ChannelState](#channelstate). You are advised to adjust service policies based on different state values, for example, suspending data transmission when the channel is disconnected and retrying services after the channel is restored. |

## ChannelState

Enumerates the connection states of the proxy channel.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Value                                      | Description      |
| --------- | ---------------------------------------- |  -------- |
| CHANNEL_WAIT_RESUME | 0 | The connection is disconnected, and the channel is unavailable.|
| CHANNEL_RESUME | 1 | The connection is restored, and the channel is available.|
| CHANNEL_EXCEPTION_SOFTWARE_FAILED | 2 | The channel is unavailable due to a software exception, for example, an internal protocol stack error or resource allocation failure. Check the logs to locate the specific cause. |
| CHANNEL_BR_NO_PAIRED | 3 | The Bluetooth pairing relationship is deleted, and the channel is unavailable.|

## LinkType

Enumerates the link types.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Value                                      | Description      |
| --------- | ---------------------------------------- |  -------- |
| LINK_BR | 0 | Bluetooth BR protocol, used for establishing a bidirectional data channel with a wearable device over a Bluetooth BR link. |