# usbControlTransfer

## usbControlTransfer

```TypeScript
function usbControlTransfer(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: number): Promise<number>
```

���ƴ��䡣ʹ��Promise�첽�ص���

**起始版本：** 12

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | ����ȷ���豸����Ҫ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)��ȡ�� |
| requestparam | USBDeviceRequestParams | 是 | ���ƴ���������������ò�������������������ο�USBЭ�顣 |
| timeout | number | 否 | ��ʱʱ�䣨��λ�����룩����ѡ������ָ��ʱ���ڵȴ����ƴ�����ɣ�����ָ��ʱ���ڴ���������������أ����򷵻س�ʱ��Ĭ��Ϊ0ʱ���޵ȴ�ֱ��������ɡ��û�����ѡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󣬻�ȡ�������յ������ݿ��С��ʧ�ܷ����������������£�<br/><br/>- -1�������쳣�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

**示例：**

```TypeScript
class PARA {
  bmRequestType: number = 0
  bRequest: number = 0
  wValue: number = 0
  wIndex: number = 0
  wLength: number = 0
  data: Uint8Array = new Uint8Array()
}

let param: PARA = {
  bmRequestType: 0x80,
  bRequest: 0x06,

  wValue:0x01 << 8 | 0,
  wIndex: 0,
  wLength: 18,
  data: new Uint8Array(18)
};

function usbControlTransfer() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  usbManager.requestRight(devicesList?.[0]?.name);
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(devicesList?.[0]);
  usbManager.usbControlTransfer(devicepipe, param).then((ret: number) => {
  console.info(`usbControlTransfer = ${ret}`);
  })
}

```

