# setInstallLocalEnterpriseAppEnabledForAccount

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## setInstallLocalEnterpriseAppEnabledForAccount

```TypeScript
function setInstallLocalEnterpriseAppEnabledForAccount(admin: Want, isEnable: boolean, accountId: number): void
```

设置指定用户下是否支持本地安装企业应用。在具备本地安装能力的PC/2in1企业设备上下发支持本地企业应用策略后，用户可以在桌面或者文件管理器直接双击企业应用安装包，即可直接安装企业应用。

仅支持enterprise_normal或enterprise_mdm签名类型的企业应用。

> **说明：**  
>  
> 满足以下任意条件，PC/2in1企业设备在当前用户下即支持本地安装企业应用：  
>

<!--RP7--><!--RP7End-->

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemManager-function setInstallLocalEnterpriseAppEnabledForAccount(admin: Want, isEnable: boolean, accountId: number): void--><!--Device-systemManager-function setInstallLocalEnterpriseAppEnabledForAccount(admin: Want, isEnable: boolean, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| isEnable | boolean | 是 | 是否支持本地安装企业应用。true表示支持，false表示不支持。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取<br>取值应为≥0的整数。 |

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

import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let isEnable: boolean = true;
let accountId: number = 100;
try {
  systemManager.setInstallLocalEnterpriseAppEnabledForAccount(wantTemp, isEnable, accountId);
  console.info('Succeeded in setting InstallLocalEnterpriseAppEnabledForAccount.');
} catch (err) {
  console.error(`Failed to set installLocalEnterpriseAppEnabledForAccount. Code is ${err.code}, message is ${err.message}`);
}

```

