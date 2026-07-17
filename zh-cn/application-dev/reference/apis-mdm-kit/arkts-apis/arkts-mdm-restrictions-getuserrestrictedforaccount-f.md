# getUserRestrictedForAccount

## 导入模块

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## getUserRestrictedForAccount

```TypeScript
function getUserRestrictedForAccount(admin: Want | null, settingsItem: string, accountId: number): boolean
```

获取指定用户设置项的禁用状态。

**起始版本：** 23

**废弃版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-restrictions-function getUserRestrictedForAccount(admin: Want | null, settingsItem: string, accountId: int): boolean--><!--Device-restrictions-function getUserRestrictedForAccount(admin: Want | null, settingsItem: string, accountId: int): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| settingsItem | string | 是 | 指定设置项。<br/>- modifyWallpaper：修改壁纸，包含锁屏壁纸和桌面壁纸。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取<br>取值应为≥0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定设置项的禁用状态，true表示已禁用，false表示未禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 需根据实际情况替换
let userId = 100;
let settingsItem: string = "modifyWallpaper";
try {
  let result: boolean = restrictions.getUserRestrictedForAccount(wantTemp, settingsItem, userId);
  console.info(`Succeeded in getting user restricted: ${result}`);
} catch (err) {
  console.error(`Failed to get user restricted. Code is ${err.code}, message is ${err.message}`);
}

```

