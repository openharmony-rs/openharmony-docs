# on

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## on('receiveData')

```TypeScript
function on(type: 'receiveData', channelId: number, callback: Callback<DataInfo>): void
```

Subscribes to data receiving events. This API uses an asynchronous callback to return the result. This method is applicable when the phone app needs to continuously receive data reported by the wearable app, for example, receiving the wearable app data. The proxy module receives data from the peer device based on the peer UUID configured when **openProxyChannel** is called, and transfers the received wearable app data to the subscriber through a callback. You can subscribe to data receiving events only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). To enable the proxy channel to wake up the phone app process to receive and process data from the peer device, set the **action** field to **action.ohos.pull.listener** in the **module.json5** file. After the subscription, call [off('receiveData')](arkts-distributedservice-proxychannelmanager-off-f.md#offreceivedata) to cancel the subscription to prevent the callback from being continuously triggered.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

<!--Device-proxyChannelManager-function on(type: 'receiveData', channelId: number, callback: Callback<DataInfo>): void--><!--Device-proxyChannelManager-function on(type: 'receiveData', channelId: number, callback: Callback<DataInfo>): void-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'receiveData' | Yes | Event type. The value **receiveData** indicates the data receiving event. |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md)&gt; | Yes | Callback used to receive data from the proxy channel. The callback parameter is a [DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md) object, which contains the **channelId** (channel ID) and **data** (received data, in bytes) fields. You can receive data only after the proxy channel is opened by calling **openProxyChannel**. If the callback function is registered multiple times, only the last registered one takes effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [32390004](../errorcode-proxyChannelManager.md#32390004-invalid-or-unavailable-channel-id) | ChannelId is invalid or unavailable. |
| [32390006](../errorcode-proxyChannelManager.md#32390006-parameter-verification-error) | Parameter error. |
| [32390100](../errorcode-proxyChannelManager.md#32390100-internal-error) | Internal error. |
| [32390101](../errorcode-proxyChannelManager.md#32390101-call-restricted) | Call is restricted. |

**Examples**

```TypeScript
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


## on('channelStateChange')

```TypeScript
function on(type: 'channelStateChange', channelId: number, callback: Callback<ChannelStateInfo>): void
```

Subscribes to channel state change events. This API uses an asynchronous callback to return the result. This method is applicable to scenarios where the phone app needs to detect the proxy channel connection state in real time. For example, the app can pause data transmission after the channel is disconnected and automatically retry services after the channel is reconnected. The proxy module monitors the BR link status in real time. When an event such as connection restoration, abnormal disconnection, or pairing relationship deletion occurs, the proxy module reports **ChannelStateInfo** using a callback. You can subscribe to channel state change events only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). After the subscription, call [off('channelStateChange')](arkts-distributedservice-proxychannelmanager-off-f.md#offchannelstatechange) to cancel the subscription to prevent the callback from being continuously triggered. After the channel is closed by calling [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md), the registered **channelStateChange** callback will be automatically unsubscribed from.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

<!--Device-proxyChannelManager-function on(type: 'channelStateChange', channelId: number, callback: Callback<ChannelStateInfo>): void--><!--Device-proxyChannelManager-function on(type: 'channelStateChange', channelId: number, callback: Callback<ChannelStateInfo>): void-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'channelStateChange' | Yes | Event type. The value **channelStateChange** indicates the channel state change event. |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md)&gt; | Yes | Callback used to receive the proxy channel state change information. The callback parameter is a [ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md) object, which contains the **channelId** (channel ID) and **state** (channel connection status) fields. You can receive the channel state information only after the proxy channel is opened by calling **openProxyChannel**. If the callback function is registered for multiple times, only the last registered callback function takes effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [32390004](../errorcode-proxyChannelManager.md#32390004-invalid-or-unavailable-channel-id) | ChannelId is invalid or unavailable. |
| [32390006](../errorcode-proxyChannelManager.md#32390006-parameter-verification-error) | Parameter error. |
| [32390100](../errorcode-proxyChannelManager.md#32390100-internal-error) | Internal error. |
| [32390101](../errorcode-proxyChannelManager.md#32390101-call-restricted) | Call is restricted. |

**Examples**

```TypeScript
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
