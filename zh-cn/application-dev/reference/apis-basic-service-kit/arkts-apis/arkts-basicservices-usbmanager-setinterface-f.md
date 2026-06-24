# setInterface

## setInterface

```TypeScript
function setInterface(pipe: USBDevicePipe, iface: USBInterface): number
```

�����豸�ӿڡ�

> **˵����**
>
> һ��USB�ӿڿ��ܴ��ڶ���ѡ��ģʽ��֧�ֶ�̬�л���ʹ�õĳ��������ݴ���ʱ��ͨ���ýӿڿ��������ö˵㣬ʹ�˵��봫������ƥ�䡣
>
> �ڵ��øýӿ�ǰ��Ҫͨ��
> [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface-1)
> claimͨ�Žӿڡ�

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | ����ȷ�����ߺź��豸��ַ����Ҫ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)��ȡ�� |
| iface | USBInterface | 是 | ����ȷ����Ҫ���õĽӿڣ���Ҫ����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ�豸��Ϣ��ͨ��id��alternateSettingȷ��Ψһ�ӿڡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | �����豸�ӿڳɹ�����0�������豸�ӿ�ʧ�ܷ����������������£�<br/><br/>- 88080389������δ����������ԭ��1.���豸���룻2.�����쳣�˳���<br/><br/>- 88080486�������ʼ���У����Ժ����ԡ�<br/><br/>- 88080488�����豸����Ȩ�ޣ����ȵ���[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1)�ӿ�������Ȩ��<br/><br/>- -1�������쳣 �� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

**示例：**

```TypeScript
function setInterface() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  usbManager.requestRight(device.name);
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  let interfaces: usbManager.USBInterface = device.configs?.[0]?.interfaces?.[0];
  let ret: number = usbManager.claimInterface(devicepipe, interfaces);
  ret = usbManager.setInterface(devicepipe, interfaces);
  console.info(`setInterface = ${ret}`);
}

```

