# setManagedBrowserPolicy

## setManagedBrowserPolicy

```TypeScript
function setManagedBrowserPolicy(admin: Want, bundleName: string, policyName: string, policyValue: string): void
```

为指定的浏览器设置浏览器策略，适用于企业统一管理员工浏览器行为的场景，例如配置浏览器安全策略等。成功后会发布系统公共事件 [COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_managed_browser_policy_changed)。 > **说明：** > > 在多MDM应用场景下，针对同一浏览器的同一策略，一旦被首个Admin配置并生效，其他Admin将无法配置。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_SET_BROWSER_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-browser-function setManagedBrowserPolicy(admin: Want, bundleName: string, policyName: string, policyValue: string): void--><!--Device-browser-function setManagedBrowserPolicy(admin: Want, bundleName: string, policyName: string, policyValue: string): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 应用包名，用于指定浏览器，表示应用的唯一标识。 |
| policyName | string | 是 | 浏览器策略名，由接口调用方和指定浏览器约定。 |
| policyValue | string | 是 | 浏览器策略值。当此值为空字符串时，表示取消浏览器策略名对应浏览器子策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

```TypeScript
import { browser } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
// 浏览器应用包名
let bundleName: string = 'com.example.testbrowser';
// 浏览器策略名称
let policyName: string = 'InsecurePrivateNetworkRequestsAllowed';
// 浏览器策略值
let policyValue: string = '{"level":"mandatory","scope":"machine","source":"platform","value":true}';

try {
  browser.setManagedBrowserPolicy(wantTemp, bundleName, policyName, policyValue);
  console.info('Succeeded in setting managed browser policy.');
} catch (err) {
  console.error(`Failed to set managed browser policy. Code is ${err.code}, message is ${err.message}`);
}
```

