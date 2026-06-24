# UsbDataTransferParams

��Ϊͨ��USB���ݴ���ӿڣ��ͻ�����Ҫ�����������еĲ��������Է���������

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## buffer

```TypeScript
buffer: Uint8Array
```

���ڴ洢������д����ʱ�����ݡ�

**类型：** Uint8Array

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## callback

```TypeScript
callback: AsyncCallback<SubmitTransferCallback>
```

�������ʱ�Ļص���Ϣ��

**类型：** AsyncCallback<SubmitTransferCallback>

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## devPipe

```TypeScript
devPipe: USBDevicePipe
```

����ȷ�����ߵ�ַ���豸��ַ����Ҫ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)��ȡ��

**类型：** USBDevicePipe

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## endpoint

```TypeScript
endpoint: number
```

�˵��ַ����������

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## flags

```TypeScript
flags: UsbTransferFlags
```

USB�����־��

**类型：** UsbTransferFlags

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## isoPacketCount

```TypeScript
isoPacketCount: number
```

ʵʱ����ʱ���ݰ��������������ھ���ʵʱ����˵��I/O�������ǷǸ���������λ����������

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## length

```TypeScript
length: number
```

���ݻ������ĳ��ȣ������ǷǸ������������ȣ�������λ���ֽڣ���

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## timeout

```TypeScript
timeout: number
```

��ʱʱ�䡣����λ�����룩��

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## type

```TypeScript
type: UsbEndpointTransferType
```

�������͡�

**类型：** UsbEndpointTransferType

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## userData

```TypeScript
userData: Uint8Array
```

�û����������ݡ�

**类型：** Uint8Array

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

