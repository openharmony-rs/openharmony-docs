# setDelegatedPolicies

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## setDelegatedPolicies

```TypeScript
function setDelegatedPolicies(admin: Want, bundleName: string, policies: Array<string>): void
```

委托其他应用来设置设备的管控策略。被委托的其他应用需申请委托策略对应接口所需权限。

**起始版本：** 14

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_DELEGATED_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function setDelegatedPolicies(admin: Want, bundleName: string, policies: Array<string>): void--><!--Device-adminManager-function setDelegatedPolicies(admin: Want, bundleName: string, policies: Array<string>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 被委托应用包名。被委托应用的分发类型需为enterprise_normal和enterprise_mdm，可以通过[getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself)接口查询应用自身的[BundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-i.md)，其中BundleInfo.appInfo.appDistributionType为应用的分发类型。 |
| policies | Array&lt;string&gt; | 是 | [委托策略列表](../../../reference/apis-mdm-kit/js-apis-enterprise-adminManager.md#可委托策略列表)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200009](../errorcode-enterpriseDeviceManager.md#9200009-授予应用权限失败) | Failed to grant the permission to the application. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let admin: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let policies: Array<string> = ["disabled_hdc"];

try {
  // 参数需根据实际情况进行替换
  adminManager.setDelegatedPolicies(admin, "com.example.enterprise.xxx", policies);
  console.info('Succeeded in setting delegated policies.');
} catch (err) {
  console.error(`Failed to set delegated policies. Code: ${err.code}, message: ${err.message}`);
}

```

