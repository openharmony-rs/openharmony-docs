# cancel (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

<a id="cancel-3"></a>

## cancel

```TypeScript
function cancel(representativeBundle: BundleOption, id: number): Promise<void>
```

Cancels the notification of other applications of the user. This API uses a promise to return the result.

The current application must have a proxy relationship with another application, or the **ohos.permission.NOTIFICATION_AGENT_CONTROLLER** permission is granted to the current application.

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| representativeBundle | [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | Yes | Bundle information of the application. |
| id | number | Yes | Notification ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |
| [1600017](../errorcode-notification.md#1600017-no-configured-proxy-relationship) | There is no corresponding agent relationship configuration. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundle: notificationManager.BundleOption = {
  bundle: "bundleName"
};
let id: number = 1;
notificationManager.cancel(bundle, id).then(() => {
  console.info("cancel success");
}).catch((err: BusinessError) => {
  console.error(`cancel failed, code is ${err.code}, message is ${err.message}`);
});
```
