# closeProxyChannel

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## closeProxyChannel

```TypeScript
function closeProxyChannel(channelId: number): void
```

Closes an opened proxy channel. This is applicable to scenarios where the phone-side app no longer needs to communicate with the wearable device-side app, such as actively releasing channel resources after completing a data synchronization task. This method must be used in pair with [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). Call this method to close the channel and release resources after use. After the channel is closed, the registered **receiveData** and **channelStateChange** callbacks are automatically unsubscribed, and data being transmitted is interrupted. Failure to close the proxy channel in a timely manner may cause channel resource leakage.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| channelId | number | Yes | Channel ID obtained when opening the proxy channel. The value range is 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004. If the value is out of range, error code 3239 0006 is returned. The channelId takes effect only when the proxy channel is available, and becomes unavailable after the channel is closed or disconnected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
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
