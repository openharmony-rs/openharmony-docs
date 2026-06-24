# setDisallowedPolicyForAccount

## setDisallowedPolicyForAccount

```TypeScript
function setDisallowedPolicyForAccount(admin: Want, feature: string, disallow: boolean, accountId: number): void
```

���ý���/����ָ���û���ĳ���ԡ�

**起始版本：** 14

**废弃版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| feature | string | 是 | feature���ơ�<br/>- fingerprint���豸ָ����֤��������ǰ��֧��PC/2in1�豸ʹ�á�ʹ�ô˲���ʱ�����¹���<br/>1. ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)��<br/>�ڽ������豸ָ����֤��������ʹ�ñ��ӿڴ���˲������ᱨ���Գ�ͻ��<br/>2. ͨ�����ӿ����ý���/����ָ���û����豸ָ����֤��������ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)��<br/>�ڽ����豸ָ����֤����ʱ�����߻Ḳ��ǰ�ߵĲ��ԡ��˺���ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)��<br/>�������豸ָ����֤�������������û�������ʹ���豸ָ����֤������<br/>- print20+���豸��ӡ��������API version 23֮ǰ��֧��PC/2in1�豸ʹ�ã���API version 2<br/>3��ʼ֧��PC/2in1��Phone��Tablet�豸�����ʹ�ñ��ӿڽ�����ָ���û����豸��ӡ��������ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)��<br/>�������豸��ӡ���������û��µ��豸��ӡ������Ȼ�����á�<br/>- mtpClient20+��MTP�ͻ���������������д�룩����ǰ��֧��PC/2in1�豸ʹ�á�MTP��<br/>MediaTransferProtocol��ý�崫��Э�飩����Э�������û����ƶ��豸�����Է���ý���ļ������Ѿ�ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)��<br/>�ڽ������豸MTP�ͻ�������ʱ����ͨ�����ӿڽ���ĳ�û�MTP�ͻ���д���������ᱨ���Գ�ͻ��<br/>- usbStorageDeviceWrite20+��USB�洢�豸д����������ǰ��֧��PC/2in<br/>1��ҵ�豸ʹ�á�<br/>�������������ͨ�����ӿڽ���ĳ�û�USB�洢�豸д���������ᱨ���Գ�ͻ��<br/>1��ͨ��<br/>[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)��<br/>���������豸USB�������á�<br/>2��ͨ��<br/>[setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setUsbStorageDeviceAccessPolicy-1)<br/>�ӿ�������USB�洢�豸���ʲ���Ϊֻ��/���á�<br/>3��ͨ��<br/>[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)�ӿ������˴洢���͵�USB�豸��<br/>�á�<br/>- diskRecoveryKey20+���ָ�<br/>[��Կ����](../../../../security/UniversalKeystoreKit/huks-export-key-arkts.md)��������ǰ��֧��PC/2in1�豸ʹ�á�<br/>- sudo20+<br/>��superuser do����ʾ�Գ����û�ִ�У���ǰ��֧��PC/2in1�豸ʹ�á����ú���ҵ�ռ����˿ռ䲻���Գ����û�ִ�С�<br/>- distributedTransmissionOutgoing20+���豸�䵥�������ݵ��������������������豸�������ݣ���<br/>- openFileBoost23+���ļ��򿪼���������ΪӦ���ṩ��<br/>���򿪼���״̬��֪������Ӧ�ÿ���ͨ�������ӦAPI����֪�ļ��ļ���״̬������Ӧ�ÿ���ʵ�ֶ��Ѽ����ļ��������ص�UI��user interface����ʶ�ȹ��ܣ��Ż��û��ļ������飬��ǰ��֧��PC/2in1�豸ʹ�á� |
| disallow | boolean | 是 | true��ʾ���ã�false��ʾ���á� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>�Ƚӿ�����ȡ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-the) | the administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
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
  restrictions.setDisallowedPolicyForAccount(wantTemp, 'fingerprint', true, 100);
  console.info('Succeeded in setting fingerprint disabled');
} catch (err) {
  console.error(`Failed to set fingerprint disabled. Code is ${err.code}, message is ${err.message}`);
}

```


## setDisallowedPolicyForAccount

```TypeScript
function setDisallowedPolicyForAccount(admin: Want, feature: FeatureForAccount, disallow: boolean, accountId: number): void
```

���ý���/����ָ���û���ĳ���ԡ�

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| feature | FeatureForAccount | 是 | feature���ơ�<br/>- - Ҫ���û��������û����ԡ�<br/>��featureֵΪSUPER_HUBʱ������Ѿ�ͨ��<br/>[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addUserNonStopApps-1)�ӿڽ���תվ���ӵ���<br/>ǰ�û��²��ɹ�ͣ��Ӧ���б��У��ٵ��ñ��ӿڽ�����תվ���ᷢ�����Գ�ͻ���׳�9200010�����롣����ͨ��<br/>[removeUserNonStopApps](arkts-mdm-applicationmanager-removeusernonstopapps-f.md#removeUserNonStopApps-1)�ӿڽ���<br/>תվ�ӵ�ǰ�û��²��ɹ�ͣ��Ӧ���б����Ƴ��������ͻ�� |
| disallow | boolean | 是 | true��ʾ���ã�false��ʾ���á� |
| accountId | number | 是 | �û�ID<br/><br/>ȡֵӦΪ��0��������<br/>- �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��<br/>[getOsAccountLocalId](@ohos.account.osAccount:osAccount.AccountManager.getOsAccountLocalId(callback:<br/>AsyncCallback))<br/>�Ƚӿ�����ȡ��<br/>��featureֵΪSUPER_HUBʱ��accountId��֧�ִ��뵱ǰ�û����û�ID����֧�ֿ��û����á�������׳�9200012�����롣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-the) | the administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
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
  restrictions.setDisallowedPolicyForAccount(wantTemp, restrictions.FeatureForAccount.SUPER_HUB, true, 100);
  console.info('Succeeded in setting super hub disabled');
} catch (err) {
  console.error(`Failed to set super hub disabled. Code is ${err.code}, message is ${err.message}`);
}

```

