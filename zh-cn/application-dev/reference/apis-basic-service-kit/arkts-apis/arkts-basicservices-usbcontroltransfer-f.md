# usbControlTransfer

## usbControlTransfer

```TypeScript
function usbControlTransfer(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: number): Promise<number>
```

控制传输。使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定设备，需要调用[usbManager.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)获取。 |
| requestparam | USBDeviceRequestParams | 是 | 控制传输参数，按需设置参数，参数传参类型请参考USB协议。 |
| timeout | number | 否 | 超时时间（单位：毫秒），可选参数，指定时间内等待控制传输完成，若在指定时间内传输完成则正常返回，否则返回超时；默认为0时无限等待直到传输完成。用户按需选择。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，获取传输或接收到的数据块大小。失败返回其他错误码如下：- -1：驱动异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.<br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
let param: usbManager.USBDeviceRequestParams = {
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
  usbManager.closePipe(devicepipe);
}

```

