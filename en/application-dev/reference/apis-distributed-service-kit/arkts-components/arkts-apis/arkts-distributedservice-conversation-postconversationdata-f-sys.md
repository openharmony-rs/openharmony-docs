# postConversationData (System API)

## Modules to Import

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## postConversationData

```TypeScript
function postConversationData(
    deviceId: string,
    bundleName: string,
    abilityName: string,
    msg: ArrayBuffer
  ): Promise<void>
```

Sends session data to the target device. The target device must be a trusted device under the same account. The network ID or UDID of the target device is used for device addressing. Data is sent to the app with the registered listener on the target device based on the specified bundle name and ability name. Typical use scenarios include sending collaboration commands across devices.

**Since:** 26.1.0

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Network ID or UDID of the target device, which can be obtained by calling [getTrustedDevices()](arkts-distributedservice-conversation-gettrusteddevices-f-sys.md). The length of both the network ID and UDID must be 64 bytes. If an invalid value is passed, error code 401 is returned. |
| bundleName | string | Yes | Name of the target bundle to which data is sent. The value contains 1 to 127 bytes and must be the same as the bundle name of the app registered with a listener on the target device by calling [registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md). If this requirement is not met, data cannot be sent to the target app. If an invalid or empty value is passed, error code 401 is returned. |
| abilityName | string | Yes | Name of the target ability to which data is sent. The value contains 1 to 127 bytes and must be the same as the ability name of the app registered with a session listener on the target device. If this requirement is not met, data cannot be sent to the target app. If an invalid or empty value is passed, error code 401 is returned. |
| msg | ArrayBuffer | Yes | Message to be sent. A maximum of 10,240 bytes can be sent at a time. The data structure is defined by the application layer protocol. If empty or invalid data is passed, error code 401 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. The application does not have the required permission to access distributed data. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. The deviceId, bundleName, abilityName or msg is invalid or empty. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2000001](../errorcode-conversation.md#2000001-internal-error) | Internal error. |
| [2004001](../errorcode-conversation.md#2004001-peer-device-system-version-outdated) | Remote system version is too low. |
| [2004002](../errorcode-conversation.md#2004002-failed-to-start-the-peer-ability) | Failed to start ability on the remote side. |
| [2004003](../errorcode-conversation.md#2004003-failure-to-send-data) | Failed to send data. |
| [2004004](../errorcode-conversation.md#2004004-peer-confirmation-timeout) | Timeout while waiting for acknowledgement from the remote side. |

**Examples**

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let deviceId: string = 'device_network_id_or_udid'; // deviceId is the network ID or UDID of the target device obtained by calling conversation.getTrustedDevices().
  let bundleName: string = 'com.example.demo';
  let abilityName: string = 'EntryAbility';
  let msg: ArrayBuffer = new ArrayBuffer(10);
  let view = new Uint8Array(msg);
  view[0] = 1;

  conversation.postConversationData(deviceId, bundleName, abilityName, msg).then(() => {
    console.info(`postConversationData success`);
  }).catch((err: BusinessError) => {
    console.error(`postConversationData errCode: ${err.code}, errMessage: ${err.message}`);
  });
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`postConversationData errCode: ${e.code}, errMessage: ${e.message}`);
}
```
