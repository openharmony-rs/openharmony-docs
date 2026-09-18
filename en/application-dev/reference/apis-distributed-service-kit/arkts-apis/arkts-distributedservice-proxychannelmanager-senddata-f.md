# sendData

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## sendData

```TypeScript
function sendData(channelId: number, data: ArrayBuffer): Promise<void>
```

Sends data to the peer end. This API uses a promise to return the result. This is applicable to scenarios where the phone-side app sends instructions or data to the wearable device-side app through the proxy channel, such as sending configuration updates or notification messages. This method can be called to send data only after [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) successfully opens a proxy channel. When the proxy channel is in an unavailable state (such as [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md). CHANNEL_WAIT_RESUME, CHANNEL_EXCEPTION_SOFTWARE_FAILED, or CHANNEL_BR_NO_PAIRED), calling this method will fail. It is recommended to subscribe to the [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) event to monitor the channel state, pause data sending when the channel is unavailable, and resume sending after the channel recovers. Data is transmitted to the peer device through the established proxy channel via the Bluetooth BR link. The maximum data length is 4096 bytes. Exceeding this limit will return error code 32390103.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| channelId | number | Yes | Channel ID obtained when opening the proxy channel. The value range is 1 to 2147483647. Using an invalid or closed channelId returns error code 32390004, and exceeding the value range returns error code 32390006. The channelId takes effect only when the proxy channel is available and becomes unavailable after the channel is closed or disconnected. |
| data | ArrayBuffer | Yes | Binary data to send to the peer end. The data format is defined by the app layer, with a maximum length of 4096 bytes. Exceeding the length limit returns error code 32390103. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
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
