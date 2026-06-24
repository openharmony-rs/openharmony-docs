# @ohos.enterprise.usbManager

��ģ���ṩUSB����������

> **˵��**��
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ��ҵ��ýӿ�ǰ�輤���豸����Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��
>
> ȫ��ͨ�������������restrictionsͳһ�ṩ����Ҫȫ�ֽ���USB����ο�
> [@ohos.enterprise.restrictions����������ԣ�](arkts-enterprise-restrictions.md#restrictions)��

**起始版本：** 10

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addAllowedUsbDevices-1) | ����USB�豸����������<br/><br/>��������£����ñ��ӿڻᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸USB����USBת����������<br/>2. �Ѿ�ͨ��[setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setUsbStorageDeviceAccessPolicy-1)�ӿ�������USB�洢�豸���ʲ���Ϊ���á�<br/>3. �Ѿ�ͨ��[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)�ӿ������˽�ֹʹ�õ�USB�豸���͡�<br/> |
| [addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1) | ���ӽ�ֹʹ�õ�USB�豸���͡�<br/><br/>��������£����ñ��ӿڻᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸USB������<br/>2. �Ѿ�ͨ��[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addAllowedUsbDevices-1)�ӿ�������USB�豸����������<br/>3. �Ѿ�ͨ��[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)�ӿڽ�����ĳ�û�USB�洢�豸д��������<br/> |
| <!--DelRow-->[disableUsb](arkts-mdm-usbmanager-disableusb-f-sys.md#disableUsb-1) | ���ý��û�����USB��<br/> |
| [getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getAllowedUsbDevices-1) | ��ȡUSB�豸����������<br/> |
| [getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getDisallowedUsbDevices-1) | ��ȡ��ֹʹ�õ�USB�豸���͡�<br/> |
| [getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getUsbStorageDeviceAccessPolicy-1) | ��ȡUSB�洢�豸���ʲ��ԡ�<br/> |
| <!--DelRow-->[isUsbDisabled](arkts-mdm-usbmanager-isusbdisabled-f-sys.md#isUsbDisabled-1) | ��ѯUSB�Ƿ���á�<br/> |
| [removeAllowedUsbDevices](arkts-mdm-usbmanager-removeallowedusbdevices-f.md#removeAllowedUsbDevices-1) | �Ƴ�USB�豸����������<br/> |
| [removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removeDisallowedUsbDevices-1) | �Ƴ���ֹʹ�õ�USB�豸���͡�<br/> |
| <!--DelRow-->[setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setUsbPolicy-1) | ����USB�Ķ�д���ԡ�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setUsbPolicy-2) | ����USB�Ķ�д���ԡ�ʹ��Promise�첽�ص���<br/> |
| [setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setUsbStorageDeviceAccessPolicy-1) | ����USB�洢�豸���ʲ��ԡ�<br/><br/>&gt; **˵��**��<br/>&gt; &gt; �ڵ��ýӿ�ǰ��ȷ������ͣUSB�洢�豸�Ķ�д��������֤�������ȶ��Ժ����ݵ������ԣ�������ܳ��ֲ���Ԥ�ڵ��쳣��<br/><br/>��������£�ͨ�����ӿ�����USB�洢�豸���ʲ���Ϊ�ɶ���д/ֻ�����ᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸USB������<br/>2. �Ѿ�ͨ��[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)�ӿڽ��洢���͵�USB�豸����Ϊ��ֹʹ�õ�USB�豸���͡�<br/>3. �Ѿ�ͨ��[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)�ӿڽ�����ĳ�û�USB�洢�豸д��������<br/><br/>��������£�ͨ�����ӿ�����USB�洢�豸���ʲ���Ϊ���ã��ᱨ���Գ�ͻ��<br/><br/>1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸USB������<br/>2. �Ѿ�ͨ��[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addAllowedUsbDevices-1)�ӿ�������USB�豸����������<br/>3. �Ѿ�ͨ��[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)�ӿڽ�����ĳ�û�USB�洢�豸д��������<br/><br/>ͨ�����ӿ����ã�����ͨ��[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)�ӿ����Ӵ洢���͵�USB�豸�����ɽ���USB�洢�豸���Ƽ�ʹ�ú��ߡ�<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [UsbDeviceId](arkts-mdm-usbmanager-usbdeviceid-i.md) | USB�豸ID��Ϣ��<br/> |
| [UsbDeviceType](arkts-mdm-usbmanager-usbdevicetype-i.md) | USB�豸������Ϣ��<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Descriptor](arkts-mdm-usbmanager-descriptor-e.md) | USB��������ö�١�<br/> |
| [UsbPolicy](arkts-mdm-usbmanager-usbpolicy-e.md) | USB��д���Ե�ö�١�<br/> |

