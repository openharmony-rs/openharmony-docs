# addKeepAliveApps

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

<a id="addkeepaliveapps"></a>
## addKeepAliveApps

```TypeScript
function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number): void
```

添加保活应用名单，添加后将自动保活应用进程。在开机和应用被杀死后，由系统主动拉起应用进程。<!--RP7--><!--RP7End-->

通过本接口添加至保活名单的应用，禁止用户在设备上手动取消保活<!--RP6--><!--RP6End-->，但可通过[removeKeepAliveApps](arkts-mdm-applicationmanager-removekeepaliveapps-f.md#removekeepaliveapps-1)接口将应用从保活名单中移除。

如果将应用添加至应用禁止运行名单[addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#adddisallowedrunningbundlessync-1)，就不能将应用添加至保活应用名单，否则会报9200010冲突错误码。

如果需要在Phone/Tablet设备使用类似功能，可以调用[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addusernonstopapps-1)或者[addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addfreezeexemptedapps-1)接口，具体功能请参考相关文档。

**起始版本：** 14

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number): void--><!--Device-applicationManager-function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleNames | Array&lt;string&gt; | 是 | 应用包名数组，指定需要添加至保活名单的应用，最大支持5个。<!--RP5--><!--RP5End--> |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-策略冲突) | A conflict policy has been configured. |
| [9201005](../errorcode-enterpriseDeviceManager.md#9201005-添加保活应用失败) | Add keep alive applications failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |

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
let bundleNames: Array<string> = ['com.example.myapplication'];

try {
  applicationManager.addKeepAliveApps(wantTemp, bundleNames, 100);
  console.info('Succeeded in adding keep alive apps.');
} catch (err) {
  console.error(`Failed to add keep alive apps. Code is ${err.code}, message is ${err.message}`);
}

```


<a id="addkeepaliveapps-1"></a>
## addKeepAliveApps

```TypeScript
function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number, disallowModify: boolean): void
```

添加保活应用名单，并设置是否禁止用户手动取消保活，添加后将自动保活应用进程。在开机和应用被杀死后，由系统主动拉起应用进程。

通过本接口、[addKeepAliveApps](arkts-mdm-applicationmanager-addkeepaliveapps-f.md#addkeepaliveapps-1)接口均可添加保活应用名单，两个接口的设置可同时生效。同一用户下，保活应用名单最多支持包含5个应用。例如：若当前名单中已有3个应用，则最多还能通过本接口为当前用户添加2个应用。

如果通过[addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#adddisallowedrunningbundlessync-1)接口将应用添加至应用禁止运行名单，就不能将应用添加至保活应用名单，否则会报9200010冲突错误码。

如果需要在Phone/Tablet设备使用类似功能，可以调用[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addusernonstopapps-1)或者[addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addfreezeexemptedapps-1)接口，具体功能请参考相关文档。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number, disallowModify: boolean): void--><!--Device-applicationManager-function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number, disallowModify: boolean): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleNames | Array&lt;string&gt; | 是 | 应用包名数组，指定需要添加至保活名单的应用，最大支持5个。<br>应用需要满足条件：安装在1用户下（1用户是支持三方应用单例运行的用户），且应用接入[后台服务](docroot://application-models/app-service-extension-ability.md#实现一个后台服务)<!--RP3--><!--RP3End-->。否则，会报错误码9201005。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |
| disallowModify | boolean | 是 | 是否禁止用户手动取消应用保活，true表示禁止，false表示允许。<!--RP2--><!--RP2End--> |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-策略冲突) | A conflict policy has been configured. |
| [9201005](../errorcode-enterpriseDeviceManager.md#9201005-添加保活应用失败) | Add keep alive applications failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |

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
let bundleNames: Array<string> = ['com.example.myapplication'];

try {
  applicationManager.addKeepAliveApps(wantTemp, bundleNames, 100, true);
  console.info('Succeeded in adding keep alive apps and set disallowModify.');
} catch (err) {
  console.error(`Failed to add keep alive apps and set disallowModify. Code is ${err.code}, message is ${err.message}`);
}

```

