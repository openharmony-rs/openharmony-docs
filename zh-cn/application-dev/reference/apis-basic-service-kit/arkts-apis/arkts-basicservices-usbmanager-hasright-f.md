# hasRight

## hasRight

```TypeScript
function hasRight(deviceName: string): boolean
```

�ж��Ƿ���Ȩ���ʸ��豸��
�����ʹ���ߡ��������App��ϵͳ����Ȩ�����豸�򷵻�true����Ȩ�����豸�򷵻�false��

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceName | string | 是 | �豸���ƣ�����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ���豸�б�USBDevice��name�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true��ʾ�з����豸��Ȩ�ޣ�false��ʾû�з����豸��Ȩ�ޡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

**示例：**

```TypeScript
function hasRight(): boolean {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return false;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  usbManager.requestRight(device.name);
  let right: boolean = usbManager.hasRight(device.name);
  console.info(`${right}`);
  return right;
}

```

