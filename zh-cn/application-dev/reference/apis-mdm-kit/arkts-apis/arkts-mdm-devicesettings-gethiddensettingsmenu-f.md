# getHiddenSettingsMenu

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## getHiddenSettingsMenu

```TypeScript
function getHiddenSettingsMenu(admin: Want): Array<SettingsMenu>
```

获取配置在当前用户下被隐藏的设置项列表。

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceSettings-function getHiddenSettingsMenu(admin: Want): Array<SettingsMenu>--><!--Device-deviceSettings-function getHiddenSettingsMenu(admin: Want): Array<SettingsMenu>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<SettingsMenu> | 隐藏的设置项列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
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
  const rawList: Array<number> = deviceSettings.getHiddenSettingsMenu(wantTemp) as Array<number>;
  for (const item of rawList) {
    const menu: deviceSettings.SettingsMenu = item as deviceSettings.SettingsMenu;
    console.info(`Valid SettingsMenu item: ${item} -> ${menu}`);
  }
  console.info('Succeeded in getting hidden settings menu.');
} catch (err) {
  console.error(`Failed to get hidden settings menu. Code: ${err.code}, message: ${err.message}`);
}

```

