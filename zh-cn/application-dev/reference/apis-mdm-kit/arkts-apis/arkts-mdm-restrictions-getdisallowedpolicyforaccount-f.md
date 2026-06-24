# getDisallowedPolicyForAccount

## getDisallowedPolicyForAccount

```TypeScript
function getDisallowedPolicyForAccount(admin: Want | null, feature: string, accountId: number): boolean
```

��ȡָ���û���ĳ����״̬��

**起始版本：** 14

**废弃版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� [since 14 - 19] |
| feature | string | 是 | feature���ơ�<br/>- fingerprint���豸ָ����֤��������ǰ��֧��PC/2in1�豸ʹ�á�ʹ�ô˲���ʱ�����¹��򣺵��Ѿ�ͨ��<br/>[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)<br/>�ӿ����ý���/����ָ���û����豸ָ����֤��������ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)��<br/>�ڽ����豸ָ����֤����ʱ�����߻Ḳ��ǰ�ߵĲ��ԡ�����ʱ���ñ��ӿڽ��Ϊfalse��<br/>- mtpClient20+��MTP�ͻ���������������д�룩����ǰ��֧��PC/2in1�豸ʹ�á�MTP��<br/>MediaTransferProtocol��ý�崫��Э�飩����Э�������û����ƶ��豸�����Է���ý���ļ���<br/>- usbStorageDeviceWrite20+��USB�洢�豸д����������ǰ��֧<br/>��PC/2in1��ҵ�豸ʹ�á�<br/>- diskRecoveryKey20+���ָ�<br/>[��Կ����](../../../../security/UniversalKeystoreKit/huks-export-key-arkts.md)��������ǰ��֧��PC/2in1�豸ʹ�á�<br/>- sudo20+<br/>��superuser do����ʾ�Գ����û�ִ�У���ǰ��֧��PC/2in1�豸ʹ�á����ú���ҵ�ռ����˿ռ䲻���Գ����û�ִ�С�<br/>- distributedTransmissionOutgoing20+���豸�䵥�������ݵ��������������������豸�������ݣ���<br/>- print20+���豸��ӡ��������API version 23֮ǰ��֧��PC/2in1�豸ʹ�ã���API<br/>version 23��ʼ֧��PC/2in1��Phone��Tablet�豸�����ʹ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)��<br/>�ڽ������豸��ӡ��������ͨ��<br/>[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)<br/>�ӿ�����ĳ�û��µ��豸��ӡ������ͨ�����ӿڲ�ѯ����Ǹ��û������ô�ӡ��������ʵ�ʴ�ӡ�����ѱ����á�<br/>- openFileBoost23+���ļ��򿪼���������ΪӦ���ṩ�ļ��򿪼���״̬��֪������Ӧ�ÿ���ͨ�������ӦAPI����֪�ļ��ļ���״̬������Ӧ�ÿ���ʵ�ֶ��Ѽ����ļ��������ص�UI��user interface����ʶ�ȹ��ܣ��Ż��û��ļ������飬��ǰ��֧��PC/<br/>2in1�豸ʹ�á� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | admin - ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� [since 20] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-the) | the administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: boolean = restrictions.getDisallowedPolicyForAccount(wantTemp, 'fingerprint', 100);
  console.info(`Succeeded in querying is the fingerprint function disabled : ${result}`);
} catch (err) {
  console.error(`Failed to set fingerprint disabled. Code is ${err.code}, message is ${err.message}`);
}

```


## getDisallowedPolicyForAccount

```TypeScript
function getDisallowedPolicyForAccount(admin: Want | null, feature: FeatureForAccount, accountId: number): boolean
```

��ȡָ���û���ĳ����״̬��

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| feature | FeatureForAccount | 是 | ָ��Ҫ��ѯ���û����ԡ� |
| accountId | number | 是 | �˺�ID<br/><br/>ȡֵӦΪ��0��������<br/>- �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��<br/>[getOsAccountLocalId](@ohos.account.osAccount:osAccount.AccountManager.getOsAccountLocalId(callback:<br/>AsyncCallback))<br/>�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | The value **true** means the feature is disabled; the value **false** means the opposite. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-the) | the administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: boolean = restrictions.getDisallowedPolicyForAccount(wantTemp, restrictions.FeatureForAccount.SUPER_HUB, 100);
  console.info(`Succeeded in querying whether the super hub is disabled: ${result}`);
} catch (err) {
  console.error(`Failed to get whether super hub is disabled. Code is ${err.code}, message is ${err.message}`);
}

```

