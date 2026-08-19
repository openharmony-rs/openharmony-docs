# usbControlTransfer

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## usbControlTransfer

```TypeScript
function usbControlTransfer(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: int): Promise<int>
```

控制传输。调用成功后完成控制命令的传输，返回传输或接收到的数据块大小。适用于需要与USB设备进行控制命令交互的场景，如获取设备描述符、设置设备地址、发送厂商自定义命令、配置HID设备特性等。使用Promise异步回调。

**起始版本：** 23

<!--Device-usbManager-function usbControlTransfer(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: int): Promise<int>--><!--Device-usbManager-function usbControlTransfer(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: int): Promise<int>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线地址和设备地址，需要调用[connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)获取。 |
| requestparam | [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md) | 是 | 控制传输参数，包含bmRequestType、bRequest、wValue、wIndex、wLength、data等字段，参数传参 类型请参考USB协议规范，根据具体设备和控制请求类型设置。 |
| timeout | int | 否 | 超时时间（单位：毫秒），可选参数，指定时间内等待控制传输完成，若在指定时间内传输完成则正常返回，否则返回超时；默认值为0，表示无限等待直到传输完成。 传入负数时抛出参数错误异常。用户按需选择。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，获取传输或接收到的数据块大小。失败返回其他错误码如下： <br>- -1：驱动异常。可能原因：1、设备连接不稳定或已断开；2、USB驱动加载失败；3、内核USB模块异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例**

```TypeScript
// 控制传输参数：根据USB协议规范、设备描述符或设备规格文档设置各字段值
// bmRequestType：请求控制类型，常见取值示例：0x00（标准请求，主机向设备）、0x20（类请求，主机向设备）、0x40（厂商请求，主机向设备）、0x80（标准请求，设备向主机）
// bRequest：具体控制请求命令（如获取描述符、设置地址等）
// wValue：请求参数内容
// wIndex：请求参数的索引值
// wLength：数据长度
// data：用于写入或读取的缓冲区
let param: usbManager.USBDeviceRequestParams = {
  bmRequestType: 0x80,
  bRequest: 0x06,
  wValue: 0x01 << 8 | 0,
  wIndex: 0,
  wLength: 18,
  data: new Uint8Array(18)
};

async function usbControlTransfer() {
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
  usbManager.usbControlTransfer(devicePipe, param).then((ret: int) => {
    console.info(`usbControlTransfer = ${ret}`);
  }).catch((error) => {
    console.error(`usbControlTransfer failed: ${error.code}, message: ${error.message}`);
  }).finally(() => {
    usbManager.closePipe(devicePipe);
  });
}
```

