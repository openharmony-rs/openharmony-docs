# closePipe

## closePipe

```TypeScript
function closePipe(pipe: USBDevicePipe): number
```

�ر��豸��Ϣ����ͨ����

1. ��Ҫ����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ�豸�б���
2. ����[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1)��ȡ�豸����Ȩ�ޣ�
3. ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)�õ�devicepipe��Ϊ������

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | ����ȷ��USB�豸��Ϣ����ͨ������Ҫ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)��ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | �ر��豸��Ϣ����ͨ���ɹ�����0���ر��豸��Ϣ����ͨ��ʧ�ܷ����������������£�<br/><br/>- 22�������쳣�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

**示例：**

```TypeScript
function closePipe() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  usbManager.requestRight(devicesList?.[0]?.name);
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(devicesList?.[0]);
  let ret: number = usbManager.closePipe(devicepipe);
  console.info(`closePipe = ${ret}`);
}

```

