# getPermissionUsedRecordToggleStatus（系统接口）

## 导入模块

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## getPermissionUsedRecordToggleStatus

```TypeScript
function getPermissionUsedRecordToggleStatus(): Promise<boolean>
```

系统应用调用此接口，可以获取当前用户的权限使用记录开关状态，例如在权限管理界面展示当前开关设置状态。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.PERMISSION_USED_STATS

<!--Device-privacyManager-function getPermissionUsedRecordToggleStatus(): Promise<boolean>--><!--Device-privacyManager-function getPermissionUsedRecordToggleStatus(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象，返回true，表示当前用户的开关状态值为开启。返回false，表示当前用户的开关状态值为关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 查询权限使用记录开关状态
privacyManager.getPermissionUsedRecordToggleStatus().then((status) => {
  console.info('getPermissionUsedRecordToggleStatus success');
  if (status == true) {
    console.info('get status is TRUE');
  } else {
    console.info('get status is FALSE');
  }
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedRecordToggleStatus fail, code: ${err.code}, message: ${err.message}`);
});

```

