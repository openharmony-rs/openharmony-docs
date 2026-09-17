# getDistributedDeviceList (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getDistributedDeviceList

```TypeScript
function getDistributedDeviceList(): Promise<Array<string>>
```

Obtains the device types that enable cross-device notification. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  }

  onForeground(): void {
    try {
      notificationManager.getDistributedDeviceList().then((data: Array<string>) => {
        console.info('getDistributedDeviceList succeeded, result = ' + data);
      }).catch((err: BusinessError) => {
        console.error(`getDistributedDeviceList failed. Code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      console.error(`getDistributedDeviceList failed. Code is ${err.code}, message is ${err.message}`);
    }
  }
}
```
