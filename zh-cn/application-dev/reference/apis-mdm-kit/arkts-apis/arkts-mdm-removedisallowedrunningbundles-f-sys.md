# removeDisallowedRunningBundles（系统接口）

## removeDisallowedRunningBundles

```TypeScript
function removeDisallowedRunningBundles(admin: Want, appIds: Array<string>, callback: AsyncCallback<void>): void
```

移除在应用运行禁止名单中的应用，在禁止名单存在的情况下，在应用运行禁止名单中的应用不允许在当前用户下运行。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [removeDisallowedRunningBundlesSync](arkts-mdm-removedisallowedrunningbundlessync-f.md#removedisallowedrunningbundlessync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIds | Array&lt;string&gt; | 是 | 应用ID数组，指定具体应用。<br/>**说明：** 从API version 21版本开始，数组中的元素支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)和[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)，仅移除传入的[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)（或[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)），不会移除同一应用的[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)（或[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)）。API version 20及之前版本，数组中的元素只支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当接口调用成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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

applicationManager.removeDisallowedRunningBundles(wantTemp, appIds, (err) => {
  if (err) {
    console.error(`Failed to remove disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in removing disallowed running bundles');
});

```


## removeDisallowedRunningBundles

```TypeScript
function removeDisallowedRunningBundles(admin: Want, appIds: Array<string>, userId: number, callback: AsyncCallback<void>): void
```

移除在应用运行禁止名单中的应用，在禁止名单存在的情况下，在应用运行禁止名单中的应用不允许在指定用户（通过userId指定）下运行。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [removeDisallowedRunningBundlesSync](arkts-mdm-removedisallowedrunningbundlessync-f.md#removedisallowedrunningbundlessync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIds | Array&lt;string&gt; | 是 | 应用ID数组，指定具体应用。<br/>**说明：** 从API version 21版本开始，数组中的元素支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)和[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)，仅移除传入的[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)（或[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)），不会移除同一应用的[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)（或[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)）。API version 20及之前版本，数组中的元素只支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)。 |
| userId | number | 是 | 用户ID，指定具体用户。取值范围：大于等于0。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当接口调用成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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

applicationManager.removeDisallowedRunningBundles(wantTemp, appIds, 100, (err) => {
  if (err) {
    console.error(`Failed to remove disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in removing disallowed running bundles');
});

```


## removeDisallowedRunningBundles

```TypeScript
function removeDisallowedRunningBundles(admin: Want, appIds: Array<string>, userId?: number): Promise<void>
```

移除当前/指定用户在应用运行禁止名单中的应用，使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [removeDisallowedRunningBundlesSync](arkts-mdm-removedisallowedrunningbundlessync-f.md#removedisallowedrunningbundlessync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIds | Array&lt;string&gt; | 是 | 应用ID数组，指定具体应用。<br/>**说明：** 从API version 21版本开始，数组中的元素支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)和[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)，仅移除传入的[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)（或[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)），不会移除同一应用的[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)（或[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)）。API version 20及之前版本，数组中的元素只支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)。 |
| userId | number | 否 | 用户ID，取值范围：大于等于0。<br> - 调用接口时，若传入userId，表示指定用户。<br> - 调用接口时，若未传入userId，表示当前用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。当移除应用运行禁止名单失败时，会抛出错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.removeDisallowedRunningBundles(wantTemp, appIds, 100).then(() => {
  console.info('Succeeded in removing disallowed running bundles');
}).catch((err: BusinessError) => {
  console.error(`Failed to remove disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
});

```

