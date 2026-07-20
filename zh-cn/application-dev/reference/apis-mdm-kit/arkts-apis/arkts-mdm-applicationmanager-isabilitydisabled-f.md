# isAbilityDisabled

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

<a id="isabilitydisabled"></a>
## isAbilityDisabled

```TypeScript
function isAbilityDisabled(admin: Want, bundleName: string, accountId: number, abilityName: string): boolean
```

获取指定应用（系统应用和三方应用均支持）的Ability组件是否被禁用。

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function isAbilityDisabled(admin: Want, bundleName: string, accountId: number, abilityName: string): boolean--><!--Device-applicationManager-function isAbilityDisabled(admin: Want, bundleName: string, accountId: number, abilityName: string): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 应用包名，指定是否禁用的应用包名。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0的整数。   - 用户ID，取值范围：大于等于0的整数。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |
| abilityName | string | 是 | 表示要禁用/解除禁用的Ability组件名称（当前仅支持UIAbility）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 该能力是否禁用。true表示该Ability组件被禁用，false表示该Ability组件未被禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

