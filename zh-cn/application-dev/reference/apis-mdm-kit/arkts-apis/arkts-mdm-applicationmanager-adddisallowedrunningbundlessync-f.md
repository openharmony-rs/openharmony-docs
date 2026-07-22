# addDisallowedRunningBundlesSync

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addDisallowedRunningBundlesSync

```TypeScript
function addDisallowedRunningBundlesSync(
    admin: Want,
    appIds: Array<string>,
    accountId?: number
  ): void
```

添加应用至应用运行禁止名单，添加至禁止名单的应用不允许在当前/指定用户下运行。从API version 21开始，如果应用运行允许名单[addallowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md#addallowedrunningbundles)非空，就不能再通过本接口添加应用运行禁止名单，否则会报9200010冲突错误码。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function addDisallowedRunningBundlesSync(    admin: Want,    appIds: Array<string>,    accountId?: number  ): void--><!--Device-applicationManager-function addDisallowedRunningBundlesSync(    admin: Want,    appIds: Array<string>,    accountId?: number  ): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIds | Array&lt;string&gt; | 是 | 应用ID数组，指定具体应用。<br/>**说明：** 从API version 21版本开始，支持传入应用的[appId](../../../quick-start/common-problem-of-application.md#什么是appid)和[appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)，推荐使用[appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)。API version 20及之前版本，仅支持[appId](../../../quick-start/common-problem-of-application.md#什么是appid)。 |
| accountId | number | 否 | 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。<br>   - 调用接口时，若传入accountId，表示指定用户。<br> - 调用接口时，若未传入accountId，表示当前用户。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-策略冲突) | A conflict policy has been configured.<br>**适用版本：** 21+ |

**示例：**

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
  applicationManager.addDisallowedRunningBundlesSync(wantTemp, appIds);
  console.info('Succeeded in adding disallowed running bundles.');
} catch (err) {
  console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
}

```

