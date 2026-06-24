# getDomainAccountPolicy

## getDomainAccountPolicy

```TypeScript
function getDomainAccountPolicy(admin: Want, domainAccountInfo: osAccount.DomainAccountInfo): DomainAccountPolicy
```

��ȡ���˺Ų��ԡ�

**起始版本：** 19

**需要权限：** ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| domainAccountInfo | osAccount.DomainAccountInfo | 是 | ���˺���Ϣ��<br/>�������domainAccountInfo�ڲ����Ծ�Ϊ�գ����ѯȫ�����˺Ų��ԡ�<br/>�������domainAccountInfo�ڲ����Բ�Ϊ�գ����ѯָ�����˺Ų��ԡ�<br/>**˵��**������ѯָ�����˺Ų��ԣ�DomainAccountInfo��serverConfigId�ֶα�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DomainAccountPolicy | ���˺Ų��ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |

**示例：**

```TypeScript
import { accountManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError, osAccount } from '@kit.BasicServicesKit';

async function getDomainAccountPolicy() {
  let wantTemp: Want = {
    // 需根据实际情况进行替换
    bundleName: 'com.example.myapplication',
    abilityName: 'EnterpriseAdminAbility'
  };
  let domainAccountPolicy: accountManager.DomainAccountPolicy = {};
  // 查询全局域账号策略
  let accountInfo: osAccount.DomainAccountInfo = {
    domain: '',
    accountName: '',
    serverConfigId: ''
  };
  try {
    domainAccountPolicy = accountManager.getDomainAccountPolicy(wantTemp, accountInfo);
    console.info('Succeeded in getting global domain account policy.');
  } catch (err) {
    console.error(`Failed to get domain account policy. Code: ${err.code}, message: ${err.message}`);
  }
  // 查询指定域账号策略
  let accountInfo2: osAccount.DomainAccountInfo = {
    domain: '',
    accountName: '',
    serverConfigId: ''
  };
  // 需根据实际情况进行替换
  let userId: number = 100;
  await osAccount.getAccountManager()
    .getOsAccountDomainInfo(userId)
    .then((domainAccountInfo: osAccount.DomainAccountInfo) => {
      accountInfo2 = domainAccountInfo;
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to get account domain info. Code: ${err.code}, message: ${err.message}`);
    })
  try {
    domainAccountPolicy = accountManager.getDomainAccountPolicy(wantTemp, accountInfo2);
    console.info('Succeeded in getting domain account policy.');
  } catch (err) {
    console.error(`Failed to get domain account policy. Code: ${err.code}, message: ${err.message}`);
  }
}

```

