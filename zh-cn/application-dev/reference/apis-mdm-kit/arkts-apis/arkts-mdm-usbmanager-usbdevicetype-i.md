# UsbDeviceType

USB�豸������Ϣ��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## baseClass

```TypeScript
baseClass: number
```

���ͱ��롣

��ͨ��[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)�ӿڻ�ȡ�ѽ������豸��USB�豸�б������ڷ���ֵ�б��в��ҵ�ǰ�豸���鿴��ֵ��

�ȸ��ݴ�ֵȷ��descriptorӦ�ô�������͡���descriptorΪDEVICE�����ֶ�ȡUSBDevice.clazz�ֶ�ֵ����descriptorΪINTERFACE�����ֶ�ȡ
USBDevice.configs.interfaces.clazz�ֶ�ֵ��

���ֶ�ֵΪ255����ʾ���豸�����ͱ����ǳ����Զ�����룬��ʹ��[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)/
[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removeDisallowedUsbDevices-1)�ӿڽ���/������豸����Ч�����ֶ�ֵδ��
[defined-class-codes](https://www.usb.org/defined-class-codes)�ж��壬��ʹ��
[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)/
[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removeDisallowedUsbDevices-1)�ӿڽ���/������豸����Ч��

**类型：** number

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## descriptor

```TypeScript
descriptor: Descriptor
```

USB��������

��ͨ��[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)�ӿڻ�ȡ�ѽ������豸��USB�豸�б������ڷ���ֵ�б��в��ҵ�ǰ�豸���鿴��ֵ��

����ֵUSBDevice.clazz�ֶ�ֵΪ0��������[defined-class-codes](https://www.usb.org/defined-class-codes)�е�Base Class�в��Ҵ�ֵ
USBDevice.configs.interfaces.clazz�ֶ�ֵ�����ҽ������������Ӧ��Descriptor Usage�оͱ�ʾ��ǰӦ�ô����descriptor���ͣ���Descriptor Usage��ΪBoth��
��ʾ�������Ͷ����Դ��룬��Ҫ�豸������ʱ����DEVICE����Ҫ�ӿڼ�����ʱ����INTERFACE��;

����ֵUSBDevice.clazz�ֶ�ֵΪ255����ʾ���豸�����ͱ����ǳ����Զ�����룬��ʹ��
[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)/
[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removeDisallowedUsbDevices-1)�ӿڽ���/������豸����Ч������ֵUSBDevice.clazz�ֶ�ֵΪ����ֵ��
������[defined-class-codes](https://www.usb.org/defined-class-codes)�е�Base Class�в��Ҹ�ֵ�����ҽ������������Ӧ��Descriptor Usage�оͱ�
ʾ��ǰӦ�ô����descriptor���ͣ���Descriptor Usage��ΪBoth����ʾ�������Ͷ����Դ��룬��Ҫ�豸������ʱ����DEVICE����Ҫ�ӿڼ�����ʱ����INTERFACE����

**类型：** Descriptor

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## protocol

```TypeScript
protocol: number
```

Э����롣

��ͨ��[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)�ӿڻ�ȡ�ѽ������豸��USB�豸�б������ڷ���ֵ�б��в��ҵ�ǰ�豸���鿴��ֵ��

�ȸ���baseClass��ֵȷ��descriptorӦ�ô�������͡���descriptorΪDEVICE�����ֶ�ȡUSBDevice.protocol�ֶ�ֵ����descriptorΪINTERFACE�����ֶ�ȡ
USBDevice.configs.interfaces.protocol�ֶ�ֵ��

���ֶ�ֵΪ255����ʾ���豸��Э������ǳ����Զ�����룬��ʹ��[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)/
[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removeDisallowedUsbDevices-1)�ӿڽ���/������豸����Ч�����ֶ�ֵδ��
[defined-class-codes](https://www.usb.org/defined-class-codes)�ж��壬��ʹ��
[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)/
[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removeDisallowedUsbDevices-1)�ӿڽ���/������豸����Ч��

**类型：** number

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## subClass

```TypeScript
subClass: number
```

�����ͱ��롣

��ͨ��[getDevices](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)�ӿڻ�ȡ�ѽ������豸��USB�豸�б������ڷ���ֵ�б��в��ҵ�ǰ�豸���鿴��ֵ��

�ȸ���baseClass��ֵȷ��descriptorӦ�ô�������͡���descriptorΪDEVICE�����ֶ�ȡUSBDevice.subClass�ֶ�ֵ����descriptorΪINTERFACE�����ֶ�ȡ
USBDevice.configs.interfaces.subClass�ֶ�ֵ��

���ֶ�ֵΪ255����ʾ���豸�������ͱ����ǳ����Զ�����룬��ʹ��[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)/
[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removeDisallowedUsbDevices-1)�ӿڽ���/������豸����Ч�����ֶ�ֵδ��
[defined-class-codes](https://www.usb.org/defined-class-codes)�ж��壬��ʹ��
[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#addDisallowedUsbDevices-1)/
[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removeDisallowedUsbDevices-1)�ӿڽ���/������豸����Ч��

**类型：** number

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

