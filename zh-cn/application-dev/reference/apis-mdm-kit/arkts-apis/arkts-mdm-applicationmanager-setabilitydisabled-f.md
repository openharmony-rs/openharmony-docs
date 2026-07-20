# setAbilityDisabled

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

<a id="setabilitydisabled"></a>
## setAbilityDisabled

```TypeScript
function setAbilityDisabled(admin: Want, bundleName: string, accountId: number, abilityName: string, isDisabled: boolean): void
```

设置是否禁用指定应用（系统应用和三方应用均支持）的Ability组件。当前仅支持UIAbility类型，禁用后无法拉起此Ability组件的用户界面。

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function setAbilityDisabled(admin: Want, bundleName: string, accountId: number, abilityName: string, isDisabled: boolean): void--><!--Device-applicationManager-function setAbilityDisabled(admin: Want, bundleName: string, accountId: number, abilityName: string, isDisabled: boolean): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 应用包名，指定是否禁用的应用包名。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0的整数。<br>取值范围为全体整数。   - 用户ID，取值范围：大于等于0的整数。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |
| abilityName | string | 是 | 表示要禁用/解除禁用的Ability组件名（当前仅支持UIAbility）。 |
| isDisabled | boolean | 是 | 是否禁用该Ability组件。true表示禁用该Ability组件，false表示解除禁用该Ability组件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let bundleName: string = "com.example.exampleapplication";
  let accountId: number = 100;
  let abilityName: string = "EntryAbility";
  applicationManager.setAbilityDisabled(wantTemp, bundleName, accountId, abilityName, true);
  console.info('Succeeded in setting ability disabled');
} catch(err) {
  console.error(`Failed to set ability disabled. Code: ${err.code}, message: ${err.message}`);
}

```

