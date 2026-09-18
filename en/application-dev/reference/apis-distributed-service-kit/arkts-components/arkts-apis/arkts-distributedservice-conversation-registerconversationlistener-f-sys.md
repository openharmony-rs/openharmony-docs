# registerConversationListener (System API)

## Modules to Import

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## registerConversationListener

```TypeScript
function registerConversationListener(
    bundleName: string,
    abilityName: string,
    dataCallback: DataCallback
  ): void
```

Registers a listener to receive data from trusted devices under the same account. When the remote device sends data to the local device by calling [postConversationData](arkts-distributedservice-conversation-postconversationdata-f-sys.md), the data is distributed to the registered callback based on the specified bundle name and ability name. Only one listener can be registered for the same bundle name and ability name. Duplicate registration will overwrite the previously registered listener.

**API called in pairs:** This API must be used in pairs with [unregisterConversationListener](arkts-distributedservice-conversation-unregisterconversationlistener-f-sys.md), which is called to unregister the listener to release resources.

**Since:** 26.1.0

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the bundle that receives data. The value contains 1 to 127 bytes and must be the same as the bundle name of the app. If this requirement is not met, the listener cannot receive data correctly. If an invalid or empty value is passed, error code 401 is returned. |
| abilityName | string | Yes | Name of the ability that receives data. The value contains 1 to 127 bytes and must be the same as the ability name of the app. If this requirement is not met, the listener cannot receive data correctly. If an invalid or empty value is passed, error code 401 is returned. |
| dataCallback | [DataCallback](arkts-distributedservice-conversation-datacallback-t-sys.md) | Yes | Callback function used to receive data transferred across devices. If an invalid value is passed, error code 401 is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. The application does not have the required permission to access distributed data. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. The bundleName, abilityName or dataCallback is invalid or empty. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2000001](../errorcode-conversation.md#2000001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName: string = 'com.example.demo';
  let abilityName: string = 'EntryAbility';

  conversation.registerConversationListener(bundleName, abilityName, (deviceId: string, msg: ArrayBuffer) => {
    console.info(`received message, deviceId: ${deviceId}, msg length: ${msg.byteLength}`);
  });
  console.info(`registerConversationListener success`);
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`registerConversationListener errCode: ${e.code}, errMessage: ${e.message}`);
}
```
