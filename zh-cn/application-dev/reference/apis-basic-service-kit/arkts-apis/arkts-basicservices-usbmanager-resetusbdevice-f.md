# resetUsbDevice

## resetUsbDevice

```TypeScript
function resetUsbDevice(pipe: USBDevicePipe): boolean
```

����USB���衣

> **˵����**
>
> ���ӿڵ��ú�����ô�ǰ���õ����ú��滻�ӿڣ����ڵ���֮ǰȷ�����ҵ���ѽ�����

**起始版本：** 20

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | ����ȷ�����ߺź��豸��ַ����Ҫ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)��ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true��ʾ�����豸�ɹ���false��ʾ�����豸ʧ�ܡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [14400001](../../errorcode-universal.md#14400001-Access) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../../errorcode-universal.md#14400004-Service) | Service exception. Possible causes: 1. No accessory is plugged in. |
| [14400008](../../errorcode-universal.md#14400008-No) | No such device(it may have been disconnected) |
| [14400010](../../errorcode-universal.md#14400010-Other) | Other USB error. Possible causes:<br/><br/>1.Unrecognized discard error code. |
| [14400013](../../errorcode-universal.md#14400013-The) | The USBDevicePipe validity check failed. Possible causes:<br/><br/>1.The input parameters fail the validation check.<br/><br/>2.The call chain used to obtain the input parameters is not reasonable. |

**示例：**

```TypeScript
function resetUsbDevice() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.error(`device list is empty`);
    return;
  }

  usbManager.requestRight(devicesList?.[0]?.name);
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(devicesList?.[0]);
  try {
    let ret: boolean = usbManager.resetUsbDevice(devicepipe);
    console.info(`resetUsbDevice  = ${ret}`);
  } catch (err) {
    console.error(`resetUsbDevice failed: ` + err);
  }
}

```

