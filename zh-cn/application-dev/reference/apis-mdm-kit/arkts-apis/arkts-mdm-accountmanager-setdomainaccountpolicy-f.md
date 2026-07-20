# setDomainAccountPolicy

## 导入模块

```TypeScript
import { accountManager } from '@kit.MDMKit';
```

<a id="setdomainaccountpolicy"></a>
## setDomainAccountPolicy

```TypeScript
function setDomainAccountPolicy(admin: Want, domainAccountInfo: osAccount.DomainAccountInfo, policy: DomainAccountPolicy): void
```

设置域账号策略。

**起始版本：** 19

**需要权限：** ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accountManager-function setDomainAccountPolicy(admin: Want, domainAccountInfo: osAccount.DomainAccountInfo, policy: DomainAccountPolicy): void--><!--Device-accountManager-function setDomainAccountPolicy(admin: Want, domainAccountInfo: osAccount.DomainAccountInfo, policy: DomainAccountPolicy): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| domainAccountInfo | osAccount.DomainAccountInfo | 是 | 域账号信息。<br />若传入的domainAccountInfo内部属性均为空，则会设置为全局域账号策略。全局策略对所有的域账号生效。<br />若传入的domainAccountInfo内部属性不为空，则为指定域账号设置策略。<br />指定域账号策略的优先级高于全局策略，若指定域账号已有域账号策略，则全局策略对其不生效。<br/>**说明**：若为指定域账号设置策略，DomainAccountInfo的serverConfigId字段必填。 |
| policy | [DomainAccountPolicy](arkts-mdm-accountmanager-domainaccountpolicy-i.md) | 是 | 域账号策略。<br />**说明**：设置域账号策略后须在设备侧修改域账号密码，若未修改密码，则DomainAccountPolicy中的passwordValidityPeriod、passwordExpirationNotification配置不生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { accountManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError, osAccount } from '@kit.BasicServicesKit';

async function setDomainAccountPolicy() {
  let wantTemp: Want = {
    // 需根据实际情况进行替换
    bundleName: 'com.example.myapplication',
    abilityName: 'EnterpriseAdminAbility'
  };
  let policy: accountManager.DomainAccountPolicy = {
    // 需根据实际情况进行替换
    authenticationValidityPeriod: 300,
    passwordValidityPeriod: 420,
    passwordExpirationNotification: 60
  };
  // 设置全局域账号策略
  let accountInfo: osAccount.DomainAccountInfo = {
    domain: '',
    accountName: '',
    serverConfigId: ''
  };
  try {
    accountManager.setDomainAccountPolicy(wantTemp, accountInfo, policy);
    console.info('Succeeded in setting global domainAccount policy.');
  } catch (err) {
    console.error(`Failed to set domainAccount policy. Code: ${err.code}, message: ${err.message}`);
  }
  // 设置指定域账号策略
  let accountInfo2: osAccount.DomainAccountInfo = {
    domain: '',
    accountName: '',
    serverConfigId: ''
  };
  // 需根据实际情况替换
  let userId: number = 100;
  await osAccount.getAccountManager().getOsAccountDomainInfo(userId)
    .then((domainAccountInfo: osAccount.DomainAccountInfo) => {
      accountInfo2 = domainAccountInfo;
    }).catch((err: BusinessError) => {
      console.error(`Failed to get account domain info. Code: ${err.code}, message: ${err.message}`);
    })
  try {
    accountManager.setDomainAccountPolicy(wantTemp, accountInfo2, policy);
    console.info('Succeeded in setting domain account policy.');
  } catch (err) {
    console.error(`Failed to set domain account policy. Code: ${err.code}, message: ${err.message}`);
  }
}

```

