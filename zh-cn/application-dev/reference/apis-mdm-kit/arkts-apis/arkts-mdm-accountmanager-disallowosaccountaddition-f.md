# disallowOsAccountAddition

## disallowOsAccountAddition

```TypeScript
function disallowOsAccountAddition(admin: Want, disallow: boolean, accountId?: number): void
```

禁止用户添加账号。调用成功后，系统将禁止指定用户或所有用户添加新账号。适用于企业设备管理场景，如防止员工随意创建本地账号、加强设备安全管理等。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accountManager-function disallowOsAccountAddition(admin: Want, disallow: boolean, accountId?: number): void--><!--Device-accountManager-function disallowOsAccountAddition(admin: Want, disallow: boolean, accountId?: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| disallow | boolean | 是 | 是否禁止创建账号，true表示禁止创建，false表示允许创建。 |
| accountId | number | 否 | 用户ID，指定具体用户。当不传入此参数时，表示禁止所有用户添加账号；当传入此参数时，表示禁止指定用户添加账号。取值范围：大于等于0。&lt;br/&gt;accountId可以通 过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId)等接口来获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

```TypeScript
import { accountManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  accountManager.disallowOsAccountAddition(wantTemp, true, 100);
  console.info('Succeeded in disallowing os account addition.');
} catch (err) {
  console.error(`Failed to disallow os account addition. Code: ${err.code}, message: ${err.message}`);
}
```

