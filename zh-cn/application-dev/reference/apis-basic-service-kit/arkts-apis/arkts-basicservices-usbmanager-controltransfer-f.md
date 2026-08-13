# controlTransfer

## controlTransfer

```TypeScript
function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise<number>
```

控制传输。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** [usbControlTransfer](arkts-basicservices-usbmanager-usbcontroltransfer-f.md#usbControlTransfer)(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: int)

<!--Device-usbManager-function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise<number>--><!--Device-usbManager-function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise<number>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定设备，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice)获取。 |
| controlparam | USBControlParams | 是 | 控制传输参数，按需设置参数，参数传参类型请参考USB协议。 |
| timeout | number | 否 | 超时时间（单位：毫秒），可选参数，指定时间内等待控制传输完成，若在指定时间内传输完成则正常返回，否则返回超时；默认为0时无限等待直到传输完成。用户按需选择。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，获取传输或接收到的数据块大小。失败返回其他错误码如下： |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |

## 示例

```TypeScript
let param: usbManager.USBControlParams = {
  request: 0x06,
  reqType: 0x80,
  target: 0,
  value: 0x01 << 8 | 0,
  index: 0,
  data: new Uint8Array(18)
};

async function controlTransfer() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let rightResult = await usbManager.requestRight(devicesList?.[0]?.name);
  if (!rightResult) {
    console.error(`request right failed`);
    return;
  }
  let devicePipe: usbManager.USBDevicePipe = usbManager.connectDevice(devicesList?.[0]);
  if (devicePipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  usbManager.controlTransfer(devicePipe, param).then((ret: number) => {
    console.info(`controlTransfer = ${ret}`);
  }).catch((error) => {
    console.error(`Failed to transfer. Code: ${error.code}, message: ${error.message}`);
  }).finally(() => {
    usbManager.closePipe(devicePipe);
  });
}
```

