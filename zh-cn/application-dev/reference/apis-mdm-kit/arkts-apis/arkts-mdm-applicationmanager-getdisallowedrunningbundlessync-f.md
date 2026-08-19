# getDisallowedRunningBundlesSync

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getDisallowedRunningBundlesSync

```TypeScript
function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array<string>
```

获取当前/指定用户下的应用运行禁止名单。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array<string>--><!--Device-applicationManager-function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 否 | 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。<br/> - 调用接口时，若传入accountId，表示指定用户。<br/> - 调用接口时，若未传入accountId，表示当前用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回当前/指定用户下的应用运行禁止名单。<br/>**说明：** API version 20及之前版本，返回值为应用 [appId](../../../quick-start/common-problem-of-application.md#什么是appid)列表。从API version 21版本开始，返回值为应用 [appId](../../../quick-start/common-problem-of-application.md#什么是appid)或 [appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<string> = applicationManager.getDisallowedRunningBundlesSync(wantTemp);
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```


## getDisallowedRunningBundlesSync

```TypeScript
function getDisallowedRunningBundlesSync(admin: Want | null, accountId?: number): Array<string>
```

获取当前/指定用户下的应用运行禁止名单。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getDisallowedRunningBundlesSync(admin: Want | null, accountId?: number): Array<string>--><!--Device-applicationManager-function getDisallowedRunningBundlesSync(admin: Want | null, accountId?: number): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 当设备存在多个MDM应用时，传入Want时查询对应企业设备管理应用设置的策略，传入null时查询实际生效的策略。 |
| accountId | number | 否 | 用户ID，取值范围：大于等于0。 <br> accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。<br/> - 调用接口时，若传入accountId，表示指定用户。<br/> - 调用接口时，若未传入accountId，表示当前用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回当前/指定用户下的应用运行禁止名单。<br/>**说明：** 返回值为应用 [appId](../../../quick-start/common-problem-of-application.md#什么是appid)或 [appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { applicationManager } from '@kit.MDMKit';

try {
  // 参数需根据实际情况进行替换
  let result: Array<string> = applicationManager.getDisallowedRunningBundlesSync(null);
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```

