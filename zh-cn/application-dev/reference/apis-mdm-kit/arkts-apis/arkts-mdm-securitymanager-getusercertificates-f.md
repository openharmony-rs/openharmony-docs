# getUserCertificates

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## getUserCertificates

```TypeScript
function getUserCertificates(admin: Want, accountId: number): Array<string>
```

获取指定系统账户下的用户证书信息。

**起始版本：** 18

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function getUserCertificates(admin: Want, accountId: number): Array<string>--><!--Device-securityManager-function getUserCertificates(admin: Want, accountId: number): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 是 | 用户ID，指定具体用户，取值范围：大于等于0。accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-2)等接口来获取。*@ohos.account.osAccount** to obtain the account ID. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | All user certificates installed under the specified account ID. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |

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
let accountId: number = 100;
try {
  let result: Array<string> = securityManager.getUserCertificates(wantTemp, accountId);
  console.info(`Succeeded in getting the uri list of user Certificates. result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get the uri list of user Certificates. Code: ${err.code}, message: ${err.message}`);
}

```

