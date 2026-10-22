# off

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## off('receiveData')

```TypeScript
function off(type: 'receiveData', channelId: number, callback?: Callback<DataInfo>): void
```

Unsubscribes from data receiving events. Data will no longer be received through a callback. This method is applicable when the phone app no longer needs to receive data from the wearable app, for example, when the user switches to another function module. You can unsubscribe from data receiving events only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). This method must be used together with [on('receiveData')](arkts-distributedservice-proxychannelmanager-on-f.md#onreceivedata) to unregister the data receiving callback registered using **on('receiveData')**.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

<!--Device-proxyChannelManager-function off(type: 'receiveData', channelId: number, callback?: Callback<DataInfo>): void--><!--Device-proxyChannelManager-function off(type: 'receiveData', channelId: number, callback?: Callback<DataInfo>): void-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'receiveData' | Yes | Event type. The value **receiveData** indicates the data receiving event. |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md)&gt; | No | Registered callback. If this parameter is not passed, all data receiving events are unsubscribed from. This parameter is not passed by default. The callback last registered using **on** needs to be passed to unsubscribe from the data receiving events. If any other callback function is passed, the unsubscription will fail. |

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


## off('channelStateChange')

```TypeScript
function off(type: 'channelStateChange', channelId: number, callback?: Callback<ChannelStateInfo>): void
```

Unsubscribes from channel state change events. This method is applicable when the phone app no longer needs to listen for the proxy channel connection state change events, for example, when the user exits the related service page or the data transmission process is completed. You can unsubscribe from data receiving events only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). This method must be used together with [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) to unregister the channel state change callback registered using **on('channelStateChange')**.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

<!--Device-proxyChannelManager-function off(type: 'channelStateChange', channelId: number, callback?: Callback<ChannelStateInfo>): void--><!--Device-proxyChannelManager-function off(type: 'channelStateChange', channelId: number, callback?: Callback<ChannelStateInfo>): void-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'channelStateChange' | Yes | Event type. The value is fixed to **'channelStateChange'**. |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md)&gt; | No | Registered callback. If this parameter is not passed, all channel state events are unsubscribed from. This parameter is not passed by default. The callback last registered using **on** needs to be passed to unsubscribe from the channel state events. If any other callback function is passed, the unsubscription will fail. |

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
