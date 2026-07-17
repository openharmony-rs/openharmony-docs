# getAllowedDistributeAbilityConnBundles

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getAllowedDistributeAbilityConnBundles

```TypeScript
function getAllowedDistributeAbilityConnBundles(admin: Want | null, serviceType: ServiceType, accountId: number): Array<string>
```

获取指定用户下允许使用指定类型的分布式能力的应用名单。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getAllowedDistributeAbilityConnBundles(admin: Want | null, serviceType: ServiceType, accountId: number): Array<string>--><!--Device-applicationManager-function getAllowedDistributeAbilityConnBundles(admin: Want | null, serviceType: ServiceType, accountId: number): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| serviceType | [ServiceType](../../apis-calendar-kit/arkts-apis/arkts-calendar-calendarmanager-servicetype-e.md) | 是 | 分布式能力类型。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0的整数。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-2)等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 允许使用指定类型的分布式能力的应用的[唯一标识符](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md)的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let accountId: number = 100;
  let result: Array<string> = applicationManager.getAllowedDistributeAbilityConnBundles(wantTemp, applicationManager.ServiceType.COLLABORATION_SERVICE, accountId);
  console.info(`Succeeded in getting allowed distribute ability conn bundles: ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get allowed distribute ability conn bundles. Code: ${err.code}, message: ${err.message}`);
}

```

