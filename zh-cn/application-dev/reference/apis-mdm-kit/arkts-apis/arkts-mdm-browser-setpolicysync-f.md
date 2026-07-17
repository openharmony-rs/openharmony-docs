# setPolicySync

## 导入模块

```TypeScript
import { browser } from '@kit.MDMKit';
```

## setPolicySync

```TypeScript
function setPolicySync(admin: Want, appId: string, policyName: string, policyValue: string): void
```

为指定的浏览器设置浏览器子策略。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_SET_BROWSER_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-browser-function setPolicySync(admin: Want, appId: string, policyName: string, policyValue: string): void--><!--Device-browser-function setPolicySync(admin: Want, appId: string, policyName: string, policyValue: string): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appId | string | 是 | 应用appId，用于指定浏览器，表示应用的唯一标识，详情信息可参考[什么是appId](../../../../quick-start/common-problem-of-application.md#什么是appid)。 |
| policyName | string | 是 | 浏览器子策略名，由接口调用方和指定浏览器约定。当此值为空字符串时，表示设置应用appId对应的浏览器策略。 |
| policyValue | string | 是 | 浏览器子策略值，由接口调用方和指定浏览器约定。当此值为空字符串时，表示取消浏览器策略名对应浏览器子策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { browser } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 此处参数appId的赋值应替换为开发者自己指定的浏览器的应用ID
let appId: string = 'com.example.******_******/******5t5CoBM=';
// 浏览器策略名称
let policyName: string = 'InsecurePrivateNetworkRequestsAllowed';
// 浏览器策略值
let policyValue: string = '{"level":"mandatory","scope":"machine","source":"platform","value":true}';

try {
  browser.setPolicySync(wantTemp, appId, policyName, policyValue);
  console.info('Succeeded in setting browser policies.');
} catch (err) {
  console.error(`Failed to set browser policies. Code is ${err.code}, message is ${err.message}`);
}

```

