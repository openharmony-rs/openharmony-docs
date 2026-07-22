# getDistributedDeviceList（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getDistributedDeviceList

```TypeScript
function getDistributedDeviceList(): Promise<Array<string>>
```

查询支持跨设备协同通知的设备类型。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function getDistributedDeviceList(): Promise<Array<string>>--><!--Device-notificationManager-function getDistributedDeviceList(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | 返回支持跨设备协同通知的设备列表。Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |

**示例：**

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

