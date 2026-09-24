# on

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## on('receiveData')

```TypeScript
function on(type: 'receiveData', channelId: number, callback: Callback<DataInfo>): void
```

Subscribes to data receive events. This API uses an asynchronous callback to return the result. This is applicable to scenarios where the phone-side app needs to continuously receive data reported by the wearable device-side app, such as receiving data from the wearable device-side app. The proxy module receives data from the peer end based on the peer UUID configured when **openProxyChannel** is called, and passes the received wearable device-side app data to the subscriber through the callback. You must call [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) to successfully open a proxy channel before subscribing to data receive events. If you need to proxy-wake the phone-side app process to receive and process peer data, configure the **action** field as **action.ohos.pull.listener** in the **module.json5** file before use. After subscribing, call [off('receiveData')](arkts-distributedservice-proxychannelmanager-off-f.md#offreceivedata) to unsubscribe and prevent the callback from being triggered continuously.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'receiveData' | Yes | Event type. The value **receiveData** indicates the data receiving event. |
| channelId | number | Yes | Channel ID obtained when opening a proxy channel. The value range is 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004. If the value is out of range, error code 32390006 is returned. The channelId takes effect only when the proxy channel is available, and becomes unavailable after the channel is closed or disconnected. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md)&gt; | Yes | Callback invoked to return the data received through the proxy channel. The callback parameter is a [DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md) object, which contains channelId (channel ID) and data (received byte data). Data can be received only after a proxy channel is opened by calling openProxyChannel. If registered multiple times, only the last registration takes effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
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

Subscribes to channel state events. This API uses an asynchronous callback to return the result. This is applicable to scenarios where the phone-side app needs to monitor the proxy channel connection state in real time, such as pausing data sending after detecting channel disconnection and automatically retrying services after channel recovery. The proxy module monitors Bluetooth BR link state changes in real time, and reports **ChannelStateInfo** through the callback when events such as connection recovery, abnormal disconnection, and pairing relationship deletion occur. You must call [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) to successfully open a proxy channel before subscribing to channel state events. After subscribing, call [off('channelStateChange')](arkts-distributedservice-proxychannelmanager-off-f.md#offchannelstatechange) to unsubscribe and prevent the callback from being triggered continuously. After calling [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md) to close the channel, the registered **channelStateChange** callback is automatically unsubscribed.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'channelStateChange' | Yes | Event type. The value **channelStateChange** indicates the channel state change event. |
| channelId | number | Yes | Channel ID obtained when opening the proxy channel. The value range is 1 to 214748364 7. Using an invalid or closed channelId returns error code 32390004, and exceeding the value range returns error code 32390006. The channelId takes effect only when the proxy channel is available, and becomes unavailable after the channel is closed or disconnected. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md)&gt; | Yes | Callback invoked to return the proxy channel state change information. The callback parameter is a [ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md) object, which contains channelId (channel ID) and state (channel connection state). The proxy channel must be opened through openProxyChannel before receiving the channel state. If registered multiple times, only the last registered callback takes effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
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
