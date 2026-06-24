# claimInterface

## claimInterface

```TypeScript
function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number
```

������USB�豸ĳ���ӿڵĿ���Ȩ��

> **˵����**
>
> ��USB����У�claim interface��һ������������ָ����Ӧ�ó����������ϵͳ��ĳ��USB�ӿڴ��ں��������ͷŲ������û��ռ������ơ�<br>
> > �����õ���claimͨ�Žӿڶ���ʾclaim interface������

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | ����ȷ�����ߺź��豸��ַ����Ҫ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)��ȡ�� |
| iface | USBInterface | 是 | ����ȷ����Ҫ��ȡ�ӿڵ���������Ҫ����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ�豸��Ϣ��ͨ��idȷ��Ψһ�ӿڡ� |
| force | boolean | 否 | ��ѡ�������Ƿ�ǿ�ƻ�ȡ��Ĭ��ֵΪfalse?����ʾ��ǿ�ƻ�ȡ���û�����ѡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | claimͨ�Žӿڳɹ�����0��claimͨ�Žӿ�ʧ�ܷ����������������£�<br/><br/>- 88080389������δ����������ԭ��1.���豸���룻2.�����쳣�˳���<br/><br/>- 88080486�������ʼ���У����Ժ����ԡ�<br/><br/>- 88080488�����豸����Ȩ�ޣ����ȵ���[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1)�ӿ�������Ȩ��<br/><br/>- -1�������쳣�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

**示例：**

```TypeScript
function claimInterface() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  usbManager.requestRight(device.name);
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  let interfaces: usbManager.USBInterface = device.configs?.[0]?.interfaces?.[0];
  let ret: number= usbManager.claimInterface(devicepipe, interfaces);
  console.info(`claimInterface = ${ret}`);
}

```

