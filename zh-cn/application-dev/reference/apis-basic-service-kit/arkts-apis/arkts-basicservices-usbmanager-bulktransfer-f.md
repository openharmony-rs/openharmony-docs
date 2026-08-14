# bulkTransfer

## bulkTransfer

```TypeScript
function bulkTransfer(
    pipe: USBDevicePipe,
    endpoint: USBEndpoint,
    buffer: Uint8Array,
    timeout?: int
  ): Promise<int>
```

批量传输。使用Promise异步回调。 > **说明：** > > 单次批量传输的传输数据总量（包括pipe、endpoint、buffer、timeout）请控制在200KB以下，数据总量过大会导致传输失败返回-1。 > > 在调用接口前需要通过 > [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface) > claim通信接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-function bulkTransfer(    pipe: USBDevicePipe,    endpoint: USBEndpoint,    buffer: Uint8Array,    timeout?: int  ): Promise<int>--><!--Device-usbManager-function bulkTransfer(    pipe: USBDevicePipe,    endpoint: USBEndpoint,    buffer: Uint8Array,    timeout?: int  ): Promise<int>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定设备，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice)获取。 |
| endpoint | USBEndpoint | 是 | 用于确定传输的端口，需要调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices)获取设备信息列表以及endpoint， address用于确定端点地址，direction用于确定端点的方向，interfaceId用于确定所属接口，当前其他属性不做处理。 |
| buffer | Uint8Array | 是 | 用于写入或读取数据的缓冲区。 |
| timeout | int | 否 | 超时时间（单位：毫秒），可选参数，指定时间内等待批量传输完成，若在指定时间内传输完成则正常返回，否则返回超时；默认为0时无限等待直到传输完成。用户按需选择。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，获取传输或接收到的数据块大小。失败返回其他错误码如下： |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## 示例

以下示例代码只是调用bulkTransfer接口的必要流程，实际调用时，设备开发者需要遵循目标USB设备的协议规范进行调用，具体协议要求请参考设备的技术文档，确保数据的正确传输和设备的兼容性。

```TypeScript
// usbManager.getDevices 接口返回数据集合，取其中一个设备对象，并获取权限。
// 把获取到的设备对象作为参数传入usbManager.connectDevice；当usbManager.connectDevice接口成功返回之后；
// 才可以调用第三个接口usbManager.claimInterface。当usbManager.claimInterface 调用成功以后,再调用该接口。
async function bulkTransfer() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  await usbManager.requestRight(device.name);
  if (!usbManager.hasRight(device.name)) {
    console.error(`request right fail`);
    return;
  }
  let devicePipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  if (devicePipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  for (let i = 0; i < device.configs?.[0]?.interfaces.length; i++) {
    if (device.configs?.[0]?.interfaces?.[i]?.endpoints?.[0]?.attributes == 2) {
      let endpoint: usbManager.USBEndpoint = device.configs?.[0]?.interfaces?.[i]?.endpoints?.[0];
      let interfaces: usbManager.USBInterface = device.configs?.[0]?.interfaces?.[i];
      let ret: int = usbManager.claimInterface(devicePipe, interfaces);
      if (ret !== 0) {
        console.error(`claim interface failed`);
        continue;
      }
      let buffer = new Uint8Array(128);
      usbManager.bulkTransfer(devicePipe, endpoint, buffer).then((ret: int) => {
        console.info(`bulkTransfer = ${ret}`);
        let relIntfRet: int = usbManager.releaseInterface(devicePipe, interfaces);
        console.info(`releaseInterface = ${relIntfRet}`);
        if (i === device.configs?.[0]?.interfaces.length - 1) {
          usbManager.closePipe(devicePipe);
        }
      }).catch((error) => {
        console.error(`Failed to transfer. Code: ${error.code}, message: ${error.message}`);
      });
    }
  }
}
```

