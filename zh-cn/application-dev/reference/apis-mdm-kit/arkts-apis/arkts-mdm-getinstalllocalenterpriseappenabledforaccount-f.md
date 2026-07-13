# getInstallLocalEnterpriseAppEnabledForAccount

## getInstallLocalEnterpriseAppEnabledForAccount

```TypeScript
function getInstallLocalEnterpriseAppEnabledForAccount(admin: Want | null, accountId: number): boolean
```

查询指定用户是否支持本地安装企业应用。

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。<br/>当设备有多个MDM应用时，传入admin查询对应admin设置的策略。传入null时查询整机实际生效的策略。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](@ohos.account.osAccount:osAccount.AccountManager.getOsAccountLocalId(callback:AsyncCallback&lt;int&gt;))等接口来获取<br>取值应为≥0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持本地安装企业应用，true为支持，false为不支持。当admin为null时，查询系统当前是否支持本地安装企业应用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let accountId: number = 100;
try {
  let isEnable: boolean = systemManager.getInstallLocalEnterpriseAppEnabledForAccount(wantTemp, accountId);
  console.info('Succeeded in getting installLocalEnterpriseAppEnabled.');
} catch (err) {
  console.error(`Failed to get installLocalEnterpriseAppEnabled. Code is ${err.code}, message is ${err.message}`);
}

```

