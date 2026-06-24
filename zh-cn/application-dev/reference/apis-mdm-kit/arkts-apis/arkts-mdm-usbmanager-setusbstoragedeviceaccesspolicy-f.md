# setUsbStorageDeviceAccessPolicy

## setUsbStorageDeviceAccessPolicy

```TypeScript
function setUsbStorageDeviceAccessPolicy(admin: Want, usbPolicy: UsbPolicy): void
```

����USB�洢�豸���ʲ��ԡ�

> **˵��**��
> > �ڵ��ýӿ�ǰ��ȷ������ͣUSB�洢�豸�Ķ�д��������֤�������ȶ��Ժ����ݵ������ԣ�������ܳ��ֲ���Ԥ�ڵ��쳣��

��������£�ͨ�����ӿ�����USB�洢�豸���ʲ���Ϊ�ɶ���д/ֻ�����ᱨ���Գ�ͻ��

1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸USB������
2. �Ѿ�ͨ��[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)�ӿڽ��洢���͵�USB�豸����Ϊ��ֹʹ�õ�USB�豸���͡�
3. �Ѿ�ͨ��[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)�ӿڽ�����ĳ�û�USB�洢�豸д��������

��������£�ͨ�����ӿ�����USB�洢�豸���ʲ���Ϊ���ã��ᱨ���Գ�ͻ��

1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸USB������
2. �Ѿ�ͨ��[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addAllowedUsbDevices-1)�ӿ�������USB�豸����������
3. �Ѿ�ͨ��[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)�ӿڽ�����ĳ�û�USB�洢�豸д��������

ͨ�����ӿ����ã�����ͨ��[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)�ӿ����Ӵ洢���͵�USB�豸�����ɽ���USB�洢�豸���Ƽ�ʹ�ú��ߡ�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB, ohos.permission.ENTERPRISE_MANAGE_USB or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| usbPolicy | UsbPolicy | 是 | USB�洢�豸���ʲ��ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200007](../../errorcode-universal.md#9200007-The) | The system ability works abnormally. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let policy: usbManager.UsbPolicy = usbManager.UsbPolicy.DISABLED;
  usbManager.setUsbStorageDeviceAccessPolicy(wantTemp, policy);
  console.info(`Succeeded in setting USB storage device access policy.`);
} catch (err) {
  console.error(`Failed to set USB storage device access policy. Code: ${err.code}, message: ${err.message}`);
}

```

