# setAdditionalConfig (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setAdditionalConfig

```TypeScript
function setAdditionalConfig(key: string, value: string): Promise<number>
```

Sets the additional system configuration information of the notification. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Additional configuration key. Currently, only **RING_TRUSTLIST_PKG** is supported, indicating that the application supports custom ringtones. |
| value | string | Yes | Additional configuration value. Example: [bundleName1,bundleName2]. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. **0** indicates successful; other values indicate failed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.setAdditionalConfig('RING_TRUSTLIST_PKG','[bundleName1,bundleName2]').then((data: number) => {
  console.info(`setAdditionalConfig success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`setAdditionalConfig failed, code is ${err.code}, message is ${err.message}`);
});
```
