# removeRight

## removeRight

```TypeScript
function removeRight(deviceName: string): boolean
```

�Ƴ������������豸��Ȩ�ޡ�ϵͳӦ��Ĭ��ӵ�з����豸Ȩ�ޣ����ô˽ӿڲ������Ӱ�졣

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceName | string | 是 | �豸���ƣ�����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ���豸�б�USBDevice��name�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ����Ȩ���Ƴ����������true��ʾȨ���Ƴ��ɹ�������false���ʾȨ���Ƴ�ʧ�ܡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

**示例：**

```TypeScript
function removeRight(): boolean {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return false;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  if (usbManager.removeRight(device.name)) {
    console.info(`Succeed in removing right`);
    return true;
  }
  return false;
}

```

