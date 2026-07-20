# setInstallLocalEnterpriseAppEnabled

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

<a id="setinstalllocalenterpriseappenabled"></a>
## setInstallLocalEnterpriseAppEnabled

```TypeScript
function setInstallLocalEnterpriseAppEnabled(admin: Want, isEnable: boolean): void
```

设置是否支持本地安装企业应用。设置为支持安装后，具备本地安装能力的PC/2in1企业设备可本地双击应用安装包，安装签名证书分发类型为enterprise_normal的企业应用。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemManager-function setInstallLocalEnterpriseAppEnabled(admin: Want, isEnable: boolean): void--><!--Device-systemManager-function setInstallLocalEnterpriseAppEnabled(admin: Want, isEnable: boolean): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| isEnable | boolean | 是 | 是否支持本地安装企业应用。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript

import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let isEnable: boolean = true;
try {
  systemManager.setInstallLocalEnterpriseAppEnabled(wantTemp, isEnable);
  console.info('Succeeded in setting InstallLocalEnterpriseAppEnabled.');
} catch (err) {
  console.error(`Failed to set installLocalEnterpriseAppEnabled. Code is ${err.code}, message is ${err.message}`);
}

```

