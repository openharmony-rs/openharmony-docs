# isOsAccountAdditionDisallowed

## isOsAccountAdditionDisallowed

```TypeScript
function isOsAccountAdditionDisallowed(admin: Want, accountId?: number): boolean
```

查询是否禁止用户添加账号。适用于企业审计和合规检查场景，帮助管理员确认账号策略执行情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accountManager-function isOsAccountAdditionDisallowed(admin: Want, accountId?: number): boolean--><!--Device-accountManager-function isOsAccountAdditionDisallowed(admin: Want, accountId?: number): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 否 | 用户ID，指定具体用户。当不传入此参数时，表示查询所有用户是否禁止添加账号；当传入此参数时，表示查询指定用户是否禁止添加账号。取值范围：大于等于0。 &lt;br/&gt;accountId可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示禁止添加账号。&lt;br/&gt;返回false表示允许添加账号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |


## isOsAccountAdditionDisallowed

```TypeScript
function isOsAccountAdditionDisallowed(admin: Want | null, accountId?: number): boolean
```

查询是否禁止用户添加账号。适用于企业审计和合规检查场景，帮助管理员确认账号策略执行情况。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accountManager-function isOsAccountAdditionDisallowed(admin: Want | null, accountId?: number): boolean--><!--Device-accountManager-function isOsAccountAdditionDisallowed(admin: Want | null, accountId?: number): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 &lt;br&gt;当设备存在多个MDM应用时，传入Want时查询对应企业设备管理应用设置的策略，传入null时查询实际生效的策略。 |
| accountId | number | 否 | 用户ID，指定具体用户。当不传入此参数时，表示查询所有用户是否禁止添加账号；当传入此参数时，表示查询指定用户是否禁止添加账号。取值范围：大于等于0。 &lt;br/&gt;accountId可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示禁止添加账号。&lt;br/&gt;返回false表示允许添加账号。 |

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
  let isDisallowed: boolean = accountManager.isOsAccountAdditionDisallowed(wantTemp, 100);
  console.info(`Succeeded in querying the os account addition or not: ${isDisallowed}`);
} catch (err) {
  console.error(`Failed to query the os account addition or not. Code: ${err.code}, message: ${err.message}`);
}
```

