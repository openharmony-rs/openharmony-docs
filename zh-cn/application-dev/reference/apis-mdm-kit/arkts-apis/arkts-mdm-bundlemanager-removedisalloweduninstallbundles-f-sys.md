# removeDisallowedUninstallBundles（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## removeDisallowedUninstallBundles

```TypeScript
function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, callback: AsyncCallback<void>): void
```

移除在应用程序包卸载禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前用户下卸载，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removedisalloweduninstallbundlessync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, callback: AsyncCallback<void>): void--><!--Device-bundleManager-function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIds | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 应用ID数组。<br/>**说明：** 从API version 21版本开始，数组中的元素支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)和[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)，仅移除传入的[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)（或[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)），不会移除同一应用的[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)（或[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)）。API version 20及之前版本，数组中的元素只支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当接口调用成功，err为null，否则为错误对象。 |

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

bundleManager.removeDisallowedUninstallBundles(wantTemp, appIds, (err) => {
  if (err) {
    console.error(`Failed to remove disallowed uninstall bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in removing disallowed uninstall bundles');
});

```


## removeDisallowedUninstallBundles

```TypeScript
function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, userId: number, callback: AsyncCallback<void>): void
```

移除在应用程序包卸载禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在指定用户（通过userId指定）下卸载。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removedisalloweduninstallbundlessync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, userId: number, callback: AsyncCallback<void>): void--><!--Device-bundleManager-function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, userId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIds | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 应用ID数组。<br/>**说明：** 从API version 21版本开始，数组中的元素支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)和[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)，仅移除传入的[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)（或[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)），不会移除同一应用的[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)（或[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)）。API version 20及之前版本，数组中的元素只支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)。 |
| userId | number | 是 | 用户ID，指定具体用户。取值范围：大于等于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当接口调用成功，err为null，否则为错误对象。 |

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

bundleManager.removeDisallowedUninstallBundles(wantTemp, appIds, 100, (err) => {
  if (err) {
    console.error(`Failed to remove disallowed uninstall bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in removing disallowed uninstall bundles');
});

```


## removeDisallowedUninstallBundles

```TypeScript
function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, userId?: number): Promise<void>
```

移除在应用程序包卸载禁止名单中的应用。在禁止名单存在的情况下，在禁止名单中的应用不允许在当前/指定用户下卸载。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removedisalloweduninstallbundlessync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, userId?: number): Promise<void>--><!--Device-bundleManager-function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, userId?: number): Promise<void>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIds | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 应用ID数组。<br/>**说明：** 从API version 21版本开始，数组中的元素支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)和[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)，仅移除传入的[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)（或[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)），不会移除同一应用的[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)（或[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)）。API version 20及之前版本，数组中的元素只支持使用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)。 |
| userId | number | 否 | 用户ID，取值范围：大于等于0。<br> - 调用接口时，若传入userId，表示指定用户。<br> - 调用接口时，若未传入userId，表示当前用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。当移除应用程序包卸载禁止名单失败时会抛出错误对象。 |

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

bundleManager.removeDisallowedUninstallBundles(wantTemp, appIds, 100).then(() => {
  console.info('Succeeded in removing disallowed uninstall bundles');
}).catch((err: BusinessError) => {
  console.error(`Failed to remove disallowed uninstall bundles. Code is ${err.code}, message is ${err.message}`);
});

```

