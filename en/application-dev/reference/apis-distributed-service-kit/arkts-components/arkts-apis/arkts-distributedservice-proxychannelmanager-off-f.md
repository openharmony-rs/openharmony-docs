# off

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## off('receiveData')

```TypeScript
function off(type: 'receiveData', channelId: number, callback?: Callback<DataInfo>): void
```

Unsubscribes from data receive events and no longer receives data through the callback. This is applicable to scenarios where the phone-side app no longer needs to receive data from the wearable device-side app, such as when the user switches to another functional module. You must call [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) to successfully open a proxy channel before unsubscribing. This method must be used in pair with [on('receiveData')](arkts-distributedservice-proxychannelmanager-on-f.md#onreceivedata) to cancel the data receive callback previously registered through **on('receiveData')**.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'receiveData' | Yes | Event type. The value **receiveData** indicates the data receiving event. |
| channelId | number | Yes | Channel ID obtained when opening the proxy channel, with a value range of 1 to 214748 3647. Using an invalid or closed channelId returns error code 32390004, and exceeding the value range returns error code 32390006. The channelId takes effect only when the proxy channel is available, and becomes unavailable after the channel is closed or disconnected. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md)&gt; | No | Callback for the data receive event. Default behavior: when this parameter is not passed, all data receive event subscriptions are unsubscribed. The callback passed must be the last one registered via the on method to unsubscribe that callback; passing any other callback will not take effect. |

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

Unsubscribes from channel state events. This is applicable to scenarios where the phone-side app no longer needs to listen for proxy channel connection state changes, such as when the user exits the relevant service page or completes the data transmission process. You must call [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) to successfully open a proxy channel before unsubscribing. This method must be used in pair with [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) to cancel the channel state callback previously registered through **on('channelStateChange')**.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'channelStateChange' | Yes | Sets the subscription type. The value is fixed to **'channelStateChange'**. |
| channelId | number | Yes | Channel ID obtained when opening a proxy channel. Value range: 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004, and exceeding the value range returns error code 32 390006. The channelId takes effect only when the proxy channel is available and becomes unavailable after the channel is closed or disconnected. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md)&gt; | No | Registered callback. Default behavior: if this parameter is not passed, all channel state event subscriptions are unsubscribed. The callback passed must be the one last registered through the **on** method to unsubscribe from that callback; passing any other callback will not take effect. |

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
