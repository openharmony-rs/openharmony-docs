# addAllowedRunningBundles

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addAllowedRunningBundles

```TypeScript
function addAllowedRunningBundles(admin: Want, appIdentifiers: Array<string>, accountId: number): void
```

添加应用至应用运行允许名单，添加至允许名单的应用允许在指定用户下运行，不在允许名单的应用不允许在指定用户下运行。 > **说明：** > > 1. 由于MDM Kit下大多数接口仅对MDM应用开放，本接口使用时，请将MDM应用同时添加至应用运行允许名单，否则会导致MDM应用不允许运行，阻塞接口调用。接口是否仅对MDM应用开放请查看对应的模块说明。 > > 2. 如果应用运行禁止名单非空，不支持再使用本接口添加应用运行允许名单，否则会报9200010冲突错误码。应用运行禁止名单相关接口包括 > [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md)、 > [addDisallowedRunningBundles](arkts-mdm-applicationmanager-adddisallowedrunningbundles-f-sys.md)、 > [addDisallowedRunningBundles](arkts-mdm-applicationmanager-adddisallowedrunningbundles-f-sys.md)、 > [addDisallowedRunningBundles](arkts-mdm-applicationmanager-adddisallowedrunningbundles-f-sys.md)。 > > 3. 本接口仅对三方应用生效，系统应用不受该名单管控，默认可以运行。

**起始版本：** 21

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function addAllowedRunningBundles(admin: Want, appIdentifiers: Array<string>, accountId: number): void--><!--Device-applicationManager-function addAllowedRunningBundles(admin: Want, appIdentifiers: Array<string>, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIdentifiers | Array&lt;string&gt; | 是 | 应用 [唯一标识符](../../../quick-start/common-problem-of-application.md#什么是appidentifier)的数组，可以通过接口 [bundleManager.getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md) 获取bundleInfo.signatureInfo.appIdentifier。 <br>取值范围： <br> - 单个用户下该名单总数不能超过200。例如100用户下已经设置了50个、101用户未设置，则100用户还能再设置150个，101用户还能再设置200个。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。 <br> accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-策略冲突) | A conflict policy has been configured. |
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
// 需根据实际情况进行替换
let appIdentifiers: Array<string> = ['0123456789123456789'];

try {
  applicationManager.addAllowedRunningBundles(wantTemp, appIdentifiers, 100);
  console.info('Succeeded in adding allowed running bundles.');
} catch (err) {
  console.error(`Failed to add allowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```

