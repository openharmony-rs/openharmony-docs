# removeDisallowedRunningBundlesSync

## removeDisallowedRunningBundlesSync

```TypeScript
function removeDisallowedRunningBundlesSync(admin: Want, appIds: Array<string>, accountId?: number): void
```

将应用从当前/指定用户下的应用运行禁止名单中移除。移除后，该应用将允许在当前/指定用户下运行。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function removeDisallowedRunningBundlesSync(admin: Want, appIds: Array<string>, accountId?: number): void--><!--Device-applicationManager-function removeDisallowedRunningBundlesSync(admin: Want, appIds: Array<string>, accountId?: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIds | Array&lt;string&gt; | 是 | 应用ID数组，指定具体应用。&lt;br/&gt;**说明：** 从API version 21版本开始，数组中的元素支持使用 [appId](../../../quick-start/common-problem-of-application.md#什么是appid)和 [appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)，仅移除传入的 [appId](../../../quick-start/common-problem-of-application.md#什么是appid)（或 [appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)），不会移除同一应用的 [appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)（或 [appId](../../../quick-start/common-problem-of-application.md#什么是appid)）。API version 20及之前版本，数组中的元素只支持使用 [appId](../../../quick-start/common-problem-of-application.md#什么是appid)。 |
| accountId | number | 否 | 用户ID，取值范围：大于等于0。 &lt;br&gt; accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId)等接口来获取。 &lt;br&gt; - 调用接口时，若传入accountId，表示指定用户。 &lt;br&gt; - 调用接口时，若未传入accountId，表示当前用户。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  applicationManager.removeDisallowedRunningBundlesSync(wantTemp, appIds);
  console.info('Succeeded in removing disallowed running bundles.');
} catch (err) {
  console.error(`Failed to remove disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```

