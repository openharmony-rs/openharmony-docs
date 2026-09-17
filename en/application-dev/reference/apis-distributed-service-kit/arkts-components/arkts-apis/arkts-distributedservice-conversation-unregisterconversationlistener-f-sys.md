# unregisterConversationListener (System API)

## Modules to Import

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## unregisterConversationListener

```TypeScript
function unregisterConversationListener(bundleName: string, abilityName: string): void
```

Unregisters the listener with the specified bundle name and ability name. This API must be used in pairs with [registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md) to unregister a registered listener. When the listener is no longer needed, call this API to unregister the listener to release resources. If the listener is not unregistered, resources will be continuously occupied. Only one listener can be registered for the same bundle name and ability name. Duplicate registration will overwrite the previously registered listener. After the listener is unregistered, the listener that is currently in effect will be removed. After this API is called, the app will no longer receive session data of the specified bundle name and ability name. If no listener has been registered for the specified bundle name and ability name, this API returns a success message.

**Since:** 26.1.0

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the bundle whose listener is to be unregistered. The value contains 1 to 127 bytes and must be the same as the bundle name used during listener registration. If an invalid or empty value is passed, error code 401 is returned. |
| abilityName | string | Yes | Name of the ability whose listener is to be unregistered. The value contains 1 to 127 bytes and must be the same as the ability name used during listener registration. If an invalid or empty value is passed, error code 401 is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. The application does not have the required permission to access distributed data. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. The bundleName or abilityName is invalid or empty. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2000001](../errorcode-conversation.md#2000001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName: string = 'com.example.demo';
  let abilityName: string = 'EntryAbility';

  conversation.unregisterConversationListener(bundleName, abilityName);
  console.info(`unregisterConversationListener success`);
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`unregisterConversationListener errCode: ${e.code}, errMessage: ${e.message}`);
}
```
