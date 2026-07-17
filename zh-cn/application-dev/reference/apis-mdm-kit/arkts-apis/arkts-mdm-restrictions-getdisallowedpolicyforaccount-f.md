# getDisallowedPolicyForAccount

## 导入模块

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## getDisallowedPolicyForAccount

```TypeScript
function getDisallowedPolicyForAccount(admin: Want | null, feature: string, accountId: number): boolean
```

获取指定用户的某特性状态。

**起始版本：** 14

**废弃版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-restrictions-function getDisallowedPolicyForAccount(admin: Want | null, feature: string, accountId: number): boolean--><!--Device-restrictions-function getDisallowedPolicyForAccount(admin: Want | null, feature: string, accountId: number): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。<br>**起始版本：** 14 - 19 |
| feature | string | 是 | feature名称。<br/>- fingerprint：设备指纹认证能力，当前仅支持PC/2in1设备使用。使用此参数时有以下规则：当已经通过[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount-1)接口设置禁用/启用指定用户的设备指纹认证能力后，再通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口禁用设备指纹认证能力时，后者会覆盖前者的策略。即此时调用本接口结果为false。<br/>- mtpClient&lt;sup&gt;20+&lt;/sup&gt;：MTP客户端能力（仅包含写入），当前仅支持PC/2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。<br/>- usbStorageDeviceWrite&lt;sup&gt;20+&lt;/sup&gt;：USB存储设备写入能力，当前仅支持PC/2in1企业设备使用。<br/>- diskRecoveryKey&lt;sup&gt;20+&lt;/sup&gt;：恢复[密钥导出](../../../../security/UniversalKeystoreKit/huks-export-key-arkts.md)能力，当前仅支持PC/2in1设备使用。<br/>- sudo&lt;sup&gt;20+&lt;/sup&gt;：superuser do，表示以超级用户执行，当前仅支持PC/2in1设备使用。禁用后企业空间或个人空间不能以超级用户执行。<br/>- distributedTransmissionOutgoing&lt;sup  &gt;20+&lt;/sup&gt;：设备间单向传输数据的能力（仅包含向其他设备传输数据）。<br/>- print&lt;sup&gt;20+&lt;/sup&gt;：设备打印能力，在API version 23之前仅支持PC/2in1设备使用，从API version 23开始支持PC/2in1、Phone、Tablet设备。如果使用[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口禁用了设备打印能力，再通过[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount-1)接口启用某用户下的设备打印能力，通过本接口查询结果是该用户已启用打印能力，但实际打印能力已被禁用。<br/>- openFileBoost&lt;sup&gt;23+&lt;/sup&gt;：&lt;!--RP6--&gt;文件打开加速能力&lt;!--RP6End--&gt;，为应用提供文件打开加速状态感知能力。应用可以通过接入对应API，感知文件的加速状态，进而应用可以实现对已加速文件给出独特的UI（user interface）标识等功能，优化用户文件打开体验，当前仅支持PC/2in1设备使用。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | admin - 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | the administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: boolean = restrictions.getDisallowedPolicyForAccount(wantTemp, 'fingerprint', 100);
  console.info(`Succeeded in querying is the fingerprint function disabled : ${result}`);
} catch (err) {
  console.error(`Failed to set fingerprint disabled. Code is ${err.code}, message is ${err.message}`);
}

```


## getDisallowedPolicyForAccount

```TypeScript
function getDisallowedPolicyForAccount(admin: Want | null, feature: FeatureForAccount, accountId: number): boolean
```

获取指定用户的某特性状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-restrictions-function getDisallowedPolicyForAccount(admin: Want | null, feature: FeatureForAccount, accountId: number): boolean--><!--Device-restrictions-function getDisallowedPolicyForAccount(admin: Want | null, feature: FeatureForAccount, accountId: number): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| feature | [FeatureForAccount](arkts-mdm-restrictions-featureforaccount-e.md) | 是 | 指定要查询的用户特性。 |
| accountId | number | 是 | 账号ID<br>取值应为≥0的整数。  - 用户ID，取值范围：大于等于0。<br>accountId可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | The value **true** means the feature is disabled; the value **false** means the opposite. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | the administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: boolean = restrictions.getDisallowedPolicyForAccount(wantTemp, restrictions.FeatureForAccount.SUPER_HUB, 100);
  console.info(`Succeeded in querying whether the super hub is disabled: ${result}`);
} catch (err) {
  console.error(`Failed to get whether super hub is disabled. Code is ${err.code}, message is ${err.message}`);
}

```

