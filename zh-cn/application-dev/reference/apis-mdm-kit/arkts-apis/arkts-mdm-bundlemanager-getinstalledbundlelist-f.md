# getInstalledBundleList

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## getInstalledBundleList

```TypeScript
function getInstalledBundleList(admin: Want, accountId: number): Promise<Array<BundleInfo>>
```

获取设备指定用户下已安装应用列表。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getInstalledBundleList(admin: Want, accountId: number): Promise<Array<BundleInfo>>--><!--Device-bundleManager-function getInstalledBundleList(admin: Want, accountId: number): Promise<Array<BundleInfo>>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 是 | 用户ID，取值为正整数，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleInfo&gt;&gt; | Promise对象，返回已安装应用包信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let accountId: number = 100;
bundleManager.getInstalledBundleList(wantTemp, accountId).then((result) => {
  console.info('Succeeded in getting installed bundle list.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get installed bundle list. Code is ${err.code}, message is ${err.message}`);
});

```


## getInstalledBundleList

```TypeScript
function getInstalledBundleList(admin: Want, accountId: number, bundleInfoGetFlag: number): Promise<Array<BundleInfo>>
```

根据给定的bundleInfoGetFlag获取设备指定用户下已安装应用列表。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getInstalledBundleList(admin: Want, accountId: int, bundleInfoGetFlag: int): Promise<Array<BundleInfo>>--><!--Device-bundleManager-function getInstalledBundleList(admin: Want, accountId: int, bundleInfoGetFlag: int): Promise<Array<BundleInfo>>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 是 | 账号ID<br>取值应为≥0的整数。   - 用户ID，取值为正整数，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。 |
| bundleInfoGetFlag | number | 是 | 指定返回的BundleInfo所包含的信息。<br>取值范围为全体整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleInfo&gt;&gt; | Promise对象，返回已安装应用包信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let accountId: number = 100;
let bundleInfoGetFlag: number = bundleManager.BundleInfoGetFlag.WITH_APPLICATION_INFO
  | bundleManager.BundleInfoGetFlag.WITH_SIGNATURE_INFO;
bundleManager.getInstalledBundleList(wantTemp, accountId, bundleInfoGetFlag).then((result) => {
  console.info('Succeeded in getting installed bundle list.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get installed bundle list. Code is ${err.code}, message is ${err.message}`);
});

```

