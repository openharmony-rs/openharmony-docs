# addAllowedUsbDevices

## addAllowedUsbDevices

```TypeScript
function addAllowedUsbDevices(admin: Want, usbDeviceIds: Array<UsbDeviceId>): void
```

����USB�豸����������

��������£����ñ��ӿڻᱨ���Գ�ͻ��

1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸USB����USBת����������
2. �Ѿ�ͨ��[setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setUsbStorageDeviceAccessPolicy-1)�ӿ�������USB�洢�豸���ʲ���Ϊ���á�
3. �Ѿ�ͨ��[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)�ӿ������˽�ֹʹ�õ�USB�豸���͡�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| usbDeviceIds | Array&lt;UsbDeviceId&gt; | 是 | USB�豸ID���飬UsbDeviceId��Ϣ����ͨ��<br/>[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)�ӿڻ�ȡ��USB�豸�����������鳤������Ϊ1000������ǰ��������������300��USB�豸ID����ֻ������<br/>����700���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200007](../../errorcode-universal.md#9200007-The) | The system ability works abnormally. |
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
  let usbDeviceIds: Array<usbManager.UsbDeviceId> = [{
    vendorId: 1,
    productId: 1
  }];
  usbManager.addAllowedUsbDevices(wantTemp, usbDeviceIds);
  console.info(`Succeeded in adding allowed USB devices.`);
} catch (err) {
  console.error(`Failed to add allowed USB devices. Code: ${err.code}, message: ${err.message}`);
}

```

