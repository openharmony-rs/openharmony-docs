# getInstalledBundleStorageStats

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## getInstalledBundleStorageStats

```TypeScript
function getInstalledBundleStorageStats(admin: Want, bundleNames: Array<string>, accountId: number): Promise<Array<BundleStorageStats>>
```

获取设备指定用户下已安装应用的存储占用信息。使用Promise异步回调。

> **说明：**  
>  
> 1.仅能获取已安装应用的存储占用信息。  
>  
> 2.bundleNames参数为empty或全部传入未安装的应用包名，会抛出9200012错误码。  
>  
> 3.bundleNames参数传递的包名部分应用已安装，部分应用未安装时，接口返回正常，已安装的应用返回实际的存储占用信息，未安装的应用存储占用信息为0。  
>  
> 4.该接口支持跨用户查询，比如可以在100用户下，查询101用户下的某些应用的存储占用信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getInstalledBundleStorageStats(admin: Want, bundleNames: Array<string>, accountId: number): Promise<Array<BundleStorageStats>>--><!--Device-bundleManager-function getInstalledBundleStorageStats(admin: Want, bundleNames: Array<string>, accountId: number): Promise<Array<BundleStorageStats>>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleNames | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 应用包名列表。取值范围：小于等于200个应用包名。 |
| accountId | number | 是 | 账号ID<br>取值应为≥0的整数。  - 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-2)等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<BundleStorageStats>> | Promise对象，返回已安装应用的存储占用信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
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
let bundleNames: Array<string> = ['com.example.app1', 'com.example.app2'];
let accountId: number = 100;
bundleManager.getInstalledBundleStorageStats(wantTemp, bundleNames, accountId).then((result) => {
  console.info('Succeeded in getting installed bundle storage stats.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get installed bundle storage stats. Code is ${err.code}, message is ${err.message}`);
});

```

```TypeScript
// 返回示例
[
  {
    "bundleName": "com.example.edmtest",
    "appSize": 38185408,
    "dataSize": 1216566
  },
  // ...
]

```

