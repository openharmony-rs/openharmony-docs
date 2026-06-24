# connectDevice

## connectDevice

```TypeScript
function connectDevice(device: USBDevice): Readonly<USBDevicePipe>
```

����getDevices()���ص��豸��Ϣ��USB�豸�����USB�����쳣�����ܷ���`undefined`��ע����Ҫ�Խӿڷ���ֵ���пմ�����

1. ��Ҫ����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ�豸��Ϣ�Լ�device;
2. ����[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1)����ʹ�ø��豸��Ȩ�ޡ�

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | USBDevice | 是 | USB�豸��Ϣ����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ��busNum��devAddressȷ���豸����ǰ�������Բ��������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly&lt;USBDevicePipe&gt; | ָ���Ĵ���ͨ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |
| [14400001](../../errorcode-universal.md#14400001-Access) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../../errorcode-universal.md#14400004) |  |
| [14400012](../../errorcode-universal.md#14400012) |  |

**示例：**

```TypeScript
function connectDevice() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  usbManager.requestRight(device.name);
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  console.info(`devicepipe = ${devicepipe}`);
}

```

