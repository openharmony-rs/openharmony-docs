# isDistributedEnabled (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isDistributedEnabled

```TypeScript
function isDistributedEnabled(deviceType: string): Promise<boolean>
```

Queries whether the device supports [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) notifications. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function isDistributedEnabled(deviceType: string): Promise<boolean>--><!--Device-notificationManager-function isDistributedEnabled(deviceType: string): Promise<boolean>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | string | Yes | Device type. The options are as follows: <br>- **headset**: wearable audio device <br>- **liteWearable**: lite wearable <br>- **wearable**: wearable <br>- **current**: current device <br>- **2in1**: PC <br>- **tablet**: tablet |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the device supports cross-device collaboration notifications, and **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |

<!--Del-->
**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  }

  onForeground(): void {
    try {
      let deviceType: string = 'wearable';
      notificationManager.isDistributedEnabled(deviceType).then((data: boolean) => {
        console.info('isDistributedEnabled succeeded, result = ' + data);
      }).catch((err: BusinessError) => {
        console.error(`isDistributedEnabled failed. Code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      console.error(`isDistributedEnabled failed. Code is ${err.code}, message is ${err.message}`);
    }
  }
}
```

<!--DelEnd-->
