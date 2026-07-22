# setValueForAccount

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## setValueForAccount

```TypeScript
function setValueForAccount(admin: Want, item: SettingsItem, accountId: number, value: string): void
```

设置指定用户的设备设置策略。该接口可以设置指定用户在设置应用中的某个参数，比如设置用户100的设备名称等。

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceSettings-function setValueForAccount(admin: Want, item: SettingsItem, accountId: number, value: string): void--><!--Device-deviceSettings-function setValueForAccount(admin: Want, item: SettingsItem, accountId: number, value: string): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| item | [SettingsItem](arkts-mdm-devicesettings-settingsitem-e.md) | 是 | 设备设置策略类型。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取<br>取值范围为全体整数。<br>   -用户ID，必须大于等于0。<br>您可以调用[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)时，value为设备名称的字符串。 字符串长度范围：大于等于1，小于等于100。只允许设置当前用户的设备名称，设置其他用户的设备名称返回9200012错误码。<br/>当item为[SettingsItem.FLOATING_NAVIGATION](arkts-mdm-devicesettings-settingsitem-e.md)时，value为三键导航的开关状态。<br/>- '0'：表示开启三键导航（通过接口[enterKioskMode](../../apis-ability-kit/arkts-apis/arkts-ability-kioskmanager-enterkioskmode-f.md#enterkioskmode)进入Kiosk模式下，三键导航显示依赖底部手势开启；即三键导航开关和底部手势开关同时开启时，三键导航才会显示。底部手势可通过接口[applicationManager.setKioskFeatures](|

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
import { deviceSettings ) from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let accountId = 100;
  let deviceName: string = "deviceName"
  deviceSettings.setValueForAccount(wantTemp, deviceSettings.SettingsItem.DEVICE_NAME, accountId, deviceName);
  console.info('Succeeded in setting device name.');
} catch (err) {
  console.error(`Failed to set device name. Code: ${err.code}, message: ${err.message}`);
}

```

