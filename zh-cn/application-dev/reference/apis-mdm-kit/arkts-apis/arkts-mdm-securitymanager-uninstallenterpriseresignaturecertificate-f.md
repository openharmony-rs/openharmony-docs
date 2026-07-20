# uninstallEnterpriseReSignatureCertificate

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

<a id="uninstallenterpriseresignaturecertificate"></a>
## uninstallEnterpriseReSignatureCertificate

```TypeScript
function uninstallEnterpriseReSignatureCertificate(admin: Want, certificateAlias: string, accountId: number): void
```

卸载企业应用重签名证书。

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function uninstallEnterpriseReSignatureCertificate(admin: Want, certificateAlias: string, accountId: int): void--><!--Device-securityManager-function uninstallEnterpriseReSignatureCertificate(admin: Want, certificateAlias: string, accountId: int): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| certificateAlias | string | 是 | 证书别名，必须以'.cer'结尾。 |
| accountId | number | 是 | 用户ID，指定具体用户，取值范围：大于等于0。accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。*@ohos.account.osAccount** to obtain the account ID. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9201008](../errorcode-enterpriseDeviceManager.md#9201008-企业重签名证书不存在) | The certificate does not exist. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let certificateAlias: string = 'test.cer';
// 需根据实际情况进行替换
let accountId: number = 100;
try {
  securityManager.uninstallEnterpriseReSignatureCertificate(
    wantTemp, certificateAlias, accountId);
  console.info('Success to uninstall enterprise re signature certificate.');
} catch (err) {
  console.error(`Failed to uninstall enterprise re signature certificate.
    Code: ${err.code}, message: ${err.message}`);
};

```

