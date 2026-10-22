# sendData

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## sendData

```TypeScript
function sendData(channelId: number, data: ArrayBuffer): Promise<void>
```

Sends data to the peer end. This API uses a promise to return the result. This method is applicable to scenarios where a phone app sends instructions or data to a wearable app through the proxy channel, for example, sending configuration updates and notifications. This method can be called to send data only after the proxy channel is successfully opened by calling [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md). This method will fail to be called if the proxy channel is unavailable (for example, in the [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md).CHANNEL_WAIT_RESUME, **CHANNEL_EXCEPTION_SOFTWARE_FAILED**, or **CHANNEL_BR_NO_PAIRED** state). You are advised to subscribe to the [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) event to monitor the channel status. When the channel is unavailable, suspend data transmission. When the channel recovers, resume data transmission. Data is transmitted to the peer device through the established proxy channel over the BR link. The maximum data length is 4096 bytes. If the data length exceeds 4096 bytes, error code 32390103 will be returned.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

<!--Device-proxyChannelManager-function sendData(channelId: int, data: ArrayBuffer): Promise<void>--><!--Device-proxyChannelManager-function sendData(channelId: int, data: ArrayBuffer): Promise<void>-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| channelId | number | Yes | Proxy channel ID obtained when the proxy channel is opened. The value ranges from 1 to 2147483647. If an invalid or closed channel ID is used, error code 32390004 will be returned. If the value is out of range, error code 32390006 will be returned. This parameter takes effect only when the proxy channel is available. After the channel is closed or disconnected, the channel ID becomes unavailable. |
| data | ArrayBuffer | Yes | Binary data sent to the peer device. The data format is defined by the app layer. The maximum length is 4096 bytes. If the length exceeds the upper limit, error code 32390103 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because bluetooth proxy function has been trimmed.<br>**Applicable version:** 26.0.0 and later |
| [32390004](../errorcode-proxyChannelManager.md#32390004-invalid-or-unavailable-channel-id) | ChannelId is invalid or unavailable. |
| [32390006](../errorcode-proxyChannelManager.md#32390006-parameter-verification-error) | Parameter error. |
| [32390100](../errorcode-proxyChannelManager.md#32390100-internal-error) | Internal error. |
| [32390101](../errorcode-proxyChannelManager.md#32390101-call-restricted) | Call is restricted. |
| [32390103](../errorcode-proxyChannelManager.md#32390103-data-too-long) | Data too long. |
| [32390104](../errorcode-proxyChannelManager.md#32390104-data-sending-failed) | Send failed. |

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
