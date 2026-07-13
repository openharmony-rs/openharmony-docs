# getValueForAccount

## getValueForAccount

```TypeScript
function getValueForAccount(admin: Want, item: SettingsItem, accountId: number): string
```

获取指定用户的设备设置策略。该接口可以获取指定用户在设置应用中的某个参数，比如获取用户100的设备名称等。

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| item | SettingsItem | 是 | 设备设置策略类型。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](@ohos.account.osAccount:osAccount.AccountManager.getOsAccountLocalId(callback:AsyncCallback&lt;int&gt;))等接口来获取<br>取值范围为全体整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Policy type value.<br>When **item** is set to [SettingsItem.DEVICE_NAME](arkts-mdm-settingsitem-e.md), this API returns thedevice name of the current user. If the device name of another user is queried, error code 9200012 is returned.<br>When **item** is set to [SettingsItem.FLOATING_NAVIGATION](arkts-mdm-settingsitem-e.md),this API returns the three-key navigation switch state for the specified user.<br>When **item** is set to [SettingsItem.FLOATING_NAVIGATION](arkts-mdm-settingsitem-e.md),this API can be called properly on phones and tablets but returns error code 801 on other devices. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let accountId = 100;
  let result: string = deviceSettings.getValueForAccount(wantTemp, deviceSettings.SettingsItem.DEVICE_NAME, accountId);
  console.info(`Succeeded in getting device name, result : ${result}`);
} catch (err) {
  console.error(`Failed to get device name. Code: ${err.code}, message: ${err.message}`);
}

```

