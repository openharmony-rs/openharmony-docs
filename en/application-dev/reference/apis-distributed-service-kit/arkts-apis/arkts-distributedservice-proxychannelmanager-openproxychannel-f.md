# openProxyChannel

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## openProxyChannel

```TypeScript
function openProxyChannel(channelInfo: ChannelInfo): Promise<number>
```

Opens a proxy channel. This API uses a promise to return the result. Based on the link type and peer device information configured in **ChannelInfo**, it negotiates with the peer device via the Bluetooth BR protocol to establish a bidirectional data channel and returns a channel ID that uniquely identifies the channel. This is applicable to scenarios where a phone-side app needs to establish a bidirectional data channel with a wearable device-side app, such as message notification forwarding. After calling this method, you must call [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md) to close the channel and release resources when the proxy channel is no longer needed.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| channelInfo | [ChannelInfo](arkts-distributedservice-proxychannelmanager-channelinfo-i.md) | Yes | Link type of the proxy channel, MAC address of the peer device, and UUID of the listening service on the peer device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. When the proxy channel is opened successfully, the promise is resolved, and the channelId of the proxy channel is returned. The value ranges from 1 to 2147483647. The lifecycle of the channelId is the same as that of the proxy channel. If the proxy is not closed, passing the same input parameters returns the same channelId. If the operation fails, the promise is rejected with error information. For details about the error codes, see the error code table. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because bluetooth proxy function has been trimmed.<br>**Applicable version:** 26.0.0 and later |
| [32390001](../errorcode-proxyChannelManager.md#32390001-bluetooth-disabled) | BR is disabled. |
| [32390002](../errorcode-proxyChannelManager.md#32390002-bluetooth-unpaired) | Device not paired. |
| [32390006](../errorcode-proxyChannelManager.md#32390006-parameter-verification-error) | Parameter error. |
| [32390100](../errorcode-proxyChannelManager.md#32390100-internal-error) | Internal error. |
| [32390101](../errorcode-proxyChannelManager.md#32390101-call-restricted) | Call is restricted. |
| [32390102](../errorcode-proxyChannelManager.md#32390102-operation-failed-or-connection-timed-out) | Operation failed or Connection timed out. |

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
