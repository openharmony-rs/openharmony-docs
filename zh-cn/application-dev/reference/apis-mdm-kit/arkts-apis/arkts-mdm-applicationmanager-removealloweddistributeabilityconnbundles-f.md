# removeAllowedDistributeAbilityConnBundles

## removeAllowedDistributeAbilityConnBundles

```TypeScript
function removeAllowedDistributeAbilityConnBundles(admin: Want, appIdentifiers: Array<string>, serviceType: ServiceType, accountId: number): void
```

为指定用户下的特定分布式业务移除允许跨设备的应用名单。移除后，若名单中还有剩余的应用，则仅名单中的应用可以不受 [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount)的限制， 通过使用该特定分布式业务跨设备传输数据；若名单已被清空，无剩余的应用，则所有应用在指定用户下都不允许使用该特定分布式业务跨设备传输数据。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function removeAllowedDistributeAbilityConnBundles(admin: Want, appIdentifiers: Array<string>, serviceType: ServiceType, accountId: number): void--><!--Device-applicationManager-function removeAllowedDistributeAbilityConnBundles(admin: Want, appIdentifiers: Array<string>, serviceType: ServiceType, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appIdentifiers | Array&lt;string&gt; | 是 | 应用[唯一标识符](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md#SignatureInfo)的数组，可以通过接口 [bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo)获取 bundleInfo.signatureInfo.appIdentifier。允许列表总数不能超过200个。 |
| serviceType | ServiceType | 是 | 分布式业务类型。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0的整数。 &lt;br&gt; accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId)等接口来获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
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

try {
  // 需根据实际情况进行替换
  let appIdentifiers: Array<string> = ['6917****3569'];
  let accountId: number = 100;
  applicationManager.removeAllowedDistributeAbilityConnBundles(wantTemp, appIdentifiers, applicationManager.ServiceType.COLLABORATION_SERVICE, accountId);
  console.info('Succeeded in removing allowed distribute ability conn bundles.');
  // 注意：移除用户下允许使用协同业务的应用名单后，是否需要解除禁用该用户下的设备间单向传输数据能力，应根据实际业务需求判断。
} catch(err) {
  console.error(`Failed to remove allowed distribute ability conn bundles. Code: ${err.code}, message: ${err.message}`);
}
```

