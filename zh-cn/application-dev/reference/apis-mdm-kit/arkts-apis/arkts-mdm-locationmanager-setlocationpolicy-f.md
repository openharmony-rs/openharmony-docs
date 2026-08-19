# setLocationPolicy

## 导入模块

```TypeScript
import { locationManager } from '@kit.MDMKit';
```

## setLocationPolicy

```TypeScript
function setLocationPolicy(admin: Want, policy: LocationPolicy): void
```

设置位置服务管理策略。可用于企业管控场景，如：在涉密区域禁用位置服务以保护信息安全，或在物流配送应用中强制开启位置服务以追踪设备位置。 > **说明：** > > - 禁用：在需要保护隐私或节省电量的场景下设置。 > > - 强制开启：在设备安全追踪、资产管理等场景下设置。 > > - 默认：取消策略限制，由用户自主控制。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_LOCATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-locationManager-function setLocationPolicy(admin: Want, policy: LocationPolicy): void--><!--Device-locationManager-function setLocationPolicy(admin: Want, policy: LocationPolicy): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| policy | [LocationPolicy](arkts-mdm-locationmanager-locationpolicy-e.md) | 是 | 位置服务策略。 <br>- 0：默认策略。 <br>- 1：禁用位置服务。 <br>- 2：强制开启位置服务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { locationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  locationManager.setLocationPolicy(wantTemp, locationManager.LocationPolicy.DISALLOW_LOCATION_SERVICE);
  console.info(`Succeeded in setting location policy.`);
} catch (err) {
  console.error(`Failed to set location policy. Code: ${err.code}, message: ${err.message}`);
}
```

