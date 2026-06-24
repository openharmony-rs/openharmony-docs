# addDisallowedUsbDevices

## addDisallowedUsbDevices

```TypeScript
function addDisallowedUsbDevices(admin: Want, usbDevices: Array<UsbDeviceType>): void
```

���ӽ�ֹʹ�õ�USB�豸���͡�

��������£����ñ��ӿڻᱨ���Գ�ͻ��

1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸USB������
2. �Ѿ�ͨ��[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addAllowedUsbDevices-1)�ӿ�������USB�豸����������
3. �Ѿ�ͨ��[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)�ӿڽ�����ĳ�û�USB�洢�豸д��������

**起始版本：** 14

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| usbDevices | Array&lt;UsbDeviceType&gt; | 是 | Ҫ���ӵ�USB�豸���͵����飬UsbDeviceType��Ϣ����ͨ��<br/>[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)�ӿڻ�ȡ��USB�豸�����������鳤������Ϊ200������ǰ��������������100��USB�豸ID����ֻ��������<br/>��100���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
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
  let usbDevices: Array<usbManager.UsbDeviceType> = [{
    baseClass: 8,
    subClass: 0,
    protocol: 0,
    descriptor: usbManager.Descriptor.INTERFACE
  }];
  usbManager.addDisallowedUsbDevices(wantTemp, usbDevices);
  console.info(`Succeeded in adding disallowed USB devices.`);
} catch (err) {
  console.error(`Failed to add disallowed USB devices. Code: ${err.code}, message: ${err.message}`);
}

```

