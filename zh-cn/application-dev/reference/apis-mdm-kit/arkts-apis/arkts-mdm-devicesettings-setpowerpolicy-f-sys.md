# setPowerPolicy（系统接口）

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

<a id="setpowerpolicy"></a>
## setPowerPolicy

```TypeScript
function setPowerPolicy(admin: Want, powerScene: PowerScene, powerPolicy: PowerPolicy): void
```

设置电源策略。

**起始版本：** 11

**废弃版本：** 26.0.0

**替代接口：** [setValue](arkts-mdm-devicesettings-setvalue-f.md#setvalue-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceSettings-function setPowerPolicy(admin: Want, powerScene: PowerScene, powerPolicy: PowerPolicy): void--><!--Device-deviceSettings-function setPowerPolicy(admin: Want, powerScene: PowerScene, powerPolicy: PowerPolicy): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| powerScene | [PowerScene](arkts-mdm-devicesettings-powerscene-e-sys.md) | 是 | 电源策略场景，当前只支持超时场景。 |
| powerPolicy | [PowerPolicy](arkts-mdm-devicesettings-powerpolicy-i-sys.md) | 是 | 电源策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
  let delayTime = 0;
  let powerScene: deviceSettings.PowerScene = deviceSettings.PowerScene.TIME_OUT;
  let powerPolicyAction: deviceSettings.PowerPolicyAction = deviceSettings.PowerPolicyAction.AUTO_SUSPEND;
  let powerPolicy: deviceSettings.PowerPolicy = {powerPolicyAction, delayTime};
  deviceSettings.setPowerPolicy(wantTemp, powerScene, powerPolicy);
  console.info(`Succeeded in setting power policy`);
} catch (err) {
  console.error(`Failed to set power policy. Code: ${err.code}, message: ${err.message}`);
}

```

