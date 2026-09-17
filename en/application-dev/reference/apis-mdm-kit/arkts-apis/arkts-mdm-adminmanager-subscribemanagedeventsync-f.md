# subscribeManagedEventSync

## Modules to Import

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## subscribeManagedEventSync

```TypeScript
function subscribeManagedEventSync(admin: Want, managedEvents: Array<ManagedEvent>): void
```

Subscribes to system management events. After the call is successful, the device administrator application will receive a notification when a subscribed system management event occurs.

Since API version 26.0.0, error code 9200002 is returned when a non-super device administrator application calls this API to subscribe to the [MANAGED_EVENT_POLICIES_CHANGED](arkts-mdm-adminmanager-managedevent-e.md) event.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_SUBSCRIBE_MANAGED_EVENT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| managedEvents | Array&lt;[ManagedEvent](arkts-mdm-adminmanager-managedevent-e.md)&gt; | Yes | Array of system management events to be subscribed to. Each element in the array is a value from the [ManagedEvent](arkts-mdm-adminmanager-managedevent-e.md) enumeration. Multiple event types can be subscribed to, such as application installation/uninstallation/start/stop events, system update events, and more. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device.<br>**Applicable version:** 26.0.0 and later |
| [9200008](../errorcode-enterpriseDeviceManager.md#9200008-invalid-system-subscription-event) | The specified system event is invalid. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let events: Array<adminManager.ManagedEvent> = [adminManager.ManagedEvent.MANAGED_EVENT_BUNDLE_ADDED, adminManager.ManagedEvent.MANAGED_EVENT_BUNDLE_REMOVED];

try {
  adminManager.subscribeManagedEventSync(wantTemp, events);
  console.info('Succeeded in subscribing managed event.');
} catch (err) {
  console.error(`Failed to subscribe managed event. Code: ${err.code}, message: ${err.message}`);
}
```
