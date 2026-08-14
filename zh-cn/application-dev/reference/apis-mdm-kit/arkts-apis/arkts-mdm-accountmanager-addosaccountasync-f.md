# addOsAccountAsync

## addOsAccountAsync

```TypeScript
function addOsAccountAsync(admin: Want, name: string, type: osAccount.OsAccountType): Promise<osAccount.OsAccountInfo>
```

后台添加账号。使用Promise异步回调。适用于企业批量创建账号或远程管理场景，无需用户交互即可完成账号创建，提升管理效率。 > **说明：** > > 创建账号的流程比较耗时，当调用此接口后，后续如果在应用主线程调用其他同步接口时需要等待该接口异步返回。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accountManager-function addOsAccountAsync(admin: Want, name: string, type: osAccount.OsAccountType): Promise<osAccount.OsAccountInfo>--><!--Device-accountManager-function addOsAccountAsync(admin: Want, name: string, type: osAccount.OsAccountType): Promise<osAccount.OsAccountInfo>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| name | string | 是 | 账号名，指要添加的账号的名称。无法创建同名、名称为空的账号，创建同名账号时会报错误码9201003，创建名称为空的账号时会报错误码401。 |
| type | osAccount.OsAccountType | 是 | 要添加的账号的类型。&lt;br/&gt;取值范围：ADMIN、NORMAL、GUEST。&lt;br/&gt;· ADMIN：管理员账号。&lt;br/&gt;· NORMAL：普 通账号。&lt;br/&gt;· GUEST：访客账号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;osAccount.OsAccountInfo&gt; | Promise对象，返回添加的账号信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9201003](../errorcode-enterpriseDeviceManager.md#9201003-创建账号失败) | Failed to add an OS account. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

```TypeScript
import { accountManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError, osAccount } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 参数需根据实际情况进行替换
accountManager.addOsAccountAsync(wantTemp, "TestAccountName", osAccount.OsAccountType.NORMAL).then((info) => {
  console.info(`Succeeded in creating os account: ${JSON.stringify(info)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create os account. Code: ${err.code}, message: ${err.message}`);
});
```

