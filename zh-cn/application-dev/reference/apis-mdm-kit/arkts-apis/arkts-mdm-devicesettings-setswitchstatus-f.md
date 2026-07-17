# setSwitchStatus

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## setSwitchStatus

```TypeScript
function setSwitchStatus(admin: Want, key: SwitchKey, status: SwitchStatus): void
```

设置开关的状态。支持设置星闪、蓝牙、Wi-Fi的状态为开启或关闭，设置完毕后，用户可以手动开关。支持设置蓝牙的状态为强制开启，设置完毕后，用户不可以手动开关。若已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口禁用了某个开关，则通过本接口设置这个开关的状态会抛出错误码203，需通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口解除该开关禁用策略。当设备有多个MDM应用时，各MDM应用设置开关状态不存在冲突，最后设置的策略生效。开启(用户可手动开启、关闭)、关闭(用户可手动开启、关闭)、强制开启(用户不可手动关闭)三个状态可以随意切换，也不存在冲突。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceSettings-function setSwitchStatus(admin: Want, key: SwitchKey, status: SwitchStatus): void--><!--Device-deviceSettings-function setSwitchStatus(admin: Want, key: SwitchKey, status: SwitchStatus): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| key | [SwitchKey](arkts-mdm-devicesettings-switchkey-e.md) | 是 | 开关的名称，应用申请权限 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS 并通过接口[startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md#startadminprovision-1)激活为自带设备管理应用，可以使用此接口设置以下开关：星闪、蓝牙、Wi-Fi。 |
| status | [SwitchStatus](arkts-mdm-devicesettings-switchstatus-e.md) | 是 | 开关的状态，应用申请权限 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS 并通过接口[startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md#startadminprovision-1)激活为自带设备管理应用，可以使用此接口设置以下状态：ON、OFF。设置为FORCE_ON状态时会报错误码9200002。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| 9201042 | Failed to toggle the switch state. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
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
  let key: deviceSettings.SwitchKey = deviceSettings.SwitchKey.BLUETOOTH;
  let status: deviceSettings.SwitchStatus  = deviceSettings.SwitchStatus.ON;
  deviceSettings.setSwitchStatus(wantTemp, key, status);
  console.info(`Succeeded in setting switch status.`);
} catch (err) {
  console.error(`Failed to set switch status. Code: ${err.code}, message: ${err.message}`);
}

```

