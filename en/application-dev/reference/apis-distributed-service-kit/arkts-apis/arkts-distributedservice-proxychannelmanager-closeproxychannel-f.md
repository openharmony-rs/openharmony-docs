# closeProxyChannel

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## closeProxyChannel

```TypeScript
function closeProxyChannel(channelId: number): void
```

Closes a proxy channel that has been opened. This method is applicable to scenarios where the mobile app no longer needs to communicate with the wearable app, for example, when the channel resources need to be released after a data synchronization task is complete. This method must be used together with [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). After using the proxy channel, call this method to close the channel and release resources. After the channel is closed, the registered **receiveData** and **channelStateChange** callbacks will be automatically unregistered, and the data that is being transmitted will be interrupted. If the proxy channel is not closed in a timely manner, a channel resource leak may occur.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

<!--Device-proxyChannelManager-function closeProxyChannel(channelId: int): void--><!--Device-proxyChannelManager-function closeProxyChannel(channelId: int): void-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because bluetooth proxy function has been trimmed.<br>**Applicable version:** 26.0.0 and later |
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
